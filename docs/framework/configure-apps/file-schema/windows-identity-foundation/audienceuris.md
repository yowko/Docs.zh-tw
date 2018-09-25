---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082444"
---
# <a name="ltaudienceurisgt"></a>&lt;audienceUris&gt;
指定是可接受的識別項的信賴憑證者的合作對象 (RP) 的 Uri 的集合。 除非其中一個允許的對象 Uri 的範圍，將不會接受權杖。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<Securitytokenhandlerconfiguration> >  
\<audienceUris >  
  
## <a name="syntax"></a>語法  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|<xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否應該套用對象限制連入的語彙基元。 可能的值為 「 永遠 」，「 從未 」，和 「 BearerKeyOnly"。 預設值為 [一律]。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`<add value=xs:string>`|將所指定的 URI `value` audienceUris 集合屬性。 `value` 屬性 (Attribute) 是必要項。 URI 是區分大小寫。|  
|`<clear>`|清除 audienceUris 集合。 從集合移除所有的識別項。|  
|`<remove value=xs:string>`|移除所指定的 URI `value` audienceUris 集合中的屬性。 `value` 屬性 (Attribute) 是必要項。 URI 是區分大小寫。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性權杖處理常式。|  
  
## <a name="remarks"></a>備註  
 根據預設，集合是空的。使用  `<add>`， `<clear>`，和`<remove>`來修改集合的項目。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 並<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件中設定任何的對象 URI 集合的值允許的對象 URI 限制的使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件。  
  
 `<audienceUris>`項目由<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>類別。 加入至集合的個別 URI 由<xref:System.IdentityModel.Configuration.AudienceUriElement>類別。  
  
> [!NOTE]
>  善用`<audienceUris>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。 上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。  
  
## <a name="example"></a>範例  
 下列 XML 示範如何設定應用程式的可接受對象 Uri。 這個範例會設定一個單一的 URI。 這個 uri 範圍的權杖會被接受，其他所有人將會遭到拒絕。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
