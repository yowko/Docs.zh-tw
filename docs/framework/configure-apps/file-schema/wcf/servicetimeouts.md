---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a1792fec4f86c9ac31107c043b976cfafcfa4c13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937099"
---
# <a name="servicetimeouts"></a><span data-ttu-id="4bfe2-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="4bfe2-101">\<serviceTimeouts></span></span>
<span data-ttu-id="4bfe2-102">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="4bfe2-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="4bfe2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4bfe2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4bfe2-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4bfe2-104">\<behaviors></span></span>  
<span data-ttu-id="4bfe2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4bfe2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="4bfe2-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4bfe2-106">\<behavior></span></span>  
<span data-ttu-id="4bfe2-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="4bfe2-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfe2-108">語法</span><span class="sxs-lookup"><span data-stu-id="4bfe2-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="4bfe2-109">類型</span><span class="sxs-lookup"><span data-stu-id="4bfe2-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bfe2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4bfe2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4bfe2-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4bfe2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bfe2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4bfe2-112">Attributes</span></span>  
  
|<span data-ttu-id="4bfe2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4bfe2-113">Attribute</span></span>|<span data-ttu-id="4bfe2-114">說明</span><span class="sxs-lookup"><span data-stu-id="4bfe2-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="4bfe2-115"><xref:System.TimeSpan> 值，指定異動必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="4bfe2-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="4bfe2-116">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="4bfe2-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4bfe2-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4bfe2-117">Child Elements</span></span>  
 <span data-ttu-id="4bfe2-118">無。</span><span class="sxs-lookup"><span data-stu-id="4bfe2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4bfe2-119">父項目</span><span class="sxs-lookup"><span data-stu-id="4bfe2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4bfe2-120">項目</span><span class="sxs-lookup"><span data-stu-id="4bfe2-120">Element</span></span>|<span data-ttu-id="4bfe2-121">描述</span><span class="sxs-lookup"><span data-stu-id="4bfe2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bfe2-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4bfe2-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4bfe2-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4bfe2-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bfe2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bfe2-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
