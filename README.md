# controller builder
`builder.proto`中定义了一些扩展选项。

用户可以在`blockchain.proto`中自定义交易，区块等数据结构，并使用扩展选项来标注各个字段的属性。

然后使用本工具生成`controller`需要的代码。

### 依赖
事先在系统中安装`protobuf`编译器。

### 命令
```
protoc --proto_path=./protos --include_imports --include_source_info -o ./descriptor.bin blockchain.proto
cargo build
./target/debug/controller_builder ./descriptor.bin > output
```

### 扩展选项
* `field_length` 对应成员的长度精确的值。
* `field_max_length` 对应成员的长度的最大值，小于等于该值均为合法。
* `field_length_func` 对应成员的长度为变量，由指定的函数来检查其合法性。
* `field_value_func` 由指定的函数来检查对应成员的值是否合法。
