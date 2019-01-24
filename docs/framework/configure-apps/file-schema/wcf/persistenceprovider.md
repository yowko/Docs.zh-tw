---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 8deca5b4bec4808ac9add201db0c936764fddcb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602217"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="d51fd-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="d51fd-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="d51fd-103">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="d51fd-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="d51fd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d51fd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d51fd-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="d51fd-105">\<behaviors></span></span>  
<span data-ttu-id="d51fd-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d51fd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d51fd-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d51fd-107">\<behavior></span></span>  
<span data-ttu-id="d51fd-108">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="d51fd-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51fd-109">語法</span><span class="sxs-lookup"><span data-stu-id="d51fd-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d51fd-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d51fd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d51fd-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d51fd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d51fd-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d51fd-112">Attributes</span></span>  
  
|<span data-ttu-id="d51fd-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d51fd-113">Attribute</span></span>|<span data-ttu-id="d51fd-114">描述</span><span class="sxs-lookup"><span data-stu-id="d51fd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d51fd-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="d51fd-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="d51fd-116"><xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。</span><span class="sxs-lookup"><span data-stu-id="d51fd-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="d51fd-117">預設值是"00: 00:30"。</span><span class="sxs-lookup"><span data-stu-id="d51fd-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="d51fd-118">類型</span><span class="sxs-lookup"><span data-stu-id="d51fd-118">type</span></span>|<span data-ttu-id="d51fd-119">字串，指定要使用的持續性提供者處理站之型別。</span><span class="sxs-lookup"><span data-stu-id="d51fd-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d51fd-120">子元素</span><span class="sxs-lookup"><span data-stu-id="d51fd-120">Child Elements</span></span>  
 <span data-ttu-id="d51fd-121">無。</span><span class="sxs-lookup"><span data-stu-id="d51fd-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d51fd-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d51fd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d51fd-123">項目</span><span class="sxs-lookup"><span data-stu-id="d51fd-123">Element</span></span>|<span data-ttu-id="d51fd-124">描述</span><span class="sxs-lookup"><span data-stu-id="d51fd-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d51fd-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d51fd-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d51fd-126">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="d51fd-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d51fd-127">備註</span><span class="sxs-lookup"><span data-stu-id="d51fd-127">Remarks</span></span>  
 <span data-ttu-id="d51fd-128">這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="d51fd-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="d51fd-129">它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。</span><span class="sxs-lookup"><span data-stu-id="d51fd-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51fd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d51fd-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
