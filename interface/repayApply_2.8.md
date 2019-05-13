## 2.8还款申请

接口说明 | 该接口用于处理用户单笔还款，包含主动还款、提前还款、提前结清
:-: | :-:    
接口名称 | zhongan.cfp.api.afterLoan

### 请求参数

名称 | 数据类型 | 父节点 |说明 | 必填 
:-: | :-:     | :-:   | :-: | :-: 
apiName | String(40) || 服务名称：__repayApply__| Y
loanOuterNo | String(64) || 合作方借款协议号 | Y
repayOuterNo | String(64) || 合作方还款流水号(每次请求唯一) | Y
repayAmount | BigDecimal || 实际还款总金额（明细汇总） | Y
cardInfo | CardInfo || 还款卡实体类 | N
bankName | String(64) | cardInfo | 还款卡银行名称 | N
bankCode | String(64) | cardInfo | 还款卡银行编码 | N
cardName | String(64) | cardInfo | 持卡人姓名 | N
certNo | String(20) | cardInfo | 持卡人身份证号码 | N
bankCardNo | String(64) | cardInfo | 还款卡号 | N
cardPhone | String(64) | cardInfo | 还款卡预留手机号码|N
cardType | String(16) | cardInfo | 卡类型:<br>DEBIT_CARD:借记卡 | N
repayMode | String(32) |  | 还款模式<br>PARTNER_REPAY :合作方代偿<br>PARTNER_COLLECT :合作方代收<br>REPAY_BY_USER : 用户主动还款<br>BACK_REPAY : 回购 | Y
repayType | String(32) |  | 还款类型<br>NORMAL_REPAY :正常还款<br>EARLY_REPAY : 提前还款<br>EARLY_SETTLE : 提前结清<br>OVERDUE_REPAY : 逾期还款 | Y
repayList | List || 还款冲销明细 | Y
installmentNo | Integer | reapyList | 当前第几期 | Y
paidPrincipal | BigDecimal | reapyList | 实还本金 | Y
paidInterest | BigDecimal | reapyList | 实还利息 | Y
paidFee | BigDecimal | reapyList | 实还服务费 | N
actualRepayDate | String(32) | reapyList | 实际还款日 格式：yyyy-MM-dd HH:mm:ss | Y



### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
loanOuterNo | String(64) | 众安借款协议号,借款合同号 | Y
repayOuterNo | String(24) | 合作方还款流水号 | Y
repayAmount | BigDecimal | 实际还款总金额 | Y
repayStatus | String(24) |还款状态：<br>PROCESSING-还款中<br>SUCCESS-还款成功<br>FAIL-还款失败 | Y





