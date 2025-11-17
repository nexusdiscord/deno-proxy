# Deno Serverless Proxy

Serverless proxy untuk Deno Deploy yang memungkinkan Anda mem-proxy request ke URL manapun.

## 🚀 Deploy ke Deno Deploy

### Cara 1: Deploy via Dashboard

1. Buka [Deno Deploy Dashboard](https://dash.deno.com/new)
2. Pilih "Deploy from GitHub" atau "Deploy from local"
3. Pilih repository ini atau upload file `main.ts`
4. Deploy akan otomatis berjalan

### Cara 2: Deploy via CLI

```bash
# Install Deno Deploy CLI (deployctl)
deno install --allow-read --allow-write --allow-env --allow-net --allow-run --no-check -r -f https://deno.land/x/deploy/deployctl.ts

# Deploy ke Deno Deploy
deployctl deploy --project=nama-project-anda main.ts
```

## 📖 Cara Penggunaan

Setelah deploy, Anda bisa mengakses proxy dengan format:

```
https://nama-project-anda.deno.dev/[URL_TARGET]
```

### Contoh Penggunaan

**Proxy ke website:**
```
https://quiet-wasp-17.deno.dev/https://example.com
```

**Proxy ke API:**
```
https://quiet-wasp-17.deno.dev/https://api.github.com/users/denoland
```

**Dengan query parameters:**
```
https://quiet-wasp-17.deno.dev/https://api.example.com/data?param=value&key=123
```

## ✨ Fitur

- ✅ Support semua HTTP methods (GET, POST, PUT, DELETE, dll)
- ✅ Meneruskan headers dan body request
- ✅ Support query parameters
- ✅ CORS enabled secara default
- ✅ Error handling yang baik
- ✅ Halaman info di root URL

## 🧪 Testing Lokal

Jalankan server di local untuk testing:

```bash
# Dengan Deno task
deno task dev

# Atau langsung
deno run --allow-net --allow-env main.ts
```

Kemudian akses:
```
http://localhost:8000/https://example.com
```

## 🔒 Catatan Keamanan

Proxy ini bersifat open dan dapat mengakses URL apapun. Untuk production:

1. Pertimbangkan untuk menambahkan authentication
2. Tambahkan rate limiting
3. Buat whitelist domain yang diizinkan
4. Monitor penggunaan untuk mencegah abuse

## 📝 Contoh Request dengan curl

**GET Request:**
```bash
curl https://quiet-wasp-17.deno.dev/https://api.github.com/zen
```

**POST Request:**
```bash
curl -X POST https://quiet-wasp-17.deno.dev/https://httpbin.org/post \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}'
```

## 🛠️ Kustomisasi

Anda bisa memodifikasi `main.ts` untuk:
- Menambahkan authentication
- Membatasi domain yang diizinkan
- Menambahkan caching
- Logging request
- Rate limiting

## 📄 License

MIT
