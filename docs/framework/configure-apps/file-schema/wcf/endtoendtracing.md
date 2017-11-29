---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1bcd7405c5e3ebf2d1c156ff3bca9f473df9fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="e12a1-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="e12a1-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="e12a1-103">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="e12a1-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="e12a1-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e12a1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e12a1-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="e12a1-105">\<diagnostic></span></span>  
<span data-ttu-id="e12a1-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="e12a1-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e12a1-107">語法</span><span class="sxs-lookup"><span data-stu-id="e12a1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e12a1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e12a1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e12a1-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e12a1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e12a1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e12a1-110">Attributes</span></span>  
  
|<span data-ttu-id="e12a1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e12a1-111">Attribute</span></span>|<span data-ttu-id="e12a1-112">描述</span><span class="sxs-lookup"><span data-stu-id="e12a1-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="e12a1-113">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="e12a1-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="e12a1-114">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="e12a1-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="e12a1-115">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="e12a1-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e12a1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e12a1-116">Child Elements</span></span>  
 <span data-ttu-id="e12a1-117">無。</span><span class="sxs-lookup"><span data-stu-id="e12a1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e12a1-118">父項目</span><span class="sxs-lookup"><span data-stu-id="e12a1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e12a1-119">項目</span><span class="sxs-lookup"><span data-stu-id="e12a1-119">Element</span></span>|<span data-ttu-id="e12a1-120">說明</span><span class="sxs-lookup"><span data-stu-id="e12a1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e12a1-121">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="e12a1-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="e12a1-122">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="e12a1-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e12a1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e12a1-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="e12a1-124">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="e12a1-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
