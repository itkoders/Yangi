# TILAKINO — Render deploy

## Ishga tushirish

- Runtime: Python
- Build: `pip install -r requirements.txt`
- Start: `gunicorn main:app --bind 0.0.0.0:$PORT --workers 1 --threads 4 --timeout 60`
- Health: `/health`

## Render Environment Variables

- `TELEGRAM_BOT_TOKEN` — BotFather bergan yangi token (maxfiy; GitHubga yozmang).
- `ADMIN_ID` — admin Telegram ID (hozirgi qiymat: `6359925487`).
- `WEBHOOK_SECRET` — Render Blueprint avtomatik yaratadi; qo‘lda yaratilsa faqat A-Z, a-z, 0-9, `_`, `-` ishlating.
- `ENABLE_SCHEDULER` — `1`.
- `DATABASE_URL` — ixtiyoriy PostgreSQL ulanish manzili.

Render `RENDER_EXTERNAL_URL` qiymatini o‘zi beradi; bot webhook shu URL orqali ro‘yxatdan o‘tadi.

## Muhim eslatmalar

- Eski `main.py` ichida token ochiq saqlangan edi. Uni BotFather orqali bekor qiling va yangisini yarating. Git tarixidagi eski qiymat ham token bekor qilinmaguncha xavf tug‘diradi.
- `DATABASE_URL` berilmasa, bot SQLite ishlatadi. Render Free servisining fayl tizimi vaqtinchalik, shuning uchun qayta ishga tushish yoki deploydan keyin baza yo‘qolishi mumkin. Doimiy ma’lumot uchun tashqi PostgreSQL kerak.
- Render Free Web Service 15 daqiqa trafik bo‘lmasa uxlaydi; webhook so‘rovi kelganda qayta uyg‘onishi mumkin.
