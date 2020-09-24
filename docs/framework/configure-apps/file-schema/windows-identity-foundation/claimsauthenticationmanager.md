---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 9e099b8de486631702548b8a035a46a7e0f4eb30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158470"
---
# \<claimsAuthenticationManager>

為傳入宣告註冊宣告驗證管理員。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a>Syntax  
  
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

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|指定衍生自類別的自訂型別 <xref:System.Security.Claims.ClaimsAuthenticationManager> 。 如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考]。|  
  
### <a name="child-elements"></a>子元素  

 如果沒有 `type` 屬性（attribute），或 `type` 屬性（attribute）參考類別，專案就不會 <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` 採用子項目; 不過，衍生自的類別 <xref:System.Security.Claims.ClaimsAuthenticationManager> 可以定義子設定元素。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  

 透過類別提供的預設行為會回應 <xref:System.Security.Claims.ClaimsAuthenticationManager> 傳入宣告。 如果未 `type` 指定屬性 `type` ，或屬性指定 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，則元素不會 `<claimsAuthenticationManager>` 採用子項目。 您可以指定 `type` 屬性來註冊衍生自類別的型別 <xref:System.Security.Claims.ClaimsAuthenticationManager> ，以執行自訂行為。 衍生的類別可以藉 `<claimsAuthenticationManager>` 由覆寫 <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> 方法來處理這些元素，藉以支援透過專案的子項目進行設定。 為子專案定義的架構是由類別的設計工具所組成。  
  
 `<claimsAuthenticationManager>`元素會設定 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> 屬性。  
  
## <a name="example"></a>範例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
