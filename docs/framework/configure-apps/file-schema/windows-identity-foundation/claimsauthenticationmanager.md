---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152745"
---
# \<claimsAuthenticationManager>
為傳入宣告註冊宣告驗證管理員。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|指定衍生自類別的自訂類型 <xref:System.Security.Claims.ClaimsAuthenticationManager> 。 如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂類型參考]。|  
  
### <a name="child-elements"></a>子元素  
 如果沒有 `type` 屬性，或 `type` 屬性參考 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，則專案不會 `<claimsAuthenticationManager>` 採用子項目; 不過，衍生自的類別 <xref:System.Security.Claims.ClaimsAuthenticationManager> 可以定義子設定元素。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  
 透過類別提供的預設行為會 <xref:System.Security.Claims.ClaimsAuthenticationManager> 回顯傳入宣告。 如果未 `type` 指定任何屬性 `type` ，或屬性指定了 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，則專案不會 `<claimsAuthenticationManager>` 採用子項目。 您可以指定 `type` 屬性來註冊衍生自類別的型別 <xref:System.Security.Claims.ClaimsAuthenticationManager> ，以執行自訂行為。 衍生類別可以藉 `<claimsAuthenticationManager>` 由覆寫 <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> 方法來處理這些專案，藉以支援透過專案的子專案進行設定。 為子專案定義的架構是由類別的設計工具所組成。  
  
 `<claimsAuthenticationManager>`元素會設定 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> 屬性。  
  
## <a name="example"></a>範例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
