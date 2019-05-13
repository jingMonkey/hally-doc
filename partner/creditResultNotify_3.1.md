## 3.1授信结果通知

接口说明 | 该接口用于授信结果回调通知
:-: | :-:    
接口地址 | 由合作方提供给众安配置回调地址


名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
respCode | String(20) | 结果编码。参见[结果代码](/base/resultCode.md) | Y
respMsg | String(256) | 结果描述 | Y
thirdUserNo | String(64) | 合作方用户编号 | Y
creditApplyNo | String(64) | 申请单号  | Y
applyAmount | BigDecimal | 申请金额 | Y
applyDate | String(32) | 申请时间 | Y
applyStatus | String(24) | 申请状态 <br>PROCESSING：处理中<br>SUCCESS：成功<br>FAIL：失败  | Y
creditAmount | BigDecimal | 授信额度 | N
creditContractNo | String(64) | 授信协议号，仅授信成功时返回 | N
availableAmount | BigDecimal | 可用额度 | N








