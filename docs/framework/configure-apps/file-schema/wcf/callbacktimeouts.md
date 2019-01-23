---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 01932fe2b7b7e699311e2c65ec8adaf0aef82dc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557899"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="94aec-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="94aec-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="94aec-103">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="94aec-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="94aec-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="94aec-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="94aec-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="94aec-105">\<behaviors></span></span>  
<span data-ttu-id="94aec-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="94aec-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="94aec-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="94aec-107">\<behavior></span></span>  
<span data-ttu-id="94aec-108">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="94aec-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94aec-109">語法</span><span class="sxs-lookup"><span data-stu-id="94aec-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="94aec-110">類型</span><span class="sxs-lookup"><span data-stu-id="94aec-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94aec-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="94aec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="94aec-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="94aec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94aec-113">屬性</span><span class="sxs-lookup"><span data-stu-id="94aec-113">Attributes</span></span>  
  
|<span data-ttu-id="94aec-114">屬性</span><span class="sxs-lookup"><span data-stu-id="94aec-114">Attribute</span></span>|<span data-ttu-id="94aec-115">描述</span><span class="sxs-lookup"><span data-stu-id="94aec-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="94aec-116"><xref:System.TimeSpan> 值，指定異動必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="94aec-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="94aec-117">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="94aec-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94aec-118">子元素</span><span class="sxs-lookup"><span data-stu-id="94aec-118">Child Elements</span></span>  
 <span data-ttu-id="94aec-119">無。</span><span class="sxs-lookup"><span data-stu-id="94aec-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94aec-120">父項目</span><span class="sxs-lookup"><span data-stu-id="94aec-120">Parent Elements</span></span>  
  
|<span data-ttu-id="94aec-121">項目</span><span class="sxs-lookup"><span data-stu-id="94aec-121">Element</span></span>|<span data-ttu-id="94aec-122">描述</span><span class="sxs-lookup"><span data-stu-id="94aec-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94aec-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="94aec-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="94aec-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="94aec-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94aec-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94aec-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
