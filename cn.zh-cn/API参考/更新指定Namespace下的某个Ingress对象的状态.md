# 更新指定Namespace下的某个Ingress对象的状态<a name="cce_02_0268"></a>

## 功能介绍<a name="section53754776"></a>

This API is used to partially update status of the specified Ingress.

其中以下字段支持更新：

status.loadBalancer

## URI<a name="section14030938"></a>

PATCH /apis/extensions/v1beta1/namespaces/\{namespace\}/ingresses/\{name\}/status

[表1](#d0e42906)描述该API的参数。

**表 1**  参数解释

<a name="d0e42906"></a>
<table><thead align="left"><tr id="row10640301"><th class="cellrowborder" valign="top" width="22.220000000000002%" id="mcps1.2.4.1.1"><p id="p65652297517"><a name="p65652297517"></a><a name="p65652297517"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="17.169999999999998%" id="mcps1.2.4.1.2"><p id="p165661629135114"><a name="p165661629135114"></a><a name="p165661629135114"></a>是否必选</p>
</th>
<th class="cellrowborder" valign="top" width="60.61%" id="mcps1.2.4.1.3"><p id="p14567629115114"><a name="p14567629115114"></a><a name="p14567629115114"></a>描述</p>
</th>
</tr>
</thead>
<tbody><tr id="row10781191719208"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p19781117112019"><a name="p19781117112019"></a><a name="p19781117112019"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p578231710205"><a name="p578231710205"></a><a name="p578231710205"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p978261710207"><a name="p978261710207"></a><a name="p978261710207"></a><span>name of the Ingress</span></p>
</td>
</tr>
<tr id="row19095777"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p3254085"><a name="p3254085"></a><a name="p3254085"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p62254326"><a name="p62254326"></a><a name="p62254326"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p9435611"><a name="p9435611"></a><a name="p9435611"></a>Object name and auth scope, such as for teams and projects.</p>
</td>
</tr>
<tr id="row17811636"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p33456451"><a name="p33456451"></a><a name="p33456451"></a>pretty</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p25618043"><a name="p25618043"></a><a name="p25618043"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p61795587"><a name="p61795587"></a><a name="p61795587"></a>If 'true', then the output is pretty printed.</p>
</td>
</tr>
<tr id="row20635306131"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p1663143041319"><a name="p1663143041319"></a><a name="p1663143041319"></a>body</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p76343015130"><a name="p76343015130"></a><a name="p76343015130"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p156373081311"><a name="p156373081311"></a><a name="p156373081311"></a>-</p>
</td>
</tr>
</tbody>
</table>

## 请求消息<a name="section18662134312520"></a>

**请求参数：**

请求参数的详细描述请参见[表2](创建Ingress.md#d0e42951)。

“Content-Type“的详细描述请参见 [PATCH请求方法操作说明](PATCH请求方法操作说明.md)。

**请求示例：**

```
{
    "status": {
        "loadBalancer": {
            "ingress": [
                {
                    "ip": "10.154.199.81",
                    "hostname": "testaa"
                }
            ]
        }
    }
}
```

## 响应消息<a name="section234242221"></a>

**响应参数：**

响应参数的详细描述请参见[表2](创建Ingress.md#d0e42951)。

**响应示例：**

```
{
    "kind": "Ingress",
    "apiVersion": "extensions/v1beta1",
    "metadata": {
        "name": "ingress-test",
        "namespace": "default",
        "selfLink": "/apis/extensions/v1beta1/namespaces/default/ingresses/ingress-test/status",
        "uid": "29817662-7adb-11e8-a5f8-fa163e458c2a",
        "resourceVersion": "1498365",
        "generation": 3,
        "creationTimestamp": "2018-06-28T13:57:14Z",
        "labels": {
            "isExternal": "true",
            "zone": "data"
        },
        "annotations": {
            "kubernetes.io/ingress.class": "public-elb",
            "protocol": "HTTP",
            "ingress.beta.kubernetes.io/role": "data",
            "ingress.kubernetes.io/secure-backends": "false",
            "kubectl.kubernetes.io/last-applied-configuration": "{\"apiVersion\":\"extensions/v1beta1\",\"kind\":\"Ingress\",\"metadata\":{\"annotations\":{\"ingress.beta.kubernetes.io/role\":\"data\",\"ingress.kubernetes.io/secure-backends\":\"false\",\"kubernetes.io/elb.id\":\"203e27c4-ceaa-4bca-b652-6947f77d1ce0\",\"kubernetes.io/elb.ip\":\"10.154.199.81\",\"kubernetes.io/elb.port\":\"80\",\"kubernetes.io/ingress.class\":\"public-elb\",\"protocol\":\"HTTP\"},\"labels\":{\"isExternal\":\"true\",\"zone\":\"data\"},\"name\":\"ingress-test\",\"namespace\":\"default\"},\"spec\":{\"rules\":[{\"host\":\"test1\",\"http\":{\"paths\":[{\"backend\":{\"serviceName\":\"ingress-test\",\"servicePort\":8086},\"path\":\"/sssss\",\"property\":{\"ingress.beta.kubernetes.io/url-match-mode\":\"STARTS_WITH\"}}]}}]}}\n",
            "kubernetes.io/elb.id": "203e27c4-ceaa-4bca-b652-6947f77d1ce0",
            "kubernetes.io/elb.ip": "10.154.199.81",
            "kubernetes.io/elb.port": "80"
        }
    },
    "spec": {
        "rules": [
            {
                "host": "agaaaa",
                "http": {
                    "paths": [
                        {
                            "path": "/sssss",
                            "backend": {
                                "serviceName": "test",
                                "servicePort": 8080
                            },
                            "property": {
                                "ingress.beta.kubernetes.io/url-match-mode": "STARTS_WITH"
                            }
                        }
                    ]
                }
            }
        ]
    },
    "status": {
        "loadBalancer": {
            "ingress": [
                {
                    "ip": "10.154.199.81",
                    "hostname": "testaa"
                }
            ]
        }
    }
}
```

## 状态码<a name="section161306553915"></a>

[表2](#d0e43055)描述API的状态码。

**表 2**  状态码

<a name="d0e43055"></a>
<table><thead align="left"><tr id="row20813512"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p8172937"><a name="p8172937"></a><a name="p8172937"></a>状态码</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p58028199"><a name="p58028199"></a><a name="p58028199"></a>描述</p>
</th>
</tr>
</thead>
<tbody><tr id="row2663689"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p20485819805"><a name="p20485819805"></a><a name="p20485819805"></a>200</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p454972318016"><a name="p454972318016"></a><a name="p454972318016"></a>success</p>
</td>
</tr>
</tbody>
</table>

异常状态码请参见[状态码](状态码.md)。

