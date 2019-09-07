---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400069"
---
# <a name="persistenceprovider"></a><span data-ttu-id="6d35d-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="6d35d-101">\<persistenceProvider></span></span>
<span data-ttu-id="6d35d-102">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="6d35d-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
<span data-ttu-id="6d35d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6d35d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6d35d-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6d35d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6d35d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6d35d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6d35d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6d35d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="6d35d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6d35d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="6d35d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistenceProvider >**</span><span class="sxs-lookup"><span data-stu-id="6d35d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d35d-109">語法</span><span class="sxs-lookup"><span data-stu-id="6d35d-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d35d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6d35d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6d35d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6d35d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d35d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6d35d-112">Attributes</span></span>  
  
|<span data-ttu-id="6d35d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6d35d-113">Attribute</span></span>|<span data-ttu-id="6d35d-114">描述</span><span class="sxs-lookup"><span data-stu-id="6d35d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d35d-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="6d35d-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="6d35d-116"><xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。</span><span class="sxs-lookup"><span data-stu-id="6d35d-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="6d35d-117">預設值為 "00:00:30"。</span><span class="sxs-lookup"><span data-stu-id="6d35d-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="6d35d-118">型別</span><span class="sxs-lookup"><span data-stu-id="6d35d-118">type</span></span>|<span data-ttu-id="6d35d-119">字串，指定要使用的持續性提供者處理站之型別。</span><span class="sxs-lookup"><span data-stu-id="6d35d-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d35d-120">子元素</span><span class="sxs-lookup"><span data-stu-id="6d35d-120">Child Elements</span></span>  
 <span data-ttu-id="6d35d-121">無。</span><span class="sxs-lookup"><span data-stu-id="6d35d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d35d-122">父項目</span><span class="sxs-lookup"><span data-stu-id="6d35d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6d35d-123">項目</span><span class="sxs-lookup"><span data-stu-id="6d35d-123">Element</span></span>|<span data-ttu-id="6d35d-124">描述</span><span class="sxs-lookup"><span data-stu-id="6d35d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d35d-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6d35d-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6d35d-126">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="6d35d-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d35d-127">備註</span><span class="sxs-lookup"><span data-stu-id="6d35d-127">Remarks</span></span>  
 <span data-ttu-id="6d35d-128">這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="6d35d-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="6d35d-129">它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。</span><span class="sxs-lookup"><span data-stu-id="6d35d-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d35d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d35d-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
