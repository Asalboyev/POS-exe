# Sozlash — bir marta bajariladi

Build mashinasi kodni GitLab'dan o'qishi kerak, shuning uchun **har bir
ilova uchun bittadan kalit** qo'yiladi. Jami to'rtta qiymat.

**Kalitlarni o'zingiz yaratasiz.** Men ularni ko'rmayman va hech qayerga
yozmayman.

## 1. GitLab'da kalit yasash (har ikki repo uchun)

Quyidagini **ikki marta** bajaring — bir marta `Aiba-pos`, bir marta
`diet-aiba-pos` uchun:

1. GitLab → kerakli proyekt →
   **Settings → Repository → Deploy tokens → Add token**
2. Name: `github-build`
3. Scopes: **faqat `read_repository`** (boshqasini belgilamang)
4. **Create** → chiqqan **username** va **password** ni nusxa oling
   (password bir marta ko'rsatiladi, keyin qayta ko'rsatilmaydi)

Nega deploy token: u faqat O'QIY oladi va faqat SHU proyektga tegishli.
Shaxsiy hisob tokeni qo'yilsa, GitHub build mashinasi butun
GitLab'ingizga kira olardi.

## 2. GitHub'ga yozish

`github.com/Asalboyev/POS-exe` →
**Settings → Secrets and variables → Actions → New repository secret**

| Secret nomi | Qiymati |
|---|---|
| `GITLAB_USER` | `Aiba-pos` deploy token **username** |
| `GITLAB_TOKEN` | `Aiba-pos` deploy token **password** |
| `GITLAB_USER_DIET` | `diet-aiba-pos` deploy token **username** |
| `GITLAB_TOKEN_DIET` | `diet-aiba-pos` deploy token **password** |

Kalit qo'yilmasa, o'sha ilova build'i «kalit sozlanmagan» deb to'xtaydi —
ikkinchisi baribir yig'iladi.

## 2b. GitLab quvuri (ixtiyoriy — tezkor signal)

Yuqoridagi to'rtta kalit yetarli: GitHub GitLab'ni **o'zi kuzatadi** va
o'zgarishni 15 daqiqada payqaydi.

Build **darhol** ketishini xohlasangiz, GitLab tomonda ham bitta
o'zgaruvchi qo'yiladi: proyekt → **Settings → CI/CD → Variables** →
`GITHUB_DISPATCH_TOKEN` (masked), qiymati — `repo` huquqli GitHub tokeni.
Qo'yilmasa quvurdagi `windows-build` ishi ogohlantirish yozib yashil
o'tadi, build esa kuzatuv orqali baribir bo'ladi.

## 3. Tekshirish

1. **Actions → Build → Run workflow**.
2. AIBA POS hozircha `test/markirovka-skaner` shoxida — u `main` ga
   qo'shilmaguncha «AIBA POS — GitLab branch» maydoniga shu nomni yozing.
   DIET-AIBA POS uchun `main` qoladi.
3. 10–15 daqiqada **Releases** sahifasida ikkita `.exe` paydo bo'ladi.

## 4. Eski GitHub reponi yopish

Kod hozir `github.com/Asalboyev/new-aiba-pos-app` da ham turibdi. Yangi
oqim ishlaganiga ishonch hosil qilgach, o'sha reponi **private** qiling
yoki o'chiring — aks holda «kod GitHub'da turmasin» degan maqsad
bajarilmaydi. Buni o'zingiz qilasiz.
