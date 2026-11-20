# Kiến trúc web + app cho Lộ Trình 90 (nghiên cứu, 20/11/2026)

Ký hiệu: **[Nguồn]** = lấy từ tài liệu chính thức/trang tra cứu (link cuối bài). **[Suy luận]** = đánh giá của Claude, chưa kiểm chứng bằng code thật.

## Kết luận ngắn

**Khuyến nghị: Phương án A+ — một app Expo (React Native + Expo Router) chạy cả iOS, Android và web, dùng Supabase làm backend, không viết BE riêng.** Đặt trong repo có sẵn cấu trúc `apps/` + `packages/` (npm workspaces) để sau này thêm Next.js khi thật sự cần.

Lý do chính [Suy luận]:
1. Đây là app học cá nhân, phần lớn màn hình nằm sau đăng nhập, nên SEO gần như không quan trọng. Lợi thế lớn nhất của Next.js (SEO, SSR) vì vậy ít giá trị.
2. Làm một mình: A viết giao diện **một lần**; B phải viết giao diện **hai lần** (DOM cho Next.js, View/Text cho React Native). Đó là chi phí lớn nhất.
3. Các tính năng "ăn tiền" của app (nhắc ôn bài, ghi âm, phát audio) đều là tính năng native. Thông báo đặt lịch chỉ chạy trên iOS/Android, không chạy trên web, ở cả A lẫn B [Nguồn: expo-notifications chỉ hỗ trợ android, ios].
4. Supabase đã đủ làm backend (Auth, Postgres + RLS, Storage cho file ghi âm, Edge Functions). BE riêng chỉ thêm việc deploy và bảo trì.

**Khi nào nên chọn B (monorepo Next.js + Expo)**: nếu grace muốn **học Next.js** như một mục tiêu riêng, hoặc định làm trang công khai cần SEO (blog, landing, chia sẻ bài học). Khi đó vẫn **không cần BE riêng**, Supabase vẫn là backend.

## Ba phương án

- **A. Expo cho tất cả**: một codebase Expo Router, xuất web bằng `expo export` (tĩnh) lên Vercel/EAS Hosting.
- **B. Monorepo Next.js (web) + Expo (app) + BE riêng** (Node/Nest...).
- **C. Monorepo Next.js + Expo, Supabase làm backend** (phương án coordinator nghiêng về).

## So sánh

| Tiêu chí | A. Expo tất cả + Supabase | B. Next + Expo + BE riêng | C. Next + Expo + Supabase |
|---|---|---|---|
| SEO / hiệu năng web | Khá. Có SSG ổn định; SSR còn experimental [Nguồn]. Bundle react-native-web nặng hơn [Suy luận] | Tốt nhất (Next.js) | Tốt nhất (Next.js) |
| Trải nghiệm app (nhắc ôn, ghi âm, audio) | Như nhau: expo-audio ghi/phát trên android, ios, web, có phát nền [Nguồn]; thông báo lịch chỉ native [Nguồn] | Như nhau | Như nhau |
| Code dùng chung | ~80–90%: cả UI lẫn logic [Suy luận] | ~30–40%: types, logic chấm điểm/SRS, API client. UI viết 2 lần [Suy luận] | ~30–40%, hoặc ~60% nếu dùng Solito/Tamagui (thêm độ khó) [Suy luận] |
| Cấu hình monorepo | Không bắt buộc | Nặng nhất: 3 app, 2 bundler (Metro + Turbopack), React versions phải khớp | Trung bình: 2 app, 2 bundler |
| Chi phí | 0đ (EAS free + Supabase free + Vercel Hobby). iOS lên store cần Apple Developer 99 USD/năm [Suy luận, giá Apple quen thuộc] | Như A + thêm chỗ chạy BE (free tier thường ngủ/giới hạn) | Như A |
| Thời gian dựng bản đầu (tối/cuối tuần) | ~2–3 tuần [Suy luận] | ~6–8 tuần [Suy luận] | ~4–5 tuần [Suy luận] |
| Rủi ro một người làm | Thấp. Rủi ro: UI web "không giống web" lắm, SSR chưa ổn định | Cao: nhiều thứ phải giữ, dễ bỏ dở giữa chừng | Trung bình: hai UI dễ lệch nhau |
| Giá trị học | Học RN/Expo + Supabase | Học nhiều nhất nhưng loãng | Học Next.js + RN + Supabase |

## Thông tin kiểm chứng [Nguồn]

- **Expo Router v55 (02/03/2026)**: web hỗ trợ static rendering (SSG), API routes, middleware; SSR là experimental (`unstable_useServerRendering`); deploy được lên Vercel, Netlify, Cloudflare, EAS Hosting.
- **Solito 5**: bỏ react-native-web, web dùng thẳng Next.js, native dùng file `.native.tsx`. Nghĩa là muốn chia sẻ UI vẫn phải viết hai bản cho web và native. Starter mẫu: Next.js 16 + Expo SDK 54.
- **expo-audio**: android, ios, web; ghi âm trên web cần HTTPS, Chrome tạo WebM thiếu thời lượng, nên dùng polyfill.
- **expo-notifications**: chỉ android, ios. Push từ xa cần development build (Expo Go Android không có từ SDK 53); thông báo cục bộ vẫn chạy trong Expo Go.
- **EAS free**: 15 build Android + 15 build iOS/tháng, hàng đợi ưu tiên thấp, EAS Update 1.000 MAU, Hosting 100.000 request/tháng.
- **Supabase free**: 2 project, DB 500 MB, Storage 1 GB, băng thông 5 GB/tháng, 50.000 MAU, 500.000 lần gọi Edge Function/tháng, **tạm dừng sau 1 tuần không hoạt động**.

## Lưu ý riêng cho app này [Suy luận]

- **Supabase tự tạm dừng sau 7 ngày không dùng**: học hằng ngày thì không sao, nhưng nghỉ Tết (tuần 11–12) có thể bị dừng. Cách đỡ: một GitHub Action gọi nhẹ API mỗi 3 ngày, hoặc chấp nhận bấm "Restore" khi quay lại.
- **Storage 1 GB**: ghi âm nói nên nén (AAC/m4a, ~1 MB/phút) và chỉ giữ 30 bản gần nhất, nếu không vài tháng là đầy.
- **Offline**: giữ cách hiện tại (localStorage → trên app dùng SQLite/MMKV), đồng bộ lên Supabase khi có mạng. Nội dung bài học (JSON + audio ngắn) đóng gói sẵn trong app.
- **TTS**: `expo-speech` dùng giọng máy, không cần mạng; web dùng Web Speech API. Đủ cho luyện từ vựng, chưa đủ cho nghe TOEIC (cần file audio thật).
- **Nhắc ôn trên web**: chỉ có Web Push, và trên iPhone/iPad phải "Thêm vào màn hình chính" mới nhận được. Vì vậy nếu grace học nhiều trên iPad, **app native mới là chỗ nhắc bài đáng tin**.

## Bước đầu tiên (nếu chọn A+)

1. Tạo `apps/mobile` bằng `create-expo-app` (Expo Router, TypeScript), thêm npm workspaces ở gốc repo, giữ `web/` tĩnh hiện tại chạy song song cho đến khi bản mới thay được.
2. Tách `packages/core`: types, dữ liệu bài học (JSON), logic chấm điểm và lịch SRS 1/3/7/14/30 (chuyển từ JS hiện có, viết test).
3. Tạo 1 project Supabase: bảng `profiles`, `progress`, `reviews`, `mistakes`, `recordings` + RLS theo `auth.uid()`; đăng nhập OTP email.
4. Làm 2 màn trước: Hôm nay + Nghe chép (theo thiết kế Stitch đã có), chạy trên web (Vercel) và điện thoại (Expo Go).
5. Sau đó: thông báo nhắc ôn (local notification, cần development build), ghi âm nói, build Android qua EAS.

## grace cần quyết định

1. **Mục tiêu học Next.js có quan trọng không?** Có → chọn C (không BE riêng). Không → A+.
2. **Có cần trang công khai/SEO không?** (landing, chia sẻ bài). Nếu chỉ dùng cho mình → A+.
3. **Có lên App Store không?** Nếu chỉ dùng trên máy mình: Android cài APK miễn phí; iPhone/iPad không có tài khoản trả phí thì phải cài lại mỗi 7 ngày [Suy luận]. Lên store iOS tốn 99 USD/năm.
4. **Thiết bị học chính** (iPad hay điện thoại hay máy tính) để ưu tiên nền tảng làm trước.

## Nguồn

- Expo Router v55: https://expo.dev/blog/expo-router-v55-more-native-navigation-more-powerful-web
- Solito 5: https://solito.dev/v5
- expo-audio: https://docs.expo.dev/versions/v57.0.0/sdk/audio
- expo-notifications: https://docs.expo.dev/versions/latest/sdk/notifications
- Bảng giá EAS: https://expo.dev/pricing
- Giới hạn Supabase free (trang tổng hợp bên thứ ba, nên đối chiếu supabase.com/pricing): https://automationatlas.io/answers/supabase-free-tier-limits-2026/
