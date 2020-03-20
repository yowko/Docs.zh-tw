---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152745"
---
# <a name="claimsauthenticationmanager"></a>\<聲明身份驗證管理器>
註冊傳入聲明的聲明身份驗證管理器。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<聲明身份驗證管理器>**  
  
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
|type|指定派生自類的<xref:System.Security.Claims.ClaimsAuthenticationManager>自訂類型。 有關如何指定屬性的詳細資訊，`type`請參閱 [自訂類型引用]。|  
  
### <a name="child-elements"></a>子元素  
 如果沒有`type`屬性，或者該`type`屬性引用該<xref:System.Security.Claims.ClaimsAuthenticationManager>類，則`<claimsAuthenticationManager>`元素不會採用子項目;如果該屬性引用該類，則元素不會採用子項目。但是，派生自的<xref:System.Security.Claims.ClaimsAuthenticationManager>類可以定義子配置元素。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<身份配置>](identityconfiguration.md)|指定服務等級標識設置。|  
  
## <a name="remarks"></a>備註  
 通過<xref:System.Security.Claims.ClaimsAuthenticationManager>類提供的預設行為與傳入的聲明相呼應。 如果未`type`指定屬性或`type`屬性指定類，<xref:System.Security.Claims.ClaimsAuthenticationManager>則`<claimsAuthenticationManager>`元素不會採用子項目。 可以指定屬性`type`以註冊從<xref:System.Security.Claims.ClaimsAuthenticationManager>類派生的類型以實現自訂行為。 派生類可以通過重寫`<claimsAuthenticationManager>`<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>處理這些元素的方法來支援通過元素的子項目進行配置。 為子項目定義的架構由類的設計器決定。  
  
 元素`<claimsAuthenticationManager>`設置<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>屬性。  
  
## <a name="example"></a>範例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
