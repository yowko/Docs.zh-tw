---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: dfa6c0d84582d55595f00f149adfdcaa9d554d6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271945"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="9cdca-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="9cdca-101">\<tokenReplayCache></span></span>
<span data-ttu-id="9cdca-102">註冊權杖重新執行快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="9cdca-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="9cdca-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9cdca-103">\<system.identityModel></span></span>  
<span data-ttu-id="9cdca-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9cdca-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9cdca-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="9cdca-105">\<caches></span></span>  
<span data-ttu-id="9cdca-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="9cdca-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdca-107">語法</span><span class="sxs-lookup"><span data-stu-id="9cdca-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cdca-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9cdca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9cdca-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9cdca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cdca-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9cdca-110">Attributes</span></span>  
  
|<span data-ttu-id="9cdca-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9cdca-111">Attribute</span></span>|<span data-ttu-id="9cdca-112">描述</span><span class="sxs-lookup"><span data-stu-id="9cdca-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cdca-113">類型</span><span class="sxs-lookup"><span data-stu-id="9cdca-113">type</span></span>|<span data-ttu-id="9cdca-114">衍生自類型<xref:System.IdentityModel.Tokens.TokenReplayCache>類別。</span><span class="sxs-lookup"><span data-stu-id="9cdca-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="9cdca-115">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="9cdca-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9cdca-116">子元素</span><span class="sxs-lookup"><span data-stu-id="9cdca-116">Child Elements</span></span>  
 <span data-ttu-id="9cdca-117">無</span><span class="sxs-lookup"><span data-stu-id="9cdca-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cdca-118">父項目</span><span class="sxs-lookup"><span data-stu-id="9cdca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9cdca-119">項目</span><span class="sxs-lookup"><span data-stu-id="9cdca-119">Element</span></span>|<span data-ttu-id="9cdca-120">描述</span><span class="sxs-lookup"><span data-stu-id="9cdca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cdca-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="9cdca-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="9cdca-122">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="9cdca-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cdca-123">備註</span><span class="sxs-lookup"><span data-stu-id="9cdca-123">Remarks</span></span>  
 <span data-ttu-id="9cdca-124">權杖重新執行快取用來偵測重新執行的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9cdca-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="9cdca-125">會啟用權杖重新執行偵測[ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)項目，也會指定權杖的最大的到期時間。</span><span class="sxs-lookup"><span data-stu-id="9cdca-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cdca-126">範例</span><span class="sxs-lookup"><span data-stu-id="9cdca-126">Example</span></span>  
 <span data-ttu-id="9cdca-127">下列 XML 顯示自訂偵測重新執行的權杖快取的設定。</span><span class="sxs-lookup"><span data-stu-id="9cdca-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cdca-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cdca-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="9cdca-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="9cdca-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
