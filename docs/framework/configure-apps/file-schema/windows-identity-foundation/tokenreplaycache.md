---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1567c669b5e682a7a771d7bedc95a8effa474e36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113382"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="3be71-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="3be71-101">\<tokenReplayCache></span></span>
<span data-ttu-id="3be71-102">註冊權杖重新執行快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="3be71-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="3be71-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3be71-103">\<system.identityModel></span></span>  
<span data-ttu-id="3be71-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3be71-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3be71-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="3be71-105">\<caches></span></span>  
<span data-ttu-id="3be71-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="3be71-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be71-107">語法</span><span class="sxs-lookup"><span data-stu-id="3be71-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3be71-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3be71-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3be71-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3be71-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3be71-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3be71-110">Attributes</span></span>  
  
|<span data-ttu-id="3be71-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3be71-111">Attribute</span></span>|<span data-ttu-id="3be71-112">描述</span><span class="sxs-lookup"><span data-stu-id="3be71-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3be71-113">類型</span><span class="sxs-lookup"><span data-stu-id="3be71-113">type</span></span>|<span data-ttu-id="3be71-114">衍生自類型<xref:System.IdentityModel.Tokens.TokenReplayCache>類別。</span><span class="sxs-lookup"><span data-stu-id="3be71-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="3be71-115">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="3be71-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="3be71-116">子元素</span><span class="sxs-lookup"><span data-stu-id="3be71-116">Child Elements</span></span>  
 <span data-ttu-id="3be71-117">None</span><span class="sxs-lookup"><span data-stu-id="3be71-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3be71-118">父項目</span><span class="sxs-lookup"><span data-stu-id="3be71-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3be71-119">項目</span><span class="sxs-lookup"><span data-stu-id="3be71-119">Element</span></span>|<span data-ttu-id="3be71-120">描述</span><span class="sxs-lookup"><span data-stu-id="3be71-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3be71-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="3be71-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="3be71-122">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="3be71-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3be71-123">備註</span><span class="sxs-lookup"><span data-stu-id="3be71-123">Remarks</span></span>  
 <span data-ttu-id="3be71-124">權杖重新執行快取用來偵測重新執行的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3be71-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="3be71-125">會啟用權杖重新執行偵測[ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)項目，也會指定權杖的最大的到期時間。</span><span class="sxs-lookup"><span data-stu-id="3be71-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3be71-126">範例</span><span class="sxs-lookup"><span data-stu-id="3be71-126">Example</span></span>  
 <span data-ttu-id="3be71-127">下列 XML 顯示自訂偵測重新執行的權杖快取的設定。</span><span class="sxs-lookup"><span data-stu-id="3be71-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3be71-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3be71-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="3be71-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="3be71-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
