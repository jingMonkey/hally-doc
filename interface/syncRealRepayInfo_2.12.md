## 2.12同步真实还款信息数据

接口说明 | 该接口用于给合作方同步真实还款信息数据，给风控使用
:-: | :-:    
接口名称 | zhongan.cfp.api.afterLoan

### 请求参数
名称 | 数据类型 | 父节点 |说明 | 必填 
:-: | :-:     | :-:   | :-: | :-: 
apiName | String(40) || 服务名称：__syncRealRepayInfo__| Y
creditContractNo | String(64) | | 授信合同号 | Y
loanOuterNo | String(64) || 合作方借款协议号 | Y
repayOuterNo | String(64) || 合作方还款流水号(每次请求唯一) | Y
repayAmount | BigDecimal || 实际还款总金额（明细汇总） | Y
repayMode | String(32) |  | 还款模式<br>PARTNER_REPAY :合作方代偿<br>PARTNER_COLLECT :合作方代收<br>REPAY_BY_USER : 用户主动还款<br>BACK_REPAY : 回购 | Y
repayType | String(32) |  | 还款类型<br>NORMAL_REPAY :正常还款<br>EARLY_REPAY : 提前还款<br>EARLY_SETTLE : 提前结清<br>OVERDUE_REPAY : 逾期还款 | Y
repayList | List || 还款冲销明细 | Y
installmentNo | Integer | reapyList | 当前第几期 | Y
paidPrincipal | BigDecimal | reapyList | 实还本金 | Y
paidInterest | BigDecimal | reapyList | 实还利息 | Y
paidFee | BigDecimal | reapyList | 实还服务费 | N
paidFundPenalty | BigDecimal | reapyList | 实还资金方的罚息 | N
paidPlatformPenalty | BigDecimal | reapyList | 实还合作方相应期数的罚息 | N
actualRepayDate | String(32) | reapyList | 实际还款日 格式：yyyy-MM-dd HH:mm:ss | Y

### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
loanOuterNo | String(64) | 众安借款协议号,借款合同号 | Y
repayOuterNo | String(24) | 合作方还款流水号 | Y
syncStatus | String(24) | 同步状态：<br>SUCCESS-还款成功<br>FAIL-还款失败 | Y





