---
title: <transport> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735928"
---
# <a name="transport-of-nettcpbinding"></a>\<netTcpBinding> 的 \<transport>
定義以[\<netTcpBinding >](nettcpbinding.md)設定之端點的訊息層級安全性需求類型。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|clientCredentialType|選擇項。 指定當使用傳輸安全性執行用戶端驗證時，要使用的認證類型。<br /><br /> -預設值為 `Windows`。<br />-這個屬性的類型是 <xref:System.ServiceModel.TcpClientCredentialType>。|  
|protectionLevel|選擇項。 定義 TCP 傳輸層級的安全性。 簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。 加密會提供傳輸期間的資料層級隱私權。<br /><br /> 預設值是 `EncryptAndSign`。|  
|sslProtocols|SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。 預設值為 [&#124;Tls&#124;Tls11 Tls12]。|  
|policyEnforcement|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。<br /><br /> 1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。<br />2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。<br />3. always –一律強制執行原則。 不支援延伸保護的用戶端將無法驗證。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|None|用戶端為匿名。 這需要服務的憑證。|  
|Windows|使用 SP Negotiation (Kerberos 交涉) 指定用戶端的 Windows 驗證。|  
|憑證|用戶端會透過憑證來驗證。 這會使用 SSL Negotiation，並需要服務的憑證。|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|None|無保護。|  
|Sign|訊息會經過簽署。|  
|EncryptAndSign|-訊息會經過加密和簽署。|  
  
### <a name="child-elements"></a>子項目  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security >](security-of-nettcpbinding.md)|指定[\<netTcpBinding >](nettcpbinding.md)的安全性功能。|  
  
## <a name="remarks"></a>備註  
 使用傳輸安全性來達成 SOAP 訊息的完整性與機密性，以及交互驗證。 如果在繫結上選取這個安全性模式，便會使用安全性傳輸設定通道堆疊，並以傳輸安全性 (如 Windows Negotiate 或 SSL over TCP) 保護 SOAP 訊息。  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
