---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 697c20d1f526cb376c2430f0006349f7d8f9b2f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257937"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="4b511-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="4b511-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="4b511-102">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="4b511-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="4b511-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4b511-103">\<system.identityModel></span></span>  
<span data-ttu-id="4b511-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b511-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4b511-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="4b511-105">\<caches></span></span>  
<span data-ttu-id="4b511-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="4b511-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b511-107">語法</span><span class="sxs-lookup"><span data-stu-id="4b511-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b511-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4b511-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b511-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4b511-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b511-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4b511-110">Attributes</span></span>  
  
|<span data-ttu-id="4b511-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4b511-111">Attribute</span></span>|<span data-ttu-id="4b511-112">描述</span><span class="sxs-lookup"><span data-stu-id="4b511-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b511-113">類型</span><span class="sxs-lookup"><span data-stu-id="4b511-113">type</span></span>|<span data-ttu-id="4b511-114">衍生自類型<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。</span><span class="sxs-lookup"><span data-stu-id="4b511-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b511-115">子元素</span><span class="sxs-lookup"><span data-stu-id="4b511-115">Child Elements</span></span>  
 <span data-ttu-id="4b511-116">無</span><span class="sxs-lookup"><span data-stu-id="4b511-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b511-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4b511-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4b511-118">項目</span><span class="sxs-lookup"><span data-stu-id="4b511-118">Element</span></span>|<span data-ttu-id="4b511-119">描述</span><span class="sxs-lookup"><span data-stu-id="4b511-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b511-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="4b511-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="4b511-121">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="4b511-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4b511-122">範例</span><span class="sxs-lookup"><span data-stu-id="4b511-122">Example</span></span>  
 <span data-ttu-id="4b511-123">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="4b511-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="4b511-124">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="4b511-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="4b511-125">如需有關此範例的詳細資訊，請參閱 < [WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="4b511-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b511-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b511-126">See also</span></span>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
