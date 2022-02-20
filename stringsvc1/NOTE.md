# NOTE

[Struct types](https://go.dev/ref/spec#Struct_types)
[How to use struct tags in go](https://www.digitalocean.com/community/tutorials/how-to-use-struct-tags-in-go)
[Type assertions](https://go.dev/ref/spec#Type_assertions)
[CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments)
## Struct tags

- Go struct tags are annotations that appear after the type in a Go struct declaration. Each tag is composed of short strings associated with some corresponding value.

Example:

```go
  type User struct{
    Name string `example:"name"`
  }
```

- Struct tags have no effect on the operation of your code without some other code that examines them.
- You can use multi struct tags

```go
type Page struct {
    PageId string                 `bson:"pageId" json:"pageId"`
    Meta   map[string]interface{} `bson:"meta" json:"meta"`
}
```

## Type assertions

```go
var i interface{}
i = int(42)

a, ok := i.(int)
// a == 42 and ok == true

b, ok := i.(string)
// b == "" (default value) and ok == false               // i has type int and value 7
```

It checks that the value of `i` is of type int. If it is, then `ok` will be true. Otherwise, it will be false

## `go-kit` middleware

Let’s use a middleware, also known as a decorator. A middleware is a function that takes an endpoint and returns an endpoint.

```go
type Middleware func(Endpoint) Endpoint
```

the Middleware type is provided for you by go-kit.