## 2.10归集还款

归集还款：文件方式归集，用于线下还款(包含正常还款/提前结清/回购)、平台代偿、回购
文件名称：批次号.txt
文件类型：线下还款、平台代偿、逾期还款信息同步、回购
文件格式：每行数据为JSON字符串，内容为[还款文件JSON字段](#还款文件JSON字段)

处理流程：
1. 合作方上传还款文件到OSS
2. 众安每天按时间点解析还款文件，对记录进行逐条冲销
3. 逾期还款同步则进行逾期信息流数据同步，再调用下游逾期真实还款信息同步接口
4. 众安回调合作方还款结果/合作方主动查询还款结果

接口说明 | 该接口用于批量文件归集还款
:-: | :-:    
接口名称 | zhongan.cfp.api.afterLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__batchRepay__| Y
batchType | Strng(20) | 归集类型：<br>OFFLINE_REPAY:线下还款<br>PLAFORM_COMPEMSATE:平台代偿<br>OVERDUE_REPAY:逾期还款<br>BUY_BACK:回购 | Y
batchNo | String(50) | 批次号：产品编码+归集类型+日期+两位序号<br>示例：51也牛贷2019年4月8日第一批次线下还款的批次号应为<br>51YNDOFFLINE_REPAY2019040801| Y
fileName | String(64) | 文件名：批次号.txt<br>示例：51也牛贷2019年4月8日第一批次线下还款文件名应为<br><br>51YNDOFFLINE_REPAY2019040801.txt| Y
fileDownloadPath | String(256) | 文件OSS路径：bucket名称/产品编码/repay/日期/文件名<br>示例：<br>__oss的bucket名称会在测试、预发、生产上有所不同，需与具体产品对接人员确认__<br>例如<font color=red>51也牛贷2019年4月8日第一批次线下还款文件合作方上传的路径应为(假设bucket名称为za-pre-ynd)：</font><br><font color=red>za-pre-ynd/51YND/repay/20190408/51YNDOFFLINE_REPAY2019040801.txt</font> | Y
batchCount | Integer | 	总笔数（以还款流水号为维度统计）| Y
batchAmount | BigDecimal | 总金额（实际还款总金额） | Y



### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
batchNo | String(50) | 批次号 | Y
batchStatus | String(24) | 归集状态：<br>PROCESSING-处理中<br>SUCCESS-成功<br>FAIL-失败 | Y

### 还款文件JSON字段
名称 | 数据类型 | 父节点 |说明 | 必填 
:-: | :-:     | :-:   | :-: | :-: 
apiName | String(40) || 服务名称：__repayApply__| Y
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
actualRepayDate | String(32) | reapyList | 实际还款日 格式：yyyy-MM-dd HH:mm:ss | Y

对于归集还款的文件,说明如下:   
1. 除了上面的字段,还要加上公共参数,参见[公共参数](common_2.1.md) 




