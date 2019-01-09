---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 85e7b1f0d009e27cbacd9f69b381e4f05984bf56
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149107"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="7cfff-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="7cfff-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="7cfff-103">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="7cfff-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="7cfff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7cfff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7cfff-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7cfff-105">\<behaviors></span></span>  
<span data-ttu-id="7cfff-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7cfff-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7cfff-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7cfff-107">\<behavior></span></span>  
<span data-ttu-id="7cfff-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="7cfff-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cfff-109">語法</span><span class="sxs-lookup"><span data-stu-id="7cfff-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="7cfff-110">類型</span><span class="sxs-lookup"><span data-stu-id="7cfff-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cfff-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7cfff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7cfff-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7cfff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cfff-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7cfff-113">Attributes</span></span>  
  
|<span data-ttu-id="7cfff-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7cfff-114">Attribute</span></span>|<span data-ttu-id="7cfff-115">描述</span><span class="sxs-lookup"><span data-stu-id="7cfff-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="7cfff-116"><xref:System.TimeSpan> 值，指定異動必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="7cfff-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="7cfff-117">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="7cfff-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cfff-118">子元素</span><span class="sxs-lookup"><span data-stu-id="7cfff-118">Child Elements</span></span>  
 <span data-ttu-id="7cfff-119">無。</span><span class="sxs-lookup"><span data-stu-id="7cfff-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cfff-120">父項目</span><span class="sxs-lookup"><span data-stu-id="7cfff-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7cfff-121">項目</span><span class="sxs-lookup"><span data-stu-id="7cfff-121">Element</span></span>|<span data-ttu-id="7cfff-122">描述</span><span class="sxs-lookup"><span data-stu-id="7cfff-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cfff-123">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7cfff-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7cfff-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="7cfff-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cfff-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cfff-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
