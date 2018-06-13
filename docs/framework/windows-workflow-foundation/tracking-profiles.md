---
title: 追蹤設定檔
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 4f70964ea7e2456f82aeac4bfb9aedfdb239d58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519980"
---
# <a name="tracking-profiles"></a><span data-ttu-id="4ed8e-102">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4ed8e-102">Tracking Profiles</span></span>
<span data-ttu-id="4ed8e-103">追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>  
  
## <a name="tracking-profiles"></a><span data-ttu-id="4ed8e-104">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4ed8e-104">Tracking Profiles</span></span>  
 <span data-ttu-id="4ed8e-105">追蹤設定檔可用來指定要為工作流程執行個體發出哪些追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="4ed8e-106">如果未指定任何設定檔，則會發出所有追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="4ed8e-107">如果有指定設定檔，則會發出設定檔中指定的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="4ed8e-108">根據您的監控需求，您可以寫入非常廣泛的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="4ed8e-109">反之，您也可以建立非常詳細的設定檔，取得充分的結果事件，以便在日後重新建構為詳細的執行流程。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="4ed8e-110">追蹤設定檔會顯示為標準 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組態檔中的 XML 項目，或在程式碼中指定。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-110">Tracking profiles manifest themselves as XML elements within a standard [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration file or specified in code.</span></span> <span data-ttu-id="4ed8e-111">下列範例是組態檔中的 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 追蹤設定檔，可允許追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <tracking>    
      <trackingProfile name="Sample Tracking Profile">  
        <workflow activityDefinitionId="*">  
          <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                <state name="Started"/>  
                <state name="Completed"/>  
              </states>  
            </workflowInstanceQuery>  
          </workflowInstanceQueries>  
        </workflow>  
      </trackingProfile>          
    </profiles>  
  </tracking>  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4ed8e-112">下列範例顯示使用程式碼來建立的同等追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-112">The following example shows the equivalent tracking profile created using code.</span></span>  
  
```csharp  
TrackingProfile profile = new TrackingProfile()  
{  
    Name = "CustomTrackingProfile",  
    Queries =   
    {  
        new WorkflowInstanceQuery()  
        {  
            // Limit workflow instance tracking records for started and  
            // completed workflow states.  
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },  
        }  
    }  
};  
```  
  
 <span data-ttu-id="4ed8e-113">追蹤記錄是利用 <xref:System.Activities.Tracking.ImplementationVisibility> 屬性，透過追蹤設定檔內的可見性模式所篩選的。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="4ed8e-114">複合活動是最上層的活動，其中包含構成其實作的其他活動。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="4ed8e-115">可見性模式會透過指定從工作流程活動內的複合活動發出的追蹤記錄，指定是否要追蹤形成實作的活動。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span>  <span data-ttu-id="4ed8e-116">可見性模式會在追蹤設定檔層級套用。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="4ed8e-117">工作流程中個別活動的追蹤記錄篩選，是由追蹤設定檔中的查詢進行控制。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="4ed8e-118">如需詳細資訊，請參閱**追蹤設定檔查詢類型**這份文件中的一節。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>  
  
 <span data-ttu-id="4ed8e-119">追蹤設定檔中，以 `implementationVisibility` 屬性指定的兩個可見性模式為 `RootScope` 和 `All`。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="4ed8e-120">若複合活動不是工作流程的根，使用 `RootScope` 模式會隱藏形成活動之實作的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span>  <span data-ttu-id="4ed8e-121">也就是說，將使用其他活動實作的活動加入至工作流程中，且 `implementationVisibility` 設定為 RootScope 時，只會追蹤該複合活動內的最上層活動。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="4ed8e-122">若活動是工作流程的根，則該活動的實作會是工作流程本身，且會針對形成實作的活動發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="4ed8e-123">使用 All 模式可發出根活動及所有其複合活動的全部追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>  
  
 <span data-ttu-id="4ed8e-124">例如，假設*MyActivity*是複合活動，其實作包含兩個活動， *Activity1*和*Activity2*。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span>  <span data-ttu-id="4ed8e-125">當這個活動加入至工作流程，並已啟用追蹤的追蹤設定檔與`implementationVisibility`設`RootScope`，追蹤記錄只會發出*MyActivity*。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span>  <span data-ttu-id="4ed8e-126">不過，活動會發出任何記錄*Activity1*和*Activity2*。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="4ed8e-127">不過，如果`implementationVisisbility`屬性的追蹤設定檔設定為`All`，則不只發出追蹤記錄*MyActivity*，但也會針對活動*Activity1*和*Activity2*。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-127">However, if the `implementationVisisbility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="4ed8e-128">`implementationVisibility` 旗標適用於下列追蹤記錄類型：</span><span class="sxs-lookup"><span data-stu-id="4ed8e-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>  
  
-   <span data-ttu-id="4ed8e-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="4ed8e-129">ActivityStateRecord</span></span>  
  
-   <span data-ttu-id="4ed8e-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="4ed8e-130">FaultPropagationRecord</span></span>  
  
-   <span data-ttu-id="4ed8e-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="4ed8e-131">CancelRequestedRecord</span></span>  
  
-   <span data-ttu-id="4ed8e-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="4ed8e-132">ActivityScheduledRecord</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ed8e-133">implementationVisibility 設定不會篩選出從活動實作發出的 CustomTrackingRecords。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>  
  
 <span data-ttu-id="4ed8e-134">在下列程式碼中的追蹤設定檔中，會將 `implementationVisibility` 功能指定為 <xref:System.Activities.Tracking.ImplementationVisibility.RootScope>：</span><span class="sxs-lookup"><span data-stu-id="4ed8e-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 <span data-ttu-id="4ed8e-135">在下列組態檔的追蹤設定檔中，會將 `implementationVisibility` 功能指定為 <xref:System.Activities.Tracking.ImplementationVisibility.All>：</span><span class="sxs-lookup"><span data-stu-id="4ed8e-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>  
  
```xml  
<tracking>  
      <profiles>  
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">  
          <workflow activityDefinitionId="*">  
...  
         </workflow>  
        </trackingProfile>  
      </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="4ed8e-136">追蹤設定檔的 `ImplementationVisibility` 設定是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="4ed8e-137">根據預設，其值會設定為 `RootScope`。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="4ed8e-138">這個屬性的值也會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-138">The values for this attribute are also case-sensitive.</span></span>  
  
### <a name="tracking-profile-query-types"></a><span data-ttu-id="4ed8e-139">追蹤設定檔查詢類型</span><span class="sxs-lookup"><span data-stu-id="4ed8e-139">Tracking Profile Query Types</span></span>  
 <span data-ttu-id="4ed8e-140">追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="4ed8e-141">您可以使用數個查詢型別訂閱不同類別的 <xref:System.Activities.Tracking.TrackingRecord> 物件。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="4ed8e-142">追蹤設定檔可在組態中指定，或是透過程式碼指定。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="4ed8e-143">以下是最常見的查詢類型：</span><span class="sxs-lookup"><span data-stu-id="4ed8e-143">Here are the most common query types:</span></span>  
  
-   <span data-ttu-id="4ed8e-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - 使用這個查詢，即可追蹤工作流程執行個體生命週期變更，例如先前示範的 `Started` 和 `Completed`。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="4ed8e-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 會用來訂閱下列 <xref:System.Activities.Tracking.TrackingRecord> 物件：</span><span class="sxs-lookup"><span data-stu-id="4ed8e-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     <span data-ttu-id="4ed8e-146">可供訂閱的狀態可於 <xref:System.Activities.Tracking.WorkflowInstanceStates> 類別中指定。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>  
  
     <span data-ttu-id="4ed8e-147">下列範例示範使用 `Started` 訂閱 <xref:System.Activities.Tracking.WorkflowInstanceQuery> 執行個體狀態之工作流程執行個體層級追蹤記錄的組態或程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new WorkflowInstanceQuery()  
            {  
                States = { WorkflowInstanceStates.Started}                                                                     
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="4ed8e-148"><xref:System.Activities.Tracking.ActivityStateQuery> - 使用這個查詢，即可追蹤組成工作流程執行個體之活動的生命週期變更。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="4ed8e-149">比方說，您可能想要追蹤的每一次 「 傳送電子郵件 」 活動完成的工作流程執行個體中。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="4ed8e-150"><xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.ActivityStateRecord> 物件時，必須要有這個查詢。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="4ed8e-151">可供訂閱的狀態可於 <xref:System.Activities.Tracking.ActivityStates> 中指定。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>  
  
     <span data-ttu-id="4ed8e-152">下列範例示範訂閱使用 <xref:System.Activities.Tracking.ActivityStateQuery> 做為 `SendEmailActivity` 活動之活動狀態追蹤記錄的組態和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>  
  
    ```xml  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new ActivityStateQuery()  
            {                              
                ActivityName = "SendEmailActivity",  
                States = { ActivityStates.Closed }  
            }  
        }  
    };  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4ed8e-153">如果多個 activityStateQuery 元素具有相同的名稱，追蹤設定檔只會使用最後一個元素中的狀態。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>  
  
-   <span data-ttu-id="4ed8e-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - 這個查詢可讓您追蹤由父活動排程執行的活動。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="4ed8e-155"><xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.ActivityScheduledRecord> 物件時，必須要有這個查詢。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>  
  
     <span data-ttu-id="4ed8e-156">下列範例示範訂閱使用 `SendEmailActivity` 排定的 <xref:System.Activities.Tracking.ActivityScheduledQuery> 子活動之相關記錄的組態和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new ActivityScheduledQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="4ed8e-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - 使用這個查詢，即可追蹤活動中發生的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="4ed8e-158"><xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.FaultPropagationRecord> 物件時，必須要有這個查詢。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>  
  
     <span data-ttu-id="4ed8e-159">下列範例示範使用 <xref:System.Activities.Tracking.FaultPropagationQuery> 訂閱與錯誤傳播相關之記錄的組態和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new FaultPropagationQuery()  
            {  
                FaultSourceActivityName = "SendEmailActivity",  
                FaultHandlerActivityName = "NotificationsFaultHandler"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="4ed8e-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - 使用這個查詢，即可追蹤父活動取消子活動的要求。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4ed8e-161"><xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.CancelRequestedRecord> 物件時，必須要有這個查詢。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>  
  
     <span data-ttu-id="4ed8e-162">用來訂閱記錄的程式碼與組態相關活動取消使用<xref:System.Activities.Tracking.CancelRequestedQuery>下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CancelRequestedQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="4ed8e-163"><xref:System.Activities.Tracking.CustomTrackingQuery>- 使用這個查詢，即可追蹤程式碼活動中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="4ed8e-164"><xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.CustomTrackingRecord> 物件時，必須要有這個查詢。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>  
  
     <span data-ttu-id="4ed8e-165">下列範例示範使用 <xref:System.Activities.Tracking.CustomTrackingQuery> 訂閱與自訂追蹤記錄相關之記錄的組態和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CustomTrackingQuery()   
            {  
                Name = "EmailAddress",  
                ActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="4ed8e-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - 使用這個查詢，即可追蹤工作流程執行個體中書籤的繼續。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4ed8e-167"><xref:System.Activities.Tracking.TrackingParticipant> 訂閱 <xref:System.Activities.Tracking.BookmarkResumptionRecord> 物件時，必須要有這個查詢。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>  
  
     <span data-ttu-id="4ed8e-168">下列範例示範使用 <xref:System.Activities.Tracking.BookmarkResumptionQuery> 訂閱與書籤繼續相關之記錄的組態和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new BookmarkResumptionQuery()  
            {  
                Name = "sentEmailBookmark"  
            }  
        }  
    };  
    ```  
  
### <a name="annotations"></a><span data-ttu-id="4ed8e-169">標註</span><span class="sxs-lookup"><span data-stu-id="4ed8e-169">Annotations</span></span>  
 <span data-ttu-id="4ed8e-170">附註可讓您使用值任意標記追蹤記錄，該值可在建置階段後設定。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="4ed8e-171">例如，您可能需要數個追蹤記錄之間加上"Mail Server"的多個工作流程 = ="Mail Server1"。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="4ed8e-172">當您稍後查詢追蹤記錄時，就可以更輕鬆地找到所有具有這個標記的記錄。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
 <span data-ttu-id="4ed8e-173">若要完成這個目的，就需要將附註加入至追蹤查詢，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="4ed8e-174">如何建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4ed8e-174">How to Create a Tracking Profile</span></span>  
 <span data-ttu-id="4ed8e-175">追蹤查詢元素可讓您使用 XML 組態檔或 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 程式碼來建立追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span>  <span data-ttu-id="4ed8e-176">以下是使用組態檔建立的追蹤設定檔範例。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-176">Here is an example of a tracking profile created using a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>  
    <profiles>  
      <trackingProfile name="Sample Tracking Profile ">  
        <workflow activityDefinitionId="*">  
          <!--Specify the tracking profile query elements to subscribe for tracking records-->  
        </workflow>  
      </trackingProfile>  
    </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
> [!WARNING]
>  <span data-ttu-id="4ed8e-177">針對使用工作流程服務主機的 WF，追蹤設定檔通常會使用組態檔建立。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="4ed8e-178">您也可以使用追蹤設定檔和追蹤查詢 API，以程式碼建立追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>  
  
 <span data-ttu-id="4ed8e-179">設定為 XML 組態檔的設定檔會使用行為擴充套用至追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="4ed8e-180">後面的章節中所述，這會加入至 WorkflowServiceHost[流程設定追蹤](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="4ed8e-181">主機發出之追蹤記錄的詳細資訊取決於追蹤設定檔內的組態設定。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="4ed8e-182">追蹤參與者可將查詢加入至追蹤設定檔，以訂閱追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="4ed8e-183">若要訂閱所有追蹤記錄，追蹤設定檔，必須先指定所有追蹤查詢，使用"\*"中每個查詢的名稱欄位。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>  
  
 <span data-ttu-id="4ed8e-184">以下是追蹤設定檔的一些通用範例。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-184">Here are some of the common examples of tracking profiles.</span></span>  
  
-   <span data-ttu-id="4ed8e-185">取得工作流程執行個體記錄和錯誤的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-185">A tracking profile to obtain workflow instance records and faults.</span></span>  
  
```xml  
<trackingProfile name="Instance and Fault Records">  
  <workflow activityDefinitionId="*">  
    <workflowInstanceQueries>  
      <workflowInstanceQuery>  
        <states>  
          <state name="*" />  
        </states>  
      </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    <activityStateQueries>  
      <activityStateQuery activityName="*">  
        <states>  
          <state name="Faulted"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
  </workflow>  
</trackingProfile>  
```  
  
1.  <span data-ttu-id="4ed8e-186">取得所有自訂追蹤記錄的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4ed8e-186">A tracking profile to obtain all custom tracking records.</span></span>  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ed8e-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ed8e-187">See Also</span></span>  
 [<span data-ttu-id="4ed8e-188">SQL 追蹤</span><span class="sxs-lookup"><span data-stu-id="4ed8e-188">SQL Tracking</span></span>](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [<span data-ttu-id="4ed8e-189">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="4ed8e-189">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="4ed8e-190">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="4ed8e-190">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
