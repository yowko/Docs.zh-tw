---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ddbf1b822550876d849f830d80cff9a74311ba9c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506770"
---
# <a name="ltaddgt"></a><span data-ttu-id="c9c08-102">&lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="c9c08-102">&lt;add&gt;</span></span>
<span data-ttu-id="c9c08-103">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="c9c08-103">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="c9c08-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c9c08-104">\<system.identityModel></span></span>  
<span data-ttu-id="c9c08-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c9c08-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c9c08-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="c9c08-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c9c08-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c9c08-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c08-108">語法</span><span class="sxs-lookup"><span data-stu-id="c9c08-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9c08-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9c08-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c9c08-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9c08-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9c08-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c9c08-111">Attributes</span></span>  
  
|<span data-ttu-id="c9c08-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c9c08-112">Attribute</span></span>|<span data-ttu-id="c9c08-113">描述</span><span class="sxs-lookup"><span data-stu-id="c9c08-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9c08-114">類型</span><span class="sxs-lookup"><span data-stu-id="c9c08-114">type</span></span>|<span data-ttu-id="c9c08-115">要加入的權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c9c08-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="c9c08-116">如需有關如何指定`type`屬性，請參閱[自訂型別參考](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。</span><span class="sxs-lookup"><span data-stu-id="c9c08-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9c08-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c9c08-117">Child Elements</span></span>  
  
|<span data-ttu-id="c9c08-118">項目</span><span class="sxs-lookup"><span data-stu-id="c9c08-118">Element</span></span>|<span data-ttu-id="c9c08-119">描述</span><span class="sxs-lookup"><span data-stu-id="c9c08-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c08-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="c9c08-120">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="c9c08-121">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="c9c08-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="c9c08-122">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="c9c08-122">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="c9c08-123">提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="c9c08-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="c9c08-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="c9c08-124">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="c9c08-125">提供組態<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="c9c08-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="c9c08-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="c9c08-126">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="c9c08-127">提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="c9c08-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9c08-128">父項目</span><span class="sxs-lookup"><span data-stu-id="c9c08-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c9c08-129">項目</span><span class="sxs-lookup"><span data-stu-id="c9c08-129">Element</span></span>|<span data-ttu-id="c9c08-130">描述</span><span class="sxs-lookup"><span data-stu-id="c9c08-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c08-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="c9c08-131">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="c9c08-132">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="c9c08-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9c08-133">備註</span><span class="sxs-lookup"><span data-stu-id="c9c08-133">Remarks</span></span>  
 <span data-ttu-id="c9c08-134">`<add>`項目可能需要單一子項目，指定的權杖處理常式的組態。</span><span class="sxs-lookup"><span data-stu-id="c9c08-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="c9c08-135">這是取決於是否有處理常式類別參考透過`type`屬性的`<add>`元素提供這項功能的支援。</span><span class="sxs-lookup"><span data-stu-id="c9c08-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="c9c08-136">提供這項功能的權杖處理常式類別必須公開 （expose) 的建構函式<xref:System.Xml.XmlElement>物件。</span><span class="sxs-lookup"><span data-stu-id="c9c08-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="c9c08-137">數個內建的安全性權杖處理常式類別並提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="c9c08-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="c9c08-138">這些類別是<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="c9c08-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c9c08-139">權杖處理常式集合只能包含單一的處理任何的常式指定的型別。</span><span class="sxs-lookup"><span data-stu-id="c9c08-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="c9c08-140">這表示，例如，如果您想要新增的處理常式，衍生自<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別加入集合中，您必須先移除<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>，這是預設的情況下，從集合存在。</span><span class="sxs-lookup"><span data-stu-id="c9c08-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="c9c08-141">您可以使用[\<移除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)若要移除的集合或使用單一處理常式的項目[\<清除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)從集合中移除所有的處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="c9c08-141">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="c9c08-142">指定處理常式上設定覆寫下的權杖處理常式集合中指定的對等設定[ \<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目和指定底下的服務層級[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c9c08-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c08-143">範例</span><span class="sxs-lookup"><span data-stu-id="c9c08-143">Example</span></span>  
 <span data-ttu-id="c9c08-144">下列 XML 示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設的工作階段權杖處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="c9c08-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="c9c08-145">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="c9c08-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
