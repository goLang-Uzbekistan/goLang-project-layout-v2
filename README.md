# goLang Proyekt yaratish strukturasi:
_Hammaga Assalomu Alaykum) Sabr qilib ko'ring videoni va bu video faqat proyektga emas, shaxsiy hayotingizdaham foyda bo'ladi degan umidaman)_
### Maslahat beraman ko'ring shu videoni:
* **Tartib va Intizom | Palapartish qilingan ishdan natija kutish axmoqlik!**
  https://www.youtube.com/watch?v=5SAt-CPijd4/

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
- man tahminan misol keltirayapman 😅

[//]: # (- **`/pkg`**: Kutubxona kodini o'z ichiga oladi. Boshqa loyihalar ushbu paketlarni kutubxona sifatida import qiladi.)

- **`/internal`**: bu folder'da /handlers, /routes, /models, /middleware, /database xullas asosiy proyetga oid kodlar buladi.
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
misol: `build.sh`
```bash
echo "Building the application..."
go build -o myapp ./cmd/myapp
echo "Build completed!"
```
misol: `deploy.sh` 
```bash
echo "Deploying the application..."
git pull origin main
./build.sh
echo "Deployment completed!"
```
--------------

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

- **`/test`**: Proyektiz sinovdan o'tkazish/testing kodlari.
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
2. Minus tarafi: agar siz **goLand** ishlatsangiz xar safar (CTRL + S) bosib zzz bulib ketasizlar xD

```bash
go install github.com/air-verse/air@latest
```

### Starting air
```bash
air
```
_________

## Testing the API for terminal
docs: https://www.codepedia.org/ama/how-to-test-a-rest-api-from-command-line-with-curl/
```bash
curl -I http://localhost:8000/api/healthChecker ## GET request
```

```bash
curl -i -X HEAD http://localhost:8000/api/healthChecker ## HEAD request
```

```bash
curl -X GET "http://localhost:8000/api/healthChecker" -H "accept: application/json" ## GET request
```

Agar siz uni yanada chiroyli ko'rsatishni istasangiz, `jq` tavsiya qilaman:
```bash
curl http://localhost:8000/api/healthChecker | jq . ## GET request
```

## Curl options
    -I or --head - fetch the headers only
    -i, --include - include the HTTP response headers in the output
    -X, --request - specify a custom request method to use when communicating with the HTTP server (GET, PUT, DELETE&)

