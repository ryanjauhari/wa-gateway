# Multi Session Whatsaapp Gatewa dengan NodeJS

Mudah di gunakan, support nodejs v16, dan dapat di install di windows dan linux.

- Mendukung berbagai devices karena menjalankann nodejs
- Mendukung multi sesi, dapat menjalankan lebih dari 1 akun Whatsapp
- Dilengkapi dengan delay anti banned.
- Dilengkapi dengan fitur kirim pesan masssal...

#### Di buat dengan library [wa-multi-session](https://github.com/mimamch/wa-multi-session)

## Konfigurasi lingkungan kerja

Untuk menjalankan file ini pastikan kamu membuat sebuah file baru .env dan meleakan format berikut ini. Port dan secretkey ganti!

```
// .env

PORT=5001 // which port to running on your machine
KEY=mysupersecretkey # For Securing Some Data
```

## Cara mengisntall program

Salin repositori ini ke folder kerja kamu.

```bash
  git clone https://github.com/ryanjauhari/wa-gateway.git
```

Buka folder yang di salin sebelumnya

```bash
  cd wa-gateway
```

Jalankan NPM ini untuk mengisntall semua paket defensi yang di butuhkan.

```bash
  npm install
```

Jalankan perintah NPM ini untuk menjalankan program.

```bash
  npm run start
```

Buka browser, dan buat sesi baru dengan mengunjungi URL berikut

```bash
  http://localhost:{PORT-ANDA}/start-session?session={NAMA-SESI}&scan=true
```

NB : Ubah port dengan kode port yang kamu gunakan, ubah Nama sesi dengan nama sesi yang di inginkan without space.


## Fitur API yang di sematkan

#### Menambah Sessi baru

```
  GET /start-session?session=NEW_SESSION_NAME&scan=true
```

| Parameter | Type      | Description                            |
| :-------- | :-------- | :------------------------------------- |
| `session` | `string`  | **Required**. Create Your Session Name |
| `scan`    | `boolean` | Print QR at Browser                    |

#### Send Text Message

```
  POST /send-message
```

| Body      | Type     | Description                                                              |
| :-------- | :------- | :----------------------------------------------------------------------- |
| `session` | `string` | **Required**. Session Name You Have Created                              |
| `to`      | `string` | **Required**. Receiver Phone Number with Country Code (e.g: 62812345678) |
| `text`    | `string` | **Required**. Text Message                                               |

#### Send Bulk Message

```
  POST /send-bulk-message
```

| Body      | Type     | Description                                         |
| :-------- | :------- | :-------------------------------------------------- |
| `session` | `string` | **Required**. Session Name You Have Created         |
| `data`    | `array`  | **Required**. Array Of Object Message Data          |
| `delay`   | `number` | Delay Per-message in Miliseconds, Default to 5000ms |

#### Delete session

```
  GET /delete-session?session=SESSION_NAME
```

| Parameter | Type     | Description                            |
| :-------- | :------- | :------------------------------------- |
| `session` | `string` | **Required**. Create Your Session Name |

#### Get All Session ID

```
  GET /sessions?key=mysupersecretkey
```

| Parameter | Type     | Description                      |
| :-------- | :------- | :------------------------------- |
| `key`     | `string` | **Required**. Key on ".env" file |

## Changelog

V3.2.0

- Add Get All Session ID
- Add Key for secret data
- Update README.md

## Upgrading

```
npm install wa-multi-session@latest
```

## Documentation

Repositori ini merupakann kloning dari repositori aslinya WhatsappGateway API liha sumber asli di sini [official documentation](https://github.com/mimamch/wa-gateway).

## Contributing

Jika ingin berkontribusi terhadap project ini, bisa langsung request ke ke reposiotri original nya. [CONTRIBUTING.md](https://github.com/mimamch/wa-gateway/blob/main/CONTRIBUTING.md) file.

## License

Project ini di lisensikan di atas [MIT License](https://github.com/mimamch/wa-gateway/blob/main/LICENSE).
