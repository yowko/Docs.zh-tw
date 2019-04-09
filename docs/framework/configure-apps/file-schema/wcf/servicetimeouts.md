---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075514"
---
# <a name="servicetimeouts"></a><span data-ttu-id="2a715-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="2a715-101">\<serviceTimeouts></span></span>
<span data-ttu-id="2a715-102">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="2a715-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="2a715-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a715-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a715-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="2a715-104">\<behaviors></span></span>  
<span data-ttu-id="2a715-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2a715-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2a715-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2a715-106">\<behavior></span></span>  
<span data-ttu-id="2a715-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="2a715-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a715-108">語法</span><span class="sxs-lookup"><span data-stu-id="2a715-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="2a715-109">類型</span><span class="sxs-lookup"><span data-stu-id="2a715-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a715-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a715-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a715-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a715-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a715-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2a715-112">Attributes</span></span>  
  
|<span data-ttu-id="2a715-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2a715-113">Attribute</span></span>|<span data-ttu-id="2a715-114">描述</span><span class="sxs-lookup"><span data-stu-id="2a715-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="2a715-115"><xref:System.TimeSpan> 值，指定異動必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2a715-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="2a715-116">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="2a715-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a715-117">子元素</span><span class="sxs-lookup"><span data-stu-id="2a715-117">Child Elements</span></span>  
 <span data-ttu-id="2a715-118">無。</span><span class="sxs-lookup"><span data-stu-id="2a715-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a715-119">父項目</span><span class="sxs-lookup"><span data-stu-id="2a715-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2a715-120">項目</span><span class="sxs-lookup"><span data-stu-id="2a715-120">Element</span></span>|<span data-ttu-id="2a715-121">描述</span><span class="sxs-lookup"><span data-stu-id="2a715-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a715-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2a715-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2a715-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="2a715-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a715-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a715-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
