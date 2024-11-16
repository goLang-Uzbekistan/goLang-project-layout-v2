# goLang-project-layout-v2
## Maslahat beraman ko'ring shu videoni:
_Hammaga Assalomu Alaykum) Sabr qilib ko'ring videoni va bu video faqat proyektga emas, shaxsiy hayotingizdaham foyda bo'ladi degan umidaman)_
* **Tartib va Intizom | Palapartish qilingan ishdan natija kutish axmoqlik!**
  https://www.youtube.com/watch?v=5SAt-CPijd4/

___________________________

## Golang standard project layout
* Project Layout: https://github.com/golang-standards/project-layout/

- **`/cmd yoki /app`**: bu folder da main.go file li turadi.
```text
/cmd
├── 1app
│   ├── main.go
│   └── go.mod
└── 2app
    ├── main.go
    └── go.mod
```
- man tahminan misol keltirayapman 😅



[//]: # (- **`/pkg`**: Kutubxona kodini o'z ichiga oladi. Boshqa loyihalar ushbu paketlarni kutubxona sifatida import qiladi.)

- **`/internal`**: bu folder'da /models, /middleware, /database, /handlers xullas asosiy proyetga oid kodlar buladi.
```text
/internal
├── auth
│   ├── auth.go
│   └── auth_test.go
└── storage
    ├── storage.go
    └── storage_test.go
```
- **`/vendor`**: `go mod vendor` - bu go.mod barcha packages offline yuklab oladi)
```text
/vendor
├── github.com
│   └── someuser
│       └── somepackage
│           ├── somefile.go
│           └── ...
└── golang.org
    └── x
        └── net
            ├── somefile.go
            └── ...
```

- **`/api`**: OpenAPI/Swagger spetsifikatsiyalari, JSON sxema fayllari yoki protokolni saqlash fayllari turadi.
```text
/api
├── openapi.yaml
├── swagger.json
├── other.json
└── protobuf
    ├── messages.proto
    └── services.proto
```
- **`/web`**: Veb statik fayllar: `/img`, `/css`, `/js`, `/.html`
```text
/web
├── static
│   ├── css
│   │   ├── style.css
│   ├── js
│   │   ├── script.js
│   └── images
│       ├── logo.png
└── templates
    ├── layout.html
    ├── index.html
    └── about.html
```

- **`/configs`**: Konfiguratsiya fayli shablonlari yoki standart konfiguratsiyalar.
```text
/configs
├── config.yaml
├── config.toml
└── example.env
```

- **`/build`**: agar Proyektiz finalga kelsa, ushanda foydasi tegadi `go build`

- **`/deployments`**: IaaS, PaaS, tizim va docker-konteyner va boshqa hosting deploy konfiguratsiyalari saqlanadi.

- **`/test`**: Proyektiz sinovdan o'tkazish/testing kodlari.

- **`/tools`**: Ushbu Proyektiz uchun yordamchi instrumentlar. Eslatma: Ushbu instrumentlar Proyektizni o'ziga tegishli emas.

- **`/docs`**: Proyektizga oid docslar saqlab quyishingiz mumkin,

- **`/examples`**: Demo screenshotlar yoki qaney ishlaydi sizning Proyektiz misol keltirishingiz mumkin

### va
- **`README.md`**: Proyektiz tushuntiruvchi fayl, Proyektiz maqsadi yoki kelajakdagi rejalariz/function yozib quyishingiz mumkin.
- **`Makefile`**: Proyektiz build qilish va sinovdan o'tkazish bo'yicha ko'rsatmalar.
