---
title: HOW TO：以 WorkflowServiceHost 設定閒置行為
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55cc10357e8ae6b5458ca3440e1728cb578208b3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="8bca7-102">HOW TO：以 WorkflowServiceHost 設定閒置行為</span><span class="sxs-lookup"><span data-stu-id="8bca7-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="8bca7-103">工作流程遇到必須由外部刺激繼續執行的書籤時，例如工作流程執行個體正在等候訊息使用 <xref:System.ServiceModel.Activities.Receive> 活動加以傳遞時，工作流程就會進入閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="8bca7-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="8bca7-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> 是一種行為，可讓您指定從服務執行個體進入閒置到此執行個體保存或卸載的間隔時間。</span><span class="sxs-lookup"><span data-stu-id="8bca7-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="8bca7-105">其中包含兩個屬性，可用來設定這些時間範圍。</span><span class="sxs-lookup"><span data-stu-id="8bca7-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="8bca7-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> 會指定從工作流程服務執行個體進入閒置到工作流程服務執行個體保存的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="8bca7-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="8bca7-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 會指定從工作流程服務執行個體進入閒置到工作流程服務執行個體卸載的時間範圍，而卸載的意義是將執行個體保存到執行個體儲存區並從記憶體中移除。</span><span class="sxs-lookup"><span data-stu-id="8bca7-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="8bca7-108">本主題說明如何設定組態檔中的 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> 。</span><span class="sxs-lookup"><span data-stu-id="8bca7-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="8bca7-109">若要設定 WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="8bca7-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="8bca7-110">新增 <`workflowIdle`> 項目 <`behavior`> 內的項目 <`serviceBehaviors`> 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8bca7-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="8bca7-111">`timeToUnload` 屬性會指定從工作流程服務執行個體進入閒置到工作流程服務卸載的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="8bca7-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="8bca7-112">`timeToPersist` 屬性會指定從工作流程服務執行個體進入閒置到工作流程服務保存的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="8bca7-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="8bca7-113">`timeToUnload` 的預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="8bca7-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="8bca7-114">`timeToPersist` 的預設值為 <xref:System.TimeSpan.MaxValue>。</span><span class="sxs-lookup"><span data-stu-id="8bca7-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="8bca7-115">如果您想要將閒置的執行個體保留在記憶體中，但保存它們以提供健全度，請設定下列值，讓 `timeToPersist` < `timeToUnload`。</span><span class="sxs-lookup"><span data-stu-id="8bca7-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="8bca7-116">如果您想要防止系統卸載閒置的執行個體，請將 `timeToUnload` 設定為 <xref:System.TimeSpan.MaxValue>。</span><span class="sxs-lookup"><span data-stu-id="8bca7-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8bca7-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>請參閱[工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="8bca7-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8bca7-118">上述組態範例會使用簡化的組態。</span><span class="sxs-lookup"><span data-stu-id="8bca7-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8bca7-119">如需詳細資訊，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="8bca7-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="8bca7-120">若要在程式碼中變更閒置行為</span><span class="sxs-lookup"><span data-stu-id="8bca7-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="8bca7-121">下列範例會以程式設計方式變更保存和卸載之前等候的時間。</span><span class="sxs-lookup"><span data-stu-id="8bca7-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8bca7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bca7-122">See Also</span></span>  
 [<span data-ttu-id="8bca7-123">工作流程服務主機擴充性</span><span class="sxs-lookup"><span data-stu-id="8bca7-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="8bca7-124">簡化設定</span><span class="sxs-lookup"><span data-stu-id="8bca7-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="8bca7-125">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="8bca7-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
