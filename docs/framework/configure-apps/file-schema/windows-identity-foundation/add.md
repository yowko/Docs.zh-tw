---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73973807"
---
# \<add>
將指定的安全性權杖處理常式加入至權杖處理常式集合。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|要加入之標記處理常式的 CLR 型別名稱。 如需如何指定屬性的詳細資訊 `type` ，請參閱[自訂類型參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 類別或其中任一個類別的衍生類別的設定。|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別或衍生類別的設定。|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 類別或衍生類別的設定。|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 類別或衍生類別的選擇性設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|指定已向端點註冊的安全性權杖處理常式集合。|  
  
## <a name="remarks"></a>備註  
 `<add>`元素可以接受指定權杖處理常式之設定的單一子項目。 這取決於透過專案的屬性所參考的處理常式類別是否會 `type` `<add>` 提供這項功能的支援。 提供這項功能的 Token 處理常式類別必須公開接受物件的函式 <xref:System.Xml.XmlElement> 。  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 有數個內建的安全性權杖處理常式類別提供這項功能。 這些類別包括 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 。  
  
> [!IMPORTANT]
> Token 處理常式集合只能包含任何指定類型的單一處理程式。 這表示，例如，如果您想要將衍生自類別的處理常式加入 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 至集合，則必須先 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 從集合中移除預設存在的。 您可以使用專案 [\<remove>](remove.md) 從集合中移除單一處理程式，或使用專案從 [\<clear>](clear.md) 集合中移除所有處理常式。  
  
 在處理常式上指定的設定會覆寫在專案下的權杖處理常式集合中指定的對等設定 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) ，以及在專案下的服務層級指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。  
  
## <a name="example"></a>範例  
 下列 XML 顯示如何使用和專案， `<add>` `<remove>` 以自訂會話權杖處理常式取代預設會話權杖處理常式。 XML 取自 `ClaimsAwareWebFarm` 範例。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
