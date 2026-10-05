<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d608b4d3-2042-4fc8-b862-ef3acc1c3348" />### 1. Login

POST /api/v1/login

Autentikasi: Tidak diperlukan

Request:
{
  "email": "mahasiswa@example.com",
  "password": "password123"
}

Response Success 200:
{
  "status": "success",
  "message": "Login berhasil",
  "data": {
    "token": "1|abc123token",
    "user": {
      "id": 1,
      "name": "Budi",
      "email": "mahasiswa@example.com",
      "role": "buyer"
    }
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Email atau password salah",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Data login tidak valid",
  "errors": {
    "email": ["Email wajib diisi"],


### 2. Logout

POST /api/v1/logout

Autentikasi: Bearer Token

Response Success 200:
{
  "status": "success",
  "message": "Logout berhasil",
  "data": null
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

### 3. Profil User

GET /api/v1/profile

Autentikasi: Bearer Token

Response Success 200:
{
  "status": "success",
  "message": "Profil berhasil diambil",
  "data": {
    "id": 1,
    "name": "Budi",
    "email": "mahasiswa@example.com",
    "phone": "081234567890",
    "role": "buyer"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

### 4. Menampilkan Semua Produk

GET /api/v1/products

Autentikasi: Bearer Token

Response Success 200:
{
  "status": "success",
  "message": "Daftar produk berhasil diambil",
  "data": [
  {
      "id": 1,
      "name": "Nasi Goreng",
      "price": 15000,
      "stock": 10,
      "category": "Makanan",
      "status": "active"
    },
    {
      "id": 2,
      "name": "Es Teh",
      "price": 5000,
      "stock": 20,
      "category": "Minuman",
      "status": "active"
    }
  ]
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}
    "password": ["Password wajib diisi"]
  }
}

### 5. Menampilkan Detail Produk

GET /api/v1/products/{id}

Autentikasi: Bearer Token

Response Success 200:
{
  "status": "success",
  "message": "Detail produk berhasil diambil",
  "data": {
    "id": 1,
    "seller_id": 2,
    "name": "Nasi Goreng",
    "description": "Nasi goreng spesial",
    "price": 15000,
    "stock": 10,
    "category": "Makanan",
    "status": "active"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Produk tidak ditemukan",
  "errors": {}
}

### 6. Menambahkan Produk

POST /api/v1/products

Autentikasi: Bearer Token

Role: Seller

Request:
{
  "name": "Nasi Goreng",
  "description": "Nasi goreng spesial",
  "price": 15000,
  "stock": 10,
  "category": "Makanan",
  "image": "nasi-goreng.jpg",
  "status": "active"
}

Response Success 201:
{
  "status": "success",
  "message": "Produk berhasil ditambahkan",
  "data": {
    "id": 1,
    "name": "Nasi Goreng",
    "price": 15000,
    "stock": 10,
    "status": "active"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin menambahkan produk",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Validasi gagal",
  "errors": {
    "name": ["Nama produk wajib diisi"],
    "price": ["Harga wajib diisi"],
    "stock": ["Stok wajib diisi"]
  }
}

### 7. Mengubah Produk

PUT /api/v1/products/{id}

Autentikasi: Bearer Token

Role: Seller pemilik produk

Request:
{
  "name": "Nasi Goreng Spesial",
  "description": "Nasi goreng dengan telur dan ayam",
  "price": 18000,
  "stock": 8,
  "category": "Makanan",
  "status": "active"
}

Response Success 200:
{
  "status": "success",
  "message": "Produk berhasil diperbarui",
  "data": {
    "id": 1,
    "name": "Nasi Goreng Spesial",
    "price": 18000,
    "stock": 8,
    "status": "active"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin mengubah produk",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Produk tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Validasi gagal",
  "errors": {
    "price": ["Harga harus lebih dari 0"],
    "stock": ["Stok tidak boleh negatif"]
  }
}

### 8. Menghapus Produk

DELETE /api/v1/products/{id}

Autentikasi: Bearer Token

Role: Seller pemilik produk

Response Success 200:
{
  "status": "success",
  "message": "Produk berhasil dihapus",
  "data": null
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin menghapus produk",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Produk tidak ditemukan",
  "errors": {}
}

### 9. Melihat Keranjang

GET /api/v1/cart

Autentikasi: Bearer Token

Role: Buyer

Response Success 200:
{
  "status": "success",
  "message": "Keranjang berhasil diambil",
  "data": {
    "items": [
      {
        "id": 1,
        "product_id": 2,
        "product_name": "Es Teh",
        "price": 5000,
        "quantity": 2,
        "subtotal": 10000
      }
    ],
    "total": 10000
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin mengakses keranjang",
  "errors": {}
}

### 10. Menambahkan Produk ke Keranjang

POST /api/v1/cart/items

Autentikasi: Bearer Token

Role: Buyer

Request:
{
  "product_id": 2,
  "quantity": 2
}

Response Success 201:
{
  "status": "success",
  "message": "Produk berhasil ditambahkan ke keranjang",
  "data": {
    "product_id": 2,
    "quantity": 2
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin menambahkan produk ke keranjang",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Produk tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Data keranjang tidak valid",
  "errors": {
    "product_id": ["Produk wajib dipilih"],
    "quantity": ["Jumlah minimal 1"]
  }
}

### 11. Mengubah Jumlah Produk di Keranjang

PATCH /api/v1/cart/items/{id}

Autentikasi: Bearer Token

Role: Buyer

Request:
{
  "quantity": 3
}

Response Success 200:
{
  "status": "success",
  "message": "Jumlah produk di keranjang berhasil diperbarui",
  "data": {
    "id": 1,
    "product_id": 2,
    "quantity": 3,
    "subtotal": 15000
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin mengubah keranjang ini",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Item keranjang tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Jumlah produk tidak valid",
  "errors": {
    "quantity": ["Jumlah minimal 1 dan tidak boleh melebihi stok"]
  }
}

### 12. Menghapus Produk dari Keranjang

DELETE /api/v1/cart/items/{id}

Autentikasi: Bearer Token

Role: Buyer

Response Success 200:
{
  "status": "success",
  "message": "Produk berhasil dihapus dari keranjang",
  "data": null
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin menghapus item keranjang ini",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Item keranjang tidak ditemukan",
  "errors": {}
}

### 13. Membuat Pesanan

POST /api/v1/orders

Autentikasi: Bearer Token

Role: Buyer

Request:
{
  "pickup_method": "pickup",
  "pickup_location": "Area Kampus UBBG",
  "notes": "Ambil pukul 12.00"
}

Response Success 201:
{
  "status": "success",
  "message": "Pesanan berhasil dibuat",
  "data": {
    "id": 10,
    "order_code": "ORD-20261005-001",
    "total_amount": 30000,
    "order_status": "pending"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin membuat pesanan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Pesanan gagal dibuat",
  "errors": {
    "cart": ["Keranjang masih kosong"],
    "pickup_method": ["Metode pengambilan wajib dipilih"]
  }
}

### 14. Melihat Daftar Pesanan

GET /api/v1/orders

Autentikasi: Bearer Token

Role: Buyer dan Seller

Response Success 200:
{
  "status": "success",
  "message": "Daftar pesanan berhasil diambil",
  "data": [
    {
      "id": 10,
      "order_code": "ORD-20261005-001",
      "total_amount": 30000,
      "order_status": "pending"
    },
    {
      "id": 11,
      "order_code": "ORD-20261005-002",
      "total_amount": 25000,
      "order_status": "processing"
    }
  ]
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin melihat daftar pesanan",
  "errors": {}
}

### 15. Melihat Detail Pesanan

GET /api/v1/orders/{id}

Autentikasi: Bearer Token

Role: Buyer pemilik pesanan atau Seller terkait

Response Success 200:
{
  "status": "success",
  "message": "Detail pesanan berhasil diambil",
  "data": {
    "id": 10,
    "order_code": "ORD-20261005-001",
    "total_amount": 30000,
    "order_status": "pending",
    "pickup_method": "pickup",
    "pickup_location": "Area Kampus UBBG",
    "notes": "Ambil pukul 12.00",
    "items": [
      {
        "product_id": 1,
        "product_name": "Nasi Goreng",
        "quantity": 2,
        "price": 15000,
        "subtotal": 30000
      }
    ]
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin melihat pesanan ini",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Pesanan tidak ditemukan",
  "errors": {}
}

### 16. Mengubah Status Pesanan

PATCH /api/v1/orders/{id}/status

Autentikasi: Bearer Token

Role: Seller

Request:
{
  "order_status": "processing"
}

Response Success 200:
{
  "status": "success",
  "message": "Status pesanan berhasil diperbarui",
  "data": {
    "id": 10,
    "order_code": "ORD-20261005-001",
    "order_status": "processing"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin mengubah status pesanan ini",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Pesanan tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Status pesanan tidak valid",
  "errors": {
    "order_status": ["Status pesanan harus pending, processing, completed, atau cancelled"]
  }
}

### 17. Membuat Pembayaran

POST /api/v1/payments

Autentikasi: Bearer Token

Role: Buyer

Request:
{
  "order_id": 10,
  "payment_method": "transfer",
  "amount": 30000,
  "payment_proof": "bukti-transfer.jpg"
}

Response Success 201:
{
  "status": "success",
  "message": "Pembayaran berhasil dikirim",
  "data": {
    "id": 5,
    "order_id": 10,
    "payment_method": "transfer",
    "amount": 30000,
    "payment_status": "pending"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin melakukan pembayaran",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Pesanan tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Data pembayaran tidak valid",
  "errors": {
    "payment_method": ["Metode pembayaran wajib dipilih"],
    "amount": ["Nominal pembayaran harus sesuai total pesanan"],
    "payment_proof": ["Bukti pembayaran wajib diunggah"]
  }
}

### 18. Melihat Detail Pembayaran

GET /api/v1/payments/{order_id}

Autentikasi: Bearer Token

Role: Buyer pemilik pesanan atau Seller terkait

Response Success 200:
{
  "status": "success",
  "message": "Detail pembayaran berhasil diambil",
  "data": {
    "id": 5,
    "order_id": 10,
    "payment_method": "transfer",
    "amount": 30000,
    "payment_status": "pending",
    "payment_proof": "bukti-transfer.jpg"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin melihat pembayaran ini",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Data pembayaran tidak ditemukan",
  "errors": {}
}

### 19. Memverifikasi Pembayaran

PATCH /api/v1/payments/{id}/verify

Autentikasi: Bearer Token

Role: Seller

Request:
{
  "payment_status": "verified"
}

Response Success 200:
{
  "status": "success",
  "message": "Pembayaran berhasil diverifikasi",
  "data": {
    "id": 5,
    "order_id": 10,
    "payment_status": "verified"
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin memverifikasi pembayaran",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Pembayaran tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Status pembayaran tidak valid",
  "errors": {
    "payment_status": ["Status pembayaran harus verified atau rejected"]
  }
}

### 20. Menambahkan Review

POST /api/v1/reviews

Autentikasi: Bearer Token

Role: Buyer

Request:
{
  "product_id": 2,
  "rating": 5,
  "comment": "Produknya bagus dan sesuai."
}

Response Success 201:
{
  "status": "success",
  "message": "Review berhasil ditambahkan",
  "data": {
    "id": 1,
    "product_id": 2,
    "rating": 5,
    "comment": "Produknya bagus dan sesuai."
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin memberikan review",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Produk tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Review tidak valid",
  "errors": {
    "rating": ["Rating harus antara 1 sampai 5"],
    "comment": ["Komentar wajib diisi"]
  }
}

### 21. Melihat Review Produk

GET /api/v1/products/{id}/reviews

Autentikasi: Bearer Token

Role: Buyer dan Seller

Response Success 200:
{
  "status": "success",
  "message": "Review produk berhasil diambil",
  "data": [
    {
      "id": 1,
      "user_name": "Budi",
      "rating": 5,
      "comment": "Produknya bagus dan sesuai."
    },
    {
      "id": 2,
      "user_name": "Siti",
      "rating": 4,
      "comment": "Produk sesuai dan pelayanan cepat."
    }
  ]
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Produk tidak ditemukan",
  "errors": {}
}

### 22. Melihat Notifikasi

GET /api/v1/notifications

Autentikasi: Bearer Token

Role: Buyer dan Seller

Response Success 200:
{
  "status": "success",
  "message": "Notifikasi berhasil diambil",
  "data": [
    {
      "id": 1,
      "title": "Pesanan Diproses",
      "message": "Pesanan ORD-20261005-001 sedang diproses.",
      "is_read": false
    },
    {
      "id": 2,
      "title": "Pembayaran Diverifikasi",
      "message": "Pembayaran untuk pesanan ORD-20261005-001 telah diverifikasi.",
      "is_read": true
    }
  ]
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

### 23. Menandai Notifikasi Sudah Dibaca

PATCH /api/v1/notifications/{id}/read

Autentikasi: Bearer Token

Role: Buyer dan Seller

Request:
{
  "is_read": true
}

Response Success 200:
{
  "status": "success",
  "message": "Notifikasi berhasil ditandai sudah dibaca",
  "data": {
    "id": 1,
    "is_read": true
  }
}

Response Error 401:
{
  "status": "error",
  "message": "Unauthenticated",
  "errors": {}
}

Response Error 403:
{
  "status": "error",
  "message": "Anda tidak memiliki izin mengubah notifikasi ini",
  "errors": {}
}

Response Error 404:
{
  "status": "error",
  "message": "Notifikasi tidak ditemukan",
  "errors": {}
}

Response Error 422:
{
  "status": "error",
  "message": "Data notifikasi tidak valid",
  "errors": {
    "is_read": ["Nilai is_read harus berupa true atau false"]
  }
}

## 5. Matriks Izin Peran

| No | Endpoint | Method | Buyer | Seller |
|---|---|---|---|---|
| 1 | /api/v1/login | POST | Ya | Ya |
| 2 | /api/v1/logout | POST | Ya | Ya |
| 3 | /api/v1/profile | GET | Ya | Ya |
| 4 | /api/v1/products | GET | Ya | Ya |
| 5 | /api/v1/products/{id} | GET | Ya | Ya |
| 6 | /api/v1/products | POST | Tidak | Ya |
| 7 | /api/v1/products/{id} | PUT | Tidak | Ya, produk sendiri |
| 8 | /api/v1/products/{id} | DELETE | Tidak | Ya, produk sendiri |
| 9 | /api/v1/cart | GET | Ya | Tidak |
| 10 | /api/v1/cart/items | POST | Ya | Tidak |
| 11 | /api/v1/cart/items/{id} | PATCH | Ya | Tidak |
| 12 | /api/v1/cart/items/{id} | DELETE | Ya | Tidak |
| 13 | /api/v1/orders | POST | Ya | Tidak |
| 14 | /api/v1/orders | GET | Ya | Ya |
| 15 | /api/v1/orders/{id} | GET | Ya, pesanan sendiri | Ya, pesanan terkait |
| 16 | /api/v1/orders/{id}/status | PATCH | Tidak | Ya |
| 17 | /api/v1/payments | POST | Ya | Tidak |
| 18 | /api/v1/payments/{order_id} | GET | Ya, pembayaran sendiri | Ya, pembayaran terkait |
| 19 | /api/v1/payments/{id}/verify | PATCH | Tidak | Ya |
| 20 | /api/v1/reviews | POST | Ya | Tidak |
| 21 | /api/v1/products/{id}/reviews | GET | Ya | Ya |
| 22 | /api/v1/notifications | GET | Ya | Ya |
| 23 | /api/v1/notifications/{id}/read | PATCH | Ya | Ya |

## 6. Log Perubahan

| Versi | Tanggal | Perubahan |
|---|---|---|
| 1.0.0 | 05-10-2026 | Membuat kontrak API awal TARMAX |
| 1.1.0 | 05-10-2026 | Menambahkan endpoint autentikasi dan profil user |
| 1.2.0 | 05-10-2026 | Menambahkan endpoint produk dan keranjang |
| 1.3.0 | 05-10-2026 | Menambahkan endpoint pesanan dan pembayaran |
| 1.4.0 | 05-10-2026 | Menambahkan endpoint review dan notifikasi |
| 1.5.0 | 05-10-2026 | Menambahkan penanganan error 401, 403, 404, dan 422 |
| 1.6.0 | 05-10-2026 | Menambahkan matriks izin peran Buyer dan Seller |

## 7. Ringkasan API

API TARMAX dirancang menggunakan pendekatan RESTful dengan format JSON yang konsisten.

Kontrak API ini memiliki 23 endpoint yang mencakup:

- Authentication
- Profile User
- Products
- Cart
- Orders
- Payments
- Reviews
- Notifications

Setiap endpoint yang membutuhkan autentikasi menggunakan Bearer Token.

Hak akses dibagi menjadi dua role, yaitu Buyer dan Seller. Buyer memiliki akses untuk melihat produk, mengelola keranjang, membuat pesanan, melakukan pembayaran, memberikan review, dan melihat notifikasi. Seller memiliki akses untuk mengelola produk, melihat pesanan terkait, memperbarui status pesanan, memverifikasi pembayaran, melihat review, dan melihat notifikasi.

Semua response API menggunakan format yang konsisten, yaitu:

Success:
{
  "status": "success",
  "message": "Pesan berhasil",
  "data": {}
}

Error:
{
  "status": "error",
  "message": "Pesan kesalahan",
  "errors": {}
}

Dengan struktur tersebut, API TARMAX telah memenuhi kebutuhan utama sistem, mencakup autentikasi, request dan response, penanganan error, izin peran, serta log perubahan.
