# Tarmax Design Tokens

## Project Information

**Application Name:** Tarmax  
**Type:** Mobile Shopping Application  
**Description:** Aplikasi belanja kebutuhan kampus yang membantu mahasiswa mencari dan membeli produk kebutuhan akademik secara digital.

Design tokens ini digunakan sebagai standar visual agar desain Figma, prototype, dan implementasi aplikasi tetap konsisten.

---

# 1. Color Tokens

## Primary Colors

Warna utama yang digunakan untuk tombol, navigasi aktif, dan elemen interaksi.

| Token | Value |
|---|---|
| primary-50 | #EFF6FF |
| primary-100 | #DBEAFE |
| primary-300 | #93C5FD |
| primary-500 | #3B82F6 |
| primary-600 | #2563EB |
| primary-700 | #1D4ED8 |

---

## Semantic Colors

Digunakan untuk status dan informasi sistem.

| Token | Value | Usage |
|---|---|---|
| success-500 | #16A34A | Status tersedia / berhasil |
| warning-500 | #F59E0B | Status menunggu |
| error-500 | #DC2626 | Status gagal |
| info-500 | #0EA5E9 | Informasi tambahan |

---

## Neutral Colors

Digunakan untuk background, teks, dan elemen pendukung.

| Token | Value |
|---|---|
| neutral-50 | #F9FAFB |
| neutral-100 | #F3F4F6 |
| neutral-300 | #D1D5DB |
| neutral-500 | #6B7280 |
| neutral-600 | #374151 |
| neutral-700 | #111827 |

---

# 2. Typography Tokens

Font utama:

```
Inter
```

| Token | Size | Weight | Usage |
|---|---|---|---|
| H1 | 32px | Bold | Selamat Datang Di Tarmax |
| H2 | 20px | Bold | Belanja kebutuhan kampus |
| H3 | 16px | Bold | Buku Pemrograman Web Dasar |
| Body | 14px | Regular | Temukan Kebutuhan Mahasiswa Dalam Satu Aplikasi |
| Caption | 12px | Regular | Tersedia • 5 Menit Lalu |
| Button | 14px | Medium | Pesan Dulu |

---

# 3. Spacing Tokens

Menggunakan sistem spacing berbasis 4px.

| Token | Value |
|---|---|
| space-4 | 4px |
| space-8 | 8px |
| space-16 | 16px |
| space-24 | 24px |
| space-32 | 32px |
| space-48 | 48px |

---

# 4. Component Tokens

## Button Primary

Component:

```
Button / Primary
```

Specification:

```
Text:
Pesan Sekarang

Height:
48px

Radius:
12px

Color:
primary-600
```

---

## Input Field

Component:

```
Input / Email-NIM
```

Content:

```
NIM ATAU EMAIL KAMPUS

2108561044@student.ac.id
```

Specification:

```
Height:
48px

Radius:
12px
```

---

## Search Bar

Component:

```
Search Bar
```

Content:

```
🔍 Cari Produk
```

Specification:

```
Height:
48px

Radius:
12px
```

---

## Product Card

Component:

```
Card / Product
```

Content:

```
Image Produk

Buku Kampus

Rp25.000

Kategori:
📚 Buku
```

Specification:

```
Radius:
16px
```

---

## Category Card

Component:

```
Category / Product
```

Content:

```
📚 Buku
```

---

## Bottom Navigation

Component:

```
Navigation / Bottom Bar
```

Items:

```
🏠 Home

🛒 Cart

📦 Order

👤 Account
```

Specification:

```
Height:
72px

Active Color:
primary-600

Inactive Color:
neutral-500
```

---

# 5. Design Rules

## Do

- Gunakan warna dari Color Tokens.
- Gunakan typography sesuai hierarchy.
- Gunakan spacing berdasarkan sistem 4px.
- Gunakan component sebagai reusable component.

## Don't

- Jangan menggunakan warna di luar token.
- Jangan menggunakan spacing acak.
- Jangan membuat komponen tanpa dokumentasi.

---

# Version

```
Tarmax Design Tokens v1.0

High Fidelity Mockup & Design System Project
```
