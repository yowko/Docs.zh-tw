---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400069"
---
# \<persistenceProvider>
<span data-ttu-id="b016b-101">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="b016b-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="b016b-102">語法</span><span class="sxs-lookup"><span data-stu-id="b016b-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b016b-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b016b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b016b-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b016b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b016b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b016b-105">Attributes</span></span>  
  
|<span data-ttu-id="b016b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b016b-106">Attribute</span></span>|<span data-ttu-id="b016b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b016b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b016b-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="b016b-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="b016b-109"><xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。</span><span class="sxs-lookup"><span data-stu-id="b016b-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="b016b-110">預設值為 "00:00:30"。</span><span class="sxs-lookup"><span data-stu-id="b016b-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="b016b-111">type</span><span class="sxs-lookup"><span data-stu-id="b016b-111">type</span></span>|<span data-ttu-id="b016b-112">字串，指定要使用的持續性提供者處理站之型別。</span><span class="sxs-lookup"><span data-stu-id="b016b-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b016b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b016b-113">Child Elements</span></span>  
 <span data-ttu-id="b016b-114">無。</span><span class="sxs-lookup"><span data-stu-id="b016b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b016b-115">父項目</span><span class="sxs-lookup"><span data-stu-id="b016b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b016b-116">元素</span><span class="sxs-lookup"><span data-stu-id="b016b-116">Element</span></span>|<span data-ttu-id="b016b-117">描述</span><span class="sxs-lookup"><span data-stu-id="b016b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b016b-118">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="b016b-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b016b-119">備註</span><span class="sxs-lookup"><span data-stu-id="b016b-119">Remarks</span></span>  
 <span data-ttu-id="b016b-120">這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="b016b-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="b016b-121">它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。</span><span class="sxs-lookup"><span data-stu-id="b016b-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b016b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b016b-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
