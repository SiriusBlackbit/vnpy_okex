# vn.py框架的OKX底层接口

<p align="center">
  <img src ="https://vnpy.oss-cn-shanghai.aliyuncs.com/vnpy-logo.png"/>
</p>

<p align="center">
    <img src ="https://img.shields.io/badge/version-2021.4.21.5-blueviolet.svg"/>
    <img src ="https://img.shields.io/badge/platform-windows|linux-yellow.svg"/>
    <img src ="https://img.shields.io/badge/python-3.7-blue.svg" />
    <img src ="https://img.shields.io/github/license/vnpy/vnpy.svg?color=orange"/>
</p>

[Github Discussions论坛](https://github.com/vn-crypto/vnpy_crypto/discussions)

## 说明

2022.09.11,旧版本已不再适配OKX(原OKEX) api交易，决定抽时间进行改进。

基于OKX交易所的V5接口开发，支持统一账户下的现货、期货、永续、期权交易。

使用时需要注意本接口：

1. 只支持单币种保证金模式
2. 只支持全仓保证金模式


请在OKEX网站完成账户的相应设置后再使用。

## 安装

安装需要基于2.2.0版本以上的[VN Studio](https://www.vnpy.com)。


下载解压后在cmd中运行

```
python setup.py install
```

安装原版vnpy_okex，下载解压后对应覆盖。

## 使用

以脚本方式启动（script/run.py）：

```
from vnpy.event import EventEngine
from vnpy.trader.engine import MainEngine
from vnpy.trader.ui import MainWindow, create_qapp

from vnpy_okex import OkxGateway


def main():
    """主入口函数"""
    qapp = create_qapp()

    event_engine = EventEngine()
    main_engine = MainEngine(event_engine)
    main_engine.add_gateway(OkxGateway)
    
    main_window = MainWindow(main_engine, event_engine)
    main_window.showMaximized()

    qapp.exec()


if __name__ == "__main__":
    main()
```
