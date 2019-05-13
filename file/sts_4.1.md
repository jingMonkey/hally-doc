## 4.1STS信息获取

OSS为阿里云的对象存储服务，OSS上传文件需要设置为加密模式上传。

oss路径说明: ${bucketName}/${productCode}/${fileType}/${withdrawDate}/${fileName}

举例: za-pre-wld/WLDBZX/idimg/20180418/ back_card_借款协议号.jpg

 

阿里云STS (Security Token Service) 是为阿里云账号（或RAM用户）提供短期访问权限管理的云服务。通过STS，您可以为联盟用户（您的本地账号系统所管理的用户）颁发一个自定义时效和访问权限的访问凭证。联盟用户可以使用STS短期访问凭证直接调用阿里云服务API，或登录阿里云管理控制台操作被授权访问的资源。

 

交互流程详细如下：


1、合作方上传请求;
合作方由对接人控制，合作方通过您提供的API或者http方式请求上传凭证，每个bucket可对应多个合作方，可使用object目录区分，并根据object进行赋权。
2、众安应用向阿里云STS请求获取一个安全令牌（Security Token）：
a、在调用STS之前，众安应用需要确定合作方的最小访问权限（使用policy语法描述）以及授权的过期时间；
b、通过调用STS的AssumeRole（扮演角色）接口来获取安全令牌。
3、阿里云STS返回给众安应用一个有效的访问凭证；
返回信息包含：安全令牌（Security Token）、临时访问密钥（AccesskeyId和AccesskeySecret）以及过期时间。
4、众安应用将访问凭证信息返回给合作方：
合作方可缓存该凭证，当凭证过期时再次请求新的有效凭证。
5、合作方使用STS凭证请求阿里云API，进行OSS上传操作。
Api参考：
[https://help.aliyun.com/document_detail/28756.html?spm=a2c4g.11186623.6.709.6Y9jpA](https://help.aliyun.com/document_detail/28756.html?spm=a2c4g.11186623.6.709.6Y9jpA)

SDK参考：
[https://help.aliyun.com/document_detail/28786.html?spm=a2c4g.11186623.6.726.XYx9LN](https://help.aliyun.com/document_detail/28786.html?spm=a2c4g.11186623.6.726.XYx9LN)

具体例子参考：
[https://blog.csdn.net/fighterandknight/article/details/80517646](https://blog.csdn.net/fighterandknight/article/details/80517646)

接口说明 | 该接口用于获取STS信息，在每次操作oss前调用
:-: | :-:    
接口名称 | zhongan.cfp.api.beforeLoan

### 请求参数

名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
apiName | String(40) | 服务名称：__applyTempOssInfo__| Y



### 返回参数
名称 | 数据类型 | 说明 | 必填 
:-: | :-:     | :-: | :-: 
stsInfo | String(1024) | sts信息 | Y

### stsInfo返回例子
```
{

  "msg": "success",

  "requestId": "6020EDB3-AE33-418D-96EA-BC78F8E44621",

  "assumedRoleUser": {

    "Arn": "acs:ram::1875377503395421:role/za-pre-wld-test/client",

    "AssumedRoleId": "319254677154847859:client"

  },

  "credentials": {

    "SecurityToken": "CAIS9AF1q6Ft5B2yfSjIr4v9MfCGt4tmz4ixVWL7iUhsRLlG3aH/gTz2IHlFfnRsB+8Zt/kzlGxX5vsTlq94T55IQ1CctTjLHzwTo22beIPkl5Gfz95t0e+IewW6Dxr8w7WhAYHQR8/cffGAck3NkjQJr5LxaTSlWS7OU/TL8+kFCO4aRQ6ldzFLKc5LLw950q8gOGDWKOymP2yB4AOSLjIx6lUh0jwgtPzkmZzBtkCHtjCglL9J/baWC4O/csxhMK14V9qIx+FsfsLDqnUJukIXqPkp0/UZpWeb4YHAUkM28RzDK/DZt8JrIEpla7MmCxuQZ19BST8TGoABKs55ITMnHiWztEI74bVObZbN1fhz8KsIO+dwl3mT0L1n46OC/PzO963hJtZFNGIWI9ewUAJoJ2OzG8eZI1zv3mwaasi46xPx68jvzNY9DZwS3DE3bmSbIC14NDSQtA/06UUuRlqXUFFQImi6ZjZKx//3C+eTmjGI5PFzlc06vkQ=",

    "AccessKeyId": "STS.NHHzJ2ZTGxJZWDJmH9H6j2dTc",

    "AccessKeySecret": "87GDJ5PkDhpCXTqFFgXD5NpM5KcPiay6skdUrxGnJwq5",

    "Expiration": "2018-06-15T11:29:09Z"

  },

  "desc": "success"

}
```
备注：使用方式请参考阿里得官方文档：[https://www.alibabacloud.com/help/zh/doc-detail/32016.htm?spm=a2c63.p38356.b99.127.5bde42a90e2GJb](https://www.alibabacloud.com/help/zh/doc-detail/32016.htm?spm=a2c63.p38356.b99.127.5bde42a90e2GJb)



