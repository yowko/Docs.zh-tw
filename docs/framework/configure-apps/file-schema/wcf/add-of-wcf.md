---
title: WCF 的 &lt;add&gt;
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: c57b1869536e68310bfbd0d574494094d2ab6388
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149484"
---
# <a name="ltaddgt-of-wcf"></a><span data-ttu-id="9a489-102">WCF 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="9a489-102">&lt;add&gt; of WCF</span></span>
<span data-ttu-id="9a489-103">設定追蹤參與者，這些參與者會接聽執行階段直接發出的追蹤記錄並處理記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="9a489-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="9a489-104">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="9a489-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="9a489-105">如需工作流程追蹤及追蹤參與者的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)並[追蹤參與者](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="9a489-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="9a489-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9a489-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9a489-107">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="9a489-107">\<tracking></span></span>  
<span data-ttu-id="9a489-108">\<參與者 ></span><span class="sxs-lookup"><span data-stu-id="9a489-108">\<participants></span></span>  
<span data-ttu-id="9a489-109">\<add></span><span class="sxs-lookup"><span data-stu-id="9a489-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a489-110">語法</span><span class="sxs-lookup"><span data-stu-id="9a489-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a489-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9a489-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9a489-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9a489-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a489-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9a489-113">Attributes</span></span>  
  
|<span data-ttu-id="9a489-114">元素</span><span class="sxs-lookup"><span data-stu-id="9a489-114">Element</span></span>|<span data-ttu-id="9a489-115">描述</span><span class="sxs-lookup"><span data-stu-id="9a489-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a489-116">name</span><span class="sxs-lookup"><span data-stu-id="9a489-116">name</span></span>|<span data-ttu-id="9a489-117">指定追蹤參與者名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9a489-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="9a489-118">profileName</span><span class="sxs-lookup"><span data-stu-id="9a489-118">profileName</span></span>|<span data-ttu-id="9a489-119">指定追蹤設定檔名稱的字串，該設定檔定義了追蹤參與者已訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="9a489-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="9a489-120">類型</span><span class="sxs-lookup"><span data-stu-id="9a489-120">type</span></span>|<span data-ttu-id="9a489-121">指定追蹤參與者型別的字串。</span><span class="sxs-lookup"><span data-stu-id="9a489-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a489-122">子元素</span><span class="sxs-lookup"><span data-stu-id="9a489-122">Child Elements</span></span>  
 <span data-ttu-id="9a489-123">無。</span><span class="sxs-lookup"><span data-stu-id="9a489-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a489-124">父項目</span><span class="sxs-lookup"><span data-stu-id="9a489-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9a489-125">項目</span><span class="sxs-lookup"><span data-stu-id="9a489-125">Element</span></span>|<span data-ttu-id="9a489-126">描述</span><span class="sxs-lookup"><span data-stu-id="9a489-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a489-127">\<參與者 ></span><span class="sxs-lookup"><span data-stu-id="9a489-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="9a489-128">追蹤參與者的清單。</span><span class="sxs-lookup"><span data-stu-id="9a489-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a489-129">備註</span><span class="sxs-lookup"><span data-stu-id="9a489-129">Remarks</span></span>  
 <span data-ttu-id="9a489-130">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="9a489-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="9a489-131">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="9a489-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="9a489-132">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="9a489-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="9a489-133">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="9a489-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="9a489-134">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="9a489-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="9a489-135">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="9a489-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="9a489-136">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="9a489-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="9a489-137">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="9a489-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a489-138">範例</span><span class="sxs-lookup"><span data-stu-id="9a489-138">Example</span></span>  
 <span data-ttu-id="9a489-139">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="9a489-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="9a489-140">ETW 追蹤參與者用來寫入追蹤記錄至 ETW 的提供者識別碼會定義於 `<diagnostics>` 區段。</span><span class="sxs-lookup"><span data-stu-id="9a489-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="9a489-141">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="9a489-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="9a489-142">這是由 `profileName` 項目的 `<add>` 屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="9a489-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="9a489-143">一旦這些定義完成，追蹤參與者就會加入至 `<etwTracking>` 服務行為。</span><span class="sxs-lookup"><span data-stu-id="9a489-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="9a489-144">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="9a489-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a489-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a489-145">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="9a489-146">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="9a489-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9a489-147">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="9a489-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
