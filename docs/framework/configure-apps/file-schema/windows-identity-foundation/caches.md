---
title: "&lt;快取&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a><span data-ttu-id="37cc5-102">&lt;快取&gt;</span><span class="sxs-lookup"><span data-stu-id="37cc5-102">&lt;caches&gt;</span></span>
<span data-ttu-id="37cc5-103">註冊用於工作階段權杖，權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="37cc5-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="37cc5-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="37cc5-104">\<system.identityModel></span></span>  
<span data-ttu-id="37cc5-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37cc5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="37cc5-106">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="37cc5-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37cc5-107">語法</span><span class="sxs-lookup"><span data-stu-id="37cc5-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37cc5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="37cc5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37cc5-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="37cc5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37cc5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="37cc5-110">Attributes</span></span>  
 <span data-ttu-id="37cc5-111">無</span><span class="sxs-lookup"><span data-stu-id="37cc5-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37cc5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="37cc5-112">Child Elements</span></span>  
  
|<span data-ttu-id="37cc5-113">項目</span><span class="sxs-lookup"><span data-stu-id="37cc5-113">Element</span></span>|<span data-ttu-id="37cc5-114">描述</span><span class="sxs-lookup"><span data-stu-id="37cc5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37cc5-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="37cc5-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="37cc5-116">使用的服務或安全性權杖處理常式集合中註冊一份快取工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="37cc5-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="37cc5-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="37cc5-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="37cc5-118">使用的服務或安全性權杖處理常式集合中註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="37cc5-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37cc5-119">父項目</span><span class="sxs-lookup"><span data-stu-id="37cc5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="37cc5-120">項目</span><span class="sxs-lookup"><span data-stu-id="37cc5-120">Element</span></span>|<span data-ttu-id="37cc5-121">描述</span><span class="sxs-lookup"><span data-stu-id="37cc5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37cc5-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37cc5-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="37cc5-123">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="37cc5-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="37cc5-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37cc5-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="37cc5-125">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="37cc5-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37cc5-126">備註</span><span class="sxs-lookup"><span data-stu-id="37cc5-126">Remarks</span></span>  
 <span data-ttu-id="37cc5-127">A`<caches>`元素可以指定在服務層級下`<identityConfiguration>`項目或安全性權杖處理常式集合層級下`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="37cc5-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="37cc5-128">權杖處理常式集合上的設定會覆寫在服務上指定。</span><span class="sxs-lookup"><span data-stu-id="37cc5-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="37cc5-129">`<caches>`項目由<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>類別。</span><span class="sxs-lookup"><span data-stu-id="37cc5-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="37cc5-130">設定快取都由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別。</span><span class="sxs-lookup"><span data-stu-id="37cc5-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37cc5-131">範例</span><span class="sxs-lookup"><span data-stu-id="37cc5-131">Example</span></span>  
 <span data-ttu-id="37cc5-132">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="37cc5-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="37cc5-133">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="37cc5-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
