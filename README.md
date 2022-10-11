# jable_downloader
download jable tv tool

### introduction
下载jable tv视频助手

支持功能：
- 指定视频url下载到指定目录
- 添加订阅某女星或者类别的视频，将该影星或类别的视频同步到指定目录
- 支持下载视频完毕后下载封面
- 支持检查输出目录，防重复下载

### usage

**使用方法**

```shell
# 安装依赖
pip install -r requirements.txt
# Linux设置代理(可选)
export https_proxy=http://127.0.0.1:7890 && export http_proxy=http://127.0.0.1:7890
# 查看帮助
python main.py --help
# 指定视频url下载，指定多个url会按队列逐个下载(下面url替换为自己的url)
python main.py videos  https://jable.tv/videos/111111/  https://jable.tv/videos/222222/

# 添加对某类别的订阅，如添加`桜空もも`的订阅，添加订阅不会发起下载
python main.py subscription --add https://jable.tv/models/sakura-momo/
# 查看当前订阅
python main.py subscription --get
# 下载/同步订阅内容到本地(不会下载已下载内容)
python main.py subscription --sync-videos
```

### config

配置项(json文件)说明

- downloadVideoCover： 是否下载封面,默认不下载
- downloadInterval： 每个视频之间的下载间隔，默认300s
- outputDir：下载的输出目录，默认当前工作目录
- subscriptions： 订阅的视频类别，支持models/tags等，建议通过命令行` python main.py subscription --add `添加

```json
{
    "downloadVideoCover": false,     
    "downloadInterval": 300,
    "outputDir": "./",
    "subscriptions": [
        {
            "url": "https://jable.tv/models/sakura-momo/",
            "name": "桜空もも"
        }
    ]
}
```

### TODO

- 支持类别的交集
- 本地缓存订阅类别的视频索引

### reference
[JableTVDownload](https://github.com/hcjohn463/JableTVDownload)