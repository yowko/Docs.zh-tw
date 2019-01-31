---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285658"
---
# <a name="caches"></a><span data-ttu-id="bff45-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="bff45-101">\<caches></span></span>
<span data-ttu-id="bff45-102">註冊用於工作階段權杖和權杖重新執行偵測快取。</span><span class="sxs-lookup"><span data-stu-id="bff45-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="bff45-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bff45-103">\<system.identityModel></span></span>  
<span data-ttu-id="bff45-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bff45-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bff45-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="bff45-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bff45-106">語法</span><span class="sxs-lookup"><span data-stu-id="bff45-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bff45-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bff45-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bff45-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bff45-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bff45-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bff45-109">Attributes</span></span>  
 <span data-ttu-id="bff45-110">無</span><span class="sxs-lookup"><span data-stu-id="bff45-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bff45-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bff45-111">Child Elements</span></span>  
  
|<span data-ttu-id="bff45-112">項目</span><span class="sxs-lookup"><span data-stu-id="bff45-112">Element</span></span>|<span data-ttu-id="bff45-113">描述</span><span class="sxs-lookup"><span data-stu-id="bff45-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bff45-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="bff45-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="bff45-115">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="bff45-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="bff45-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="bff45-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="bff45-117">註冊權杖重新執行快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="bff45-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bff45-118">父項目</span><span class="sxs-lookup"><span data-stu-id="bff45-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bff45-119">項目</span><span class="sxs-lookup"><span data-stu-id="bff45-119">Element</span></span>|<span data-ttu-id="bff45-120">描述</span><span class="sxs-lookup"><span data-stu-id="bff45-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bff45-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bff45-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="bff45-122">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="bff45-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="bff45-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="bff45-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="bff45-124">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="bff45-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bff45-125">備註</span><span class="sxs-lookup"><span data-stu-id="bff45-125">Remarks</span></span>  
 <span data-ttu-id="bff45-126">A`<caches>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="bff45-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="bff45-127">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="bff45-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="bff45-128">`<caches>`項目由<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>類別。</span><span class="sxs-lookup"><span data-stu-id="bff45-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="bff45-129">設定快取都由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別。</span><span class="sxs-lookup"><span data-stu-id="bff45-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bff45-130">範例</span><span class="sxs-lookup"><span data-stu-id="bff45-130">Example</span></span>  
 <span data-ttu-id="bff45-131">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="bff45-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="bff45-132">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="bff45-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
