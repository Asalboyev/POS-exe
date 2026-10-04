# AIBA POS — o'rnatuvchilar

Kassa dasturini Windows kompyuterga o'rnatish uchun.

**Bu repoda dastur kodi YO'Q va bo'lmaydi.** Bu yerda faqat o'rnatuvchini
yig'adigan bitta fayl turadi. Manba kod GitLab'da qoladi.

## Yuklab olish

**https://github.com/Asalboyev/POS-exe/releases/latest**

Havola hech qachon o'zgarmaydi — har build shu sahifani yangilaydi.

| Fayl | Kimga |
|---|---|
| `AIBA-POS-Setup-*.exe` | AIBA POS |
| `DIET-AIBA-POS-Setup-*.exe` | DIET-AIBA POS (DIET BISTRO) |

Ikkalasini bitta kompyuterga o'rnatsa ham bo'ladi — ular bir-biriga xalaqit
bermaydi: alohida papka, alohida yorliq, alohida sozlama.

## O'rnatish

1. Kerakli `.exe` ni yuklab oling.
2. Ikki marta bosing.
3. Windows **«noma'lum nashriyot»** deb ogohlantirsa —
   **Batafsil → Baribir ishga tushirish**. Bu normal: o'rnatuvchi Microsoft
   sertifikati bilan imzolanmagan.
4. O'rnatilgach ish stolida yorliq paydo bo'ladi.

Birinchi ishga tushirishda server manzili va terminal kodi so'raladi —
ularni menejeringiz beradi.

## Yangi versiya chiqarish

**Hech narsa qilish shart emas.** GitLab'dagi `main` ga push qilsangiz, bu
yerdagi kuzatuvchi uni **15 daqiqada** payqaydi va o'rnatuvchilarni o'zi
yig'adi. Yuqoridagi havola o'zgarmaydi — shunchaki yangi fayl paydo bo'ladi.

Darhol kerak bo'lsa: **Actions → Build → Run workflow** — 10–15 daqiqa.

Qanday ishlaydi: har 15 daqiqada ishlaydigan `check` ishi GitLab'dagi `main`
ning SHA sini o'qiydi va oxirgi yig'ilgani bilan solishtiradi. Teng bo'lsa ish
20 soniyada tugaydi (Windows mashina umuman band qilinmaydi), farq bo'lsa
build ketadi. Oxirgi yig'ilgan SHA `.state/built.json` da turadi.

Birinchi marta ishlatishdan oldin kalitlarni sozlash kerak:
[SOZLASH.md](SOZLASH.md).
