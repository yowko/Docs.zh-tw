---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750783"
---
# <a name="caches"></a><span data-ttu-id="f7f4f-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="f7f4f-101">\<caches></span></span>
<span data-ttu-id="f7f4f-102">註冊用於工作階段權杖和權杖重新執行偵測快取。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="f7f4f-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f7f4f-103">\<system.identityModel></span></span>  
<span data-ttu-id="f7f4f-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f7f4f-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f7f4f-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="f7f4f-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f4f-106">語法</span><span class="sxs-lookup"><span data-stu-id="f7f4f-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7f4f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f7f4f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f7f4f-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7f4f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f7f4f-109">Attributes</span></span>  
 <span data-ttu-id="f7f4f-110">None</span><span class="sxs-lookup"><span data-stu-id="f7f4f-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7f4f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f7f4f-111">Child Elements</span></span>  
  
|<span data-ttu-id="f7f4f-112">項目</span><span class="sxs-lookup"><span data-stu-id="f7f4f-112">Element</span></span>|<span data-ttu-id="f7f4f-113">描述</span><span class="sxs-lookup"><span data-stu-id="f7f4f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7f4f-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="f7f4f-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="f7f4f-115">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="f7f4f-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="f7f4f-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="f7f4f-117">註冊權杖重新執行快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7f4f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f7f4f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f7f4f-119">項目</span><span class="sxs-lookup"><span data-stu-id="f7f4f-119">Element</span></span>|<span data-ttu-id="f7f4f-120">描述</span><span class="sxs-lookup"><span data-stu-id="f7f4f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7f4f-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f7f4f-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="f7f4f-122">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="f7f4f-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="f7f4f-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="f7f4f-124">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7f4f-125">備註</span><span class="sxs-lookup"><span data-stu-id="f7f4f-125">Remarks</span></span>  
 <span data-ttu-id="f7f4f-126">A`<caches>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="f7f4f-127">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="f7f4f-128">`<caches>`項目由<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>類別。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="f7f4f-129">設定快取都由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7f4f-130">範例</span><span class="sxs-lookup"><span data-stu-id="f7f4f-130">Example</span></span>  
 <span data-ttu-id="f7f4f-131">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="f7f4f-132">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="f7f4f-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
