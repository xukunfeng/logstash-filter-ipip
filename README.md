# logstash-filter-ipip 插件

这是logstash的插件，fork 自[logstash-filter-ipip](https://github.com/bittopaz/logstash-filter-ipip).

适配于 https://www.ipip.net/ 的免费版数据库

# 安装
1.下载插件文件夹
```shell
git clone https://github.com/xukunfeng/logstash-filter-ipip 
```
2.修改logstash 安装目录下的Gemfile文件，添加一行：
```
gem "logstash-filter-ipip", "0.1.1", :path => "plugin/logstash-filter-ipip/logstash-filter-ipip"
```
path 根据自己的实际情况配置

3.在logstash的安装目录执行安装命令
```
bin/plugin install --no-verify
```
# 使用

在配置文件中添加：
```
filter {
    ipip {
                source => "remote_addr"
                target => "ipip"
        }
}
```
remote_addr 存放的是ip，根据自己的情况修改

在输出的中，会增加以下字段：
```
"ipip": {
      "country": "中国",
      "province": "福建",
      "city": "漳州"
    }
```

#注意事项
ipip 的数据库位于 logstash-filter-ipip/lib/logstash/filters/data 目录，可以定时从ipip.net 上下载更新
