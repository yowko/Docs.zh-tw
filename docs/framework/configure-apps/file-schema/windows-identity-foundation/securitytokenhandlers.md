---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: d892fbd802ed366ca7af9b85fbf5c23d4d27e0f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157001"
---
# \<securityTokenHandlers>

<span data-ttu-id="f5b2d-101">指定向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="f5b2d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5b2d-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5b2d-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f5b2d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f5b2d-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5b2d-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f5b2d-105">Attributes</span></span>  
  
|<span data-ttu-id="f5b2d-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f5b2d-106">Attribute</span></span>|<span data-ttu-id="f5b2d-107">描述</span><span class="sxs-lookup"><span data-stu-id="f5b2d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5b2d-108">NAME</span><span class="sxs-lookup"><span data-stu-id="f5b2d-108">name</span></span>|<span data-ttu-id="f5b2d-109">指定權杖處理常式集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="f5b2d-110">架構唯一能辨識的值為 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="f5b2d-111">如果使用其中一個名稱指定權杖處理常式集合，則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5b2d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f5b2d-112">Child Elements</span></span>  
  
|<span data-ttu-id="f5b2d-113">項目</span><span class="sxs-lookup"><span data-stu-id="f5b2d-113">Element</span></span>|<span data-ttu-id="f5b2d-114">描述</span><span class="sxs-lookup"><span data-stu-id="f5b2d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="f5b2d-115">將安全性權杖處理常式新增至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="f5b2d-116">從權杖處理常式集合中清除所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="f5b2d-117">從權杖處理常式集合中移除安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f5b2d-118">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5b2d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f5b2d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f5b2d-120">項目</span><span class="sxs-lookup"><span data-stu-id="f5b2d-120">Element</span></span>|<span data-ttu-id="f5b2d-121">描述</span><span class="sxs-lookup"><span data-stu-id="f5b2d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="f5b2d-122">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5b2d-123">備註</span><span class="sxs-lookup"><span data-stu-id="f5b2d-123">Remarks</span></span>  

 <span data-ttu-id="f5b2d-124">您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="f5b2d-125">您可以使用屬性來指定集合的名稱 `name` 。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="f5b2d-126">架構所處理的唯一名稱為 "ActAs" 和 "OnBehalfOf"。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="f5b2d-127">如果處理常式存在於這些集合中，安全性權杖服務會使用這些處理常式 (STS) ，而不是處理和權杖時的預設處理常式 `ActAs` `OnBehalfOf` 。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="f5b2d-128">根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="f5b2d-129">您可以使用 `<add>` 、和元素來修改集合 `<remove>` `<clear>` 。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="f5b2d-130">您必須確定集合中只存在任何特定類型的單一處理程式。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="f5b2d-131">例如，如果您從類別衍生處理常式 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ，您的處理常式或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 可以在單一集合中設定，但不能同時設定兩者。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="f5b2d-132">您 `<securityTokenHandlerConfiguration>` 可以使用元素來指定集合中處理常式的配置設定。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="f5b2d-133">透過這個專案指定的設定會透過專案覆寫服務上指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f5b2d-134">某些處理常式 (包括數個內建處理常式類型) 可透過專案的子項目支援其他設定 `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="f5b2d-135">處理常式上指定的設定會覆寫集合或服務上指定的對等設定。</span><span class="sxs-lookup"><span data-stu-id="f5b2d-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
