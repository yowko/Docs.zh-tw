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
<span data-ttu-id="d1c44-101">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="d1c44-101">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d1c44-102">語法</span><span class="sxs-lookup"><span data-stu-id="d1c44-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1c44-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1c44-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d1c44-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d1c44-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1c44-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d1c44-105">Attributes</span></span>  
  
|<span data-ttu-id="d1c44-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d1c44-106">Attribute</span></span>|<span data-ttu-id="d1c44-107">描述</span><span class="sxs-lookup"><span data-stu-id="d1c44-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1c44-108">type</span><span class="sxs-lookup"><span data-stu-id="d1c44-108">type</span></span>|<span data-ttu-id="d1c44-109">要加入之標記處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c44-109">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="d1c44-110">如需如何指定屬性的詳細資訊 `type` ，請參閱[自訂類型參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="d1c44-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1c44-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d1c44-111">Child Elements</span></span>  
  
|<span data-ttu-id="d1c44-112">元素</span><span class="sxs-lookup"><span data-stu-id="d1c44-112">Element</span></span>|<span data-ttu-id="d1c44-113">描述</span><span class="sxs-lookup"><span data-stu-id="d1c44-113">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="d1c44-114">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="d1c44-114">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="d1c44-115">提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="d1c44-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="d1c44-116">提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="d1c44-116">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="d1c44-117">提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 類別或衍生類別的選擇性設定。</span><span class="sxs-lookup"><span data-stu-id="d1c44-117">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1c44-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d1c44-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d1c44-119">元素</span><span class="sxs-lookup"><span data-stu-id="d1c44-119">Element</span></span>|<span data-ttu-id="d1c44-120">描述</span><span class="sxs-lookup"><span data-stu-id="d1c44-120">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="d1c44-121">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="d1c44-121">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1c44-122">備註</span><span class="sxs-lookup"><span data-stu-id="d1c44-122">Remarks</span></span>  
 <span data-ttu-id="d1c44-123">`<add>`元素可以接受指定權杖處理常式之設定的單一子項目。</span><span class="sxs-lookup"><span data-stu-id="d1c44-123">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="d1c44-124">這取決於透過專案的屬性所參考的處理常式類別是否會 `type` `<add>` 提供這項功能的支援。</span><span class="sxs-lookup"><span data-stu-id="d1c44-124">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="d1c44-125">提供這項功能的 Token 處理常式類別必須公開接受物件的函式 <xref:System.Xml.XmlElement> 。</span><span class="sxs-lookup"><span data-stu-id="d1c44-125">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="d1c44-126">有數個內建的安全性權杖處理常式類別提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="d1c44-126">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="d1c44-127">這些類別包括 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="d1c44-127">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1c44-128">Token 處理常式集合只能包含任何指定類型的單一處理程式。</span><span class="sxs-lookup"><span data-stu-id="d1c44-128">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="d1c44-129">這表示，例如，如果您想要將衍生自類別的處理常式加入 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 至集合，則必須先 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 從集合中移除預設存在的。</span><span class="sxs-lookup"><span data-stu-id="d1c44-129">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="d1c44-130">您可以使用專案 [\<remove>](remove.md) 從集合中移除單一處理程式，或使用專案從 [\<clear>](clear.md) 集合中移除所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="d1c44-130">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="d1c44-131">在處理常式上指定的設定會覆寫在專案下的權杖處理常式集合中指定的對等設定 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) ，以及在專案下的服務層級指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="d1c44-131">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1c44-132">範例</span><span class="sxs-lookup"><span data-stu-id="d1c44-132">Example</span></span>  
 <span data-ttu-id="d1c44-133">下列 XML 顯示如何使用和專案， `<add>` `<remove>` 以自訂會話權杖處理常式取代預設會話權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="d1c44-133">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d1c44-134">XML 取自 `ClaimsAwareWebFarm` 範例。</span><span class="sxs-lookup"><span data-stu-id="d1c44-134">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
