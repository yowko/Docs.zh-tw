---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 34643d10ef1ed2e87152e5013634e62859e0594e
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759479"
---
# <a name="add"></a><span data-ttu-id="762e6-101">\<add></span><span class="sxs-lookup"><span data-stu-id="762e6-101">\<add></span></span>
<span data-ttu-id="762e6-102">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="762e6-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="762e6-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="762e6-103">\<system.identityModel></span></span>  
<span data-ttu-id="762e6-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="762e6-104">\<identityConfiguration></span></span>  
<span data-ttu-id="762e6-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="762e6-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="762e6-106">\<add></span><span class="sxs-lookup"><span data-stu-id="762e6-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="762e6-107">語法</span><span class="sxs-lookup"><span data-stu-id="762e6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="762e6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="762e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="762e6-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="762e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="762e6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="762e6-110">Attributes</span></span>  
  
|<span data-ttu-id="762e6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="762e6-111">Attribute</span></span>|<span data-ttu-id="762e6-112">描述</span><span class="sxs-lookup"><span data-stu-id="762e6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="762e6-113">類型</span><span class="sxs-lookup"><span data-stu-id="762e6-113">type</span></span>|<span data-ttu-id="762e6-114">要加入的權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="762e6-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="762e6-115">如需有關如何指定`type`屬性，請參閱[自訂型別參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="762e6-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="762e6-116">子元素</span><span class="sxs-lookup"><span data-stu-id="762e6-116">Child Elements</span></span>  
  
|<span data-ttu-id="762e6-117">項目</span><span class="sxs-lookup"><span data-stu-id="762e6-117">Element</span></span>|<span data-ttu-id="762e6-118">描述</span><span class="sxs-lookup"><span data-stu-id="762e6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="762e6-119">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="762e6-119">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="762e6-120">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="762e6-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="762e6-121">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="762e6-121">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="762e6-122">提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="762e6-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="762e6-123">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="762e6-123">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="762e6-124">提供組態<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="762e6-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="762e6-125">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="762e6-125">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="762e6-126">提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="762e6-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="762e6-127">父項目</span><span class="sxs-lookup"><span data-stu-id="762e6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="762e6-128">項目</span><span class="sxs-lookup"><span data-stu-id="762e6-128">Element</span></span>|<span data-ttu-id="762e6-129">描述</span><span class="sxs-lookup"><span data-stu-id="762e6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="762e6-130">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="762e6-130">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="762e6-131">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="762e6-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="762e6-132">備註</span><span class="sxs-lookup"><span data-stu-id="762e6-132">Remarks</span></span>  
 <span data-ttu-id="762e6-133">`<add>`項目可能需要單一子項目，指定的權杖處理常式的組態。</span><span class="sxs-lookup"><span data-stu-id="762e6-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="762e6-134">這是取決於是否有處理常式類別參考透過`type`屬性的`<add>`元素提供這項功能的支援。</span><span class="sxs-lookup"><span data-stu-id="762e6-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="762e6-135">提供這項功能的權杖處理常式類別必須公開 （expose) 的建構函式<xref:System.Xml.XmlElement>物件。</span><span class="sxs-lookup"><span data-stu-id="762e6-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="762e6-136">數個內建的安全性權杖處理常式類別並提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="762e6-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="762e6-137">這些類別是<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="762e6-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="762e6-138">權杖處理常式集合只能包含單一的處理任何的常式指定的型別。</span><span class="sxs-lookup"><span data-stu-id="762e6-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="762e6-139">這表示，例如，如果您想要新增的處理常式，衍生自<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別加入集合中，您必須先移除<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>，這是預設的情況下，從集合存在。</span><span class="sxs-lookup"><span data-stu-id="762e6-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="762e6-140">您可以使用[\<移除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)若要移除的集合或使用單一處理常式的項目[\<清除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)從集合中移除所有的處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="762e6-140">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="762e6-141">指定處理常式上設定覆寫下的權杖處理常式集合中指定的對等設定[ \<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目和指定底下的服務層級[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="762e6-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="762e6-142">範例</span><span class="sxs-lookup"><span data-stu-id="762e6-142">Example</span></span>  
 <span data-ttu-id="762e6-143">下列 XML 示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設的工作階段權杖處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="762e6-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="762e6-144">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="762e6-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
