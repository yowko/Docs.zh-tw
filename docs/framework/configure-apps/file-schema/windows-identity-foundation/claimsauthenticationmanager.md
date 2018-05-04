---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;claimsAuthenticationManager&gt;
註冊的連入宣告的宣告驗證管理員。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthenticationManager >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|指定自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別。 如需有關如何指定`type`屬性，請參閱 [自訂型別參考]。|  
  
### <a name="child-elements"></a>子項目  
 如果沒有任何`type`屬性，或如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別`<claimsAuthenticationManager>`項目不接受子項目; 不過，類別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>可以定義子組態項目。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
  
## <a name="remarks"></a>備註  
 透過所提供的預設行為<xref:System.Security.Claims.ClaimsAuthenticationManager>類別回應連入宣告。 如果沒有`type`指定屬性或`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthenticationManager>類別，`<claimsAuthenticationManager>`項目不接受子項目。 您可以指定`type`屬性註冊型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別來實作自訂行為。 在衍生的類別可以支援透過子項目的組態`<claimsAuthenticationManager>`藉由覆寫的項目<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>方法來處理這些項目。 子項目定義的結構描述是由類別的設計工具。  
  
 `<claimsAuthenticationManager>`項目集合<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>屬性。  
  
## <a name="example"></a>範例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
