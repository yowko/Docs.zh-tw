---
title: <participants> WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 4ee70d3a9b5d75adc639f1e3922cfde6737e9e01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170151"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="ad5de-102">\<participants> WCF</span><span class="sxs-lookup"><span data-stu-id="ad5de-102">\<participants> of WCF</span></span>

<span data-ttu-id="ad5de-103">設定追蹤參與者的清單，這些參與者接聽執行階段直接發出的追蹤記錄並處理這些記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="ad5de-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="ad5de-104">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="ad5de-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="ad5de-105">如需工作流程追蹤和追蹤參與者的詳細資訊，請參閱 [工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 追蹤和 [追蹤參與者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="ad5de-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="ad5de-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad5de-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad5de-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad5de-107">Attributes and Elements</span></span>  

 <span data-ttu-id="ad5de-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad5de-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad5de-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ad5de-109">Attributes</span></span>  

 <span data-ttu-id="ad5de-110">無。</span><span class="sxs-lookup"><span data-stu-id="ad5de-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad5de-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ad5de-111">Child Elements</span></span>  
  
|<span data-ttu-id="ad5de-112">項目</span><span class="sxs-lookup"><span data-stu-id="ad5de-112">Element</span></span>|<span data-ttu-id="ad5de-113">描述</span><span class="sxs-lookup"><span data-stu-id="ad5de-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="ad5de-114">包含追蹤參與者的設定。</span><span class="sxs-lookup"><span data-stu-id="ad5de-114">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad5de-115">父項目</span><span class="sxs-lookup"><span data-stu-id="ad5de-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ad5de-116">項目</span><span class="sxs-lookup"><span data-stu-id="ad5de-116">Element</span></span>|<span data-ttu-id="ad5de-117">描述</span><span class="sxs-lookup"><span data-stu-id="ad5de-117">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="ad5de-118">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="ad5de-118">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad5de-119">備註</span><span class="sxs-lookup"><span data-stu-id="ad5de-119">Remarks</span></span>  

 <span data-ttu-id="ad5de-120">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="ad5de-120">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="ad5de-121">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="ad5de-121">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="ad5de-122">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="ad5de-122">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="ad5de-123">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="ad5de-123">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="ad5de-124">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="ad5de-124">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ad5de-125">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="ad5de-125">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="ad5de-126">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ad5de-126">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="ad5de-127">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="ad5de-127">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad5de-128">範例</span><span class="sxs-lookup"><span data-stu-id="ad5de-128">Example</span></span>  

 <span data-ttu-id="ad5de-129">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="ad5de-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="ad5de-130">ETW 追蹤參與者用來寫入追蹤記錄至 ETW 的提供者識別碼會定義於 `<diagnostics>` 區段。</span><span class="sxs-lookup"><span data-stu-id="ad5de-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="ad5de-131">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ad5de-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="ad5de-132">這是由 `profileName` 項目的 `<add>` 屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="ad5de-132">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="ad5de-133">一旦這些定義完成，追蹤參與者就會加入至 `<etwTracking>` 服務行為。</span><span class="sxs-lookup"><span data-stu-id="ad5de-133">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="ad5de-134">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ad5de-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad5de-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad5de-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="ad5de-136">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="ad5de-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ad5de-137">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="ad5de-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
