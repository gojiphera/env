# env

Package env provides an `env` struct field tag to unmarshal environment variables.

Supported types for unmarshaling:
* int, int8, int16, int32, int64
* float32, float64
* time.Duration
* string
* bool

## Example of use

```go
package main

import (
    "fmt"

    "github.com/gojiphera/env"
)

type Config struct {
    Duration     time.Duration `env:"TYPE_DURATION,default=1s"`
    DefaultValue string        `env:"MISSING_ENV,default=default_value"`
    Bool         bool          `env:"TYPE_BOOL"`
}

func main() {
    var config Config
    if err := env.Unmarshal(&config); err != nil {
        fmt.Printf("error: %v\n", err)
    }
    fmt.Printf("%#v\n", config)
}
```
