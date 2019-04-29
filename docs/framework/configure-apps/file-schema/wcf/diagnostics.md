---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 3fc7828d399555f7c459f6dd067ce9a24b8998b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704049"
---
# <a name="diagnostics"></a><span data-ttu-id="5ad48-101">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="5ad48-101">\<diagnostics></span></span>
<span data-ttu-id="5ad48-102">`diagnostics` 項目會定義可由系統管理員用於執行階段檢查和控制的設定。</span><span class="sxs-lookup"><span data-stu-id="5ad48-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="5ad48-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ad48-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ad48-104">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="5ad48-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ad48-105">語法</span><span class="sxs-lookup"><span data-stu-id="5ad48-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ad48-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5ad48-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5ad48-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5ad48-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ad48-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5ad48-108">Attributes</span></span>  
  
|<span data-ttu-id="5ad48-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5ad48-109">Attribute</span></span>|<span data-ttu-id="5ad48-110">描述</span><span class="sxs-lookup"><span data-stu-id="5ad48-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ad48-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="5ad48-111">etwProviderId</span></span>|<span data-ttu-id="5ad48-112">字串，這個字串會指定 Event-Tracing 提供者的識別項，此識別項會將事件寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="5ad48-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="5ad48-113">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="5ad48-113">performanceCounters</span></span>|<span data-ttu-id="5ad48-114">指定是否啟用組件的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5ad48-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="5ad48-115">有效值為</span><span class="sxs-lookup"><span data-stu-id="5ad48-115">Valid values are</span></span><br /><br /> <span data-ttu-id="5ad48-116">關閉：停用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5ad48-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="5ad48-117">-ServiceOnly:僅啟用與這個服務相關的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5ad48-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="5ad48-118">-所有：可在執行階段檢視效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5ad48-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="5ad48-119">-預設值：已建立單一效能計數器執行個體 _WCF_Admin。</span><span class="sxs-lookup"><span data-stu-id="5ad48-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="5ad48-120">這個執行個體用於啟用基礎結構所使用之 SQM 資料的集合。</span><span class="sxs-lookup"><span data-stu-id="5ad48-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="5ad48-121">這個執行個體所有的計數器值都未更新，因此將維持在零。</span><span class="sxs-lookup"><span data-stu-id="5ad48-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="5ad48-122">如果沒有 WCF 的組態，則這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5ad48-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="5ad48-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="5ad48-123">wmiProviderEnabled</span></span>|<span data-ttu-id="5ad48-124">布林值，指定是否為組件啟用 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="5ad48-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="5ad48-125">使用者需要 WMI 提供者來取得 Windows Communication Foundation (WCF) 的檢查和控制功能的執行階段存取權。</span><span class="sxs-lookup"><span data-stu-id="5ad48-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="5ad48-126">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5ad48-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ad48-127">子元素</span><span class="sxs-lookup"><span data-stu-id="5ad48-127">Child Elements</span></span>  
  
|<span data-ttu-id="5ad48-128">項目</span><span class="sxs-lookup"><span data-stu-id="5ad48-128">Element</span></span>|<span data-ttu-id="5ad48-129">描述</span><span class="sxs-lookup"><span data-stu-id="5ad48-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ad48-130">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="5ad48-130">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="5ad48-131">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="5ad48-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="5ad48-132">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="5ad48-132">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="5ad48-133">描述 WCF 訊息記錄的設定。</span><span class="sxs-lookup"><span data-stu-id="5ad48-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ad48-134">父項目</span><span class="sxs-lookup"><span data-stu-id="5ad48-134">Parent Elements</span></span>  
  
|<span data-ttu-id="5ad48-135">項目</span><span class="sxs-lookup"><span data-stu-id="5ad48-135">Element</span></span>|<span data-ttu-id="5ad48-136">描述</span><span class="sxs-lookup"><span data-stu-id="5ad48-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ad48-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="5ad48-137">serviceModel</span></span>|<span data-ttu-id="5ad48-138">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="5ad48-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ad48-139">備註</span><span class="sxs-lookup"><span data-stu-id="5ad48-139">Remarks</span></span>  
 <span data-ttu-id="5ad48-140">`diagnostics` 區段會定義位於組件中所有服務的診斷設定。</span><span class="sxs-lookup"><span data-stu-id="5ad48-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="5ad48-141">無法在服務等級上定義個別的診斷設定，除非組件中只有一個服務。</span><span class="sxs-lookup"><span data-stu-id="5ad48-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="5ad48-142">根據區段的需求設定屬性。</span><span class="sxs-lookup"><span data-stu-id="5ad48-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ad48-143">範例</span><span class="sxs-lookup"><span data-stu-id="5ad48-143">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a><span data-ttu-id="5ad48-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ad48-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
