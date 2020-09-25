---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: c9787d8e0d8d66494bbf2dbd0e24ff39178a4cde
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189899"
---
# \<audienceUris>

指定 Uri 的集合，這些 Uri 是信賴憑證者 (RP) 可接受的識別碼。 除非權杖屬於其中一個允許的 Audience URI，否則不接受這些權杖。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|mode|<xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否應將物件限制套用至連入權杖。 可能的值為「一律」、「永不」和「BearerKeyOnly」。 預設值為「一律」。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`<add value=xs:string>`|將屬性所指定的 URI 加入 `value` 至 audienceUris 集合。 `value` 屬性 (Attribute) 是必要項。 URI 會區分大小寫。|  
|`<clear>`|清除 audienceUris 集合。 所有識別碼都會從集合中移除。|  
|`<remove value=xs:string>`|`value`從 audienceUris 集合中移除屬性所指定的 URI。 `value` 屬性 (Attribute) 是必要項。 URI 會區分大小寫。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  

 根據預設，集合是空的;使用 `<add>` 、 `<clear>` 和 `<remove>` 元素來修改集合。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 物件會使用物件 uri 集合中的值，來設定物件中任何允許的 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 物件 URI 限制。  
  
 `<audienceUris>`元素是由 <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> 類別表示。 加入至集合的個別 URI 會由 <xref:System.IdentityModel.Configuration.AudienceUriElement> 類別表示。  
  
> [!NOTE]
> 使用 `<audienceUris>` 元素做為專案的子專案 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。 元素上的設定會覆 `<securityTokenHandlerConfiguration>` 寫元素上的設定 `<identityConfiguration>` 。  
  
## <a name="example"></a>範例  

 下列 XML 說明如何為應用程式設定可接受的物件 Uri。 此範例會設定單一 URI。 將接受此 URI 範圍內的權杖，所有其他權杖都會遭到拒絕。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
