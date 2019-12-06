---
title: 工作流程持續性
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: c49e287c6132103d4bb85a8ae892a76f9b582274
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837528"
---
# <a name="workflow-persistence"></a><span data-ttu-id="f9639-102">工作流程持續性</span><span class="sxs-lookup"><span data-stu-id="f9639-102">Workflow Persistence</span></span>
<span data-ttu-id="f9639-103">工作流程持續性是永久擷取工作流程執行個體的狀態，與處理序或電腦資訊無關。</span><span class="sxs-lookup"><span data-stu-id="f9639-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="f9639-104">這麼做是為了在發生系統故障時提供已知的工作流程執行個體復原點，或者藉由卸載非正在進行工作的工作流程執行個體來保留記憶體，或者將工作流程執行個體的狀態從某個節點移到伺服器陣列中的另一個節點。</span><span class="sxs-lookup"><span data-stu-id="f9639-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="f9639-105">持續性可讓處理序擁有靈活度、擴充性、發生錯誤時的復原能力，以及以更高的效率管理記憶體的能力。</span><span class="sxs-lookup"><span data-stu-id="f9639-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="f9639-106">持續性處理序包括識別保存點、收集要儲存的資料，最後將資料的實際儲存委派給持續性提供者。</span><span class="sxs-lookup"><span data-stu-id="f9639-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="f9639-107">若要啟用工作流程的持續性，您必須將實例存放區與**WorkflowApplication**或**WorkflowServiceHost**建立關聯，如[如何：啟用工作流程和工作流程服務的持續](how-to-enable-persistence-for-workflows-and-workflow-services.md)性中所述。</span><span class="sxs-lookup"><span data-stu-id="f9639-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="f9639-108">**WorkflowApplication**和**WorkflowServiceHost**會使用與其相關聯的實例存放區，以便將工作流程實例保存至持續性存放區，並根據儲存在持續性存放區中的工作流程實例資料，將工作流程實例載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="f9639-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="f9639-109">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 隨附于**SqlWorkflowInstanceStore**類別，可讓您將有關工作流程實例的資料和中繼資料保存到 SQL Server 2005 或 SQL Server 2008 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9639-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="f9639-110">如需詳細資訊，請參閱[SQL 工作流程實例存放區](sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="f9639-110">See [SQL Workflow Instance Store](sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="f9639-111">若要儲存及載入應用程式特定資料與工作流程執行個體相關資訊，您可以建立擴充 <xref:System.Activities.Persistence.PersistenceParticipant> 類別的持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="f9639-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="f9639-112">持續性參與者會參與保存程序，將自訂可序列化資料儲存至持續性存放區中，以便將執行個體存放區中的資料載入記憶體中，以及在持續性異動下執行任何其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="f9639-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="f9639-113">如需詳細資訊，請參閱[持續性參與者](persistence-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="f9639-113">For more information, see [Persistence Participants](persistence-participants.md).</span></span>  
  
 <span data-ttu-id="f9639-114">Windows Server App Fabric 會簡化設定持續性的程序。</span><span class="sxs-lookup"><span data-stu-id="f9639-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="f9639-115">如需詳細資訊，請參閱[Windows Server App Fabric 的持續性概念](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f9639-115">For more information, see [Persistence Concepts with Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="f9639-116">隱含的保存點</span><span class="sxs-lookup"><span data-stu-id="f9639-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="f9639-117">下列清單包含當執行個體存放區與工作流程相關時，保存工作流程的條件範例。</span><span class="sxs-lookup"><span data-stu-id="f9639-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
- <span data-ttu-id="f9639-118">當**TransactionScope**活動完成或**TransactedReceiveScope**活動完成時。</span><span class="sxs-lookup"><span data-stu-id="f9639-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
- <span data-ttu-id="f9639-119">當工作流程實例變成閒置，且已在工作流程主機上設定**WorkflowIdleBehavior**時。</span><span class="sxs-lookup"><span data-stu-id="f9639-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="f9639-120">例如，當您使用訊息活動或**延遲**活動時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="f9639-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
- <span data-ttu-id="f9639-121">當 WorkflowApplication 變成閒置，且應用程式的**PersistableIdle**屬性設定為 PersistableIdleAction 時，就會**保存**。</span><span class="sxs-lookup"><span data-stu-id="f9639-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
- <span data-ttu-id="f9639-122">當指示主應用程式保存或卸載工作流程執行個體時。</span><span class="sxs-lookup"><span data-stu-id="f9639-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
- <span data-ttu-id="f9639-123">當工作流程執行個體終止或完成時。</span><span class="sxs-lookup"><span data-stu-id="f9639-123">When a workflow instance is terminated or finishes.</span></span>  
  
- <span data-ttu-id="f9639-124">當**保存**活動執行時。</span><span class="sxs-lookup"><span data-stu-id="f9639-124">When a **Persist** activity executes.</span></span>  
  
- <span data-ttu-id="f9639-125">當使用舊版 Windows Workflow Foundation 開發的工作流程執行個體在互通的執行期間遇到保存點時。</span><span class="sxs-lookup"><span data-stu-id="f9639-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9639-126">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f9639-126">In This Section</span></span>  
  
- [<span data-ttu-id="f9639-127">SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="f9639-127">SQL Workflow Instance Store</span></span>](sql-workflow-instance-store.md)  
  
- [<span data-ttu-id="f9639-128">執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="f9639-128">Instance Stores</span></span>](instance-stores.md)  
  
- [<span data-ttu-id="f9639-129">持續性參與者</span><span class="sxs-lookup"><span data-stu-id="f9639-129">Persistence Participants</span></span>](persistence-participants.md)  
  
- [<span data-ttu-id="f9639-130">持續性最佳做法</span><span class="sxs-lookup"><span data-stu-id="f9639-130">Persistence Best Practices</span></span>](persistence-best-practices.md)  
  
- [<span data-ttu-id="f9639-131">非持續性工作流程執行個體</span><span class="sxs-lookup"><span data-stu-id="f9639-131">Non-Persisted Workflow Instances</span></span>](non-persisted-workflow-instances.md)  
  
- [<span data-ttu-id="f9639-132">暫停及繼續工作流程</span><span class="sxs-lookup"><span data-stu-id="f9639-132">Pausing and Resuming a Workflow</span></span>](pausing-and-resuming-a-workflow.md)
