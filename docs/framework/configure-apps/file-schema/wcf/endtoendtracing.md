---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855291"
---
# \<endToEndTracing>
<span data-ttu-id="e4c92-101">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4c92-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="e4c92-102">語法</span><span class="sxs-lookup"><span data-stu-id="e4c92-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4c92-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4c92-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e4c92-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4c92-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4c92-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e4c92-105">Attributes</span></span>  
  
|<span data-ttu-id="e4c92-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e4c92-106">Attribute</span></span>|<span data-ttu-id="e4c92-107">描述</span><span class="sxs-lookup"><span data-stu-id="e4c92-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="e4c92-108">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4c92-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="e4c92-109">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="e4c92-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="e4c92-110">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="e4c92-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4c92-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e4c92-111">Child Elements</span></span>  
 <span data-ttu-id="e4c92-112">無。</span><span class="sxs-lookup"><span data-stu-id="e4c92-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4c92-113">父項目</span><span class="sxs-lookup"><span data-stu-id="e4c92-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e4c92-114">元素</span><span class="sxs-lookup"><span data-stu-id="e4c92-114">Element</span></span>|<span data-ttu-id="e4c92-115">描述</span><span class="sxs-lookup"><span data-stu-id="e4c92-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="e4c92-116">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="e4c92-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4c92-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4c92-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="e4c92-118">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="e4c92-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
