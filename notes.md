# Chapter1
# Chapter7 Go Web 服务
# Chapter8 应用测试
## 单元测试门类
1. 功能测试：测试模块功能是否正常
2. 基准测试（benchmarking）：测试模块运行效率（速度）
## 独立的单元测试
被测试代码独立性不足以进行替身测试时，需要使用依赖注入方法对模块进行解耦合。如本书第七章的Web服务中，server.go中的每个函数都严重依赖于data.go中的全局变量sql.Db。
### 1. 依赖注入
将一个包含sql.Db的Post结构传递到函数调用流程中，以此来对简单的Web服务实现依赖注入模式。由于Post结构中包含了sql.Db，server.go中所有函数都不再依赖data.go中的全局变量sql.Db。Post结构使用接口进行定义。
### 2. 测试替身
定义FakePost代替Post传入handleRequest中让测试模块不用去操作数据库，有利于对每个部分的独立测试。
