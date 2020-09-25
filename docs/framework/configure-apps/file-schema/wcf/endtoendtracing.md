---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b50c0c3db644787fe41ee58ced7eb640e7295f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190016"
---
# \<endToEndTracing>

<span data-ttu-id="4fe2d-101">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="4fe2d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fe2d-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe2d-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4fe2d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4fe2d-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe2d-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4fe2d-105">Attributes</span></span>  
  
|<span data-ttu-id="4fe2d-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4fe2d-106">Attribute</span></span>|<span data-ttu-id="4fe2d-107">描述</span><span class="sxs-lookup"><span data-stu-id="4fe2d-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="4fe2d-108">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="4fe2d-109">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="4fe2d-110">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe2d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4fe2d-111">Child Elements</span></span>  

 <span data-ttu-id="4fe2d-112">無。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe2d-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4fe2d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe2d-114">項目</span><span class="sxs-lookup"><span data-stu-id="4fe2d-114">Element</span></span>|<span data-ttu-id="4fe2d-115">描述</span><span class="sxs-lookup"><span data-stu-id="4fe2d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="4fe2d-116">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="4fe2d-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fe2d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe2d-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="4fe2d-118">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="4fe2d-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
