# Gitlab-EE破解，仅供测试使用，切勿用于公司正式服务

1. 安装ruby

- 安装完gitlab ee之后
- 安装ruby：yum install ruby
- ruby版本需要2.3或以上。

2. 生成许可证

- gem install gitlab-license

3. 创建一个rb文件 license.rb，

- 执行 ```ruby license.rb``` 生成 GitLabBV.gitlab-license、license_key、license_key.pub 这三个文件。

4. 使用许可证

- 用 license_key.pub 文件替换 /opt/gitlab/embedded/service/gitlab-rails/.license_encryption_key.pub。

- 修改订阅等级

``` ruby
    --- /opt/gitlab/embedded/service/gitlab-rails/ee/app/models/license.rb
    +++ /opt/gitlab/embedded/service/gitlab-rails/ee/app/models/license.rb
    @@ -458,7 +458,7 @@
    end
    
    def plan
    -    restricted_attr(:plan).presence || STARTER_PLAN
    +    restricted_attr(:plan).presence || ULTIMATE_PLAN
    end
    
```

- ```gitlab-ctl restart``` 重启

- GitLabBV.gitlab-license 即是许可证，admim-subscription订阅页面上传GitLabBV.gitlab-license文本内容即可。
