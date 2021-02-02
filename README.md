# controller builder
根据用户自定义的`blockchain.proto`文件，生成controller需要的代码。

本项目作为一个`protoc`插件运行。

`protoc`会先将`proto`文件解析，然后传递`descriptor`结构给插件继续进行处理。

这个`descriptor`结构定义在[descriptor.proto](https://github.com/protocolbuffers/protobuf/blob/master/src/google/protobuf/descriptor.proto)。

这里使用[protobuf](https://crates.io/crates/protobuf)中已经实现好的解析函数，来解析其中的扩展信息，并生成相应的代码。

### 命令
```
protoc --proto_path=./protos --plugin=protoc-gen-controller=./target/debug/controller_builder --controller_out=controller blockchain.proto > output 2>&1
```

### 扩展选项
* `field_length` 对应成员的长度精确的值。
* `field_max_length` 对应成员的长度的最大值，小于等于该值均为合法。
* `field_length_func` 对应成员的长度为变量，由指定的函数来检查其合法性。
* `field_value_func` 由指定的函数来检查对应成员的值是否合法。
