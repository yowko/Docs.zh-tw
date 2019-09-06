---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251868"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="11877-101">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="11877-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="11877-102">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="11877-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
<span data-ttu-id="11877-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="11877-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="11877-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="11877-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="11877-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="11877-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="11877-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlers >**</span><span class="sxs-lookup"><span data-stu-id="11877-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11877-107">語法</span><span class="sxs-lookup"><span data-stu-id="11877-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11877-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="11877-108">Attributes and Elements</span></span>  
 <span data-ttu-id="11877-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="11877-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11877-110">屬性</span><span class="sxs-lookup"><span data-stu-id="11877-110">Attributes</span></span>  
  
|<span data-ttu-id="11877-111">屬性</span><span class="sxs-lookup"><span data-stu-id="11877-111">Attribute</span></span>|<span data-ttu-id="11877-112">說明</span><span class="sxs-lookup"><span data-stu-id="11877-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11877-113">NAME</span><span class="sxs-lookup"><span data-stu-id="11877-113">name</span></span>|<span data-ttu-id="11877-114">指定權杖處理常式集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="11877-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="11877-115">架構所能辨識的唯一值為 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="11877-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="11877-116">如果使用上述其中一個名稱來指定權杖處理常式集合, 則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。</span><span class="sxs-lookup"><span data-stu-id="11877-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11877-117">子元素</span><span class="sxs-lookup"><span data-stu-id="11877-117">Child Elements</span></span>  
  
|<span data-ttu-id="11877-118">項目</span><span class="sxs-lookup"><span data-stu-id="11877-118">Element</span></span>|<span data-ttu-id="11877-119">說明</span><span class="sxs-lookup"><span data-stu-id="11877-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11877-120">\<add></span><span class="sxs-lookup"><span data-stu-id="11877-120">\<add></span></span>](add.md)|<span data-ttu-id="11877-121">將安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="11877-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="11877-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="11877-122">\<clear></span></span>](clear.md)|<span data-ttu-id="11877-123">清除權杖處理常式集合中的所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="11877-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="11877-124">\<remove></span><span class="sxs-lookup"><span data-stu-id="11877-124">\<remove></span></span>](remove.md)|<span data-ttu-id="11877-125">從權杖處理常式集合中移除安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="11877-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="11877-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="11877-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="11877-127">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="11877-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11877-128">父項目</span><span class="sxs-lookup"><span data-stu-id="11877-128">Parent Elements</span></span>  
  
|<span data-ttu-id="11877-129">項目</span><span class="sxs-lookup"><span data-stu-id="11877-129">Element</span></span>|<span data-ttu-id="11877-130">說明</span><span class="sxs-lookup"><span data-stu-id="11877-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11877-131">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="11877-131">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="11877-132">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="11877-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11877-133">備註</span><span class="sxs-lookup"><span data-stu-id="11877-133">Remarks</span></span>  
 <span data-ttu-id="11877-134">您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="11877-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="11877-135">您可以使用`name`屬性來指定集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="11877-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="11877-136">架構所處理的唯一名稱是 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="11877-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="11877-137">如果處理常式存在於這些集合中, 則會由 Security Token Service (STS) 使用, 而不是處理`ActAs`和`OnBehalfOf`標記時的預設處理常式。</span><span class="sxs-lookup"><span data-stu-id="11877-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="11877-138">根據預設, 集合會填入下列處理<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>程式類型:、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="11877-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="11877-139">您可以使用`<add>`、 `<remove>`和`<clear>`元素來修改集合。</span><span class="sxs-lookup"><span data-stu-id="11877-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="11877-140">您必須確定集合中只存在任何特定類型的單一處理程式。</span><span class="sxs-lookup"><span data-stu-id="11877-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="11877-141">例如, 如果您從<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別衍生處理常式, 則您的<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>處理常式或可以在單一集合中設定, 但不能同時在兩者中設定。</span><span class="sxs-lookup"><span data-stu-id="11877-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="11877-142">`<securityTokenHandlerConfiguration>`使用元素來指定集合中處理常式的設定。</span><span class="sxs-lookup"><span data-stu-id="11877-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="11877-143">透過這個專案指定的設定, 會透過[ \<identityConfiguration >](identityconfiguration.md)專案來覆寫在服務上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="11877-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="11877-144">某些處理常式 (包括數個內建處理常式類型) 可以透過專案的子`<add>`專案支援其他設定。</span><span class="sxs-lookup"><span data-stu-id="11877-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="11877-145">在處理常式上指定的設定會覆寫集合或服務上指定的對等設定。</span><span class="sxs-lookup"><span data-stu-id="11877-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
