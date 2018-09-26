---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: d21a819f789b5be4bdf7ebf57b37a072e1d213ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206214"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="19a2c-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="19a2c-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="19a2c-103">註冊權杖重新執行快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="19a2c-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="19a2c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="19a2c-104">\<system.identityModel></span></span>  
<span data-ttu-id="19a2c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="19a2c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="19a2c-106">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="19a2c-106">\<caches></span></span>  
<span data-ttu-id="19a2c-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="19a2c-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a2c-108">語法</span><span class="sxs-lookup"><span data-stu-id="19a2c-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19a2c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19a2c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="19a2c-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="19a2c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19a2c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="19a2c-111">Attributes</span></span>  
  
|<span data-ttu-id="19a2c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="19a2c-112">Attribute</span></span>|<span data-ttu-id="19a2c-113">描述</span><span class="sxs-lookup"><span data-stu-id="19a2c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19a2c-114">類型</span><span class="sxs-lookup"><span data-stu-id="19a2c-114">type</span></span>|<span data-ttu-id="19a2c-115">衍生自類型<xref:System.IdentityModel.Tokens.TokenReplayCache>類別。</span><span class="sxs-lookup"><span data-stu-id="19a2c-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="19a2c-116">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="19a2c-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="19a2c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="19a2c-117">Child Elements</span></span>  
 <span data-ttu-id="19a2c-118">無</span><span class="sxs-lookup"><span data-stu-id="19a2c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19a2c-119">父項目</span><span class="sxs-lookup"><span data-stu-id="19a2c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="19a2c-120">項目</span><span class="sxs-lookup"><span data-stu-id="19a2c-120">Element</span></span>|<span data-ttu-id="19a2c-121">描述</span><span class="sxs-lookup"><span data-stu-id="19a2c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19a2c-122">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="19a2c-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="19a2c-123">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="19a2c-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19a2c-124">備註</span><span class="sxs-lookup"><span data-stu-id="19a2c-124">Remarks</span></span>  
 <span data-ttu-id="19a2c-125">權杖重新執行快取用來偵測重新執行的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="19a2c-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="19a2c-126">會啟用權杖重新執行偵測[ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)項目，也會指定權杖的最大的到期時間。</span><span class="sxs-lookup"><span data-stu-id="19a2c-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a2c-127">範例</span><span class="sxs-lookup"><span data-stu-id="19a2c-127">Example</span></span>  
 <span data-ttu-id="19a2c-128">下列 XML 顯示自訂偵測重新執行的權杖快取的設定。</span><span class="sxs-lookup"><span data-stu-id="19a2c-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19a2c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19a2c-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="19a2c-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="19a2c-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
