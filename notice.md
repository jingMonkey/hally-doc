# 简要说明

## 数据格式
* 金额：单位为元，统一是2位小数的数字，例如：1.00
* 日期String(32)：yyyy-MM-dd，除非特别说明
* 时间String(32)：yyyy-MM-dd HH:mm:ss，除非特别说明
* 金额BigDecimal：如果不存在该项费用，统一传0.00
* 用户编号和各个接口的流水号，都是字符串型，最大长度为64个字节。

## 回调地址
合作方后台回调地址使用说明：
有些业务流程比较复杂或者耗时较长，比如支付处理通常耗时较长，我司采取支付完成后，后台通知合作方的方式，把支付结果通知给合作方。
合作方在调用众安接口时候，接口参数中提供后台回调通知notifyUrl，或者提前告知notifyUrl给众安作为系统配置。