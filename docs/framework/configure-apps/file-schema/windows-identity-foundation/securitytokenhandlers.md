---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942464"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="18d6b-101">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="18d6b-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="18d6b-102">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="18d6b-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="18d6b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="18d6b-103">\<system.identityModel></span></span>  
<span data-ttu-id="18d6b-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="18d6b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="18d6b-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="18d6b-105">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18d6b-106">語法</span><span class="sxs-lookup"><span data-stu-id="18d6b-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18d6b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18d6b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="18d6b-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18d6b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18d6b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="18d6b-109">Attributes</span></span>  
  
|<span data-ttu-id="18d6b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="18d6b-110">Attribute</span></span>|<span data-ttu-id="18d6b-111">說明</span><span class="sxs-lookup"><span data-stu-id="18d6b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18d6b-112">NAME</span><span class="sxs-lookup"><span data-stu-id="18d6b-112">name</span></span>|<span data-ttu-id="18d6b-113">指定權杖處理常式集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="18d6b-113">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="18d6b-114">架構所能辨識的唯一值為 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="18d6b-114">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="18d6b-115">如果使用上述其中一個名稱來指定權杖處理常式集合, 則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。</span><span class="sxs-lookup"><span data-stu-id="18d6b-115">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18d6b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="18d6b-116">Child Elements</span></span>  
  
|<span data-ttu-id="18d6b-117">項目</span><span class="sxs-lookup"><span data-stu-id="18d6b-117">Element</span></span>|<span data-ttu-id="18d6b-118">描述</span><span class="sxs-lookup"><span data-stu-id="18d6b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18d6b-119">\<add></span><span class="sxs-lookup"><span data-stu-id="18d6b-119">\<add></span></span>](add.md)|<span data-ttu-id="18d6b-120">將安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="18d6b-120">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="18d6b-121">\<clear></span><span class="sxs-lookup"><span data-stu-id="18d6b-121">\<clear></span></span>](clear.md)|<span data-ttu-id="18d6b-122">清除權杖處理常式集合中的所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="18d6b-122">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="18d6b-123">\<remove></span><span class="sxs-lookup"><span data-stu-id="18d6b-123">\<remove></span></span>](remove.md)|<span data-ttu-id="18d6b-124">從權杖處理常式集合中移除安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="18d6b-124">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="18d6b-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="18d6b-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="18d6b-126">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-126">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18d6b-127">父項目</span><span class="sxs-lookup"><span data-stu-id="18d6b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="18d6b-128">項目</span><span class="sxs-lookup"><span data-stu-id="18d6b-128">Element</span></span>|<span data-ttu-id="18d6b-129">描述</span><span class="sxs-lookup"><span data-stu-id="18d6b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18d6b-130">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="18d6b-130">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="18d6b-131">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-131">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18d6b-132">備註</span><span class="sxs-lookup"><span data-stu-id="18d6b-132">Remarks</span></span>  
 <span data-ttu-id="18d6b-133">您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="18d6b-133">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="18d6b-134">您可以使用`name`屬性來指定集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="18d6b-134">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="18d6b-135">架構所處理的唯一名稱是 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="18d6b-135">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="18d6b-136">如果處理常式存在於這些集合中, 則會由 Security Token Service (STS) 使用, 而不是處理`ActAs`和`OnBehalfOf`標記時的預設處理常式。</span><span class="sxs-lookup"><span data-stu-id="18d6b-136">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="18d6b-137">根據預設, 集合會填入下列處理<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>程式類型:、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="18d6b-137">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="18d6b-138">您可以使用`<add>`、 `<remove>`和`<clear>`元素來修改集合。</span><span class="sxs-lookup"><span data-stu-id="18d6b-138">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="18d6b-139">您必須確定集合中只存在任何特定類型的單一處理程式。</span><span class="sxs-lookup"><span data-stu-id="18d6b-139">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="18d6b-140">例如, 如果您從<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別衍生處理常式, 則您的<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>處理常式或可以在單一集合中設定, 但不能同時在兩者中設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-140">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="18d6b-141">`<securityTokenHandlerConfiguration>`使用元素來指定集合中處理常式的設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-141">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="18d6b-142">透過這個專案指定的設定, 會透過[ \<identityConfiguration >](identityconfiguration.md)專案來覆寫在服務上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-142">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="18d6b-143">某些處理常式 (包括數個內建處理常式類型) 可以透過專案的子`<add>`專案支援其他設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-143">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="18d6b-144">在處理常式上指定的設定會覆寫集合或服務上指定的對等設定。</span><span class="sxs-lookup"><span data-stu-id="18d6b-144">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
