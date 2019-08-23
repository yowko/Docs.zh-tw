---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919006"
---
# <a name="endtoendtracing"></a><span data-ttu-id="4b7e3-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="4b7e3-101">\<endToEndTracing></span></span>
<span data-ttu-id="4b7e3-102">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="4b7e3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b7e3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b7e3-104">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="4b7e3-104">\<diagnostic></span></span>  
<span data-ttu-id="4b7e3-105">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="4b7e3-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b7e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="4b7e3-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b7e3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4b7e3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4b7e3-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b7e3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4b7e3-109">Attributes</span></span>  
  
|<span data-ttu-id="4b7e3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4b7e3-110">Attribute</span></span>|<span data-ttu-id="4b7e3-111">描述</span><span class="sxs-lookup"><span data-stu-id="4b7e3-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="4b7e3-112">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="4b7e3-113">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="4b7e3-114">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b7e3-115">子元素</span><span class="sxs-lookup"><span data-stu-id="4b7e3-115">Child Elements</span></span>  
 <span data-ttu-id="4b7e3-116">無。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b7e3-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4b7e3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4b7e3-118">項目</span><span class="sxs-lookup"><span data-stu-id="4b7e3-118">Element</span></span>|<span data-ttu-id="4b7e3-119">描述</span><span class="sxs-lookup"><span data-stu-id="4b7e3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b7e3-120">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="4b7e3-120">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="4b7e3-121">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="4b7e3-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b7e3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b7e3-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="4b7e3-123">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="4b7e3-123">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
