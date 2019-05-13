## 3.2借款结果通知

接口说明 | 该接口用于放款结果回调通知
:-: | :-:    
接口地址 | 由合作方提供给众安配置回调地址


名称 | 数据类型 | 父节点 | 说明 | 必填 
:-: | :-:     | :-: | :-: | :-: 
respCode | String(20) |  | 结果编码。参见[结果代码](/base/resultCode.md)| Y
respMsg | String(256) |  | 结果描述| Y
loanOuterNo | String(64) | | 众安借款协议号,借款合同号 | Y
loanStatus | String(24) | | 借款状态：<br>PROCESSING：放款中<br>SUCCESS：放款成功<br>FAIL：放款失败 | Y
withdrawDate | Date | | 放款时间 | N
loanMsg | String(500) || 借款结果描述 | N
fundCode | String(32) || 资金方编码 | N
fundYearRate | BigDecimal || 资金方利率 | N
platformFee | BigDecimal || 平台服务费 | N
insurancePremium | BigDecimal || 签单保费,秒扣的保费 | N
riskPremium | BigDecimal || 风险保费 | N
basicPremium | BigDecimal || 基础保费 | N
__repayPlanList__ | List || *还款计划，仅放款成功时返回* | N
installmentNo | Integer |repayPlanList| 当前第几期 | N
principal | BigDecimal |repayPlanList| 应还本金 | N
interest | BigDecimal |repayPlanList| 应还利息 | N
agreeRepayDate | Date |repayPlanList| 应还款日 | N








