---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 932e8452542ace66824fba1262694c220ce88676
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252191"
---
# <a name="add"></a><span data-ttu-id="110ca-101">\<add></span><span class="sxs-lookup"><span data-stu-id="110ca-101">\<add></span></span>
<span data-ttu-id="110ca-102">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="110ca-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="110ca-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="110ca-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="110ca-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="110ca-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="110ca-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="110ca-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="110ca-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="110ca-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="110ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="110ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110ca-108">語法</span><span class="sxs-lookup"><span data-stu-id="110ca-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="110ca-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="110ca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="110ca-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="110ca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="110ca-111">屬性</span><span class="sxs-lookup"><span data-stu-id="110ca-111">Attributes</span></span>  
  
|<span data-ttu-id="110ca-112">屬性</span><span class="sxs-lookup"><span data-stu-id="110ca-112">Attribute</span></span>|<span data-ttu-id="110ca-113">描述</span><span class="sxs-lookup"><span data-stu-id="110ca-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="110ca-114">型別</span><span class="sxs-lookup"><span data-stu-id="110ca-114">type</span></span>|<span data-ttu-id="110ca-115">要加入之標記處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="110ca-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="110ca-116">如需如何指定屬性的`type`詳細資訊，請參閱[自訂類型參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="110ca-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="110ca-117">子元素</span><span class="sxs-lookup"><span data-stu-id="110ca-117">Child Elements</span></span>  
  
|<span data-ttu-id="110ca-118">項目</span><span class="sxs-lookup"><span data-stu-id="110ca-118">Element</span></span>|<span data-ttu-id="110ca-119">說明</span><span class="sxs-lookup"><span data-stu-id="110ca-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="110ca-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="110ca-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="110ca-121"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="110ca-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="110ca-122">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="110ca-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="110ca-123"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>提供類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="110ca-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="110ca-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="110ca-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="110ca-125"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>提供類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="110ca-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="110ca-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="110ca-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="110ca-127">提供<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生類別的選擇性設定。</span><span class="sxs-lookup"><span data-stu-id="110ca-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="110ca-128">父項目</span><span class="sxs-lookup"><span data-stu-id="110ca-128">Parent Elements</span></span>  
  
|<span data-ttu-id="110ca-129">項目</span><span class="sxs-lookup"><span data-stu-id="110ca-129">Element</span></span>|<span data-ttu-id="110ca-130">描述</span><span class="sxs-lookup"><span data-stu-id="110ca-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="110ca-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="110ca-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="110ca-132">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="110ca-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="110ca-133">備註</span><span class="sxs-lookup"><span data-stu-id="110ca-133">Remarks</span></span>  
 <span data-ttu-id="110ca-134">`<add>`元素可以接受指定權杖處理常式之設定的單一子項目。</span><span class="sxs-lookup"><span data-stu-id="110ca-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="110ca-135">這取決於透過專案的`type`屬性`<add>`所參考的處理常式類別是否會提供這項功能的支援。</span><span class="sxs-lookup"><span data-stu-id="110ca-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="110ca-136">提供這項功能的 Token 處理常式類別必須公開接受物件的<xref:System.Xml.XmlElement>函式。</span><span class="sxs-lookup"><span data-stu-id="110ca-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="110ca-137">有數個內建的安全性權杖處理常式類別提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="110ca-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="110ca-138">這些類別包括<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>和。<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="110ca-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="110ca-139">Token 處理常式集合只能包含任何指定類型的單一處理程式。</span><span class="sxs-lookup"><span data-stu-id="110ca-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="110ca-140">這表示，例如，如果您想要將衍生自<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別的處理常式加入至集合，則必須先從集合中移除預設存在的。 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="110ca-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="110ca-141">您可以使用[ \<remove >](remove.md)專案，從[ \<](clear.md)集合中移除單一處理程式，或使用 clear > 元素來移除集合中的所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="110ca-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="110ca-142">在處理常式上指定的設定會覆寫在[ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)專案下的權杖處理常式集合中指定的對等設定，以及在[ \<服務層級的identityConfiguration >](identityconfiguration.md)元素。</span><span class="sxs-lookup"><span data-stu-id="110ca-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="110ca-143">範例</span><span class="sxs-lookup"><span data-stu-id="110ca-143">Example</span></span>  
 <span data-ttu-id="110ca-144">下列 XML 顯示如何使用`<add>`和`<remove>`專案，以自訂會話權杖處理常式取代預設會話權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="110ca-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="110ca-145">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="110ca-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
