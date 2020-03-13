

# 快速上手

## 通用高防

![](/images/流程.png)

### 1. 使用新IP替换旧IP

如果IP已经被封，购买新的源站IP替换旧的源站IP。

如果IP没有被封，建议申请新的源站IP替换旧的源站IP，旧的源站IP可能因攻击而被封堵或已经暴露，存在被直接攻击的风险。

``` 
注意：

被封的IP一定要使用新的IP替换被封的IP后才能正常使用高防。

```

### 2. 添加IP，开通服务

在【安全防护】-【DDoS攻击防护 UDDoS】-【高防】页面，点击“详情”-“IP管理”-“添加IP”。注意 **下图适用华南BGP、华东BGP杭州2、华东双线。华东BGP杭州配置请见[操作指南-添加转发规则](security/uads/opintro/addrules)**。

![](/images/V4自建添加IP.png)


**高防线路：**
指将采用哪种线路的高防机房，有以下两方面影响：（1）相同线路的高防机房弹性收费的时候仅取IP攻击峰值最高的进行收费；（2）假设高防机房采用的是电信线路，则回源时是同线路，延迟较小。如果源站是联通，则延迟比源站是电信的延迟要大一些。

**源站IP：** 填写需要防护的源站IP地址。

**备注说明：** 填写备注说明，可以为空。

### 3. 防火墙或相关安全防护软件上对所有回源IP放行

如果有安全软件或者硬件限制访问真实源站的来源IP，则需要将回源IP放行。

### 4.1 修改CNAME记录

如果是网站业务，并且具有域名，可以通过修改cname的方式进行高防防护。

首先获取高防的cname（添加源站IP后会在列表中给出），如下图所示：

![](/images/Cname.png)

到DNS服务商处删除A记录，添加CNAME记录。

![](/images/dns_cname.png)

说明：上一步添加IP后，每条记录会生成对应的CNAME值，需要去修改对应网站域名的DNS解析为CNAME解析方式。

通过域名接入高防可以享受自动调度，当受到攻击的时候自动接入到高防，当攻击结束后一段时间自动切回源站。

### 4.2 使用高防IP接入业务

如果是非网站业务，或者不具有域名。一般需要修改客户端配置文件中对应的源站IP或者对应域名的解析IP。将原来解析到源站IP的地方填写为高防IP。

注意：

通用高防到期后，我们将为您保留配置一天，请及时重新购买并开启服务，或者确保不再使用高防IP接入相关业务，否则服务到期一天后配置将自动回收，会导致业务中断。