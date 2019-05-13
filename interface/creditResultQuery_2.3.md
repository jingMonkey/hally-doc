## 2.3授信结果查询

接口说明 | 该接口用于查询用户的授信结果
:-: | :-:    
接口名称 | zhongan.cfp.api.beforeLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__creditResultQuery__| Y
creditApplyNo | String(64) | 申请单号 | Y

### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
thirdUserNo | String(64) | 合作方用户编号 | Y
creditApplyNo | String(64) | 申请单号  | Y
applyAmount | BigDecimal | 申请金额 | Y
applyDate | String(32) | 申请时间 | Y
applyStatus | String(24) | 申请状态 <br>PROCESSING：处理中<br>SUCCESS：成功<br>FAIL：失败  | Y
creditAmount | BigDecimal | 授信额度 | N
creditContractNo | String(64) | 授信协议号，仅授信成功时返回 | N
availableAmount | BigDecimal | 可用额度 | N


