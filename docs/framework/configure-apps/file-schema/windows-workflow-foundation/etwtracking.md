---
title: '&lt;etwTracking&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: f9d1acd5dafb9df181b036db9d3ad783ca618874
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684318"
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="f57e9-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="f57e9-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="f57e9-103">這個服務行為可讓服務能夠利用 ETW 追蹤使用<xref:System.Activities.Tracking.EtwTrackingParticipant>。</span><span class="sxs-lookup"><span data-stu-id="f57e9-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="f57e9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f57e9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f57e9-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f57e9-105">\<behaviors></span></span>  
<span data-ttu-id="f57e9-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f57e9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f57e9-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f57e9-107">\<behavior></span></span>  
<span data-ttu-id="f57e9-108">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="f57e9-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57e9-109">語法</span><span class="sxs-lookup"><span data-stu-id="f57e9-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f57e9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f57e9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f57e9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f57e9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f57e9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f57e9-112">Attributes</span></span>  
  
|<span data-ttu-id="f57e9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f57e9-113">Attribute</span></span>|<span data-ttu-id="f57e9-114">描述</span><span class="sxs-lookup"><span data-stu-id="f57e9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f57e9-115">profileName</span><span class="sxs-lookup"><span data-stu-id="f57e9-115">profileName</span></span>|<span data-ttu-id="f57e9-116">可指定與這個行為相關聯的追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="f57e9-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f57e9-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f57e9-117">Child Elements</span></span>  
 <span data-ttu-id="f57e9-118">無。</span><span class="sxs-lookup"><span data-stu-id="f57e9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f57e9-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f57e9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f57e9-120">項目</span><span class="sxs-lookup"><span data-stu-id="f57e9-120">Element</span></span>|<span data-ttu-id="f57e9-121">描述</span><span class="sxs-lookup"><span data-stu-id="f57e9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f57e9-122">\<行為 > 的\<v ></span><span class="sxs-lookup"><span data-stu-id="f57e9-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f57e9-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="f57e9-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f57e9-124">備註</span><span class="sxs-lookup"><span data-stu-id="f57e9-124">Remarks</span></span>  
 <span data-ttu-id="f57e9-125">加入至服務的行為組態時，這個組態項目會在工作流程服務中，設定追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="f57e9-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="f57e9-126">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="f57e9-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="f57e9-127">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="f57e9-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f57e9-128">範例</span><span class="sxs-lookup"><span data-stu-id="f57e9-128">Example</span></span>  
 <span data-ttu-id="f57e9-129">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="f57e9-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="f57e9-130">ETW 追蹤參與者用來寫入追蹤記錄到 ETW 提供者識別碼會定義在**\<診斷 >** 一節。</span><span class="sxs-lookup"><span data-stu-id="f57e9-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="f57e9-131">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="f57e9-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="f57e9-132">這由定義**profileName**屬性**\<新增 >** 項目。</span><span class="sxs-lookup"><span data-stu-id="f57e9-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="f57e9-133">一旦這些定義加入追蹤參與者 **\<etwTracking >** 服務行為。</span><span class="sxs-lookup"><span data-stu-id="f57e9-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="f57e9-134">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="f57e9-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f57e9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f57e9-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="f57e9-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="f57e9-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f57e9-137">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="f57e9-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
