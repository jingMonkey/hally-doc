#2.2授信申请接口

接口说明 | 该接口用于授信申请  
:-: | :-:    
接口名称 | zhongan.cfp.api.beforeLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__creditApply__| Y
creditApplyNo | String(64) | 申请单号 | Y
applyAmount | BigDecimal | 申请额度 | Y
applyDate | String(32) | 申请时间yyyy-MM-dd HH:mm:ss | Y
userName | String(32) | 用户姓名 | Y
certType | String(16) | 证件类型：ID-身份证 | Y
certNo | String(32) | 证件号码 | Y
userMobile | String(20) | 手机号码 | Y
riskInfo | String(4096) | 风控扩展信息JSON格式，具体详见各个产品风控提供的授信风控字段 | Y

### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
thirdUserNo | String(64) | 合作方用户编号 | Y
creditApplyNo | String(64) | 申请单号  | Y
applyStatus | String(24) | 申请状态 <br>PROCESSING：处理中<br>SUCCESS：成功<br>FAIL：失败  | Y

