## 2.13同步真实用户还款计划

接口说明 | 该接口用于给合作方同步真实对客用户还款计划数据，给风控使用
:-: | :-:    
接口名称 | zhongan.cfp.api.afterLoan

### 请求参数
名称 | 数据类型 |说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__syncRealRepayInfo__| Y
creditContractNo | String(64) | 授信合同号 | Y
loanOuterNo | String(64) | 合作方借款协议号 | Y
repayOuterNo | String(64) | 合作方还款流水号(每次请求唯一) | Y
status | String(20) | 状态 WAIT_REPAY-未还款 REPAYED-已还款 | Y
installmentNo | Integer | 分期期数 | Y
totalInstallmentNo | Integer | 总期数 | Y
duePrincipal | BigDecimal(15,2) | 应还本金 元 | Y
dueInterest | BigDecimal(15,2) | 应还利息 元 | Y
dueCharge | BigDecimal(15,2) | 应还费用 服务费 元 | N
dueFundPenalty | BigDecimal(15,2) | 应还资金方的罚息 | N
duePlatformPenalty | BigDecimal(15,2) | 应还合作方相应期数的罚息 | N
dueOther | BigDecimal(15,2) | 其它应还费用 元 | N
actualRepayDate | String(32) | 实际还款日 格式：yyyy-MM-dd HH:mm:ss |Y
paidPrincipal | BigDecimal(15,2) | 实还本金 元 | Y
paidInterest | BigDecimal(15,2) | 实还利息 元 | Y
paidCharge | BigDecimal(15,2) | 实还费用 服务费 元 | N
paidFundPenalty | BigDecimal(15,2) | 实还资金方的罚息 | N
paidPlatformPenalty | BigDecimal(15,2) | 实还合作方相应期数的罚息 | N
paidOther | BigDecimal(15,2) | 其它实还费用 元 | N
repayType | String(32) | 还款类型<br>NORMAL_REPAY :正常还款<br>EARLY_REPAY : 提前还款<br>EARLY_SETTLE : 提前结清<br>OVERDUE_REPAY : 逾期还款 | Y
claimApplyNo | String(64) | 理赔号 | N
reportApplyNo | String(64) | 报案号 | N
reportStatus | String(1) |  报案状态 Y-报案 N-未报案 | N


### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
loanOuterNo | String(64) | 众安借款协议号,借款合同号 | Y
repayOuterNo | String(24) | 合作方还款流水号 | Y
syncStatus | String(24) | 同步状态：<br>SUCCESS-还款成功<br>FAIL-还款失败 | Y





