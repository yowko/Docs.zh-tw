---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0b0d3c01a81f110f79f64d75aa2ab2ff2873fedd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755041"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="97dfa-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="97dfa-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="97dfa-103">使用的服務或安全性權杖處理常式集合中註冊一份快取工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="97dfa-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="97dfa-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="97dfa-104">\<system.identityModel></span></span>  
<span data-ttu-id="97dfa-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="97dfa-105">\<identityConfiguration></span></span>  
<span data-ttu-id="97dfa-106">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="97dfa-106">\<caches></span></span>  
<span data-ttu-id="97dfa-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="97dfa-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97dfa-108">語法</span><span class="sxs-lookup"><span data-stu-id="97dfa-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97dfa-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="97dfa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97dfa-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="97dfa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97dfa-111">屬性</span><span class="sxs-lookup"><span data-stu-id="97dfa-111">Attributes</span></span>  
  
|<span data-ttu-id="97dfa-112">屬性</span><span class="sxs-lookup"><span data-stu-id="97dfa-112">Attribute</span></span>|<span data-ttu-id="97dfa-113">描述</span><span class="sxs-lookup"><span data-stu-id="97dfa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97dfa-114">類型</span><span class="sxs-lookup"><span data-stu-id="97dfa-114">type</span></span>|<span data-ttu-id="97dfa-115">從衍生的型別<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。</span><span class="sxs-lookup"><span data-stu-id="97dfa-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97dfa-116">子項目</span><span class="sxs-lookup"><span data-stu-id="97dfa-116">Child Elements</span></span>  
 <span data-ttu-id="97dfa-117">無</span><span class="sxs-lookup"><span data-stu-id="97dfa-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97dfa-118">父項目</span><span class="sxs-lookup"><span data-stu-id="97dfa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="97dfa-119">項目</span><span class="sxs-lookup"><span data-stu-id="97dfa-119">Element</span></span>|<span data-ttu-id="97dfa-120">描述</span><span class="sxs-lookup"><span data-stu-id="97dfa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97dfa-121">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="97dfa-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="97dfa-122">註冊快取使用的服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="97dfa-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97dfa-123">範例</span><span class="sxs-lookup"><span data-stu-id="97dfa-123">Example</span></span>  
 <span data-ttu-id="97dfa-124">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="97dfa-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="97dfa-125">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="97dfa-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="97dfa-126">如需有關此範例的詳細資訊，請參閱[WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="97dfa-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97dfa-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97dfa-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
