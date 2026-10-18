# mekanSAL takvim: Supabase + Vercel kurulumu (ücretsiz planlarla)

Klasördeki dosyalar:
- `index.html`: sitenin kendisi (tek dosya)
- `supabase.sql`: veritabanı ve güvenlik kuralları
- `supabase-guncelleme.sql`: yalnızca `supabase.sql`i daha önce çalıştırdıysanız gerekli (bekleyen talep göstergesi)

## 1) Supabase (veritabanı + yönetici girişi)
1. supabase.com → hesap aç → **New project** (ücretsiz plan). Bölge olarak Frankfurt gibi yakın bir yer seç, bir veritabanı şifresi belirle.
2. `supabase.sql` dosyasının en altındaki `BURAYA_ADMIN_EPOSTASI` yerine **kendi e-postanı** yaz.
3. Sol menü **SQL Editor** → New query → dosyanın tamamını yapıştır → **Run**.
4. **Authentication → Users → Add user**: aynı e-posta ve **güçlü bir şifre** (Auto Confirm User açık). Bu, yönetici girişin olacak.
5. **Authentication → Sign In / Providers**: "Allow new users to sign up" seçeneğini **kapat**. Böylece kimse kendine hesap açamaz.
6. **Project Settings → API**: `Project URL` ve `anon public` anahtarını kopyala.
7. `index.html` dosyasının en üstündeki `SB_URL` ve `SB_KEY` satırlarına yapıştır.
   (anon anahtarı herkese açık olacak şekilde tasarlanmıştır. Güvenliği SQL'deki kurallar sağlar.)

## 2) Vercel (yayın)
**Yol A, GitHub ile:** `vercel-site` klasörünü yeni bir GitHub deposuna yükle → vercel.com → **Add New → Project** → depoyu seç → **Deploy**. Başka ayar gerekmez (statik site).
**Yol B, komut satırıyla:** klasörün içinde `npx vercel` çalıştır, soruları Enter ile geç.

Sonra Vercel'in verdiği adresi aç. İstersen **Settings → Domains** bölümünden kendi alan adını bağlayabilirsin.

## 3) Deneme listesi
- Gizli sekmede siteyi aç → boş güne tıkla → talep gönder (giriş gerekmez).
- Sağ alttaki "Yönetici girişi" ile e-posta + şifreyle gir → Talepler panelinde talebi gör → düzenle → Onayla.
- Gizli sekmede sayfayı yenile → etkinlik takvimde görünmeli (telefon/ad görünmemeli).

## Bilmeniz gerekenler
- Ücretsiz Supabase projeleri uzun süre kullanılmazsa duraklatılabilir. Dashboard'dan tek tıkla devam ettirilir.
- Talep formu herkese açık olduğu için sahte/spam talep gelebilir. Gerekirse reddedersin. Sorun olursa captcha ekleyebiliriz.
- Şifreni sayfada değil Supabase'de tuttuğun için artık gerçek korumalı: yönetici verilerine yalnızca bu girişle ulaşılır.
