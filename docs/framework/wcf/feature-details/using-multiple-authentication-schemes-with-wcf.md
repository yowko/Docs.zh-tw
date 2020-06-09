---
title: 搭配 WCF 使用多個驗證配置
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 1874963573a6ec12939bd12b79574f1e2c889bfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600214"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>搭配 WCF 使用多個驗證配置
WCF 現在允許您在單一端點上指定多個驗證配置。 此外，Web 裝載服務可以直接從 IIS 繼承驗證設定。 自我裝載服務可以指定可使用的驗證配置。 如需在 IIS 中設定驗證設定的詳細資訊，請參閱[Iis 驗證](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS 裝載的服務  
 對於 IIS 裝載的服務，設定您希望在 IIS 中使用的驗證配置。 然後在您服務的 web.config 檔案中，將系結設定中的 clientCredential 類型指定為 "InheritedFromHost"，如下列 XML 程式碼片段所示：  
  
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
  
 您可以使用 ServiceAuthenticationBehavior 或專案，指定您只想要將驗證配置子集與您的服務搭配使用 \<serviceAuthenticationManager> 。 在程式碼中進行這項設定時，請使用 ServiceAuthenticationBehavior，如下列程式碼片段所示。  
  
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
  
 在設定檔中進行此設定時，請使用 \<serviceAuthenticationManager> 元素，如下列 XML 程式碼片段所示。  
  
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
 自我裝載服務的設定方式有點不同，因為沒有可繼承其設定的 IIS。 在這裡，您會使用 \<serviceAuthenticationManager> 元素或 ServiceAuthenticationBehavior 來指定將繼承的驗證設定。 在程式碼中，看起來像這樣：  
  
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
  
## <a name="see-also"></a>請參閱

- [繫結和安全性](bindings-and-security.md)
- [端點：位址、繫結和合約](endpoints-addresses-bindings-and-contracts.md)
- [設定系統提供的繫結](configuring-system-provided-bindings.md)
- [自訂繫結的安全性功能](security-capabilities-with-custom-bindings.md)
- [繫結](bindings.md)
- [自訂繫結](../extending/custom-bindings.md)
