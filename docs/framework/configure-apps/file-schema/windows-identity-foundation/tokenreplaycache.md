---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251776"
---
# \<tokenReplayCache>
<span data-ttu-id="34c79-101">向服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="34c79-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="34c79-102">語法</span><span class="sxs-lookup"><span data-stu-id="34c79-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34c79-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="34c79-103">Attributes and Elements</span></span>  
 <span data-ttu-id="34c79-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="34c79-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34c79-105">屬性</span><span class="sxs-lookup"><span data-stu-id="34c79-105">Attributes</span></span>  
  
|<span data-ttu-id="34c79-106">屬性</span><span class="sxs-lookup"><span data-stu-id="34c79-106">Attribute</span></span>|<span data-ttu-id="34c79-107">描述</span><span class="sxs-lookup"><span data-stu-id="34c79-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34c79-108">type</span><span class="sxs-lookup"><span data-stu-id="34c79-108">type</span></span>|<span data-ttu-id="34c79-109">衍生自類別的類型 <xref:System.IdentityModel.Tokens.TokenReplayCache> 。</span><span class="sxs-lookup"><span data-stu-id="34c79-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="34c79-110">如需如何指定自訂的詳細資訊 `type` ，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="34c79-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="34c79-111">子元素</span><span class="sxs-lookup"><span data-stu-id="34c79-111">Child Elements</span></span>  
 <span data-ttu-id="34c79-112">無</span><span class="sxs-lookup"><span data-stu-id="34c79-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34c79-113">父項目</span><span class="sxs-lookup"><span data-stu-id="34c79-113">Parent Elements</span></span>  
  
|<span data-ttu-id="34c79-114">元素</span><span class="sxs-lookup"><span data-stu-id="34c79-114">Element</span></span>|<span data-ttu-id="34c79-115">描述</span><span class="sxs-lookup"><span data-stu-id="34c79-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="34c79-116">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="34c79-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34c79-117">備註</span><span class="sxs-lookup"><span data-stu-id="34c79-117">Remarks</span></span>  
 <span data-ttu-id="34c79-118">權杖重新執行快取是用來偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="34c79-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="34c79-119">權杖重新執行偵測是由 [\<tokenReplayDetection>](tokenreplaydetection.md) 元素啟用，這也會指定權杖的最長到期時間。</span><span class="sxs-lookup"><span data-stu-id="34c79-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34c79-120">範例</span><span class="sxs-lookup"><span data-stu-id="34c79-120">Example</span></span>  
 <span data-ttu-id="34c79-121">下列 XML 顯示用來偵測重新執行權杖的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="34c79-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34c79-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34c79-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
