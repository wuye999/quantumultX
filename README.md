# 三个月撸完后的感叹

首次撸满了50元，审核通过后多日未到账，联系小小影视管理员，表示需要升级到最新版本，因提现金额已变更为100元，还表示会退回金币，然后过了三个月也并未退回。
10月20日再次于撸满了100元并提现，在审核通过后还是出现多日不打款。再次联系小小影视管理员，对方表示不能一直靠签到提现，需要邀请用户。但我也有2个邀请用户，并且保持一个日活。再次追问下，小小影视管理不再继续理会。根据这个情况，即使通过邀请方式撸满100元的提现，也有可能被判断为刷单行为，所以继续撸的金币只能用来兑换一些下载及观影权限。是否继续使用，请各位大佬们自行斟酌！

# 小小影视

> 代码已同时兼容 Surge & QuanX, 使用同一份签到脚本即可

> 目前分开两个版本，一个是完整版8任务同时执行，但是可能会存在偶尔到点抽风不执行（签到，广告，分享，评论，10次观影，5次收藏，30分钟连续观影，每日22点开宝箱）

## 配置 (QuanX)
```properties
[MITM]

*.xjxjappss.com,*.xjxjapps.com,*.xxjjappss.com,*.xjwdapps.com,*.leleapps.com,*.leyiapps.com,*.hpplay.cn,*.gqbyh.com

[rewrite_local]

# 189及以前版本
^https:\/\/.*\..*\.com\/ucp\/index url script-response-body xxys.cookie.js
# 190及以后版本
^https:\/\/.*\..*\.com\/ucp\/index url script-request-header xxys.cookie.js

[task_local]

## 完整版执行请严格按下面格式

*/10 0-30 9,22 * * * xxysrw.js

## 多任务版本不限时间格式(9点执行6任务，22点执行开箱)

0 9,22 * * * xxys_6rw.js

## 连续观影30分钟的任务，分钟时间必须0-30分钟

*/10 0-30 9 * * * xxys_play.js
```
## 说明

1. 登陆小小影视APP，点击“我的”，自动获取到cookie，就可以注释获取cookie脚本了


## 常见问题

1. 无法写入 Cookie

   - 请查看配置的mitm是否正确，可以抓包看域名。

2. 写入 Cookie 成功, 但签到不成功

   - 看看是否因为task的任务执行时间错了。

3. 为什么有时成功有时失败

   - 很正常，网络问题，因为执行的时候网络卡一下，跳过了配对时间执行不会生效，尤其是完整版。


