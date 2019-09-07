---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: 368b37f3ff10b660260ddd5735c70b8d72063e11
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398704"
---
# <a name="participants"></a><span data-ttu-id="1fea0-101">\<participants></span><span class="sxs-lookup"><span data-stu-id="1fea0-101">\<participants></span></span>
<span data-ttu-id="1fea0-102">設定追蹤參與者的清單，這些參與者接聽執行階段直接發出的追蹤記錄並處理這些記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="1fea0-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="1fea0-103">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="1fea0-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="1fea0-104">如需工作流程追蹤和追蹤參與者的詳細資訊，請參閱[工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)追蹤[參與者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="1fea0-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="1fea0-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1fea0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1fea0-106">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="1fea0-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="1fea0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="1fea0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="1fea0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<參與者 >**</span><span class="sxs-lookup"><span data-stu-id="1fea0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fea0-109">語法</span><span class="sxs-lookup"><span data-stu-id="1fea0-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fea0-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1fea0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1fea0-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1fea0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fea0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1fea0-112">Attributes</span></span>  
 <span data-ttu-id="1fea0-113">無。</span><span class="sxs-lookup"><span data-stu-id="1fea0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1fea0-114">子元素</span><span class="sxs-lookup"><span data-stu-id="1fea0-114">Child Elements</span></span>  
  
|<span data-ttu-id="1fea0-115">項目</span><span class="sxs-lookup"><span data-stu-id="1fea0-115">Element</span></span>|<span data-ttu-id="1fea0-116">描述</span><span class="sxs-lookup"><span data-stu-id="1fea0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fea0-117">\<add></span><span class="sxs-lookup"><span data-stu-id="1fea0-117">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="1fea0-118">包含追蹤參與者的設定。</span><span class="sxs-lookup"><span data-stu-id="1fea0-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fea0-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1fea0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1fea0-120">項目</span><span class="sxs-lookup"><span data-stu-id="1fea0-120">Element</span></span>|<span data-ttu-id="1fea0-121">說明</span><span class="sxs-lookup"><span data-stu-id="1fea0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fea0-122">\<tracking></span><span class="sxs-lookup"><span data-stu-id="1fea0-122">\<tracking></span></span>](tracking.md)|<span data-ttu-id="1fea0-123">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="1fea0-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fea0-124">備註</span><span class="sxs-lookup"><span data-stu-id="1fea0-124">Remarks</span></span>  
 <span data-ttu-id="1fea0-125">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="1fea0-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="1fea0-126">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="1fea0-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="1fea0-127">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="1fea0-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="1fea0-128">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="1fea0-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="1fea0-129">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="1fea0-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1fea0-130">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="1fea0-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="1fea0-131">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="1fea0-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="1fea0-132">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="1fea0-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fea0-133">範例</span><span class="sxs-lookup"><span data-stu-id="1fea0-133">Example</span></span>  
 <span data-ttu-id="1fea0-134">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="1fea0-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="1fea0-135">ETW 追蹤參與者用來寫入追蹤記錄到 ETW 提供者識別碼會定義在 **\<診斷>** 一節。</span><span class="sxs-lookup"><span data-stu-id="1fea0-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="1fea0-136">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="1fea0-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="1fea0-137">這由定義 **profileName** 屬性 **\<新增>** 項目。</span><span class="sxs-lookup"><span data-stu-id="1fea0-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="1fea0-138">這些定義完成後，追蹤參與者就會新增至 **\<etwTracking >** 服務行為中。</span><span class="sxs-lookup"><span data-stu-id="1fea0-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="1fea0-139">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="1fea0-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1fea0-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fea0-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="1fea0-141">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="1fea0-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1fea0-142">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="1fea0-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
