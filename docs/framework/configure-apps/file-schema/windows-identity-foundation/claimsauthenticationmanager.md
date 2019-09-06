---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252096"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
為傳入宣告註冊宣告驗證管理員。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**  
  
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
|型別|指定衍生<xref:System.Security.Claims.ClaimsAuthenticationManager>自類別的自訂類型。 如需如何指定屬性的`type`詳細資訊，請參閱 [自訂類型參考]。|  
  
### <a name="child-elements"></a>子元素  
 <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager>如果沒有`type`屬性，或屬性參考類別，則專案不會採用子項目; 不過，衍生自的類別可以定義子設定元素。 `type`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  
 透過<xref:System.Security.Claims.ClaimsAuthenticationManager>類別提供的預設行為會回顯傳入宣告。 如果未`type`指定任何屬性，或`type`屬性指定了<xref:System.Security.Claims.ClaimsAuthenticationManager>類別，則`<claimsAuthenticationManager>`專案不會採用子項目。 您可以指定`type`屬性來註冊衍生自類別的<xref:System.Security.Claims.ClaimsAuthenticationManager>型別，以執行自訂行為。 衍生類別可以藉由覆`<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>寫方法來處理這些專案，藉以支援透過專案的子專案進行設定。 為子專案定義的架構是由類別的設計工具所組成。  
  
 `<claimsAuthenticationManager>`元素會<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>設定屬性。  
  
## <a name="example"></a>範例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
