---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: a5af3893ab72d23c2b3814569decfc50431b8e55
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277520"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="ac56c-101">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ac56c-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="ac56c-102">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="ac56c-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="ac56c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ac56c-103">\<system.identityModel></span></span>  
<span data-ttu-id="ac56c-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ac56c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ac56c-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ac56c-105">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac56c-106">語法</span><span class="sxs-lookup"><span data-stu-id="ac56c-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac56c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ac56c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ac56c-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ac56c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac56c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ac56c-109">Attributes</span></span>  
  
|<span data-ttu-id="ac56c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ac56c-110">Attribute</span></span>|<span data-ttu-id="ac56c-111">描述</span><span class="sxs-lookup"><span data-stu-id="ac56c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac56c-112">名稱</span><span class="sxs-lookup"><span data-stu-id="ac56c-112">name</span></span>|<span data-ttu-id="ac56c-113">指定的權杖處理常式集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac56c-113">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="ac56c-114">架構所辨識的唯一值是"ActAs"和"OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="ac56c-114">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="ac56c-115">如果使用這些名稱指定權杖處理常式集合，分別處理 ActAs 或 OnBehalfOf 權杖時，將會使用集合。</span><span class="sxs-lookup"><span data-stu-id="ac56c-115">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac56c-116">子元素</span><span class="sxs-lookup"><span data-stu-id="ac56c-116">Child Elements</span></span>  
  
|<span data-ttu-id="ac56c-117">項目</span><span class="sxs-lookup"><span data-stu-id="ac56c-117">Element</span></span>|<span data-ttu-id="ac56c-118">描述</span><span class="sxs-lookup"><span data-stu-id="ac56c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac56c-119">\<add></span><span class="sxs-lookup"><span data-stu-id="ac56c-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="ac56c-120">將權杖處理常式集合中的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="ac56c-120">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="ac56c-121">\<clear></span><span class="sxs-lookup"><span data-stu-id="ac56c-121">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="ac56c-122">清除所有的安全性權杖處理常式，從權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="ac56c-122">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="ac56c-123">\<remove></span><span class="sxs-lookup"><span data-stu-id="ac56c-123">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="ac56c-124">從權杖處理常式集合中移除的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="ac56c-124">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="ac56c-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="ac56c-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="ac56c-126">提供的權杖處理常式集合的組態。</span><span class="sxs-lookup"><span data-stu-id="ac56c-126">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac56c-127">父項目</span><span class="sxs-lookup"><span data-stu-id="ac56c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ac56c-128">項目</span><span class="sxs-lookup"><span data-stu-id="ac56c-128">Element</span></span>|<span data-ttu-id="ac56c-129">描述</span><span class="sxs-lookup"><span data-stu-id="ac56c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac56c-130">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ac56c-130">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="ac56c-131">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="ac56c-131">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac56c-132">備註</span><span class="sxs-lookup"><span data-stu-id="ac56c-132">Remarks</span></span>  
 <span data-ttu-id="ac56c-133">您可以在服務組態中指定一個或多個安全性權杖處理常式的具名的集合。</span><span class="sxs-lookup"><span data-stu-id="ac56c-133">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="ac56c-134">您可以指定集合的名稱使用`name`屬性。</span><span class="sxs-lookup"><span data-stu-id="ac56c-134">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="ac56c-135">架構會處理的唯一名稱是"ActAs"和"OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="ac56c-135">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="ac56c-136">如果處理常式存在於這些集合，這些安全性權杖服務 (STS) 而不預設處理常式處理時使用`ActAs`和`OnBehalfOf`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ac56c-136">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="ac56c-137">根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="ac56c-137">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="ac56c-138">您可以使用，以修改集合`<add>`， `<remove>`，和`<clear>`項目。</span><span class="sxs-lookup"><span data-stu-id="ac56c-138">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="ac56c-139">您必須確定任何特定的型別中的單一處理常式存在於集合。</span><span class="sxs-lookup"><span data-stu-id="ac56c-139">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="ac56c-140">比方說，如果您衍生從處理常式<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別，可能是您的處理常式或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>可能在單一集合，但不是能同時設定。</span><span class="sxs-lookup"><span data-stu-id="ac56c-140">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="ac56c-141">使用`<securityTokenHandlerConfiguration>`項目來指定集合中的處理常式的組態設定。</span><span class="sxs-lookup"><span data-stu-id="ac56c-141">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="ac56c-142">透過這個項目指定的設定會覆寫透過在服務上指定[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="ac56c-142">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="ac56c-143">有些 （包括數個內建的處理常式型別） 的處理常式可以支援額外的設定，透過的子項目`<add>`項目。</span><span class="sxs-lookup"><span data-stu-id="ac56c-143">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="ac56c-144">指定處理常式上設定覆寫集合或服務上所指定的對等設定。</span><span class="sxs-lookup"><span data-stu-id="ac56c-144">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
