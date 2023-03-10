# rust_erajp

Rust library for japanese era.  
This is a sample inspired from [go-erajp](https://github.com/mattn/go-erajp).

## Usage

```rust
println!("{}", rust_erajp::to_era(2023).unwrap());  // 令和
```

## Examples

```sh
cargo run --example to_era
cargo run --example to_era_from_time
cargo run --example find
```

## License

MIT

## Note

- 寛永への改元日(1624/2/30)は何とかなるのか
  - chronoでは[グレゴリオ暦を想定している](https://docs.rs/chrono/latest/chrono/offset/trait.TimeZone.html#method.with_ymd_and_hms:~:text=current%20time%20zone.-,This%20assumes%20the%20proleptic%20Gregorian%20calendar%2C%20with%20the%20year%200%20being%201%20BCE.,-Returns%20LocalResult%3A%3ANone)とのことで、`No such local time`というエラーとなった
  - [日本では明治6年にグレゴリオ暦が採用された](https://www1.kaiho.mlit.go.jp/KOHO/faq/reki/shinreki.html)とのこと
  - [go-erajpの実装](https://github.com/mattn/go-erajp/blob/6d6d9810ce59f08930f7ad41b817a49c16ed38ba/era.go#L34-L39)を真似て[試した](https://go.dev/play/p/2Hwm_Sjr7GR)ら、`1624-03-01 00:00:00 +0000 UTC`となったのでデータを調整してごまかすことにした
