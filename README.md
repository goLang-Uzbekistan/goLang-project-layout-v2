# goLang Proyekt yaratish strukturasi:
_Hammaga Assalomu Alaykum) Sabr qilib ko'ring videoni va bu video faqat proyektga emas, shaxsiy hayotingizdaham foyda bo'ladi degan umidaman)_
### Maslahat beraman ko'ring shu videoni:
* **Tartib va Intizom | Palapartish qilingan ishdan natija kutish axmoqlik!**
  https://www.youtube.com/watch?v=5SAt-CPijd4/

## Testing example getAlbums project:
https://go.dev/doc/tutorial/web-service-gin/

___________________________

## Golang standard project layout
* Project Layout: https://github.com/golang-standards/project-layout/

- **`/cmd yoki /app`**: bu folder da main.go file li turadi.
```text
/cmd
├── GIN
│   ├── main.go
│   └── go.mod
└── Gorilla
    ├── main.go
    └── go.mod
```
- man tahminan misol keltirayapman 😁
  
[//]: # (- **`/pkg`**: Kutubxona kodini o'z ichiga oladi. Boshqa loyihalar ushbu paketlarni kutubxona sifatida import qiladi.)

- **`/internal`**: bu folder'da (/api, /handlers, /routes), /models, /middleware, /database xullas asosiy proyetga oid kodlar buladi.
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
--------------
- **`/scripts`**: voqti kelsa tushunib olasiz 😁
```text
/scripts
├── build.sh
├── deploy.sh
└── test.sh
```
misol: `deploy.sh` 
```bash
echo "Deploying the application..."
git pull origin main
./build.sh
echo "Deployment completed!"
```
--------------
## go build
### Linux (amd64)
```bash
GOOS=linux GOARCH=amd64 go build -o app-linux-amd64
````
### macOS (amd64)
```bash
GOOS=darwin GOARCH=amd64 go build -o app-darwin-amd64
```
### macOS (arm64 - M1/M2)
```bash
GOOS=darwin GOARCH=arm64 go build -o app-darwin-arm64
```
### Windows (amd64)
```bash
GOOS=windows GOARCH=amd64 go build -o app-windows-amd64.exe
```
- **`/build`**: agar Proyektiz finalga kelsa, ushanda foydasi tegadi `go build`
```text
/build
├── docker
│   ├── Dockerfile
│   └── entrypoint.sh
├── scripts
│   ├── build.sh
│   └── deploy.sh
└── artifacts
    └── README.md
```
__________________________

- **`/deployments`**: IaaS, PaaS, tizim va docker-konteyner va boshqa hosting deploy konfiguratsiyalari saqlanadi, yoki boshqa fayllar.
```text
/deployments
├── docker
│   ├── Dockerfile
│   └── docker-compose.yml
├── k8s
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
├── scripts
│   ├── deploy.sh
│   └── rollback.sh
└── README.md
```

- **`/test`**,  **`/testing`**: Proyektiz testing kodlari.
```text
/test
├── integration_test.go
└── test_data
    ├── sample_input.json
    └── sample_output.json
```
_______________
- **`/tools`**: Ushbu Proyektiz uchun yordamchi instrumentlar. Eslatma: Ushbu instrumentlar Proyektizni o'ziga tegishli emas.
```text
/tools
├── build
│   └── build.go
├── lint
│   └── lint.go
└── format
    └── format.go
```
// tools/build/build.go
```go
package main

import (
    "fmt"
    "os"
    "os/exec"
)

func main() {
    fmt.Println("Building the project...")
    cmd := exec.Command("go", "build", "./cmd/myapp")
    cmd.Stdout = os.Stdout
    cmd.Stderr = os.Stderr
    if err := cmd.Run(); err != nil {
        fmt.Printf("Error building application: %v\n", err)
        os.Exit(1)
    }
    fmt.Println("Build completed successfully!")
}
```

- **`/docs`**: Proyektizga oid docslar saqlab quyishingiz mumkin,
```text
/docs
├── architecture.md
├── API.md
├── getting_started.md
└── examples
    ├── basic_usage.md
    └── advanced_features.md
```
- **`/examples`**: Proyektizga oid examplelarni saqlab quyishingiz mumkin, xullas voqti kelsa tushunib olasiz 😁yoki esdan chiqaring xD
```text
/examples
├── basic_usage.go
├── advanced_usage.go
└── cli_example.go
```
### va
- **`README.md`**: Proyektiz tushuntiruvchi fayl, Proyektiz maqsadi yoki kelajakdagi rejalariz/function yozib quyishingiz mumkin.
- **`Makefile`**: Proyektiz build qilish va sinovdan o'tkazish bo'yicha ko'rsatmalar.
[makefile](configs%2Fmakefile)

_________________
# autoUpdate: air
1. Plus tarafi: agar Windows/Mac/Linux Terminal autoUpdate air buladi va juda qulay.
2. Minus tarafi: agar siz **goLand** ishlatsangiz xar safar `CTRL + S` bosib zzz bulib ketasizlar xD, `CTRL + S` dan keyin autoUpdate buladi... 

```bash
go install github.com/air-verse/air@latest
```

### Starting air
```bash
air
```
_________

# Kod editorlar haqida
Nomi  | Shaxsiy fikrim
--- | ---
**JetBrains**: https://www.jetbrains.com/  | `Rolls Royce +` ga o‘xshaydi va komport va qulaylik, bergan pulimga achinmayman. 
**GoLand**: https://www.jetbrains.com/go/  | `Rolls Royce` ga o‘xshaydi va qulay va zur va RUN qilishda juda oson. reDuber va test qilishda ham juda qulay.
**ZED**: https://zed.dev/  | `Ferrari`ga o'xshaydi va juda tez va qulay, faqat xozircha (MacOS, Linux) larga ishlaydi. Windowschilar sabr qilasizlar xD
**Visual Studio Code**: https://code.visualstudio.com/  | Universal dastur, tez va qulay va juda mashhur.
**Vim**: https://vim.org/ | `BMW` ga o‘xshaydi (komfort kerak emas, tezlikni sevadiganlar uchun) va uchun zur va tez editor, va Local yoki Serverlar bilan ishlashda juda Nomer1 app va juda mashhur va qulay.
**Sublime Text**: https://www.sublimetext.com/  | Boshlang'ichlar uchun juda qulay va tez editor. va Hardware(Intel celeron 2yadro, 2patok)ham bulaveradi.

