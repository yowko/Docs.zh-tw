---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e43e79416ddb8862cbc6e52d9d449a02b123af83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="bb33a-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="bb33a-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="bb33a-103">使用的服務或安全性權杖處理常式集合中註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="bb33a-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="bb33a-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="bb33a-104">\<system.identityModel></span></span>  
<span data-ttu-id="bb33a-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bb33a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="bb33a-106">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="bb33a-106">\<caches></span></span>  
<span data-ttu-id="bb33a-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="bb33a-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb33a-108">語法</span><span class="sxs-lookup"><span data-stu-id="bb33a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb33a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bb33a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bb33a-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bb33a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb33a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bb33a-111">Attributes</span></span>  
  
|<span data-ttu-id="bb33a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bb33a-112">Attribute</span></span>|<span data-ttu-id="bb33a-113">描述</span><span class="sxs-lookup"><span data-stu-id="bb33a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb33a-114">類型</span><span class="sxs-lookup"><span data-stu-id="bb33a-114">type</span></span>|<span data-ttu-id="bb33a-115">從衍生的型別<xref:System.IdentityModel.Tokens.TokenReplayCache>類別。</span><span class="sxs-lookup"><span data-stu-id="bb33a-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="bb33a-116">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="bb33a-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="bb33a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="bb33a-117">Child Elements</span></span>  
 <span data-ttu-id="bb33a-118">無</span><span class="sxs-lookup"><span data-stu-id="bb33a-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb33a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="bb33a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bb33a-120">項目</span><span class="sxs-lookup"><span data-stu-id="bb33a-120">Element</span></span>|<span data-ttu-id="bb33a-121">說明</span><span class="sxs-lookup"><span data-stu-id="bb33a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb33a-122">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="bb33a-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="bb33a-123">註冊快取使用的服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="bb33a-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb33a-124">備註</span><span class="sxs-lookup"><span data-stu-id="bb33a-124">Remarks</span></span>  
 <span data-ttu-id="bb33a-125">權杖重新執行快取用來偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="bb33a-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="bb33a-126">會啟用權杖重新執行偵測[ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)項目，也會指定權杖的最大的到期時間。</span><span class="sxs-lookup"><span data-stu-id="bb33a-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb33a-127">範例</span><span class="sxs-lookup"><span data-stu-id="bb33a-127">Example</span></span>  
 <span data-ttu-id="bb33a-128">下列 XML 顯示用於偵測重新執行的權杖的自訂快取的設定。</span><span class="sxs-lookup"><span data-stu-id="bb33a-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb33a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb33a-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="bb33a-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="bb33a-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
