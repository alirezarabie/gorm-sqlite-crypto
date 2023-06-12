# gorm-sqlite-crypto



### Description

Go sqlite3 driver for [GORM](https://gorm.io/) with an AES-256 encrypted sqlite3 database
conforming to the built-in database/sql interface. It is based on:

- Go sqlite3 driver: https://github.com/mattn/go-sqlite3
- SQLite extension with AES-256 codec: https://github.com/sqlcipher/sqlcipher
- AES-256 implementation from: https://github.com/libtom/libtomcrypt
- GORM sqlite driver : https://github.com/go-gorm/sqlite

SQLite itself is part of SQLCipher.

### Installation

This package can be installed with the go get command:

    go get github.com/alirezarabie/gorm-sqlite-crypto

## USAGE

```go
import (
  sqliteEncrypt "github.com/alirezarabie/gorm-sqlite-crypto"
  "gorm.io/gorm"
)
key := "passphrase"
dbname := "go-sqlcipher.sqlite"
dbnameWithDSN := dbname + fmt.Sprintf("?_pragma_key=%s&_pragma_cipher_page_size=4096", key)
db, err := gorm.Open(sqliteEncrypt.Open(dbnameWithDSN), &gorm.Config{})
```

### License

The code of the originating packages is covered by their respective licenses.
See [LICENSE](LICENSE) file for details.
