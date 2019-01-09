---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 4cb4b4ae6fe01430989d9ee5f3d94b16778595aa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148470"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="29107-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="29107-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="29107-103">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="29107-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="29107-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="29107-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="29107-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="29107-105">\<behaviors></span></span>  
<span data-ttu-id="29107-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="29107-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="29107-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="29107-107">\<behavior></span></span>  
<span data-ttu-id="29107-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="29107-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29107-109">語法</span><span class="sxs-lookup"><span data-stu-id="29107-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="29107-110">類型</span><span class="sxs-lookup"><span data-stu-id="29107-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29107-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="29107-111">Attributes and Elements</span></span>  
 <span data-ttu-id="29107-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="29107-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29107-113">屬性</span><span class="sxs-lookup"><span data-stu-id="29107-113">Attributes</span></span>  
  
|<span data-ttu-id="29107-114">屬性</span><span class="sxs-lookup"><span data-stu-id="29107-114">Attribute</span></span>|<span data-ttu-id="29107-115">描述</span><span class="sxs-lookup"><span data-stu-id="29107-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="29107-116"><xref:System.TimeSpan> 值，指定異動必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="29107-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="29107-117">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="29107-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29107-118">子元素</span><span class="sxs-lookup"><span data-stu-id="29107-118">Child Elements</span></span>  
 <span data-ttu-id="29107-119">無。</span><span class="sxs-lookup"><span data-stu-id="29107-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29107-120">父項目</span><span class="sxs-lookup"><span data-stu-id="29107-120">Parent Elements</span></span>  
  
|<span data-ttu-id="29107-121">項目</span><span class="sxs-lookup"><span data-stu-id="29107-121">Element</span></span>|<span data-ttu-id="29107-122">描述</span><span class="sxs-lookup"><span data-stu-id="29107-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29107-123">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="29107-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="29107-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="29107-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29107-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29107-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
