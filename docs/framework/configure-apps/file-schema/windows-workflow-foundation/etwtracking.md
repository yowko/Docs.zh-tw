---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: e1048cf3a9f56e4177f3ffe2dcd561a1babadacd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198765"
---
# \<etwTracking>

<span data-ttu-id="1e1df-101">服務行為，可讓服務透過使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 來利用 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e1df-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="1e1df-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="1e1df-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e1df-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e1df-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1e1df-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1e1df-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e1df-105">屬性</span><span class="sxs-lookup"><span data-stu-id="1e1df-105">Attributes</span></span>  
  
|<span data-ttu-id="1e1df-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1e1df-106">Attribute</span></span>|<span data-ttu-id="1e1df-107">描述</span><span class="sxs-lookup"><span data-stu-id="1e1df-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e1df-108">profileName</span><span class="sxs-lookup"><span data-stu-id="1e1df-108">profileName</span></span>|<span data-ttu-id="1e1df-109">可指定與這個行為相關聯的追蹤設定檔名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="1e1df-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e1df-110">子元素</span><span class="sxs-lookup"><span data-stu-id="1e1df-110">Child Elements</span></span>  

 <span data-ttu-id="1e1df-111">無。</span><span class="sxs-lookup"><span data-stu-id="1e1df-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e1df-112">父項目</span><span class="sxs-lookup"><span data-stu-id="1e1df-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1e1df-113">項目</span><span class="sxs-lookup"><span data-stu-id="1e1df-113">Element</span></span>|<span data-ttu-id="1e1df-114">描述</span><span class="sxs-lookup"><span data-stu-id="1e1df-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e1df-115">\<behavior> 次數 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e1df-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="1e1df-116">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="1e1df-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e1df-117">備註</span><span class="sxs-lookup"><span data-stu-id="1e1df-117">Remarks</span></span>  

 <span data-ttu-id="1e1df-118">加入至服務的行為組態時，這個組態項目會在工作流程服務中，設定追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="1e1df-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="1e1df-119">追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。</span><span class="sxs-lookup"><span data-stu-id="1e1df-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="1e1df-120">同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。</span><span class="sxs-lookup"><span data-stu-id="1e1df-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e1df-121">範例</span><span class="sxs-lookup"><span data-stu-id="1e1df-121">Example</span></span>  

 <span data-ttu-id="1e1df-122">以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="1e1df-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="1e1df-123">ETW 追蹤參與者用來將追蹤記錄寫入至 ETW 的提供者識別碼，是在一節中定義的 **\<diagnostics>** 。</span><span class="sxs-lookup"><span data-stu-id="1e1df-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="1e1df-124">追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="1e1df-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="1e1df-125">這是由元素的 **profileName** 屬性所定義 **\<add>** 。</span><span class="sxs-lookup"><span data-stu-id="1e1df-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="1e1df-126">一旦定義這些定義之後，追蹤參與者就會加入至 **\<etwTracking>** 服務行為。</span><span class="sxs-lookup"><span data-stu-id="1e1df-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="1e1df-127">如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="1e1df-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e1df-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e1df-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="1e1df-129">工作流程追蹤與追查</span><span class="sxs-lookup"><span data-stu-id="1e1df-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1e1df-130">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="1e1df-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
