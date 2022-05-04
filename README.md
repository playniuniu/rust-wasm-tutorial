# 使用 Rust 生成 WebAssembly 应用简要教程

### 1. 使用 Cargo 创建项目

```shell
cargo init --lib
```

### 2. 修改 Cargo.toml, 增加如下配置

```toml
[lib]
crate-type = ["cdylib"]

[dependencies]
wasm-bindgen = "0.2.80"
```

### 3. 编写 WebAssembly 应用

```rust
use wasm_bindgen::prelude::*;

#[wasm_bindgen]
pub fn add(a: i32, b: i32) -> i32 {
    return a + b;
}
```

### 4. 编译 WebAssembly 应用并生成 pkg 文件夹

```shell
wasm-pack build --target web
```

### 5. 编写 HTML 页面

```html

<body>
<script type="module">
    import init, {add} from './pkg/learn_wasm.js'

    await init()
    console.log(add(1, 2))
</script>
</body>
```
