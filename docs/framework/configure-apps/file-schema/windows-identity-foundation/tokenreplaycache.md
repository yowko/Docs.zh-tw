---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5e695bb56b59da40ce9e83f9f4f77d0d22d0b40f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202418"
---
# \<tokenReplayCache>

<span data-ttu-id="f22b1-101">使用服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="f22b1-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="f22b1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f22b1-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f22b1-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f22b1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f22b1-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f22b1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f22b1-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f22b1-105">Attributes</span></span>  
  
|<span data-ttu-id="f22b1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f22b1-106">Attribute</span></span>|<span data-ttu-id="f22b1-107">描述</span><span class="sxs-lookup"><span data-stu-id="f22b1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f22b1-108">type</span><span class="sxs-lookup"><span data-stu-id="f22b1-108">type</span></span>|<span data-ttu-id="f22b1-109">衍生自類別的型別 <xref:System.IdentityModel.Tokens.TokenReplayCache> 。</span><span class="sxs-lookup"><span data-stu-id="f22b1-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="f22b1-110">如需如何指定自訂的詳細資訊 `type` ，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="f22b1-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="f22b1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f22b1-111">Child Elements</span></span>  

 <span data-ttu-id="f22b1-112">無</span><span class="sxs-lookup"><span data-stu-id="f22b1-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f22b1-113">父項目</span><span class="sxs-lookup"><span data-stu-id="f22b1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f22b1-114">項目</span><span class="sxs-lookup"><span data-stu-id="f22b1-114">Element</span></span>|<span data-ttu-id="f22b1-115">描述</span><span class="sxs-lookup"><span data-stu-id="f22b1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="f22b1-116">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="f22b1-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f22b1-117">備註</span><span class="sxs-lookup"><span data-stu-id="f22b1-117">Remarks</span></span>  

 <span data-ttu-id="f22b1-118">權杖重新執行快取可用來偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="f22b1-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="f22b1-119">專案會啟用權杖重新執行偵測 [\<tokenReplayDetection>](tokenreplaydetection.md) ，這也會指定權杖的最長到期時間。</span><span class="sxs-lookup"><span data-stu-id="f22b1-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f22b1-120">範例</span><span class="sxs-lookup"><span data-stu-id="f22b1-120">Example</span></span>  

 <span data-ttu-id="f22b1-121">下列 XML 會顯示自訂快取的設定，用於偵測重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="f22b1-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f22b1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f22b1-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
