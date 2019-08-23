---
title: <windows> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940301"
---
# <a name="windows-of-clientcredentials-element"></a>\<clientCredentials > 元素\<的 windows >
指定要用於代表用戶端的 Windows 認證的設定。  
  
 \<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
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
|`allowedImpersonationLevel`|設定用戶端與伺服器通訊的模擬喜好設定。 用戶端選取的模擬模式不會在伺服器上強制使用。 有效值包括以下的值：<br /><br /> 發現伺服器可以取得用戶端的身分識別和許可權, 但無法模擬用戶端。<br />申請伺服器可以在本機系統上模擬用戶端的安全性內容。<br />其它伺服器可以在遠端系統上模擬用戶端的安全性內容。<br />匿名伺服器無法模擬或識別用戶端。<br />無未指派模擬層級。<br /><br /> 預設為 Identification。 此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。|  
|`allowNtlm`|將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。<br /><br /> 將此屬性設定`false`為, 會使 Windows Communication Foundation (WCF) 在使用 NTLM 時能夠盡力擲回例外狀況。 請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [保護用戶端安全](../../../wcf/securing-clients.md)
- [使用憑證](../../../wcf/feature-details/working-with-certificates.md)
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
