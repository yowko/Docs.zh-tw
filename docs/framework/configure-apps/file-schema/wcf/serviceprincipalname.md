---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 75e95bcbaee229f19bdfdd119b548ed612f4ddaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204402"
---
# <a name="serviceprincipalname"></a>\<servicePrincipalName>
由其服務原則名稱 (SPN) 指定的服務身分識別。  
  
 如需有關如何設定 SPN 的詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
 \<identity>  
\<servicePrincipalName>  
  
## <a name="syntax"></a>語法  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|value|用戶端用來唯一識別服務執行個體的名稱。 若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。 若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## <a name="remarks"></a>備註  
 安全的 Windows Communication Foundation (WCF) 用戶端連接至使用這個身分識別端點對端點進行 SSPI 驗證時，會使用 SPN。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
