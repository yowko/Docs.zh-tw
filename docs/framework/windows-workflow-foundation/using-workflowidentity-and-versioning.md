---
title: 使用 WorkflowIdentity 與版本控制
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 64abab815c523abce88b00515239155499de9c4c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708167"
---
# <a name="using-workflowidentity-and-versioning"></a>使用 WorkflowIdentity 與版本控制
<xref:System.Activities.WorkflowIdentity> 提供一種方法，讓工作流程應用程式開發人員能夠將名稱和 <xref:System.Version> 與工作流程定義建立關聯，並為這項資訊與持續性的工作流程執行個體建立關聯。 此身分識別資訊可由工作流程應用程式開發人員使用以啟用案例 (例如並存執行多個版本的工作流程定義)，以及提供動態更新等其他功能的基礎。 本主題提供使用 <xref:System.Activities.WorkflowIdentity> 搭配 <xref:System.Activities.WorkflowApplication> 裝載的概觀。 並排顯示執行工作流程服務中的工作流程定義的資訊，請參閱[WorkflowServiceHost 中的並存版本控制](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)。 如需動態更新的資訊，請參閱[動態更新](dynamic-update.md)。  
  
## <a name="in-this-topic"></a>本主題內容  
  
-   [使用 WorkflowIdentity](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [使用 WorkflowIdentity 的並排顯示執行](using-workflowidentity-and-versioning.md#SxS)  
  
-   [升級.NET Framework 4 持續性資料庫，以支援工作流程版本控制](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [若要升級資料庫結構描述](using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> 使用 WorkflowIdentity  
 若要使用 <xref:System.Activities.WorkflowIdentity>，請建立執行個體、加以設定，並將其與 <xref:System.Activities.WorkflowApplication> 執行個體建立關聯。 <xref:System.Activities.WorkflowIdentity> 執行個體包含三項識別資訊。 <xref:System.Activities.WorkflowIdentity.Name%2A> 和 <xref:System.Activities.WorkflowIdentity.Version%2A> 包含名稱及 <xref:System.Version>，兩者都是必要項，而 <xref:System.Activities.WorkflowIdentity.Package%2A> 則是選用項，可用來指定包含資訊 (例如組件名稱或其他所需資訊) 的其他字串。 如果 <xref:System.Activities.WorkflowIdentity> 的三個屬性中有任何屬性與另一個 <xref:System.Activities.WorkflowIdentity> 的不同，則其為唯一識別。  
  
> [!IMPORTANT]
>  <xref:System.Activities.WorkflowIdentity> 不應包含任何個人可識別資訊 (PII)。 執行階段會在數個不同的活動生命週期點，將有關<xref:System.Activities.WorkflowIdentity> (用來建立執行個體) 的資訊發出到任何已設定的追蹤服務。 WF 追蹤沒有任何機制可隱藏 PII (機密的使用者資料)。 因此，<xref:System.Activities.WorkflowIdentity> 執行個體不應包含任何 PII 資料，因為執行階段會在追蹤記錄中發出這項資訊，因此存取檢視追蹤記錄的人有可能看見這項資訊。  
  
 在下列範例中，建立了 <xref:System.Activities.WorkflowIdentity>，並將其與使用 `MortgageWorkflow` 工作流程定義來建立的工作流程執行個體建立關聯。  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 重新載入並繼續工作流程時，所使用的 <xref:System.Activities.WorkflowIdentity> 必須設定為符合持續性工作流程執行個體的 <xref:System.Activities.WorkflowIdentity>。  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 如果在重新載入工作流程執行個體時，使用的 <xref:System.Activities.WorkflowIdentity> 與持續性 <xref:System.Activities.WorkflowIdentity> 不相符，會擲回 <xref:System.Activities.VersionMismatchException>。 在下列範例中，會在上一個範例中持續性 `MortgageWorkflow` 執行個體上載入。 這個載入嘗試是使用針對較新版抵押工作流程設定的 <xref:System.Activities.WorkflowIdentity>，該工作流程與持續性執行個體不相符。  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 執行先前的程式碼時，會擲回 <xref:System.Activities.VersionMismatchException>。  
  
 **WorkflowIdentity ('MortgageWorkflow v1;版本 = 1.0.0.0') 載入的執行個體不符的 WorkflowIdentity ('MortgageWorkflow v2;版本 = 2.0.0.0') 提供的工作流程定義。執行個體可以載入使用不同的定義，或使用動態更新來更新。**  
### <a name="SxS"></a> 使用 WorkflowIdentity 的並排顯示執行  
 <xref:System.Activities.WorkflowIdentity> 可加速並存執行多種版本的工作流程。 常見的案例之一是變更長時間執行工作流程的業務需求。 部署更新版本時，可以執行同一個工作流程的多個執行個體。 主應用程式可以設定為在啟動新執行個體時使用更新的工作流程定義，而且主應用程式必須在繼續執行個體時，負責提供正確的工作流程定義。 <xref:System.Activities.WorkflowIdentity> 可以在繼續工作流程執行個體時識別和提供相符的工作流程定義。  
  
 為了擷取持續性工作流程執行個體的 <xref:System.Activities.WorkflowIdentity>，會使用 <xref:System.Activities.WorkflowApplication.GetInstance%2A> 方法。 <xref:System.Activities.WorkflowApplication.GetInstance%2A> 方法會採用持續性工作流程執行個體的 <xref:System.Activities.WorkflowApplication.Id%2A> 及包含持續性執行個體的 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，並且傳回 <xref:System.Activities.WorkflowApplicationInstance>。 <xref:System.Activities.WorkflowApplicationInstance> 包含持續性工作流程執行個體的相關資訊，包括與其相關聯的 <xref:System.Activities.WorkflowIdentity>。 載入及繼續工作流程執行個體時，主機可以使用此相關聯的 <xref:System.Activities.WorkflowIdentity> 來提供正確的工作流程定義。  
  
> [!NOTE]
>  Null <xref:System.Activities.WorkflowIdentity> 為有效，而且可讓主機用來將沒有相關聯 <xref:System.Activities.WorkflowIdentity> 的持續性執行個體，對應至適當的工作流程定義。 當工作流程應用程式一開始未以工作流程版本控制撰寫時，或是當應用程式從 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]升級時，就會發生這種案例。 如需詳細資訊，請參閱 <<c0> [ 升級.NET Framework 4 持續性資料庫以支援工作流程版本控制](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)。  
  
 在下列範例中`Dictionary<WorkflowIdentity, Activity>`用來建立關聯<xref:System.Activities.WorkflowIdentity>執行個體，其比對的工作流程定義和工作流程會使用啟動`MortgageWorkflow`相關聯的工作流程定義`identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowIdentity identityV2 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v2",  
    Version = new Version(2, 0, 0, 0)  
};  
  
Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();  
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());  
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 在下列範例中，會呼叫 <xref:System.Activities.WorkflowApplication.GetInstance%2A>，以從上一個範例擷取持續性工作流程執行個體的相關資訊，並使用持續性 <xref:System.Activities.WorkflowIdentity> 資訊來擷取相符的工作流程定義。 此資訊可用來設定 <xref:System.Activities.WorkflowApplication>，然後載入工作流程。 請注意，因為使用 <xref:System.Activities.WorkflowApplication.Load%2A> 的 <xref:System.Activities.WorkflowApplicationInstance> 多載，<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 會使用在 <xref:System.Activities.WorkflowApplicationInstance> 上設定的 <xref:System.Activities.WorkflowApplication>，因此不需設定其 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 屬性。  
  
> [!NOTE]
>  如果設定了<xref:System.Activities.WorkflowApplication.InstanceStore%2A> 屬性，必須以 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 使用的同一個 <xref:System.Activities.WorkflowApplicationInstance> 執行個體進行設定，否則會擲回 <xref:System.ArgumentException>，並出現下列訊息：`The instance is configured with a different InstanceStore than this WorkflowApplication.`。  
  
```csharp  
// Get the WorkflowApplicationInstance of the desired workflow from the specified  
// SqlWorkflowInstanceStore.  
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);  
  
// Use the persisted WorkflowIdentity to retrieve the correct workflow  
// definition from the dictionary.  
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];  
  
WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(instance);  
  
// Resume the workflow...  
```  
  
## <a name="UpdatingWF4PersistenceDatabases"></a> 升級.NET Framework 4 持續性資料庫，以支援工作流程版本控制  
 提供 SqlWorkflowInstanceStoreSchemaUpgrade.sql 資料庫指令碼，以升級使用 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 資料庫指令碼建立的持續性資料庫。 這個指令碼可更新資料庫，以支援 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中引進的新版本控制功能。 資料庫中的任何持續性工作流程執行個體，都會有版本控制預設值，並可以參與並存執行和動態更新。  
  
 如果 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 工作流程應用程式嘗試的任何持續性作業，在未使用提供之指令碼進行升級的持續性資料庫上使用新版本功能，就會擲回 <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException>，並顯示類似下列訊息。  
  
 **SqlWorkflowInstanceStore 有 '4.0.0.0' 的資料庫版本。無法對這個資料庫版本執行 InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand'。請升級為 '4.5.0.0' 的資料庫。**  
### <a name="ToUpgrade"></a> 若要升級資料庫結構描述  
  
1.  開啟 SQL Server Management Studio 並連接至持續性資料庫伺服器，例如 **。 \SQLEXPRESS**。  
  
2.  選擇**開放**，**檔案**從**檔案**功能表。 瀏覽至下列資料夾：`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  選取  **SqlWorkflowInstanceStoreSchemaUpgrade.sql**然後按一下**開啟**。  
  
4.  選取持續性資料庫中的名稱**可用的資料庫**下拉式清單。  
  
5.  選擇**Execute**從**查詢**功能表。  
  
 查詢完成時，資料庫結構描述即已升級，若有需要，可以檢視指派給持續性工作流程執行個體的預設工作流程識別。 展開您的持續性資料庫中**資料庫**節點**物件總管**，然後展開**檢視**節點。 以滑鼠右鍵按一下**System.Activities.DurableInstancing.Instances** ，然後選擇**選取前 1000 個資料列**。 捲動到 資料行的結尾，請注意，有六個額外的資料行加入至檢視：**IdentityName**， **IdentityPackage**，**建置**，**主要**，**次要**，以及**修訂**. 任何持續性工作流程會有值**NULL**為這些欄位，表示 null 工作流程識別。
