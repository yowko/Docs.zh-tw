---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 266b33e9b0386d0346a86ba8bd82cc65def4f0c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180150"
---
# <a name="endtoendtracing"></a><span data-ttu-id="56b23-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="56b23-101">\<endToEndTracing></span></span>
<span data-ttu-id="56b23-102">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="56b23-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="56b23-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56b23-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="56b23-104">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="56b23-104">\<diagnostic></span></span>  
<span data-ttu-id="56b23-105">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="56b23-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b23-106">語法</span><span class="sxs-lookup"><span data-stu-id="56b23-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56b23-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56b23-107">Attributes and Elements</span></span>  
 <span data-ttu-id="56b23-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56b23-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56b23-109">屬性</span><span class="sxs-lookup"><span data-stu-id="56b23-109">Attributes</span></span>  
  
|<span data-ttu-id="56b23-110">屬性</span><span class="sxs-lookup"><span data-stu-id="56b23-110">Attribute</span></span>|<span data-ttu-id="56b23-111">描述</span><span class="sxs-lookup"><span data-stu-id="56b23-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="56b23-112">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="56b23-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="56b23-113">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="56b23-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="56b23-114">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="56b23-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56b23-115">子元素</span><span class="sxs-lookup"><span data-stu-id="56b23-115">Child Elements</span></span>  
 <span data-ttu-id="56b23-116">無。</span><span class="sxs-lookup"><span data-stu-id="56b23-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56b23-117">父項目</span><span class="sxs-lookup"><span data-stu-id="56b23-117">Parent Elements</span></span>  
  
|<span data-ttu-id="56b23-118">項目</span><span class="sxs-lookup"><span data-stu-id="56b23-118">Element</span></span>|<span data-ttu-id="56b23-119">描述</span><span class="sxs-lookup"><span data-stu-id="56b23-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56b23-120">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="56b23-120">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="56b23-121">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="56b23-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56b23-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56b23-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="56b23-123">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="56b23-123">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
