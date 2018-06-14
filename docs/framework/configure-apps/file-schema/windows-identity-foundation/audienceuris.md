---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7415cb3f1792d2de566161ae6c348ef591b4a0c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755990"
---
# <a name="ltaudienceurisgt"></a>&lt;audienceUris&gt;
指定是可接受的識別項的信賴憑證者的合作對象 (RP) 的 Uri 的集合。 除非它們適用其中一個允許的 audience Uri，將不會接受權杖。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
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
|模式|<xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否應該套用對象限制傳入語彙基元。 可能的值為 「 永遠 」、 「 永不 」，和 「 BearerKeyOnly"。 預設為"Always"。 選擇性。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|`<add value=xs:string>`|加入所指定的 URI `value` audienceUris 集合屬性。 `value` 屬性 (Attribute) 是必要項。 URI 是區分大小寫。|  
|`<clear>`|清除 audienceUris 集合。 從集合移除所有的識別項。|  
|`<remove value=xs:string>`|移除所指定的 URI `value` audienceUris 集合中的屬性。 `value` 屬性 (Attribute) 是必要項。 URI 是區分大小寫。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性權杖處理常式。|  
  
## <a name="remarks"></a>備註  
 根據預設，這個集合是空的。使用`<add>`， `<clear>`，和`<remove>`修改該集合的項目。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 和<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件來設定任何的對象 URI 集合中的值允許的 audience URI 限制使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件。  
  
 `<audienceUris>`項目由<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>類別。 加入至集合的個別 URI 由<xref:System.IdentityModel.Configuration.AudienceUriElement>類別。  
  
> [!NOTE]
>  使用`<audienceUris>`為的子元素的項目[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。 設定`<securityTokenHandlerConfiguration>`元素會覆寫上`<identityConfiguration>`項目。  
  
## <a name="example"></a>範例  
 下列 XML 會示範如何設定應用程式可接受的 audience Uri。 這個範例會設定單一的 URI。 此 URI 範圍內的語彙基元會被接受，其他所有項目將會遭到拒絕。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
