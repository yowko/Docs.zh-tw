---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941970"
---
# <a name="caches"></a><span data-ttu-id="8eed7-101">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="8eed7-101">\<caches></span></span>
<span data-ttu-id="8eed7-102">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="8eed7-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="8eed7-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8eed7-103">\<system.identityModel></span></span>  
<span data-ttu-id="8eed7-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8eed7-104">\<identityConfiguration></span></span>  
<span data-ttu-id="8eed7-105">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="8eed7-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eed7-106">語法</span><span class="sxs-lookup"><span data-stu-id="8eed7-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eed7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8eed7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8eed7-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8eed7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eed7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8eed7-109">Attributes</span></span>  
 <span data-ttu-id="8eed7-110">無</span><span class="sxs-lookup"><span data-stu-id="8eed7-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8eed7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8eed7-111">Child Elements</span></span>  
  
|<span data-ttu-id="8eed7-112">項目</span><span class="sxs-lookup"><span data-stu-id="8eed7-112">Element</span></span>|<span data-ttu-id="8eed7-113">描述</span><span class="sxs-lookup"><span data-stu-id="8eed7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eed7-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="8eed7-114">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="8eed7-115">向服務或安全性權杖處理常式集合註冊會話權杖的快取。</span><span class="sxs-lookup"><span data-stu-id="8eed7-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="8eed7-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="8eed7-116">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="8eed7-117">向服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="8eed7-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8eed7-118">父項目</span><span class="sxs-lookup"><span data-stu-id="8eed7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8eed7-119">項目</span><span class="sxs-lookup"><span data-stu-id="8eed7-119">Element</span></span>|<span data-ttu-id="8eed7-120">說明</span><span class="sxs-lookup"><span data-stu-id="8eed7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eed7-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8eed7-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="8eed7-122">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="8eed7-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="8eed7-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8eed7-123">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8eed7-124">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="8eed7-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eed7-125">備註</span><span class="sxs-lookup"><span data-stu-id="8eed7-125">Remarks</span></span>  
 <span data-ttu-id="8eed7-126">元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<caches>`</span><span class="sxs-lookup"><span data-stu-id="8eed7-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="8eed7-127">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="8eed7-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="8eed7-128">`<caches>`元素是<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="8eed7-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="8eed7-129">設定的快取是由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別表示。</span><span class="sxs-lookup"><span data-stu-id="8eed7-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eed7-130">範例</span><span class="sxs-lookup"><span data-stu-id="8eed7-130">Example</span></span>  
 <span data-ttu-id="8eed7-131">下列 XML 顯示用來保存會話安全性權杖 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) 的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="8eed7-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="8eed7-132">此設定取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="8eed7-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
