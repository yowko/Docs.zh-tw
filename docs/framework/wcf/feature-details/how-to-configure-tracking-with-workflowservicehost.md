---
title: HOW TO：以 WorkflowServiceHost 設定追蹤
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 56b9f95019995cdb55ec36769ff179ce1125c4b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490730"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="4306e-102">HOW TO：以 WorkflowServiceHost 設定追蹤</span><span class="sxs-lookup"><span data-stu-id="4306e-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="4306e-103">本主題說明如何設定裝載於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 之 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 工作流程的追蹤。</span><span class="sxs-lookup"><span data-stu-id="4306e-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="4306e-104">此追蹤是透過 Web.config 檔案指定服務行為而設定的。</span><span class="sxs-lookup"><span data-stu-id="4306e-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="4306e-105">在組態中設定追蹤</span><span class="sxs-lookup"><span data-stu-id="4306e-105">Configure Tracking in Configuration</span></span>  
  
1.  <span data-ttu-id="4306e-106">您可以使用組態檔中的 <<xref:System.Activities.Tracking.EtwTrackingParticipant>> 項目來加入 `behavior`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4306e-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4306e-107">上述組態範例會使用簡化的組態。</span><span class="sxs-lookup"><span data-stu-id="4306e-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="4306e-108">如需詳細資訊，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="4306e-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="4306e-109">上述組態範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="4306e-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="4306e-110">追蹤設定檔是在 <`trackingProfile`> 內的 <`tracking`> 項目中建立的。</span><span class="sxs-lookup"><span data-stu-id="4306e-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="4306e-111">追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="4306e-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="4306e-112">下列範例示範如何建立追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4306e-112">The following example shows how to create a tracking profile.</span></span>  
  
    ```xml  
    <system.serviceModel>  
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
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="4306e-113">如需追蹤設定檔的詳細資訊，請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4306e-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="4306e-114">如需一般追蹤的詳細資訊，請參閱[工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="4306e-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="4306e-115">在程式碼中設定追蹤</span><span class="sxs-lookup"><span data-stu-id="4306e-115">Configure Tracking in Code</span></span>  
  
1.  <span data-ttu-id="4306e-116">您可以使用程式碼中的 <xref:System.Activities.Tracking.EtwTrackingParticipant> 行為來加入 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4306e-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="4306e-117">上述程式碼範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="4306e-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="4306e-118">追蹤設定檔是在 <`trackingProfile`> 項目內的 <`tracking`> 項目中建立的，如上一節所示。</span><span class="sxs-lookup"><span data-stu-id="4306e-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="4306e-119">如需追蹤設定檔的詳細資訊，請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4306e-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="4306e-120">如需一般追蹤的詳細資訊，請參閱[工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="4306e-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="4306e-121">如需設定追蹤以程式設計方式的範例，請參閱[流程設定追蹤](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="4306e-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4306e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4306e-122">See Also</span></span>  
 [<span data-ttu-id="4306e-123">WCF 服務的簡化組態</span><span class="sxs-lookup"><span data-stu-id="4306e-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [<span data-ttu-id="4306e-124">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="4306e-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="4306e-125">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4306e-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
