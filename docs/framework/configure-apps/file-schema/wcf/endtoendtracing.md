---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: c2f5e33eff4fdc6dfa85bcc10b59a7c1436cabb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519364"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="49208-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="49208-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="49208-103">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="49208-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="49208-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="49208-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="49208-105">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="49208-105">\<diagnostic></span></span>  
<span data-ttu-id="49208-106">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="49208-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49208-107">語法</span><span class="sxs-lookup"><span data-stu-id="49208-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49208-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="49208-108">Attributes and Elements</span></span>  
 <span data-ttu-id="49208-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="49208-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49208-110">屬性</span><span class="sxs-lookup"><span data-stu-id="49208-110">Attributes</span></span>  
  
|<span data-ttu-id="49208-111">屬性</span><span class="sxs-lookup"><span data-stu-id="49208-111">Attribute</span></span>|<span data-ttu-id="49208-112">描述</span><span class="sxs-lookup"><span data-stu-id="49208-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="49208-113">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="49208-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="49208-114">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="49208-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="49208-115">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="49208-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49208-116">子元素</span><span class="sxs-lookup"><span data-stu-id="49208-116">Child Elements</span></span>  
 <span data-ttu-id="49208-117">無。</span><span class="sxs-lookup"><span data-stu-id="49208-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49208-118">父項目</span><span class="sxs-lookup"><span data-stu-id="49208-118">Parent Elements</span></span>  
  
|<span data-ttu-id="49208-119">項目</span><span class="sxs-lookup"><span data-stu-id="49208-119">Element</span></span>|<span data-ttu-id="49208-120">描述</span><span class="sxs-lookup"><span data-stu-id="49208-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49208-121">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="49208-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="49208-122">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="49208-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49208-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49208-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="49208-124">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="49208-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
