---
title: '&lt;netTcpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 0405d3fa8e2155d21fd7bf5b20df39ff3db86b02
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835790"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;netTcpBinding&gt; 的 &lt;transport&gt;
定義設定之端點的訊息層級安全性需求的型別[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
 \<system.ServiceModel>  
\<繫結 >  
\<netTcpBinding>  
\<繫結 >  
\<安全性 >  
\<transport>  
  
## <a name="syntax"></a>語法  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
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
|clientCredentialType|選擇項。 指定當使用傳輸安全性執行用戶端驗證時，要使用的認證類型。<br /><br /> -預設值是`Windows`。<br />-此屬性為類型<xref:System.ServiceModel.TcpClientCredentialType>。|  
|protectionLevel|選擇項。 定義 TCP 傳輸層級的安全性。 簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。 加密會提供傳輸期間的資料層級隱私權。<br /><br /> 預設值是 `EncryptAndSign`。|  
|sslProtocols|SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。 預設值是 Tls&#124;Tls11&#124;Tls12。|  
|policyEnforcement|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。<br /><br /> 1.Never：絕不強制執行此原則 (延伸保護已停用)。<br />2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。<br />3.Always：一律強制執行此原則。 不支援延伸保護的用戶端將無法驗證。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|用戶端為匿名。 這需要服務的憑證。|  
|Windows|使用 SP Negotiation (Kerberos 交涉) 指定用戶端的 Windows 驗證。|  
|憑證|用戶端會透過憑證來驗證。 這會使用 SSL Negotiation，並需要服務的憑證。|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|無保護。|  
|Sign|訊息會經過簽署。|  
|EncryptAndSign|-訊息會經過加密及簽署。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|指定的安全性功能[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。|  
  
## <a name="remarks"></a>備註  
 使用傳輸安全性來達成 SOAP 訊息的完整性與機密性，以及交互驗證。 如果在繫結上選取這個安全性模式，便會使用安全性傳輸設定通道堆疊，並以傳輸安全性 (如 Windows Negotiate 或 SSL over TCP) 保護 SOAP 訊息。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
