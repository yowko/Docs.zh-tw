---
title: HOW TO：啟用工作流程與工作流程服務的持續性
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761425"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="fd433-102">HOW TO：啟用工作流程與工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="fd433-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="fd433-103">本主題描述如何啟用工作流程與工作流程服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="fd433-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="fd433-104">啟用工作流程的持續性</span><span class="sxs-lookup"><span data-stu-id="fd433-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="fd433-105">您可以建立與執行個體存放區的關聯**WorkflowApplication**利用<xref:System.Activities.WorkflowApplication.InstanceStore%2A>屬性<xref:System.Activities.WorkflowApplication>類別。</span><span class="sxs-lookup"><span data-stu-id="fd433-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="fd433-106"><xref:System.Activities.WorkflowApplication.Persist%2A> 方法會將工作流程儲存或保存在與應用程式相關的執行個體存放區中。</span><span class="sxs-lookup"><span data-stu-id="fd433-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="fd433-107"><xref:System.Activities.WorkflowApplication.Unload%2A> 方法會將工作流程保存在執行個體存放區中，然後從記憶體卸載該執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd433-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="fd433-108">**負載**方法會載入使用執行個體持續性存放區中的工作流程資料的記憶體中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="fd433-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="fd433-109">**Persist**方法會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fd433-109">The **Persist** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="fd433-110">暫停工作流程排程器，直到工作流程進入閒置狀態為止。</span><span class="sxs-lookup"><span data-stu-id="fd433-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="fd433-111">將工作流程保存或儲存在持續性存放區中。</span><span class="sxs-lookup"><span data-stu-id="fd433-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="fd433-112">恢復工作流程排程器。</span><span class="sxs-lookup"><span data-stu-id="fd433-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="fd433-113">**卸載**方法會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fd433-113">The **Unload** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="fd433-114">暫停工作流程排程器，直到工作流程進入閒置狀態為止。</span><span class="sxs-lookup"><span data-stu-id="fd433-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="fd433-115">將工作流程保存或儲存在持續性存放區中。</span><span class="sxs-lookup"><span data-stu-id="fd433-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="fd433-116">處置記憶體中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd433-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="fd433-117">這兩個**Persist**並**卸載**方法將會封鎖直到工作流程離開不保存區域工作流程是在非保存區域時。</span><span class="sxs-lookup"><span data-stu-id="fd433-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="fd433-118">不保存區完成後，此方法會繼續進行保存或卸載作業。</span><span class="sxs-lookup"><span data-stu-id="fd433-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="fd433-119">如果不保存區未在逾時時間過去前完成，或者持續性處理序所花的時間過長，就會擲回 TimeoutException。</span><span class="sxs-lookup"><span data-stu-id="fd433-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="fd433-120">在程式碼中啟用工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="fd433-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="fd433-121">**DurableInstancingOptions**隸屬<xref:System.ServiceModel.WorkflowServiceHost>類別具有名為**InstanceStore**可用來建立與執行個體存放區的關聯**WorkflowServiceHost**.</span><span class="sxs-lookup"><span data-stu-id="fd433-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="fd433-122">當**WorkflowServiceHost**已開啟，持續性會自動啟用**DurableInstancingOptions.InstanceStore**不是 null。</span><span class="sxs-lookup"><span data-stu-id="fd433-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="fd433-123">一般而言，服務行為會提供搭配使用工作流程服務主機的實體執行個體存放區**InstanceStore**屬性。</span><span class="sxs-lookup"><span data-stu-id="fd433-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="fd433-124">例如，SqlWorkflowInstanceStoreBehavior 會建立的執行個體**SqlWorkflowInstanceStore**、 加以設定，然後將其指派給**DurableInstancingOptions.InstanceStore**。</span><span class="sxs-lookup"><span data-stu-id="fd433-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="fd433-125">使用應用程式組態檔啟用工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="fd433-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="fd433-126">在 app.config 或 web.config 檔案中加入下列程式碼，即可使用應用程式組態檔啟用持續性：</span><span class="sxs-lookup"><span data-stu-id="fd433-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
