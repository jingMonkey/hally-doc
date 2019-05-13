## 2.9还款结果查询

接口说明 | 该接口用于查询单笔还款结果
:-: | :-:    
接口名称 | zhongan.cfp.api.afterLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__repayApply__| Y
repayOuterNo | String(64) | 合作方还款流水号(每次请求唯一) | Y


### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
loanOuterNo | String(64) | 众安借款协议号,借款合同号 | Y
repayOuterNo | String(24) | 合作方还款流水号 | Y
repayAmount | BigDecimal | 实际还款总金额 | N
repayStatus | String(24) |还款状态：<br>PROCESSING-还款中<br>SUCCESS-还款成功<br>FAIL-还款失败 | Y





