---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 4fc9e1332effc51e183a84cf2d3653357277d2ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934145"
---
# <a name="persistenceprovider"></a><span data-ttu-id="70aed-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="70aed-101">\<persistenceProvider></span></span>
<span data-ttu-id="70aed-102">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="70aed-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="70aed-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70aed-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="70aed-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="70aed-104">\<behaviors></span></span>  
<span data-ttu-id="70aed-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="70aed-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="70aed-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="70aed-106">\<behavior></span></span>  
<span data-ttu-id="70aed-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="70aed-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70aed-108">語法</span><span class="sxs-lookup"><span data-stu-id="70aed-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70aed-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70aed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70aed-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="70aed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70aed-111">屬性</span><span class="sxs-lookup"><span data-stu-id="70aed-111">Attributes</span></span>  
  
|<span data-ttu-id="70aed-112">屬性</span><span class="sxs-lookup"><span data-stu-id="70aed-112">Attribute</span></span>|<span data-ttu-id="70aed-113">描述</span><span class="sxs-lookup"><span data-stu-id="70aed-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70aed-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="70aed-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="70aed-115"><xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。</span><span class="sxs-lookup"><span data-stu-id="70aed-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="70aed-116">預設值為 "00:00:30"。</span><span class="sxs-lookup"><span data-stu-id="70aed-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="70aed-117">型別</span><span class="sxs-lookup"><span data-stu-id="70aed-117">type</span></span>|<span data-ttu-id="70aed-118">字串，指定要使用的持續性提供者處理站之型別。</span><span class="sxs-lookup"><span data-stu-id="70aed-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70aed-119">子元素</span><span class="sxs-lookup"><span data-stu-id="70aed-119">Child Elements</span></span>  
 <span data-ttu-id="70aed-120">無。</span><span class="sxs-lookup"><span data-stu-id="70aed-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70aed-121">父項目</span><span class="sxs-lookup"><span data-stu-id="70aed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="70aed-122">項目</span><span class="sxs-lookup"><span data-stu-id="70aed-122">Element</span></span>|<span data-ttu-id="70aed-123">說明</span><span class="sxs-lookup"><span data-stu-id="70aed-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70aed-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="70aed-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="70aed-125">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="70aed-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70aed-126">備註</span><span class="sxs-lookup"><span data-stu-id="70aed-126">Remarks</span></span>  
 <span data-ttu-id="70aed-127">這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="70aed-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="70aed-128">它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。</span><span class="sxs-lookup"><span data-stu-id="70aed-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70aed-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70aed-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
