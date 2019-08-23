---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941949"
---
# <a name="audienceuris"></a>\<audienceUris>
指定 Uri 的集合, 這是信賴憑證者 (RP) 可接受的識別碼。 除非權杖的範圍是其中一個允許的物件 Uri, 否則將不會接受。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<audienceUris>  
  
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
  
|屬性|說明|  
|---------------|-----------------|  
|模式|<xref:System.IdentityModel.Selectors.AudienceUriMode>值, 指定物件限制是否應套用至傳入的權杖。 可能的值為「永遠」、「永不」和「BearerKeyOnly」。 預設值為「一律」。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`<add value=xs:string>`|將`value`屬性所指定的 URI 新增至 audienceUris 集合。 `value` 屬性 (Attribute) 是必要項。 URI 會區分大小寫。|  
|`<clear>`|清除 audienceUris 集合。 所有識別碼都會從集合中移除。|  
|`<remove value=xs:string>`|從 audienceUris 集合中移除`value`屬性所指定的 URI。 `value` 屬性 (Attribute) 是必要項。 URI 會區分大小寫。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 根據預設, 集合是空的;使用`<add>`、 `<clear>`和`<remove>`元素來修改集合。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>和<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件會使用物件 uri 集合中的值, 來設定物件中任何允許的<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>觀眾 uri 限制。  
  
 `<audienceUris>`元素是<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>由類別表示。 新增至集合的個別 URI 會以<xref:System.IdentityModel.Configuration.AudienceUriElement>類別表示。  
  
> [!NOTE]
> 使用`<audienceUris>`元素做為[ \<identityConfiguration >](identityconfiguration.md)元素的子專案已被取代, 但仍支援回溯相容性。 元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。  
  
## <a name="example"></a>範例  
 下列 XML 顯示如何為應用程式設定可接受的物件 Uri。 這個範例會設定單一 URI。 將會接受此 URI 範圍內的權杖, 其他所有專案則會遭到拒絕。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
