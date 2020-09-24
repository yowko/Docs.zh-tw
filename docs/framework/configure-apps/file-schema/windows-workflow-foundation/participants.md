---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: 51c7824a4dcbd95eac098d25e9a971514e2a1e0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167037"
---
# \<participants>

<span data-ttu-id="62bf2-101">設定追蹤參與者的清單，這些參與者接聽執行階段直接發出的追蹤記錄並處理這些記錄，無論記錄的設定為何。</span><span class="sxs-lookup"><span data-stu-id="62bf2-101">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="62bf2-102">這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。</span><span class="sxs-lookup"><span data-stu-id="62bf2-102">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="62bf2-103">如需工作流程追蹤和追蹤參與者的詳細資訊，請參閱 [工作流程追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 追蹤和 [追蹤參與者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="62bf2-103">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="62bf2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="62bf2-104">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62bf2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62bf2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="62bf2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="62bf2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62bf2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="62bf2-107">Attributes</span></span>  

 <span data-ttu-id="62bf2-108">無。</span><span class="sxs-lookup"><span data-stu-id="62bf2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62bf2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="62bf2-109">Child Elements</span></span>  
  
|<span data-ttu-id="62bf2-110">項目</span><span class="sxs-lookup"><span data-stu-id="62bf2-110">Element</span></span>|<span data-ttu-id="62bf2-111">描述</span><span class="sxs-lookup"><span data-stu-id="62bf2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-participants.md)|<span data-ttu-id="62bf2-112">包含追蹤參與者的設定。</span><span class="sxs-lookup"><span data-stu-id="62bf2-112">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62bf2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="62bf2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="62bf2-114">項目</span><span class="sxs-lookup"><span data-stu-id="62bf2-114">Element</span></span>|<span data-ttu-id="62bf2-115">描述</span><span class="sxs-lookup"><span data-stu-id="62bf2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="62bf2-116">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="62bf2-116">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62bf2-117">備註</span><span class="sxs-lookup"><span data-stu-id="62bf2-117">Remarks</span></span>  

 <span data-ttu-id="62bf2-118">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="62bf2-118">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="62bf2-119">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="62bf2-119">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="62bf2-120">多個追蹤參與者可同時使用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="62bf2-120">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="62bf2-121">每個追蹤參與者都可以與不同的追蹤設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="62bf2-121">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="62bf2-122">此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="62bf2-122">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="62bf2-123">透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。</span><span class="sxs-lookup"><span data-stu-id="62bf2-123">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="62bf2-124">啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="62bf2-124">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="62bf2-125">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="62bf2-125">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62bf2-126">範例</span><span class="sxs-lookup"><span data-stu-id="62bf2-126">Example</span></span>  

 <span data-ttu-id="62bf2-127">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="62bf2-127">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="62bf2-128">ETW 追蹤參與者用來將追蹤記錄寫入至 ETW 的提供者識別碼，是在一節中定義的 **\<diagnostics>** 。</span><span class="sxs-lookup"><span data-stu-id="62bf2-128">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="62bf2-129">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="62bf2-129">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="62bf2-130">這是由元素的 **profileName** 屬性所定義 **\<add>** 。</span><span class="sxs-lookup"><span data-stu-id="62bf2-130">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="62bf2-131">一旦定義這些定義之後，追蹤參與者就會加入至 **\<etwTracking>** 服務行為。</span><span class="sxs-lookup"><span data-stu-id="62bf2-131">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="62bf2-132">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="62bf2-132">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62bf2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62bf2-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="62bf2-134">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="62bf2-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="62bf2-135">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="62bf2-135">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
