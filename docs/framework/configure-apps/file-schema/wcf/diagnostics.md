---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 775ec3a4d3dd8709c61fb46155b5085a3343d218
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192265"
---
# \<diagnostics>

<span data-ttu-id="b5811-101">`diagnostics` 項目會定義可由系統管理員用於執行階段檢查和控制的設定。</span><span class="sxs-lookup"><span data-stu-id="b5811-101">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="b5811-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5811-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5811-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b5811-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b5811-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b5811-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5811-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b5811-105">Attributes</span></span>  
  
|<span data-ttu-id="b5811-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b5811-106">Attribute</span></span>|<span data-ttu-id="b5811-107">描述</span><span class="sxs-lookup"><span data-stu-id="b5811-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5811-108">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="b5811-108">etwProviderId</span></span>|<span data-ttu-id="b5811-109">字串，這個字串會指定 Event-Tracing 提供者的識別項，此識別項會將事件寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b5811-109">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="b5811-110">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="b5811-110">performanceCounters</span></span>|<span data-ttu-id="b5811-111">指定是否啟用組件的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b5811-111">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="b5811-112">有效值為</span><span class="sxs-lookup"><span data-stu-id="b5811-112">Valid values are</span></span><br /><br /> <span data-ttu-id="b5811-113">-Off：效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="b5811-113">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="b5811-114">-ServiceOnly：只啟用與此服務相關的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b5811-114">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="b5811-115">-All：可在執行時間查看效能計數器。</span><span class="sxs-lookup"><span data-stu-id="b5811-115">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="b5811-116">-Default： _WCF_Admin 建立單一效能計數器實例。</span><span class="sxs-lookup"><span data-stu-id="b5811-116">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="b5811-117">這個執行個體用於啟用基礎結構所使用之 SQM 資料的集合。</span><span class="sxs-lookup"><span data-stu-id="b5811-117">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="b5811-118">這個執行個體所有的計數器值都未更新，因此將維持在零。</span><span class="sxs-lookup"><span data-stu-id="b5811-118">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="b5811-119">如果沒有 WCF 的組態，則這是預設值。</span><span class="sxs-lookup"><span data-stu-id="b5811-119">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="b5811-120">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="b5811-120">wmiProviderEnabled</span></span>|<span data-ttu-id="b5811-121">布林值，指定是否為組件啟用 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="b5811-121">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="b5811-122">使用者需要 WMI 提供者來取得 Windows Communication Foundation (WCF) 的檢查和控制功能的執行階段存取權。</span><span class="sxs-lookup"><span data-stu-id="b5811-122">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b5811-123">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b5811-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5811-124">子元素</span><span class="sxs-lookup"><span data-stu-id="b5811-124">Child Elements</span></span>  
  
|<span data-ttu-id="b5811-125">項目</span><span class="sxs-lookup"><span data-stu-id="b5811-125">Element</span></span>|<span data-ttu-id="b5811-126">描述</span><span class="sxs-lookup"><span data-stu-id="b5811-126">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="b5811-127">組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。</span><span class="sxs-lookup"><span data-stu-id="b5811-127">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="b5811-128">描述 WCF 訊息記錄的設定。</span><span class="sxs-lookup"><span data-stu-id="b5811-128">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5811-129">父項目</span><span class="sxs-lookup"><span data-stu-id="b5811-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b5811-130">項目</span><span class="sxs-lookup"><span data-stu-id="b5811-130">Element</span></span>|<span data-ttu-id="b5811-131">描述</span><span class="sxs-lookup"><span data-stu-id="b5811-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5811-132">serviceModel</span><span class="sxs-lookup"><span data-stu-id="b5811-132">serviceModel</span></span>|<span data-ttu-id="b5811-133">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="b5811-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5811-134">備註</span><span class="sxs-lookup"><span data-stu-id="b5811-134">Remarks</span></span>  

 <span data-ttu-id="b5811-135">`diagnostics` 區段會定義位於組件中所有服務的診斷設定。</span><span class="sxs-lookup"><span data-stu-id="b5811-135">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="b5811-136">無法在服務等級上定義個別的診斷設定，除非組件中只有一個服務。</span><span class="sxs-lookup"><span data-stu-id="b5811-136">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="b5811-137">根據區段的需求設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b5811-137">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5811-138">範例</span><span class="sxs-lookup"><span data-stu-id="b5811-138">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5811-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5811-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
