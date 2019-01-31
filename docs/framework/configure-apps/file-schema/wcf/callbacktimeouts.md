---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 269500324ad1beaa0b519fa17d251ee942276faa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269064"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="c954b-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="c954b-101">\<callbackTimeouts></span></span>
<span data-ttu-id="c954b-102">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="c954b-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="c954b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c954b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c954b-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c954b-104">\<behaviors></span></span>  
<span data-ttu-id="c954b-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c954b-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="c954b-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c954b-106">\<behavior></span></span>  
<span data-ttu-id="c954b-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="c954b-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c954b-108">語法</span><span class="sxs-lookup"><span data-stu-id="c954b-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="c954b-109">類型</span><span class="sxs-lookup"><span data-stu-id="c954b-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c954b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c954b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c954b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c954b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c954b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c954b-112">Attributes</span></span>  
  
|<span data-ttu-id="c954b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c954b-113">Attribute</span></span>|<span data-ttu-id="c954b-114">描述</span><span class="sxs-lookup"><span data-stu-id="c954b-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="c954b-115"><xref:System.TimeSpan> 值，指定異動必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c954b-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="c954b-116">預設值是"00: 00:00"。</span><span class="sxs-lookup"><span data-stu-id="c954b-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c954b-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c954b-117">Child Elements</span></span>  
 <span data-ttu-id="c954b-118">無。</span><span class="sxs-lookup"><span data-stu-id="c954b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c954b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c954b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c954b-120">項目</span><span class="sxs-lookup"><span data-stu-id="c954b-120">Element</span></span>|<span data-ttu-id="c954b-121">描述</span><span class="sxs-lookup"><span data-stu-id="c954b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c954b-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c954b-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c954b-123">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="c954b-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c954b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c954b-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
