---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 1bb0c8ac4cbe11cdfa31beb16b00b3863acabf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltuserprincipalnamegt"></a>&lt;userPrincipalName&gt;
指定要由用戶端驗證之服務的使用者主要名稱 (UPN)。  
  
 如需設定 UPN 的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
\<身分識別 >  
\<userPrincipalName>  
  
## <a name="syntax"></a>語法  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|value|使用者帳戶名稱 (有時稱為使用者登入名稱) 和識別使用者帳戶所在網域的網域名稱。 這是登入 Windows 網域時的標準用法。 格式為： someone@example.com （如同電子郵件地址）。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<身分識別 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## <a name="remarks"></a>備註  
 安全的 Windows Communication Foundation (WCF) 用戶端連接至使用這個身分識別端點進行 SSPI 驗證與端點時，會使用 UPN。  
  
## <a name="example"></a>範例  
 下列組態程式碼會指定要由用戶端驗證之服務的 UPN。  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<身分識別 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
