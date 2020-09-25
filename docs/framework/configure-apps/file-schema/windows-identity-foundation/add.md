---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 2f37019fa0787f5c5553dbd3debc173ec0a047ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189951"
---
# \<add>

將指定的安全性權杖處理常式新增至權杖處理常式集合。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntax  
  
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
|type|要加入之 token 處理常式的 CLR 型別名稱。 如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、類別或其中一個類別的 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 衍生類別的設定。|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別或衍生類別的設定。|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 類別或衍生類別的設定。|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 類別或衍生類別的選擇性設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|指定向端點註冊的安全性權杖處理常式集合。|  
  
## <a name="remarks"></a>備註  

 專案 `<add>` 可以採用單一子項目，以指定權杖處理常式的設定。 這取決於透過元素的屬性所參考的處理常式類別是否 `type` `<add>` 提供這項功能的支援。 提供此功能的 Token 處理常式類別必須公開接受物件的函式 <xref:System.Xml.XmlElement> 。  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 數個內建安全性權杖處理常式類別提供這項功能。 這些類別包括 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 。  
  
> [!IMPORTANT]
> Token 處理常式集合只能包含任何指定類型的單一處理程式。 這表示，如果您想要將衍生自類別的處理常式加入 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 至集合，則必須先 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 從集合中移除預設存在的。 您可以使用專案 [\<remove>](remove.md) 從集合中移除單一處理程式，或使用 [\<clear>](clear.md) 元素從集合移除所有處理常式。  
  
 在處理常式上指定的設定會覆寫在專案底下的權杖處理常式集合上指定的對等設定 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) ，以及在專案下的服務層級所指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。  
  
## <a name="example"></a>範例  

 下列 XML 會示範如何使用和專案 `<add>` ， `<remove>` 以自訂會話權杖處理常式來取代預設的會話 token 處理常式。 XML 取自 `ClaimsAwareWebFarm` 範例。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
