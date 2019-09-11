---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855291"
---
# <a name="endtoendtracing"></a><span data-ttu-id="73a91-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="73a91-101">\<endToEndTracing></span></span>
<span data-ttu-id="73a91-102">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="73a91-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
<span data-ttu-id="73a91-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="73a91-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="73a91-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="73a91-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="73a91-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<診斷 >** ](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="73a91-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="73a91-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endToEndTracing >**</span><span class="sxs-lookup"><span data-stu-id="73a91-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a91-107">語法</span><span class="sxs-lookup"><span data-stu-id="73a91-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73a91-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73a91-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73a91-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73a91-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73a91-110">屬性</span><span class="sxs-lookup"><span data-stu-id="73a91-110">Attributes</span></span>  
  
|<span data-ttu-id="73a91-111">屬性</span><span class="sxs-lookup"><span data-stu-id="73a91-111">Attribute</span></span>|<span data-ttu-id="73a91-112">說明</span><span class="sxs-lookup"><span data-stu-id="73a91-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="73a91-113">布林值，指定是否啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="73a91-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="73a91-114">布林值，指定是否啟用訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="73a91-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="73a91-115">布林值，指定傳播屬性是否設為 true。</span><span class="sxs-lookup"><span data-stu-id="73a91-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73a91-116">子元素</span><span class="sxs-lookup"><span data-stu-id="73a91-116">Child Elements</span></span>  
 <span data-ttu-id="73a91-117">無。</span><span class="sxs-lookup"><span data-stu-id="73a91-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73a91-118">父項目</span><span class="sxs-lookup"><span data-stu-id="73a91-118">Parent Elements</span></span>  
  
|<span data-ttu-id="73a91-119">項目</span><span class="sxs-lookup"><span data-stu-id="73a91-119">Element</span></span>|<span data-ttu-id="73a91-120">描述</span><span class="sxs-lookup"><span data-stu-id="73a91-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73a91-121">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="73a91-121">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="73a91-122">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="73a91-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73a91-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73a91-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="73a91-124">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="73a91-124">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
