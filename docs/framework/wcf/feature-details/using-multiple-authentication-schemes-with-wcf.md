---
title: 搭配 WCF 使用多個驗證配置
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: cdf40d6c0ca25a21cbdac07abab04d2bc144bf69
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521695"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>搭配 WCF 使用多個驗證配置
WCF 現在允許您在單一端點上指定多個驗證配置。 此外，Web 裝載服務可以直接從 IIS 繼承驗證設定。 自我裝載服務可以指定可使用的驗證配置。 如需在 IIS 中設定驗證設定的詳細資訊，請參閱[IIS 驗證](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS 裝載的服務  
 對於 IIS 裝載的服務，設定您希望在 IIS 中使用的驗證配置。 然後在您服務的 web.config 檔案中，將繫結組態 clientCredential 類型指定為"InheritedFromHost"下列 XML 程式碼片段所示：  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 您可以指定您只想要使用 ServiceAuthenticationBehavior 服務搭配使用的驗證配置的子集或\<serviceAuthenticationManager > 項目。 在程式碼中進行這項設定時，請使用 ServiceAuthenticationBehavior，如下列程式碼片段所示。  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 當設定此組態檔中，使用\<serviceAuthenticationManager > 項目，如下列 XML 程式碼片段所示。  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 這將確保只會根據在 IIS 中選取的部分，考慮將這裡列出的驗證配置子集套用在服務端點。 這表示開發人員可以在 serviceAuthenticationManager 清單中省略該項基本驗證，將其從清單中排除，即使已在 IIS 中啟用亦同，這項驗證將不會套用在服務端點上。  
  
## <a name="self-hosted-services"></a>自我裝載的服務  
 自我裝載服務的設定方式有點不同，因為沒有可繼承其設定的 IIS。 您在這裡使用\<serviceAuthenticationManager > 項目或 ServiceAuthenticationBehavior 來指定可供繼承的驗證設定。 在程式碼中，看起來像這樣：  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 在組態中，看起來像這樣：  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 然後您可以在繫結設定中指定 InheritFromHost，如下列 XML 片段所示。  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 或者，您可在 HTTP 傳輸繫結元素上設定驗證配置，以指定自訂繫結中的驗證配置，如下列組態片段所示。  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>另請參閱  
 [繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [端點：位址、繫結和合約](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [設定系統提供的繫結](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [繫結](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [繫結](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)
