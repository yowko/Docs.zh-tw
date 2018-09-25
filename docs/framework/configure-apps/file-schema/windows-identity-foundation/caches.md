---
title: '&lt;快取&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: a91a389e53354e4f5b26e1510fc2f025300d65cc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084237"
---
# <a name="ltcachesgt"></a><span data-ttu-id="66c7c-102">&lt;快取&gt;</span><span class="sxs-lookup"><span data-stu-id="66c7c-102">&lt;caches&gt;</span></span>
<span data-ttu-id="66c7c-103">註冊用於工作階段權杖和權杖重新執行偵測快取。</span><span class="sxs-lookup"><span data-stu-id="66c7c-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="66c7c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="66c7c-104">\<system.identityModel></span></span>  
<span data-ttu-id="66c7c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="66c7c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="66c7c-106">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="66c7c-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c7c-107">語法</span><span class="sxs-lookup"><span data-stu-id="66c7c-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66c7c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66c7c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="66c7c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66c7c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66c7c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="66c7c-110">Attributes</span></span>  
 <span data-ttu-id="66c7c-111">無</span><span class="sxs-lookup"><span data-stu-id="66c7c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66c7c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="66c7c-112">Child Elements</span></span>  
  
|<span data-ttu-id="66c7c-113">項目</span><span class="sxs-lookup"><span data-stu-id="66c7c-113">Element</span></span>|<span data-ttu-id="66c7c-114">描述</span><span class="sxs-lookup"><span data-stu-id="66c7c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66c7c-115">\<Sessionsecuritytokencache> ></span><span class="sxs-lookup"><span data-stu-id="66c7c-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="66c7c-116">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="66c7c-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="66c7c-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="66c7c-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="66c7c-118">註冊權杖重新執行快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="66c7c-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66c7c-119">父項目</span><span class="sxs-lookup"><span data-stu-id="66c7c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="66c7c-120">項目</span><span class="sxs-lookup"><span data-stu-id="66c7c-120">Element</span></span>|<span data-ttu-id="66c7c-121">描述</span><span class="sxs-lookup"><span data-stu-id="66c7c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66c7c-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="66c7c-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="66c7c-123">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="66c7c-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="66c7c-124">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="66c7c-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="66c7c-125">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="66c7c-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66c7c-126">備註</span><span class="sxs-lookup"><span data-stu-id="66c7c-126">Remarks</span></span>  
 <span data-ttu-id="66c7c-127">A`<caches>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="66c7c-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="66c7c-128">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="66c7c-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="66c7c-129">`<caches>`項目由<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>類別。</span><span class="sxs-lookup"><span data-stu-id="66c7c-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="66c7c-130">設定快取都由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別。</span><span class="sxs-lookup"><span data-stu-id="66c7c-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66c7c-131">範例</span><span class="sxs-lookup"><span data-stu-id="66c7c-131">Example</span></span>  
 <span data-ttu-id="66c7c-132">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="66c7c-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="66c7c-133">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="66c7c-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
