---
title: 訊息安全性視窗
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 8706eee341dd1a5852efae0aad5195e09f62fec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183500"
---
# <a name="message-security-windows"></a>訊息安全性視窗
這個範例會示範如何將 <xref:System.ServiceModel.WSHttpBinding> 繫結設定成搭配 Windows 驗證使用的訊息層級安全性。 此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 在這個範例中，服務會由網際網路資訊服務 (IIS) 裝載，而用戶端是主控台應用程式 (.exe)。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 wsHttpBinding>的預設安全性是使用 Windows 身份驗證的消息安全性。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 此示例中的設定檔顯式將[\<安全>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)的屬性`Message`和`mode``clientCredentialType`屬性設置為`Windows`。 這些值是這個繫結的預設值，但是已經明確設定成可示範其使用方式，如下列範例組態所示。  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 用戶端端點組態是由服務端點的絕對位址、繫結及合約所組成。 用戶端繫結是透過適當的 `securityMode` 和 `authenticationMode` 所設定。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"
            binding="wsHttpBinding"
            bindingConfiguration="Binding1"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 服務原始程式碼已修改成可示範如何使用 <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> 存取呼叫者的身分識別。  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 所呼叫的第一個方法 `GetCallerIdentity`，會將呼叫者身分識別的名稱傳回給用戶端。 在主控台視窗中按 ENTER 鍵，即可關閉用戶端。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
