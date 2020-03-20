---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152167"
---
# <a name="etwtracking"></a><span data-ttu-id="b0ba1-101">\<etw 跟蹤></span><span class="sxs-lookup"><span data-stu-id="b0ba1-101">\<etwTracking></span></span>
<span data-ttu-id="b0ba1-102">服務行為，可讓服務透過使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 來利用 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="b0ba1-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0ba1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b0ba1-104">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b0ba1-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b0ba1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b0ba1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b0ba1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b0ba1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b0ba1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b0ba1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b0ba1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etw 跟蹤>**</span><span class="sxs-lookup"><span data-stu-id="b0ba1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ba1-109">語法</span><span class="sxs-lookup"><span data-stu-id="b0ba1-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0ba1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b0ba1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b0ba1-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0ba1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b0ba1-112">Attributes</span></span>  
  
|<span data-ttu-id="b0ba1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b0ba1-113">Attribute</span></span>|<span data-ttu-id="b0ba1-114">描述</span><span class="sxs-lookup"><span data-stu-id="b0ba1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0ba1-115">profileName</span><span class="sxs-lookup"><span data-stu-id="b0ba1-115">profileName</span></span>|<span data-ttu-id="b0ba1-116">可指定與這個行為相關聯的追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0ba1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="b0ba1-117">Child Elements</span></span>  
 <span data-ttu-id="b0ba1-118">無。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0ba1-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b0ba1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b0ba1-120">元素</span><span class="sxs-lookup"><span data-stu-id="b0ba1-120">Element</span></span>|<span data-ttu-id="b0ba1-121">描述</span><span class="sxs-lookup"><span data-stu-id="b0ba1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0ba1-122">\<服務行為行為\<>></span><span class="sxs-lookup"><span data-stu-id="b0ba1-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b0ba1-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0ba1-124">備註</span><span class="sxs-lookup"><span data-stu-id="b0ba1-124">Remarks</span></span>  
 <span data-ttu-id="b0ba1-125">加入至服務的行為組態時，這個組態項目會在工作流程服務中，設定追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="b0ba1-126">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="b0ba1-127">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0ba1-128">範例</span><span class="sxs-lookup"><span data-stu-id="b0ba1-128">Example</span></span>  
 <span data-ttu-id="b0ba1-129">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="b0ba1-130">ETW 追蹤參與者用於將追蹤記錄寫入 ETW 的提供程式 ID 在**\<診斷>** 部分中定義。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="b0ba1-131">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="b0ba1-132">這由**\<添加>** 元素的**設定檔名稱**屬性定義。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="b0ba1-133">定義這些後，追蹤參與者將添加到**\<etw 跟蹤>** 服務行為。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="b0ba1-134">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="b0ba1-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0ba1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0ba1-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="b0ba1-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="b0ba1-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b0ba1-137">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="b0ba1-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
