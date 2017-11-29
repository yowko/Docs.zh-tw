---
title: '&lt;etwTracking&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 583c5bcb1e864b79f80a9c3095ed8ce7b74a19eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="22f9a-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="22f9a-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="22f9a-103">可讓服務利用 ETW 追蹤使用的服務行為<xref:System.Activities.Tracking.EtwTrackingParticipant>。</span><span class="sxs-lookup"><span data-stu-id="22f9a-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="22f9a-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="22f9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="22f9a-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="22f9a-105">\<behaviors></span></span>  
<span data-ttu-id="22f9a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="22f9a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="22f9a-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="22f9a-107">\<behavior></span></span>  
<span data-ttu-id="22f9a-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="22f9a-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f9a-109">語法</span><span class="sxs-lookup"><span data-stu-id="22f9a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22f9a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22f9a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="22f9a-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="22f9a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22f9a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="22f9a-112">Attributes</span></span>  
  
|<span data-ttu-id="22f9a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="22f9a-113">Attribute</span></span>|<span data-ttu-id="22f9a-114">描述</span><span class="sxs-lookup"><span data-stu-id="22f9a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22f9a-115">profileName</span><span class="sxs-lookup"><span data-stu-id="22f9a-115">profileName</span></span>|<span data-ttu-id="22f9a-116">可指定與這個行為相關聯的追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="22f9a-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22f9a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="22f9a-117">Child Elements</span></span>  
 <span data-ttu-id="22f9a-118">無。</span><span class="sxs-lookup"><span data-stu-id="22f9a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22f9a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="22f9a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="22f9a-120">項目</span><span class="sxs-lookup"><span data-stu-id="22f9a-120">Element</span></span>|<span data-ttu-id="22f9a-121">說明</span><span class="sxs-lookup"><span data-stu-id="22f9a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f9a-122">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="22f9a-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="22f9a-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="22f9a-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f9a-124">備註</span><span class="sxs-lookup"><span data-stu-id="22f9a-124">Remarks</span></span>  
 <span data-ttu-id="22f9a-125">加入至服務的行為組態時，這個組態項目會在工作流程服務中，設定追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="22f9a-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="22f9a-126">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="22f9a-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="22f9a-127">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="22f9a-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f9a-128">範例</span><span class="sxs-lookup"><span data-stu-id="22f9a-128">Example</span></span>  
 <span data-ttu-id="22f9a-129">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="22f9a-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="22f9a-130">中所定義的 ETW 追蹤參與者用來寫入追蹤記錄至 ETW 的提供者 Id **\<診斷 >** > 一節。</span><span class="sxs-lookup"><span data-stu-id="22f9a-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="22f9a-131">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="22f9a-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="22f9a-132">這由定義**profileName**屬性**\<新增 >**項目。</span><span class="sxs-lookup"><span data-stu-id="22f9a-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="22f9a-133">這些定義之後，追蹤參與者會加入至 **\<etwTracking >**服務行為。</span><span class="sxs-lookup"><span data-stu-id="22f9a-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="22f9a-134">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="22f9a-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22f9a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22f9a-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="22f9a-136">工作流程追蹤及追蹤</span><span class="sxs-lookup"><span data-stu-id="22f9a-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="22f9a-137">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="22f9a-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
