---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: d57a888a19e684ac13632c1ab2476e304667c3e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919656"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="44952-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="44952-101">\<callbackTimeouts></span></span>
<span data-ttu-id="44952-102">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="44952-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="44952-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="44952-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="44952-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="44952-104">\<behaviors></span></span>  
<span data-ttu-id="44952-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="44952-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="44952-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="44952-106">\<behavior></span></span>  
<span data-ttu-id="44952-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="44952-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44952-108">語法</span><span class="sxs-lookup"><span data-stu-id="44952-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="44952-109">類型</span><span class="sxs-lookup"><span data-stu-id="44952-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44952-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="44952-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44952-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="44952-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44952-112">屬性</span><span class="sxs-lookup"><span data-stu-id="44952-112">Attributes</span></span>  
  
|<span data-ttu-id="44952-113">屬性</span><span class="sxs-lookup"><span data-stu-id="44952-113">Attribute</span></span>|<span data-ttu-id="44952-114">描述</span><span class="sxs-lookup"><span data-stu-id="44952-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="44952-115"><xref:System.TimeSpan> 值，指定異動必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="44952-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="44952-116">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="44952-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44952-117">子元素</span><span class="sxs-lookup"><span data-stu-id="44952-117">Child Elements</span></span>  
 <span data-ttu-id="44952-118">無。</span><span class="sxs-lookup"><span data-stu-id="44952-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44952-119">父項目</span><span class="sxs-lookup"><span data-stu-id="44952-119">Parent Elements</span></span>  
  
|<span data-ttu-id="44952-120">項目</span><span class="sxs-lookup"><span data-stu-id="44952-120">Element</span></span>|<span data-ttu-id="44952-121">描述</span><span class="sxs-lookup"><span data-stu-id="44952-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44952-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="44952-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="44952-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="44952-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44952-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44952-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
