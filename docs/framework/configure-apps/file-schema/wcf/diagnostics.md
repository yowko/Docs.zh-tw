---
title: '&lt;diagnostics&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: de11145620e8fdf96785908df85ab5ecdfd2e25e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524584"
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="b8e5d-102">&lt;diagnostics&gt;</span><span class="sxs-lookup"><span data-stu-id="b8e5d-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="b8e5d-103">`diagnostics` 項目會定義可由系統管理員用於執行階段檢查和控制的設定。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="b8e5d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8e5d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8e5d-105">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="b8e5d-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e5d-106">語法</span><span class="sxs-lookup"><span data-stu-id="b8e5d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8e5d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8e5d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8e5d-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8e5d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e5d-109">Attributes</span></span>  
  
|<span data-ttu-id="b8e5d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e5d-110">Attribute</span></span>|<span data-ttu-id="b8e5d-111">描述</span><span class="sxs-lookup"><span data-stu-id="b8e5d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8e5d-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="b8e5d-112">etwProviderId</span></span>|<span data-ttu-id="b8e5d-113">字串，這個字串會指定 Event-Tracing 提供者的識別項，此識別項會將事件寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="b8e5d-114">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="b8e5d-114">performanceCounters</span></span>|<span data-ttu-id="b8e5d-115">指定是否啟用組件的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="b8e5d-116">有效值為</span><span class="sxs-lookup"><span data-stu-id="b8e5d-116">Valid values are</span></span><br /><br /> <span data-ttu-id="b8e5d-117">關閉：停用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="b8e5d-118">-ServiceOnly:僅啟用與這個服務相關的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="b8e5d-119">-所有：可在執行階段檢視效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="b8e5d-120">-預設值：已建立單一效能計數器執行個體 _WCF_Admin。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="b8e5d-121">這個執行個體用於啟用基礎結構所使用之 SQM 資料的集合。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="b8e5d-122">這個執行個體所有的計數器值都未更新，因此將維持在零。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="b8e5d-123">如果沒有 WCF 的組態，則這是預設值。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="b8e5d-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="b8e5d-124">wmiProviderEnabled</span></span>|<span data-ttu-id="b8e5d-125">布林值，指定是否為組件啟用 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="b8e5d-126">使用者需要 WMI 提供者來取得 Windows Communication Foundation (WCF) 的檢查和控制功能的執行階段存取權。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b8e5d-127">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8e5d-128">子元素</span><span class="sxs-lookup"><span data-stu-id="b8e5d-128">Child Elements</span></span>  
  
|<span data-ttu-id="b8e5d-129">項目</span><span class="sxs-lookup"><span data-stu-id="b8e5d-129">Element</span></span>|<span data-ttu-id="b8e5d-130">描述</span><span class="sxs-lookup"><span data-stu-id="b8e5d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e5d-131">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="b8e5d-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="b8e5d-132">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="b8e5d-133">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="b8e5d-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="b8e5d-134">描述 WCF 訊息記錄的設定。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8e5d-135">父項目</span><span class="sxs-lookup"><span data-stu-id="b8e5d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b8e5d-136">項目</span><span class="sxs-lookup"><span data-stu-id="b8e5d-136">Element</span></span>|<span data-ttu-id="b8e5d-137">描述</span><span class="sxs-lookup"><span data-stu-id="b8e5d-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8e5d-138">serviceModel</span><span class="sxs-lookup"><span data-stu-id="b8e5d-138">serviceModel</span></span>|<span data-ttu-id="b8e5d-139">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e5d-140">備註</span><span class="sxs-lookup"><span data-stu-id="b8e5d-140">Remarks</span></span>  
 <span data-ttu-id="b8e5d-141">`diagnostics` 區段會定義位於組件中所有服務的診斷設定。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="b8e5d-142">無法在服務等級上定義個別的診斷設定，除非組件中只有一個服務。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="b8e5d-143">根據區段的需求設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b8e5d-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e5d-144">範例</span><span class="sxs-lookup"><span data-stu-id="b8e5d-144">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8e5d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e5d-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
