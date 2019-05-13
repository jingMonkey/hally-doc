## 3.3 还款结果通知

接口说明 | 该接口用于还款结果回调通知
:-: | :-:    
接口地址 | 由合作方提供给众安配置回调地址


名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
respCode | String(20) | 结果编码。参见[结果代码](/base/resultCode.md)| Y
respMsg | String(256) | 结果描述| Y
loanOuterNo | String(64) | 众安借款协议号,借款合同号 | Y
repayOuterNo | String(24) | 合作方还款流水号 | Y
repayAmount | BigDecimal | 实际还款总金额 | N
repayStatus | String(24) |还款状态：<br>PROCESSING-还款中<br>SUCCESS-还款成功<br>FAIL-还款失败 | Y








