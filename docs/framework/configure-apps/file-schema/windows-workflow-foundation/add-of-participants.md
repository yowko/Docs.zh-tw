---
title: <add> 的 <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 479430abd06561cc294b3da3d0922b737364b50f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398922"
---
# <a name="add-of-participants"></a><span data-ttu-id="98374-102">\<新增參與者的\<> ></span><span class="sxs-lookup"><span data-stu-id="98374-102">\<add> of \<participants></span></span>
<span data-ttu-id="98374-103">設定追蹤參與者，這些參與者會接聽執行階段直接發出的追蹤記錄並處理記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="98374-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="98374-104">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="98374-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="98374-105">如需工作流程追蹤和追蹤參與者的詳細資訊，請參閱[工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)追蹤[參與者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="98374-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="98374-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="98374-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="98374-107">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="98374-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="98374-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="98374-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="98374-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<參與者 >** ](participants.md)</span><span class="sxs-lookup"><span data-stu-id="98374-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="98374-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="98374-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98374-111">語法</span><span class="sxs-lookup"><span data-stu-id="98374-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98374-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="98374-112">Attributes and Elements</span></span>  
 <span data-ttu-id="98374-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="98374-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98374-114">屬性</span><span class="sxs-lookup"><span data-stu-id="98374-114">Attributes</span></span>  
  
|<span data-ttu-id="98374-115">項目</span><span class="sxs-lookup"><span data-stu-id="98374-115">Element</span></span>|<span data-ttu-id="98374-116">說明</span><span class="sxs-lookup"><span data-stu-id="98374-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98374-117">NAME</span><span class="sxs-lookup"><span data-stu-id="98374-117">name</span></span>|<span data-ttu-id="98374-118">指定追蹤參與者名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="98374-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="98374-119">profileName</span><span class="sxs-lookup"><span data-stu-id="98374-119">profileName</span></span>|<span data-ttu-id="98374-120">指定追蹤設定檔名稱的字串，該設定檔定義了追蹤參與者已訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98374-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="98374-121">型別</span><span class="sxs-lookup"><span data-stu-id="98374-121">type</span></span>|<span data-ttu-id="98374-122">指定追蹤參與者型別的字串。</span><span class="sxs-lookup"><span data-stu-id="98374-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98374-123">子元素</span><span class="sxs-lookup"><span data-stu-id="98374-123">Child Elements</span></span>  
 <span data-ttu-id="98374-124">無。</span><span class="sxs-lookup"><span data-stu-id="98374-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98374-125">父項目</span><span class="sxs-lookup"><span data-stu-id="98374-125">Parent Elements</span></span>  
  
|<span data-ttu-id="98374-126">項目</span><span class="sxs-lookup"><span data-stu-id="98374-126">Element</span></span>|<span data-ttu-id="98374-127">說明</span><span class="sxs-lookup"><span data-stu-id="98374-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98374-128">\<participants></span><span class="sxs-lookup"><span data-stu-id="98374-128">\<participants></span></span>](participants.md)|<span data-ttu-id="98374-129">追蹤參與者的清單。</span><span class="sxs-lookup"><span data-stu-id="98374-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98374-130">備註</span><span class="sxs-lookup"><span data-stu-id="98374-130">Remarks</span></span>  
 <span data-ttu-id="98374-131">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="98374-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="98374-132">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="98374-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="98374-133">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="98374-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="98374-134">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="98374-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="98374-135">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="98374-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="98374-136">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="98374-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="98374-137">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98374-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="98374-138">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="98374-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98374-139">範例</span><span class="sxs-lookup"><span data-stu-id="98374-139">Example</span></span>  
 <span data-ttu-id="98374-140">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="98374-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="98374-141">ETW 追蹤參與者用來寫入追蹤記錄到 ETW 提供者識別碼會定義在 **\<診斷>** 一節。</span><span class="sxs-lookup"><span data-stu-id="98374-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="98374-142">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98374-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="98374-143">這由定義 **profileName** 屬性 **\<新增>** 項目。</span><span class="sxs-lookup"><span data-stu-id="98374-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="98374-144">這些定義完成後，追蹤參與者就會新增至 **\<etwTracking >** 服務行為中。</span><span class="sxs-lookup"><span data-stu-id="98374-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="98374-145">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98374-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98374-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98374-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="98374-147">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="98374-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="98374-148">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="98374-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
