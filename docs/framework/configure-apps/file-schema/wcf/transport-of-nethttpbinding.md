---
title: <transport> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 996b3655b0698595256c9a7197f705d46e6e9fcf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169813"
---
# <a name="transport-of-nethttpbinding"></a>\<transport> 的 \<netHttpBinding>

定義可控制 HTTP 傳輸之驗證參數的屬性。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|clientCredentialType|-指定使用 HTTP 驗證執行用戶端驗證時，所要使用的認證類型。  預設值為 `None`。 此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。|  
|proxyCredentialType|-指定在使用透過 HTTP 的 proxy 從網域內執行用戶端驗證時，所要使用的認證類型。 這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。 此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。|  
|realm|字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。 預設值是空字串。|  
|policyEnforcement|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。<br /><br /> 1. 永不–不會強制執行原則， (已停用) 的擴充保護。<br />2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行此原則。<br />3. 一律：一律強制執行此原則。 不支援延伸保護的用戶端將無法驗證。|  
|protectionScenario|此列舉會指定原則強制執行的保護案例。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|傳輸期間不會保護訊息的安全。|  
|基本|指定基本驗證。|  
|Digest|指定摘要式驗證。|  
|Ntlm|指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。|  
|Windows|指定 Windows 整合式驗證。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|-傳輸期間不會保護訊息。|  
|基本|指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的基本驗證。|  
|Digest|指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的摘要式驗證。|  
|Ntlm|指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。|  
|Windows|指定 Windows 整合式驗證。|  
|憑證|使用憑證執行用戶端驗證。 這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|定義的安全性功能 [\<netHttpBinding>](nethttpbinding.md) 。|  
  
## <a name="example"></a>範例  

 下列範例示範透過基本繫結來使用 SSL 傳輸安全性。 根據預設，基本繫結支援 HTTP 通訊。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [確保服務與用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結來設定服務和用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
