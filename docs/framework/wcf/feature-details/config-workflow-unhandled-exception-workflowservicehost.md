---
title: HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: e09575a7998f676ea188a0500f31012c25c19738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489189"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="e9f6b-102">HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為</span><span class="sxs-lookup"><span data-stu-id="e9f6b-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="e9f6b-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 是一項行為，可讓您指定裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程內發生未處理的例外狀況時，所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="e9f6b-104">本主題示範如何組態檔中設定此行為。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="e9f6b-105">若要設定 WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="e9f6b-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="e9f6b-106">新增 <`workflowUnhandledException`> 中的項目 <`behavior`> 內的項目 <`serviceBehaviors`> 項目，使用`action`屬性來指定在下列範例所示，就會發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e9f6b-107">上述組態範例會使用簡化的組態。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="e9f6b-108">如需詳細資訊，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="e9f6b-109">此行為可以在程式碼中設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="e9f6b-110">`action`屬性 <`workflowUnhandledException`> 項目可以設定為下列值之一：</span><span class="sxs-lookup"><span data-stu-id="e9f6b-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="e9f6b-111">**放棄**</span><span class="sxs-lookup"><span data-stu-id="e9f6b-111">**abandon**</span></span>  
     <span data-ttu-id="e9f6b-112">不改變永續性執行個體的狀態，放棄記憶體中的執行個體 (亦即，回復到上一次的永續點)。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="e9f6b-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="e9f6b-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="e9f6b-114">放棄記憶體中的執行個體，並更新要暫停的永續執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="e9f6b-115">**[取消]**</span><span class="sxs-lookup"><span data-stu-id="e9f6b-115">**cancel**</span></span>  
     <span data-ttu-id="e9f6b-116">呼叫執行個體的取消處理常式，然後完成記憶體中的執行個體，該記憶體可能也會將執行個體從執行個體庫中移除。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="e9f6b-117">**terminate**</span><span class="sxs-lookup"><span data-stu-id="e9f6b-117">**terminate**</span></span>  
     <span data-ttu-id="e9f6b-118">完成記憶體中的執行個體並將其從執行個體庫中移除。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="e9f6b-119">如需有關<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>，請參閱[工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f6b-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f6b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f6b-120">See Also</span></span>  
 [<span data-ttu-id="e9f6b-121">工作流程服務主機擴充性</span><span class="sxs-lookup"><span data-stu-id="e9f6b-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="e9f6b-122">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="e9f6b-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
