## 关于本项目

本项目是达梦官方下载包的gorm适配包，修改而来。

## 使用方法

```go
package main

import (
	"github.com/aveyuan/dmgorm"
	"gorm.io/gorm"
	"log"
)

func main() {
	dsn := "dm://username:password@127.0.0.1:5236?autoCommit=true"
	db, err := gorm.Open(dmgorm.Open(dsn), &gorm.Config{})
	if err != nil {
		log.Fatal(err)
	}

	sdb, err := db.DB()
	if err != nil {
		log.Fatal(err)
	}
	if err := sdb.Ping(); err != nil {
		log.Printf("connect ping fail %v", err)
		return
	}
	log.Printf("connect ping success")
}

```