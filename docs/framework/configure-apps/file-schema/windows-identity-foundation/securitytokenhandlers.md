---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251868"
---
# \<securityTokenHandlers>
<span data-ttu-id="47923-101">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="47923-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="47923-102">語法</span><span class="sxs-lookup"><span data-stu-id="47923-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47923-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="47923-103">Attributes and Elements</span></span>  
 <span data-ttu-id="47923-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="47923-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47923-105">屬性</span><span class="sxs-lookup"><span data-stu-id="47923-105">Attributes</span></span>  
  
|<span data-ttu-id="47923-106">屬性</span><span class="sxs-lookup"><span data-stu-id="47923-106">Attribute</span></span>|<span data-ttu-id="47923-107">描述</span><span class="sxs-lookup"><span data-stu-id="47923-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47923-108">NAME</span><span class="sxs-lookup"><span data-stu-id="47923-108">name</span></span>|<span data-ttu-id="47923-109">指定權杖處理常式集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="47923-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="47923-110">架構所能辨識的唯一值為 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="47923-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="47923-111">如果使用上述其中一個名稱來指定權杖處理常式集合，則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。</span><span class="sxs-lookup"><span data-stu-id="47923-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47923-112">子元素</span><span class="sxs-lookup"><span data-stu-id="47923-112">Child Elements</span></span>  
  
|<span data-ttu-id="47923-113">元素</span><span class="sxs-lookup"><span data-stu-id="47923-113">Element</span></span>|<span data-ttu-id="47923-114">描述</span><span class="sxs-lookup"><span data-stu-id="47923-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="47923-115">將安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="47923-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="47923-116">清除權杖處理常式集合中的所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="47923-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="47923-117">從權杖處理常式集合中移除安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="47923-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="47923-118">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="47923-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47923-119">父項目</span><span class="sxs-lookup"><span data-stu-id="47923-119">Parent Elements</span></span>  
  
|<span data-ttu-id="47923-120">元素</span><span class="sxs-lookup"><span data-stu-id="47923-120">Element</span></span>|<span data-ttu-id="47923-121">描述</span><span class="sxs-lookup"><span data-stu-id="47923-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="47923-122">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="47923-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47923-123">備註</span><span class="sxs-lookup"><span data-stu-id="47923-123">Remarks</span></span>  
 <span data-ttu-id="47923-124">您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="47923-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="47923-125">您可以使用屬性來指定集合的名稱 `name` 。</span><span class="sxs-lookup"><span data-stu-id="47923-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="47923-126">架構所處理的唯一名稱是 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="47923-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="47923-127">如果處理常式存在於這些集合中，則會由 Security Token Service （STS）使用，而不是處理和標記時的預設處理常式 `ActAs` `OnBehalfOf` 。</span><span class="sxs-lookup"><span data-stu-id="47923-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="47923-128">根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> 、、、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="47923-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="47923-129">您可以使用 `<add>` 、和元素來修改集合 `<remove>` `<clear>` 。</span><span class="sxs-lookup"><span data-stu-id="47923-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="47923-130">您必須確定集合中只存在任何特定類型的單一處理程式。</span><span class="sxs-lookup"><span data-stu-id="47923-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="47923-131">例如，如果您從類別衍生處理常式 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ，則您的處理常式或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 可以在單一集合中設定，但不能同時在兩者中設定。</span><span class="sxs-lookup"><span data-stu-id="47923-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="47923-132">使用 `<securityTokenHandlerConfiguration>` 元素來指定集合中處理常式的設定。</span><span class="sxs-lookup"><span data-stu-id="47923-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="47923-133">透過這個專案指定的設定，會透過專案覆寫在服務上指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="47923-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="47923-134">某些處理常式（包括數個內建處理常式類型）可以透過專案的子專案支援其他設定 `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="47923-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="47923-135">在處理常式上指定的設定會覆寫集合或服務上指定的對等設定。</span><span class="sxs-lookup"><span data-stu-id="47923-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
