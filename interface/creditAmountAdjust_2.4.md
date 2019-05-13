## 2.4授信调额申请

接口说明 | 该接口用于授信额度调整
:-: | :-:    
接口名称 | zhongan.cfp.api.beforeLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__creditAmountAdjust__| Y
creditApplyNo | String(64) | 申请单号 | Y
adjustAmount | BigDecimal | 调额申请额度 | Y
adjustDate | String(32) | 调额申请时间 | Y

### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
thirdUserNo | String(64) | 合作方用户编号 | Y
creditApplyNo | String(64) | 申请单号  | Y
adjustStatus | String(24) | 申请状态 <br>PROCESSING：处理中<br>SUCCESS：成功<br>FAIL：失败  | Y



