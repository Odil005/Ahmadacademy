# Telegram botni ishga tushirish

Bot kodi tayyor. Haqiqiy Telegram bilan ulash uchun quyidagi maxfiy qiymatlar va ishlab turgan Vercel domeni kerak.

## 1. BotFather'da bot yaratish

1. Telegram'da `@BotFather`ni oching.
2. `/newbot` yuboring.
3. Bot nomini kiriting, masalan `UNICRM Akhmad Academy`.
4. Username kiriting. U `bot` bilan tugashi kerak, masalan `unicrm_akhmad_bot`.
5. BotFather bergan tokenni hech kimga yubormang va GitHub'ga yozmang.

Tavsiya etilgan qo'shimcha sozlamalar:

- `/setuserpic` — akademiya logotipi;
- `/setabouttext` — `Akhmad Academy o'quv markazi yordamchisi`;
- `/setdescription` — davomat, to'lov, jadval va xabarlar haqida qisqa matn;
- `/setjoingroups` → `Disable` — bot faqat shaxsiy chatda ishlaydi.

## 2. Vercel maxfiy sozlamalari

Vercel → Project → Settings → Environment Variables bo'limida Production, Preview va Development uchun kiriting:

- `TELEGRAM_BOT_TOKEN` — BotFather tokeni;
- `TELEGRAM_WEBHOOK_SECRET` — 32+ belgili tasodifiy qiymat, faqat harf, raqam, `_` va `-`;
- `CRON_SECRET` — kamida 16 belgili boshqa tasodifiy qiymat;
- `APP_BASE_URL` — production domen, masalan `https://unicrm.vercel.app`;
- `SUPABASE_URL` va `SUPABASE_SERVICE_ROLE_KEY` — Supabase server qiymatlari.

Maxfiy qiymatlarni `.env`, skrinshot, chat yoki GitHub orqali tarqatmang.

## 3. Baza va deploy

1. Yangi Supabase migratsiyalarini production bazaga qo'llang.
2. Vercel'ga qayta deploy qiling.
3. CRM'ga direktor yoki administrator sifatida kiring.
4. Sozlamalar → Telegram / SMS bo'limini oching.
5. `Webhook o'rnatish` tugmasini bosing.
6. Holat yashil `Bot va webhook ishlayapti` bo'lishini kuting.

`vercel.json` avtomatik eslatmalarni UTC vaqtida ishga tushiradi. Vercel Hobby rejasida cron vazifalari faqat kuniga bir marta bajarilishi mumkin; shu sababli navbatdagi xabarlar belgilangan kunlik jo'natishda yetkaziladi.

## 4. Sinov

1. CRM'da `Tezkor Telegram ID yaratish` bo'limidan ota-ona yoki xodim uchun havola yarating.
2. Havolani faqat o'sha odamga yuboring. Havola bir martalik va muddati cheklangan.
3. Foydalanuvchi Telegram'da `Start`ni bosadi.
4. Ota-onada to'lov, davomat, o'qituvchiga yozish va AI yordamchi menyularini tekshiring.
5. O'qituvchida bugungi darslar va ota-ona xabarlarini tekshiring.
6. CRM → Sozlamalar → Telegram / SMS → Test xabari orqali real xabar yuboring.

## Xavfsizlik

- Bot faqat shaxsiy Telegram chatida ishlaydi.
- Telefon orqali ulanishda foydalanuvchi faqat o'z contact raqamini yubora oladi.
- O'quvchi UUID sini `/start` havolasiga yozib ulanish yopilgan.
- Ulanish tokenlari bazada SHA-256 hash ko'rinishida saqlanadi.
- Webhook faqat Telegram yuborgan maxfiy header bilan ishlaydi.
- Cron endpointlari `CRON_SECRET` bilan himoyalangan.
