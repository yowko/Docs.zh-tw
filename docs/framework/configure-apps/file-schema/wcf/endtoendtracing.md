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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="c0fc5-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="c0fc5-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="c0fc5-103">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="c0fc5-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c0fc5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0fc5-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="c0fc5-105">\<diagnostic></span></span>  
<span data-ttu-id="c0fc5-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="c0fc5-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0fc5-107">語法</span><span class="sxs-lookup"><span data-stu-id="c0fc5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0fc5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0fc5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c0fc5-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0fc5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c0fc5-110">Attributes</span></span>  
  
|<span data-ttu-id="c0fc5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c0fc5-111">Attribute</span></span>|<span data-ttu-id="c0fc5-112">描述</span><span class="sxs-lookup"><span data-stu-id="c0fc5-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="c0fc5-113">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="c0fc5-114">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="c0fc5-115">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0fc5-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c0fc5-116">Child Elements</span></span>  
 <span data-ttu-id="c0fc5-117">無。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0fc5-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c0fc5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c0fc5-119">項目</span><span class="sxs-lookup"><span data-stu-id="c0fc5-119">Element</span></span>|<span data-ttu-id="c0fc5-120">說明</span><span class="sxs-lookup"><span data-stu-id="c0fc5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0fc5-121">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="c0fc5-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="c0fc5-122">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="c0fc5-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0fc5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0fc5-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="c0fc5-124">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="c0fc5-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
