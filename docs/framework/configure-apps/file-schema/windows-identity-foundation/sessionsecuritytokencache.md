---
title: '&lt;Sessionsecuritytokencache>&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: b812673ac1c015adde357d3c0707d85643aad3e9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084328"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="f0ddc-102">&lt;Sessionsecuritytokencache>&gt;</span><span class="sxs-lookup"><span data-stu-id="f0ddc-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="f0ddc-103">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="f0ddc-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f0ddc-104">\<system.identityModel></span></span>  
<span data-ttu-id="f0ddc-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f0ddc-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f0ddc-106">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="f0ddc-106">\<caches></span></span>  
<span data-ttu-id="f0ddc-107">\<Sessionsecuritytokencache> ></span><span class="sxs-lookup"><span data-stu-id="f0ddc-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ddc-108">語法</span><span class="sxs-lookup"><span data-stu-id="f0ddc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0ddc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f0ddc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f0ddc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0ddc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f0ddc-111">Attributes</span></span>  
  
|<span data-ttu-id="f0ddc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f0ddc-112">Attribute</span></span>|<span data-ttu-id="f0ddc-113">描述</span><span class="sxs-lookup"><span data-stu-id="f0ddc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0ddc-114">類型</span><span class="sxs-lookup"><span data-stu-id="f0ddc-114">type</span></span>|<span data-ttu-id="f0ddc-115">衍生自類型<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0ddc-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f0ddc-116">Child Elements</span></span>  
 <span data-ttu-id="f0ddc-117">無</span><span class="sxs-lookup"><span data-stu-id="f0ddc-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0ddc-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f0ddc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f0ddc-119">項目</span><span class="sxs-lookup"><span data-stu-id="f0ddc-119">Element</span></span>|<span data-ttu-id="f0ddc-120">描述</span><span class="sxs-lookup"><span data-stu-id="f0ddc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0ddc-121">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="f0ddc-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="f0ddc-122">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f0ddc-123">範例</span><span class="sxs-lookup"><span data-stu-id="f0ddc-123">Example</span></span>  
 <span data-ttu-id="f0ddc-124">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="f0ddc-125">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="f0ddc-126">如需有關此範例的詳細資訊，請參閱 < [WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ddc-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0ddc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0ddc-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
