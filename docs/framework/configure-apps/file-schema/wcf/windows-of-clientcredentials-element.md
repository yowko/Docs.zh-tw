---
title: <windows> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: b5e92745b9e39534d2a0bc35504c2dbc8346d2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221016"
---
# <a name="windows-of-clientcredentials-element"></a>\<windows > 的\<clientCredentials > 項目
指定要用於代表用戶端的 Windows 認證的設定。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<clientCredentials>  
\<windows>  
  
## <a name="syntax"></a>語法  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|設定用戶端與伺服器通訊的模擬喜好設定。 用戶端選取的模擬模式不會在伺服器上強制使用。 有效值包括以下的值：<br /><br /> 識別：伺服器可以取得身分識別和權限的用戶端，但無法模擬用戶端。<br />模擬：伺服器可以模擬用戶端的本機系統上的安全性內容。<br />-委派：伺服器可以模擬用戶端的安全性內容，在遠端系統上。<br />匿名：伺服器無法模擬或識別用戶端。<br />-None:未指派模擬等級。<br /><br /> 預設為 Identification。 此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。|  
|`allowNtlm`|將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。<br /><br /> 將此屬性設定為`false`會導致 Windows Communication Foundation (WCF) 讓最大努力擲回例外狀況，如果使用 NTLM。 請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)
- [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
