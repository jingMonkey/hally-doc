## 2.5绑卡/鉴权

接口说明 | 该接口用于绑定用户相关银行卡操作
:-: | :-:    
接口名称 | zhongan.cfp.api.beforeLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__bindCard__| Y
bankName | String(100) | 银行名称 | Y
cardName | String(64) | 银行户名 | Y
bankCardNo | String(64) | 银行账号 | Y
bankCode | String(20) | 发卡行编码 | Y
cardPhone | String(20) | 银行预留手机号 | Y
certNo | String(20) | 身份证件号 | Y
cardUse | String(24) | 卡用途：<br>WITHDRAW:放款<br>REPAY:还款<br>WITHDRAW_AND_REPAY:放款与还款 | Y
transType | Integer | 绑卡业务类型:<br>1-发验证码<br>2-根据验证码绑卡<br>3-无需验证码-绑卡 | Y
smsCode | String(6) | 短信验证码：当transType为2时此字段不能为空 为3时 默认填写666666 | N
cardType | String(24) | 卡类型:<br>DEBIT_CARD:借记卡<br>CREDIT_CARD:贷记卡<br>SEMI_CREDIT_CARD:准贷记卡（只可用于放款） | Y

### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
cardStatus | String(20) | 绑卡状态：<br>UNBIND-未绑定<br>BIND-已绑定 | N




