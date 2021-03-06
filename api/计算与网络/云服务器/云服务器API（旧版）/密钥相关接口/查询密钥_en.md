## 1. API Description
 
This API (DescribeKeyPairs) is used to query keys.

Domain name for API request: <font style="color:red">cvm.api.qcloud.com</font>

* [Key Pair](/document/product/213/6092) is a pair of keys generated by an algorithm. In the generated key pair, one key is open to the public and called public key, and the other key is kept by user and called private key. The public key content of the key can be queried through this API, but the private key content is not retained by system.
*`keyIds.n` or `keyName` input parameters can be used as the filter during the query.

## 2. Input Parameters

The following list only provides API request parameters. For additional parameters, refer to [Public Request Parameters](/document/api/213/6976) page.

| Parameter Name | Required | Type | Description |
|---------|---------|---------|---------|
| keyIds.n | No | String | Key ID (This API allows passing multiple IDs for filtering at a time. For the format of this parameter, refer to `id.n` section of API [Introduction](https://cloud.tencent.com/doc/api/229/568)).
| keyName | No | String | Name of Key.
| projectId | No | String | Project ID, by which the results are filtered.
| offset | No | Int | Offset; default value is 0. For more information about `offset`, refer to the relevant sections in API [Introduction](/doc/api/229/568#.E8.BE.93.E5.85.A5.E5.8F.82.E6.95.B0.E4.B8.8E.E8.BF.94.E5.9B.9E.E5.8F.82.E6.95.B0.E9.87.8A.E4.B9.89).
| limit | No | Int | Number of returned results. The default value is 20, and the maximum is 100. For more information on `limit`, refer to relevant sections in API [Introduction](/doc/api/229/568#.E8.BE.93.E5.85.A5.E5.8F.82.E6.95.B0.E4.B8.8E.E8.BF.94.E5.9B.9E.E5.8F.82.E6.95.B0.E9.87.8A.E4.B9.89).
## 3. Output Parameters
| Parameter Name | Type | Description |
|---------|---------|---------|
| code | Int | Common error code. A value of 0 indicates success, and other values indicate failure. For more information, refer to [Common Error Codes](https://cloud.tencent.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#1.E3.80.81.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81) on Error Code page. |
| message | String | Module error message description depending on API. For more information, refer to [Module Error Codes](https://cloud.tencent.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#2.E3.80.81.E6.A8.A1.E5.9D.97.E9.94.99.E8.AF.AF.E7.A0.81) on Error Code page. |
| totalCount | int | Number of keys matching the filter criteria. |
| keyId | String | ID of key. |
| keyName | String | Name of key. |
| pubkey | String | The public key content of the key. |
| status | int | Status of key. 0 indicates "Normal", and 1 indicates "Abnormal". |
| bindUnInstanceIds | int | List of instance IDs to which the key is bound. |
| bindIps | String List | List of instance IPs to which the key is bound. |
| createTime | String | Creation time of key. |



## 4. Example

Input
<pre>
  https://cvm.api.qcloud.com/v2/index.php?Action=DescribeKeyPairs
  &<<a href="https://cloud.tencent.com/doc/api/229/6976">Public request parameters</a>>
</pre>

Output
```
{
    "code": 0,
    "message": "",
    "data": {
        "totalCount": 2,
        "sshSet": [
            {
                "keyId": "skey-xxxx",
                "keyName": "test1",
                "pubkey": "ssh-rsa xxxxxx skey_32228",
                "status": 0,
                "bindIps": [
                    
                ],
                "createTime": "2015-11-05 17:26:21",
                "bindUnInstanceIds": [
                    
                ]
            },
            {
                "keyId": "skey-xxxxx",
                "keyName": "test2",
                "pubkey": "ssh-rsa xxxxxx skey_32228",
                "status": 0,
                "bindIps": [
                    "xx.xx.xx.xx"
                ],
                "createTime": "2015-11-06 20:52:21",
                "bindUnInstanceIds": [
                    "ins-xxxxxx"
                ]
            },
            
        ]
    },
    
}

```





