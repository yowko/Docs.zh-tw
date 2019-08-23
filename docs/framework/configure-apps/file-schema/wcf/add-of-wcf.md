---
title: <add>WCF 的
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: fa94f15a296aa03640bf0a262eb45ea1664944cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926612"
---
# <a name="add-of-wcf"></a><span data-ttu-id="d3dd5-102">\<新增 WCF 的 ></span><span class="sxs-lookup"><span data-stu-id="d3dd5-102">\<add> of WCF</span></span>
<span data-ttu-id="d3dd5-103">設定追蹤參與者，這些參與者會接聽執行階段直接發出的追蹤記錄並處理記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="d3dd5-104">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="d3dd5-105">如需工作流程追蹤和追蹤參與者的詳細資訊, 請參閱[工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)追蹤[參與者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="d3dd5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d3dd5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d3dd5-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d3dd5-107">\<tracking></span></span>  
<span data-ttu-id="d3dd5-108">\<participants></span><span class="sxs-lookup"><span data-stu-id="d3dd5-108">\<participants></span></span>  
<span data-ttu-id="d3dd5-109">\<add></span><span class="sxs-lookup"><span data-stu-id="d3dd5-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3dd5-110">語法</span><span class="sxs-lookup"><span data-stu-id="d3dd5-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3dd5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3dd5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d3dd5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3dd5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d3dd5-113">Attributes</span></span>  
  
|<span data-ttu-id="d3dd5-114">項目</span><span class="sxs-lookup"><span data-stu-id="d3dd5-114">Element</span></span>|<span data-ttu-id="d3dd5-115">描述</span><span class="sxs-lookup"><span data-stu-id="d3dd5-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3dd5-116">NAME</span><span class="sxs-lookup"><span data-stu-id="d3dd5-116">name</span></span>|<span data-ttu-id="d3dd5-117">指定追蹤參與者名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="d3dd5-118">profileName</span><span class="sxs-lookup"><span data-stu-id="d3dd5-118">profileName</span></span>|<span data-ttu-id="d3dd5-119">指定追蹤設定檔名稱的字串，該設定檔定義了追蹤參與者已訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="d3dd5-120">型別</span><span class="sxs-lookup"><span data-stu-id="d3dd5-120">type</span></span>|<span data-ttu-id="d3dd5-121">指定追蹤參與者型別的字串。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3dd5-122">子元素</span><span class="sxs-lookup"><span data-stu-id="d3dd5-122">Child Elements</span></span>  
 <span data-ttu-id="d3dd5-123">無。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3dd5-124">父項目</span><span class="sxs-lookup"><span data-stu-id="d3dd5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d3dd5-125">項目</span><span class="sxs-lookup"><span data-stu-id="d3dd5-125">Element</span></span>|<span data-ttu-id="d3dd5-126">說明</span><span class="sxs-lookup"><span data-stu-id="d3dd5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3dd5-127">\<participants></span><span class="sxs-lookup"><span data-stu-id="d3dd5-127">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="d3dd5-128">追蹤參與者的清單。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3dd5-129">備註</span><span class="sxs-lookup"><span data-stu-id="d3dd5-129">Remarks</span></span>  
 <span data-ttu-id="d3dd5-130">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="d3dd5-131">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="d3dd5-132">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="d3dd5-133">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="d3dd5-134">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="d3dd5-135">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="d3dd5-136">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="d3dd5-137">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3dd5-138">範例</span><span class="sxs-lookup"><span data-stu-id="d3dd5-138">Example</span></span>  
 <span data-ttu-id="d3dd5-139">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="d3dd5-140">ETW 追蹤參與者用來寫入追蹤記錄至 ETW 的提供者識別碼會定義於 `<diagnostics>` 區段。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="d3dd5-141">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="d3dd5-142">這是由 `profileName` 項目的 `<add>` 屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="d3dd5-143">一旦這些定義完成，追蹤參與者就會加入至 `<etwTracking>` 服務行為。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="d3dd5-144">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="d3dd5-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="d3dd5-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3dd5-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="d3dd5-146">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="d3dd5-146">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d3dd5-147">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="d3dd5-147">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
