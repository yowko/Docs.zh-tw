---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 79022319944c4042c6f62a7521784b826b90d4ce
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="503c8-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="503c8-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="503c8-103">使用的服務或安全性權杖處理常式集合中註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="503c8-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="503c8-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="503c8-104">\<system.identityModel></span></span>  
<span data-ttu-id="503c8-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="503c8-105">\<identityConfiguration></span></span>  
<span data-ttu-id="503c8-106">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="503c8-106">\<caches></span></span>  
<span data-ttu-id="503c8-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="503c8-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503c8-108">語法</span><span class="sxs-lookup"><span data-stu-id="503c8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="503c8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="503c8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="503c8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="503c8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="503c8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="503c8-111">Attributes</span></span>  
  
|<span data-ttu-id="503c8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="503c8-112">Attribute</span></span>|<span data-ttu-id="503c8-113">描述</span><span class="sxs-lookup"><span data-stu-id="503c8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="503c8-114">類型</span><span class="sxs-lookup"><span data-stu-id="503c8-114">type</span></span>|<span data-ttu-id="503c8-115">從衍生的型別<xref:System.IdentityModel.Tokens.TokenReplayCache>類別。</span><span class="sxs-lookup"><span data-stu-id="503c8-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="503c8-116">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="503c8-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="503c8-117">子項目</span><span class="sxs-lookup"><span data-stu-id="503c8-117">Child Elements</span></span>  
 <span data-ttu-id="503c8-118">無</span><span class="sxs-lookup"><span data-stu-id="503c8-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="503c8-119">父項目</span><span class="sxs-lookup"><span data-stu-id="503c8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="503c8-120">項目</span><span class="sxs-lookup"><span data-stu-id="503c8-120">Element</span></span>|<span data-ttu-id="503c8-121">描述</span><span class="sxs-lookup"><span data-stu-id="503c8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="503c8-122">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="503c8-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="503c8-123">註冊快取使用的服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="503c8-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="503c8-124">備註</span><span class="sxs-lookup"><span data-stu-id="503c8-124">Remarks</span></span>  
 <span data-ttu-id="503c8-125">權杖重新執行快取用來偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="503c8-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="503c8-126">會啟用權杖重新執行偵測[ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)項目，也會指定權杖的最大的到期時間。</span><span class="sxs-lookup"><span data-stu-id="503c8-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="503c8-127">範例</span><span class="sxs-lookup"><span data-stu-id="503c8-127">Example</span></span>  
 <span data-ttu-id="503c8-128">下列 XML 顯示用於偵測重新執行的權杖的自訂快取的設定。</span><span class="sxs-lookup"><span data-stu-id="503c8-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="503c8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="503c8-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="503c8-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="503c8-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
