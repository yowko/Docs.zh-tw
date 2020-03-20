---
title: <add> 的 <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152355"
---
# <a name="add-of-participants"></a><span data-ttu-id="85f00-102">\<添加參與者>> \<</span><span class="sxs-lookup"><span data-stu-id="85f00-102">\<add> of \<participants></span></span>
<span data-ttu-id="85f00-103">設定追蹤參與者，這些參與者會接聽執行階段直接發出的追蹤記錄並處理記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="85f00-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="85f00-104">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="85f00-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="85f00-105">有關工作流跟蹤和追蹤參與者的詳細資訊，請參閱[工作流跟蹤和跟蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[參與者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="85f00-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="85f00-106">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85f00-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85f00-107">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="85f00-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="85f00-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="85f00-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="85f00-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<參與者>**](participants.md)</span><span class="sxs-lookup"><span data-stu-id="85f00-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="85f00-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="85f00-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f00-111">語法</span><span class="sxs-lookup"><span data-stu-id="85f00-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85f00-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85f00-112">Attributes and Elements</span></span>  
 <span data-ttu-id="85f00-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85f00-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85f00-114">屬性</span><span class="sxs-lookup"><span data-stu-id="85f00-114">Attributes</span></span>  
  
|<span data-ttu-id="85f00-115">元素</span><span class="sxs-lookup"><span data-stu-id="85f00-115">Element</span></span>|<span data-ttu-id="85f00-116">描述</span><span class="sxs-lookup"><span data-stu-id="85f00-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85f00-117">NAME</span><span class="sxs-lookup"><span data-stu-id="85f00-117">name</span></span>|<span data-ttu-id="85f00-118">指定追蹤參與者名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="85f00-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="85f00-119">profileName</span><span class="sxs-lookup"><span data-stu-id="85f00-119">profileName</span></span>|<span data-ttu-id="85f00-120">指定追蹤設定檔名稱的字串，該設定檔定義了追蹤參與者已訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="85f00-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="85f00-121">type</span><span class="sxs-lookup"><span data-stu-id="85f00-121">type</span></span>|<span data-ttu-id="85f00-122">指定追蹤參與者型別的字串。</span><span class="sxs-lookup"><span data-stu-id="85f00-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85f00-123">子元素</span><span class="sxs-lookup"><span data-stu-id="85f00-123">Child Elements</span></span>  
 <span data-ttu-id="85f00-124">無。</span><span class="sxs-lookup"><span data-stu-id="85f00-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85f00-125">父項目</span><span class="sxs-lookup"><span data-stu-id="85f00-125">Parent Elements</span></span>  
  
|<span data-ttu-id="85f00-126">元素</span><span class="sxs-lookup"><span data-stu-id="85f00-126">Element</span></span>|<span data-ttu-id="85f00-127">描述</span><span class="sxs-lookup"><span data-stu-id="85f00-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85f00-128">\<參與者></span><span class="sxs-lookup"><span data-stu-id="85f00-128">\<participants></span></span>](participants.md)|<span data-ttu-id="85f00-129">追蹤參與者的清單。</span><span class="sxs-lookup"><span data-stu-id="85f00-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85f00-130">備註</span><span class="sxs-lookup"><span data-stu-id="85f00-130">Remarks</span></span>  
 <span data-ttu-id="85f00-131">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="85f00-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="85f00-132">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="85f00-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="85f00-133">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="85f00-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="85f00-134">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="85f00-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="85f00-135">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="85f00-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="85f00-136">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="85f00-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="85f00-137">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="85f00-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="85f00-138">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="85f00-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85f00-139">範例</span><span class="sxs-lookup"><span data-stu-id="85f00-139">Example</span></span>  
 <span data-ttu-id="85f00-140">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="85f00-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="85f00-141">ETW 追蹤參與者用於將追蹤記錄寫入 ETW 的提供程式 ID 在**\<診斷>** 部分中定義。</span><span class="sxs-lookup"><span data-stu-id="85f00-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="85f00-142">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="85f00-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="85f00-143">這由**\<添加>** 元素的**設定檔名稱**屬性定義。</span><span class="sxs-lookup"><span data-stu-id="85f00-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="85f00-144">定義這些後，追蹤參與者將添加到**\<etw 跟蹤>** 服務行為。</span><span class="sxs-lookup"><span data-stu-id="85f00-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="85f00-145">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="85f00-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85f00-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85f00-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="85f00-147">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="85f00-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="85f00-148">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="85f00-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
