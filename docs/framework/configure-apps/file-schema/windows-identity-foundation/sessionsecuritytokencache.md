---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943716"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="7d7d2-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7d7d2-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="7d7d2-102">向服務或安全性權杖處理常式集合註冊會話權杖的快取。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="7d7d2-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7d7d2-103">\<system.identityModel></span></span>  
<span data-ttu-id="7d7d2-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7d7d2-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7d7d2-105">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="7d7d2-105">\<caches></span></span>  
<span data-ttu-id="7d7d2-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7d7d2-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7d2-107">語法</span><span class="sxs-lookup"><span data-stu-id="7d7d2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d7d2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7d7d2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d7d2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d7d2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7d7d2-110">Attributes</span></span>  
  
|<span data-ttu-id="7d7d2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7d7d2-111">Attribute</span></span>|<span data-ttu-id="7d7d2-112">描述</span><span class="sxs-lookup"><span data-stu-id="7d7d2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d7d2-113">型別</span><span class="sxs-lookup"><span data-stu-id="7d7d2-113">type</span></span>|<span data-ttu-id="7d7d2-114">衍生自<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別的類型。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d7d2-115">子元素</span><span class="sxs-lookup"><span data-stu-id="7d7d2-115">Child Elements</span></span>  
 <span data-ttu-id="7d7d2-116">無</span><span class="sxs-lookup"><span data-stu-id="7d7d2-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d7d2-117">父項目</span><span class="sxs-lookup"><span data-stu-id="7d7d2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7d7d2-118">項目</span><span class="sxs-lookup"><span data-stu-id="7d7d2-118">Element</span></span>|<span data-ttu-id="7d7d2-119">描述</span><span class="sxs-lookup"><span data-stu-id="7d7d2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d7d2-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="7d7d2-120">\<caches></span></span>](caches.md)|<span data-ttu-id="7d7d2-121">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d7d2-122">範例</span><span class="sxs-lookup"><span data-stu-id="7d7d2-122">Example</span></span>  
 <span data-ttu-id="7d7d2-123">下列 XML 顯示用來保存會話安全性權杖 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) 的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="7d7d2-124">此設定取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="7d7d2-125">如需此範例的詳細資訊, 請參閱[WIF 程式碼範例索引](../../../security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="7d7d2-125">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d7d2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d7d2-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
