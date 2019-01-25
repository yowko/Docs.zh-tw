---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 024375cb114bb080c576ea033e5588526350ecdf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510087"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="cdb15-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="cdb15-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="cdb15-103">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="cdb15-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="cdb15-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cdb15-104">\<system.identityModel></span></span>  
<span data-ttu-id="cdb15-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cdb15-105">\<identityConfiguration></span></span>  
<span data-ttu-id="cdb15-106">\<caches></span><span class="sxs-lookup"><span data-stu-id="cdb15-106">\<caches></span></span>  
<span data-ttu-id="cdb15-107">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="cdb15-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb15-108">語法</span><span class="sxs-lookup"><span data-stu-id="cdb15-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdb15-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cdb15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cdb15-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cdb15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdb15-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cdb15-111">Attributes</span></span>  
  
|<span data-ttu-id="cdb15-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cdb15-112">Attribute</span></span>|<span data-ttu-id="cdb15-113">描述</span><span class="sxs-lookup"><span data-stu-id="cdb15-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdb15-114">類型</span><span class="sxs-lookup"><span data-stu-id="cdb15-114">type</span></span>|<span data-ttu-id="cdb15-115">衍生自類型<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。</span><span class="sxs-lookup"><span data-stu-id="cdb15-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdb15-116">子元素</span><span class="sxs-lookup"><span data-stu-id="cdb15-116">Child Elements</span></span>  
 <span data-ttu-id="cdb15-117">無</span><span class="sxs-lookup"><span data-stu-id="cdb15-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdb15-118">父項目</span><span class="sxs-lookup"><span data-stu-id="cdb15-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cdb15-119">項目</span><span class="sxs-lookup"><span data-stu-id="cdb15-119">Element</span></span>|<span data-ttu-id="cdb15-120">描述</span><span class="sxs-lookup"><span data-stu-id="cdb15-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdb15-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="cdb15-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="cdb15-122">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="cdb15-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cdb15-123">範例</span><span class="sxs-lookup"><span data-stu-id="cdb15-123">Example</span></span>  
 <span data-ttu-id="cdb15-124">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="cdb15-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="cdb15-125">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="cdb15-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="cdb15-126">如需有關此範例的詳細資訊，請參閱 < [WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb15-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdb15-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdb15-127">See also</span></span>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
