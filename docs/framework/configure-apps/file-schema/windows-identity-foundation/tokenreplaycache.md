---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251776"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="628b1-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="628b1-101">\<tokenReplayCache></span></span>
<span data-ttu-id="628b1-102">向服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="628b1-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="628b1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="628b1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="628b1-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="628b1-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="628b1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="628b1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="628b1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<快取 >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="628b1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="628b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayCache >**</span><span class="sxs-lookup"><span data-stu-id="628b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628b1-108">語法</span><span class="sxs-lookup"><span data-stu-id="628b1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="628b1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="628b1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="628b1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="628b1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="628b1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="628b1-111">Attributes</span></span>  
  
|<span data-ttu-id="628b1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="628b1-112">Attribute</span></span>|<span data-ttu-id="628b1-113">描述</span><span class="sxs-lookup"><span data-stu-id="628b1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="628b1-114">型別</span><span class="sxs-lookup"><span data-stu-id="628b1-114">type</span></span>|<span data-ttu-id="628b1-115">衍生自<xref:System.IdentityModel.Tokens.TokenReplayCache>類別的類型。</span><span class="sxs-lookup"><span data-stu-id="628b1-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="628b1-116">如需如何指定自訂`type`的詳細資訊, 請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="628b1-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="628b1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="628b1-117">Child Elements</span></span>  
 <span data-ttu-id="628b1-118">無</span><span class="sxs-lookup"><span data-stu-id="628b1-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="628b1-119">父項目</span><span class="sxs-lookup"><span data-stu-id="628b1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="628b1-120">項目</span><span class="sxs-lookup"><span data-stu-id="628b1-120">Element</span></span>|<span data-ttu-id="628b1-121">說明</span><span class="sxs-lookup"><span data-stu-id="628b1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="628b1-122">\<caches></span><span class="sxs-lookup"><span data-stu-id="628b1-122">\<caches></span></span>](caches.md)|<span data-ttu-id="628b1-123">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="628b1-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="628b1-124">備註</span><span class="sxs-lookup"><span data-stu-id="628b1-124">Remarks</span></span>  
 <span data-ttu-id="628b1-125">權杖重新執行快取是用來偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="628b1-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="628b1-126">TokenReplayDetection > 元素會啟用[ \<](tokenreplaydetection.md)權杖重新執行偵測, 這也會指定權杖的最長到期時間。</span><span class="sxs-lookup"><span data-stu-id="628b1-126">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="628b1-127">範例</span><span class="sxs-lookup"><span data-stu-id="628b1-127">Example</span></span>  
 <span data-ttu-id="628b1-128">下列 XML 顯示用來偵測重新執行權杖的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="628b1-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="628b1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="628b1-129">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="628b1-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="628b1-130">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
