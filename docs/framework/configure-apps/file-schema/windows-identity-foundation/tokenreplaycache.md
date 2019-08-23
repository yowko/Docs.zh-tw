---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944069"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="c519e-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c519e-101">\<tokenReplayCache></span></span>
<span data-ttu-id="c519e-102">向服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="c519e-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="c519e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c519e-103">\<system.identityModel></span></span>  
<span data-ttu-id="c519e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c519e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c519e-105">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="c519e-105">\<caches></span></span>  
<span data-ttu-id="c519e-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c519e-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c519e-107">語法</span><span class="sxs-lookup"><span data-stu-id="c519e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c519e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c519e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c519e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c519e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c519e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c519e-110">Attributes</span></span>  
  
|<span data-ttu-id="c519e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c519e-111">Attribute</span></span>|<span data-ttu-id="c519e-112">描述</span><span class="sxs-lookup"><span data-stu-id="c519e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c519e-113">型別</span><span class="sxs-lookup"><span data-stu-id="c519e-113">type</span></span>|<span data-ttu-id="c519e-114">衍生自<xref:System.IdentityModel.Tokens.TokenReplayCache>類別的類型。</span><span class="sxs-lookup"><span data-stu-id="c519e-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="c519e-115">如需如何指定自訂`type`的詳細資訊, 請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="c519e-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="c519e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c519e-116">Child Elements</span></span>  
 <span data-ttu-id="c519e-117">無</span><span class="sxs-lookup"><span data-stu-id="c519e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c519e-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c519e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c519e-119">項目</span><span class="sxs-lookup"><span data-stu-id="c519e-119">Element</span></span>|<span data-ttu-id="c519e-120">描述</span><span class="sxs-lookup"><span data-stu-id="c519e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c519e-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="c519e-121">\<caches></span></span>](caches.md)|<span data-ttu-id="c519e-122">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="c519e-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c519e-123">備註</span><span class="sxs-lookup"><span data-stu-id="c519e-123">Remarks</span></span>  
 <span data-ttu-id="c519e-124">權杖重新執行快取是用來偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="c519e-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="c519e-125">TokenReplayDetection > 元素會啟用[ \<](tokenreplaydetection.md)權杖重新執行偵測, 這也會指定權杖的最長到期時間。</span><span class="sxs-lookup"><span data-stu-id="c519e-125">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c519e-126">範例</span><span class="sxs-lookup"><span data-stu-id="c519e-126">Example</span></span>  
 <span data-ttu-id="c519e-127">下列 XML 顯示用來偵測重新執行權杖的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="c519e-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c519e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c519e-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="c519e-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="c519e-129">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
