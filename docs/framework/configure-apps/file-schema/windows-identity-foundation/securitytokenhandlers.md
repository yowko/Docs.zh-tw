---
title: '&lt;securityTokenHandlers&gt;'
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: e63f02add81495e474b59b6c5cc090bd69add3d2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206165"
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="6c8f1-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="6c8f1-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="6c8f1-103">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="6c8f1-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6c8f1-104">\<system.identityModel></span></span>  
<span data-ttu-id="6c8f1-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="6c8f1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="6c8f1-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="6c8f1-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c8f1-107">語法</span><span class="sxs-lookup"><span data-stu-id="6c8f1-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c8f1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c8f1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6c8f1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c8f1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6c8f1-110">Attributes</span></span>  
  
|<span data-ttu-id="6c8f1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6c8f1-111">Attribute</span></span>|<span data-ttu-id="6c8f1-112">描述</span><span class="sxs-lookup"><span data-stu-id="6c8f1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c8f1-113">名稱</span><span class="sxs-lookup"><span data-stu-id="6c8f1-113">name</span></span>|<span data-ttu-id="6c8f1-114">指定的權杖處理常式集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="6c8f1-115">架構所辨識的唯一值是"ActAs"和"OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="6c8f1-116">如果使用這些名稱指定權杖處理常式集合，分別處理 ActAs 或 OnBehalfOf 權杖時，將會使用集合。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c8f1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="6c8f1-117">Child Elements</span></span>  
  
|<span data-ttu-id="6c8f1-118">項目</span><span class="sxs-lookup"><span data-stu-id="6c8f1-118">Element</span></span>|<span data-ttu-id="6c8f1-119">描述</span><span class="sxs-lookup"><span data-stu-id="6c8f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c8f1-120">\<add></span><span class="sxs-lookup"><span data-stu-id="6c8f1-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="6c8f1-121">將權杖處理常式集合中的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="6c8f1-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="6c8f1-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="6c8f1-123">清除所有的安全性權杖處理常式，從權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="6c8f1-124">\<remove></span><span class="sxs-lookup"><span data-stu-id="6c8f1-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="6c8f1-125">從權杖處理常式集合中移除的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="6c8f1-126">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="6c8f1-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="6c8f1-127">提供的權杖處理常式集合的組態。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c8f1-128">父項目</span><span class="sxs-lookup"><span data-stu-id="6c8f1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6c8f1-129">項目</span><span class="sxs-lookup"><span data-stu-id="6c8f1-129">Element</span></span>|<span data-ttu-id="6c8f1-130">描述</span><span class="sxs-lookup"><span data-stu-id="6c8f1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c8f1-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6c8f1-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="6c8f1-132">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c8f1-133">備註</span><span class="sxs-lookup"><span data-stu-id="6c8f1-133">Remarks</span></span>  
 <span data-ttu-id="6c8f1-134">您可以在服務組態中指定一個或多個安全性權杖處理常式的具名的集合。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="6c8f1-135">您可以指定集合的名稱使用`name`屬性。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="6c8f1-136">架構會處理的唯一名稱是"ActAs"和"OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="6c8f1-137">如果處理常式存在於這些集合，這些安全性權杖服務 (STS) 而不預設處理常式處理時使用`ActAs`和`OnBehalfOf`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="6c8f1-138">根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="6c8f1-139">您可以使用，以修改集合`<add>`， `<remove>`，和`<clear>`項目。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="6c8f1-140">您必須確定任何特定的型別中的單一處理常式存在於集合。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="6c8f1-141">比方說，如果您衍生從處理常式<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別，可能是您的處理常式或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>可能在單一集合，但不是能同時設定。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="6c8f1-142">使用`<securityTokenHandlerConfiguration>`項目來指定集合中的處理常式的組態設定。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="6c8f1-143">透過這個項目指定的設定會覆寫透過在服務上指定[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="6c8f1-144">有些 （包括數個內建的處理常式型別） 的處理常式可以支援額外的設定，透過的子項目`<add>`項目。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="6c8f1-145">指定處理常式上設定覆寫集合或服務上所指定的對等設定。</span><span class="sxs-lookup"><span data-stu-id="6c8f1-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
