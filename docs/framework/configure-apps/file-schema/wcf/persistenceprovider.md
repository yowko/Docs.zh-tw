---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 054991687a54ecbf95cc18f58717a4ed3e36f050
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260797"
---
# <a name="persistenceprovider"></a><span data-ttu-id="f6e98-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="f6e98-101">\<persistenceProvider></span></span>
<span data-ttu-id="f6e98-102">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="f6e98-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="f6e98-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f6e98-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6e98-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f6e98-104">\<behaviors></span></span>  
<span data-ttu-id="f6e98-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f6e98-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f6e98-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f6e98-106">\<behavior></span></span>  
<span data-ttu-id="f6e98-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="f6e98-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e98-108">語法</span><span class="sxs-lookup"><span data-stu-id="f6e98-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6e98-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f6e98-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f6e98-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f6e98-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6e98-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f6e98-111">Attributes</span></span>  
  
|<span data-ttu-id="f6e98-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f6e98-112">Attribute</span></span>|<span data-ttu-id="f6e98-113">描述</span><span class="sxs-lookup"><span data-stu-id="f6e98-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6e98-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="f6e98-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="f6e98-115"><xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。</span><span class="sxs-lookup"><span data-stu-id="f6e98-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="f6e98-116">預設值是"00: 00:30"。</span><span class="sxs-lookup"><span data-stu-id="f6e98-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="f6e98-117">類型</span><span class="sxs-lookup"><span data-stu-id="f6e98-117">type</span></span>|<span data-ttu-id="f6e98-118">字串，指定要使用的持續性提供者處理站之型別。</span><span class="sxs-lookup"><span data-stu-id="f6e98-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6e98-119">子元素</span><span class="sxs-lookup"><span data-stu-id="f6e98-119">Child Elements</span></span>  
 <span data-ttu-id="f6e98-120">無。</span><span class="sxs-lookup"><span data-stu-id="f6e98-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6e98-121">父項目</span><span class="sxs-lookup"><span data-stu-id="f6e98-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f6e98-122">項目</span><span class="sxs-lookup"><span data-stu-id="f6e98-122">Element</span></span>|<span data-ttu-id="f6e98-123">描述</span><span class="sxs-lookup"><span data-stu-id="f6e98-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6e98-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f6e98-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f6e98-125">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="f6e98-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6e98-126">備註</span><span class="sxs-lookup"><span data-stu-id="f6e98-126">Remarks</span></span>  
 <span data-ttu-id="f6e98-127">這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="f6e98-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="f6e98-128">它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。</span><span class="sxs-lookup"><span data-stu-id="f6e98-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e98-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e98-129">See also</span></span>
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
