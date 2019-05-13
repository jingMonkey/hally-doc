## 2.11归集还款结果查询

接口说明 | 该接口用于批量文件归集还款结果查询
:-: | :-:    
接口名称 | zhongan.cfp.api.afterLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__batchRepayResultQuery__| Y
batchNo | String(50) | 批次号 | Y

### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
batchNo | String(50) | 批次号 | Y
batchCount | Integer | 总笔数（以还款流水号为维度统计） | Y
batchAmount | BigDecimal | 总金额（实际对公代扣总金额） | Y
successCount | Integer | 成功笔数(处理成功时返回) | N
successAmount | BigDecimal | 成功金额(处理成功时返回) | N
batchStatus | String(24) | 归集状态：<br>PROCESSING-处理中<br>SUCCESS-成功<br>FAIL-失败 | Y





