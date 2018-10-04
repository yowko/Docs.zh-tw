---
title: '&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 5c7e96beee2fc1e4780729e56f10a52b63dde4e8
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580059"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;
定義 HTTP 傳輸的驗證設定。  
  
 \<system.serviceModel>  
\<繫結 >  
\<ws2007HttpBinding>  
\<繫結 >  
\<安全性 >  
\<transport>  
  
## <a name="syntax"></a>語法  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a>類型  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`clientCredentialType`|指定用來對服務驗證用戶端的認證。 此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。|  
|`proxyCredentialType`|指定用來對網域 Proxy 驗證用戶端的認證。 此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。|  
|`realm`|摘要式或基本驗證的驗證領域。 預設為空字串。<br /><br /> 驗證領域至少會指定負責執行驗證之主機的名稱， 也可以指定具有存取權之使用者的集合。 使用者可以查詢驗證領域，判斷其中可以使用的一組使用者名稱和密碼。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|停用安全性。|  
|基本|使用基本驗證。|  
|摘要|使用摘要式驗證。|  
|Ntlm|使用 NTLM 驗證做為 Windows 網域的後援。|  
|Windows|使用整合式 Windows 驗證。|  
|憑證|使用 X.509 憑證來驗證用戶端。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|停用安全性。|  
|基本|使用基本驗證。|  
|摘要|使用摘要式驗證。|  
|Ntlm|使用 NTLM 做為 Windows 網域的後援。|  
|Windows|使用整合式 Windows 驗證。|  
|憑證|使用 X.509 憑證來驗證用戶端。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|代表的安全性功能[ \<lt;ws2007httpbinding&gt >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)項目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
