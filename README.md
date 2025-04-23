[![PkgGoDev](https://pkg.go.dev/badge/github.com/mbsulliv/ini)](https://pkg.go.dev/github.com/mbsulliv/ini)

# ini

A Go package that encodes and decodes INI-files.

# Usage

```go
data := `[settings]
username=root
password=swordfish
shell[unix]=/bin/sh
shell[win32]=PowerShell.exe
`

var config struct {
    Settings struct {
        Username string            `ini:"username"`
        Password string            `ini:"password"`
        Shell    map[string]string `ini:"shell"`
    } `ini:"settings"`
}

if err := ini.Unmarshal(data, &config); err != nil {
    fmt.Println(err)
}
fmt.Println(config)
```
