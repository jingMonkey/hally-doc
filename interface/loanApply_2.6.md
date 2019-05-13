## 2.6借款申请

接口说明 | 该接口用于用户发起借款申请
:-: | :-:    
接口名称 | zhongan.cfp.api.inLoan

### 请求参数

名称 | 数据类型 | 父节点 |说明 | 必填 
:-: | :-:     | :-:   | :-: | :-: 
apiName | String(40) || 服务名称：__loanApply__| Y
loanApplyNo | String(64) || 借款申请号 | Y
loanOuterNo | String(64) || 合作方借款协议号 | N
creditContractNo | String(64) || 借款金额 | Y
loanAmount | BigDecimal || 发卡行编码 | Y
loanDate | String(32) || 借款时间 | Y
installmentNo | Integer || 借款期数 | Y
installmentRate | BigDecimal || 对客年利率，分期利率 | Y
repayWay | String(30) || 还款方式:<br>MONTH_INTEREST-先息后本(月付利息)<br>FULL_PAYMENT-利随本清(趸交)<br>EQUAL_INSTALLMENT-等额本息<br>EQUAL_PRINCIPAL-等额本金<br>EQUAL_INTEREST-等本等息<br>QUARTERLY_INTEREST-先息后本(季付利息)<br>DAILY_INTEREST-按日计息<br>__默认为EQUAL_INSTALLMENT-等额本息__ | N
certStartDate | String(10) || 身份证起始日期：yyyyMMdd | Y
certExpireDate | String(10) || 身份证截止日期：yyyyMMdd | Y
cardInfos | List | | 卡信息（支持传入多张卡：一张还款卡、一张放款卡；不可传入多张放款卡）：__必传入一张放款卡__ | N
cardName | String(64) | cardInfos | 持卡人姓名 | Y
certNo | String(20) | cardInfos | 持卡人身份证号码 | Y
bankName | String(100) | cardInfos | 银行名称 | Y
bankCode | String(20) | cardInfos | 银行编码 | Y
bankCardNo | String(64) | cardInfos | 银行卡号 | Y
cardPhone | String(64) | cardInfos | 预留手机号码 | Y
cardType | String(24) | cardInfos | 卡类型:<br>DEBIT_CARD-借记卡<br>CREDIT_CARD-贷记卡<br>SEMI_CREDIT_CARD-准贷记卡 | Y
cardUse | String(24) | cardInfos | 持卡人姓名 | Y
loanPurpose | String(2) || 借款用途:<br>"01"- "房贷"<br>"02"- "车贷"<br>"03"- "消费贷"<br>"04"- "经营贷"<br>"05"- "现金贷"<br>"06"- "偿还信用卡"<br>"07"- "购物"<br>"08"- "流动性经营资金"<br>"09"- "个人日常消费"<br>"10"- "家电数码"<br>"11"- "旅游"<br>"12"- "教育"<br>"13"- "装修"<br>"14"- "医疗"<br>"15"- "租房"<br>"16"- "经营场所、设备支出"<br>"99"- "其他"
riskInfo | String(4096) | | 贷中风控决策扩展信息，具体详见各个产品风控提供的贷中风控字段

### 返回参数
名称 | 数据类型 | 父节点 |说明 | 必填 
:-: | :-:     | :-: | :-: | :-: 
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




