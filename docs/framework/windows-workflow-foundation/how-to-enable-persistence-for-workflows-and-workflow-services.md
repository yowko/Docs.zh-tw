---
title: HOW TO：啟用工作流程與工作流程服務的持續性
description: 瞭解如何設定 SQL 工作流程實例存放區，以程式設計方式和使用設定檔來啟用工作流程和工作流程服務的持續性。
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421510"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="2c636-103">HOW TO：啟用工作流程與工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="2c636-103">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="2c636-104">本主題描述如何啟用工作流程與工作流程服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="2c636-104">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="2c636-105">啟用工作流程的持續性</span><span class="sxs-lookup"><span data-stu-id="2c636-105">Enable Persistence for Workflows</span></span>

<span data-ttu-id="2c636-106">您可以使用類別的屬性，將實例存放區與**WorkflowApplication**產生關聯 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication> 。</span><span class="sxs-lookup"><span data-stu-id="2c636-106">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="2c636-107"><xref:System.Activities.WorkflowApplication.Persist%2A> 方法會將工作流程儲存或保存在與應用程式相關的執行個體存放區中。</span><span class="sxs-lookup"><span data-stu-id="2c636-107">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="2c636-108"><xref:System.Activities.WorkflowApplication.Unload%2A> 方法會將工作流程保存在執行個體存放區中，然後從記憶體卸載該執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c636-108">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="2c636-109">**Load**方法會使用儲存在實例持續性存放區中的工作流程資料，將工作流程載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="2c636-109">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="2c636-110">**保存**方法會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2c636-110">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="2c636-111">暫停工作流程排程器，直到工作流程進入閒置狀態為止。</span><span class="sxs-lookup"><span data-stu-id="2c636-111">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="2c636-112">將工作流程保存或儲存在持續性存放區中。</span><span class="sxs-lookup"><span data-stu-id="2c636-112">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="2c636-113">恢復工作流程排程器。</span><span class="sxs-lookup"><span data-stu-id="2c636-113">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="2c636-114">**Unload**方法會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2c636-114">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="2c636-115">暫停工作流程排程器，直到工作流程進入閒置狀態為止。</span><span class="sxs-lookup"><span data-stu-id="2c636-115">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="2c636-116">將工作流程保存或儲存在持續性存放區中。</span><span class="sxs-lookup"><span data-stu-id="2c636-116">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="2c636-117">處置記憶體中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c636-117">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="2c636-118">當工作流程在不保存區域中時，**保存\*\*\*\*和卸載**方法都會遭到封鎖，直到工作流程離開不保存區域為止。</span><span class="sxs-lookup"><span data-stu-id="2c636-118">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="2c636-119">不保存區完成後，此方法會繼續進行保存或卸載作業。</span><span class="sxs-lookup"><span data-stu-id="2c636-119">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="2c636-120">如果不保存區未在逾時時間過去前完成，或者持續性處理序所花的時間過長，就會擲回 TimeoutException。</span><span class="sxs-lookup"><span data-stu-id="2c636-120">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="2c636-121">在程式碼中啟用工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="2c636-121">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="2c636-122">類別的**DurableInstancingOptions**成員 <xref:System.ServiceModel.WorkflowServiceHost> 具有名為**InstanceStore**的屬性，可讓您用來建立實例存放區與**WorkflowServiceHost**的關聯。</span><span class="sxs-lookup"><span data-stu-id="2c636-122">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="2c636-123">當**WorkflowServiceHost**開啟時，如果**DurableInstancingOptions**不是 null，就會自動啟用持續性。</span><span class="sxs-lookup"><span data-stu-id="2c636-123">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="2c636-124">一般而言，服務行為會提供具象實例存放區，以搭配使用**InstanceStore**屬性與工作流程服務主機。</span><span class="sxs-lookup"><span data-stu-id="2c636-124">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="2c636-125">例如，SqlWorkflowInstanceStoreBehavior 會建立**SqlWorkflowInstanceStore**的實例、設定它，並將它指派給**DurableInstancingOptions**。</span><span class="sxs-lookup"><span data-stu-id="2c636-125">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="2c636-126">使用應用程式組態檔啟用工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="2c636-126">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="2c636-127">在 app.config 或 web.config 檔案中加入下列程式碼，即可使用應用程式組態檔啟用持續性：</span><span class="sxs-lookup"><span data-stu-id="2c636-127">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
