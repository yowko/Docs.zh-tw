---
title: HOW TO：啟用工作流程與工作流程服務的 SQL 持續性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 55869c3c8a957de98962378cc1a93e7058e24e38
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386730"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>HOW TO：啟用工作流程與工作流程服務的 SQL 持續性

本主題描述如何設定 SQL 工作流程執行個體存放區功能，以程式設計方式或使用組態檔來啟用工作流程與工作流程服務的持續性。  
  
Windows Server App Fabric 會簡化設定持續性的程序。 如需詳細資訊，請參閱[App Fabric 持續性組態](https://go.microsoft.com/fwlink/?LinkId=201204)  
  
使用 SQL 工作流程執行個體存放區功能之前，請建立一個讓此功能用於保存工作流程執行個體的資料庫。 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安裝程式會將與 SQL 工作流程執行個體存放區功能相關聯的 SQL 指令碼檔複製至 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 資料夾。 針對 SQL Server 2005 或 SQL Server 2008 資料庫執行這些指令碼檔，且這個資料庫可供 SQL 工作流程執行個體存放區用來保存工作流程執行個體。 先執行 SqlWorkflowInstanceStoreSchema.sql 檔，然後再執行 SqlWorkflowInstanceStoreLogic.sql 檔。

> [!NOTE]
> 若要清除持續性資料庫來擁有乾淨的資料庫，請依照下列順序執行 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 中的指令碼。  
>
> 1. SqlWorkflowInstanceStoreSchema.sql
> 2. SqlWorkflowInstanceStoreLogic.sql

> [!IMPORTANT]
> 如果您並未建立持續性資料庫，則當主機嘗試保存工作流程時，SQL 工作流程執行個體存放區功能就會擲回與下列其中一個相似的例外狀況。  
> 
> System.Data.SqlClient.SqlException：找不到預存程序 'System.Activities.DurableInstancing.CreateLockOwner'  

下列各節描述如何使用 SQL 工作流程執行個體存放區啟用工作流程與工作流程服務的持續性。 如需 SQL 工作流程執行個體存放區屬性的詳細資訊，請參閱[屬性的 SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)。  

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>啟用使用 WorkflowApplication 之自我裝載工作流程的持續性

您可以使用 <xref:System.Activities.WorkflowApplication> 物件模型，以程式設計方式啟用使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 之自我裝載工作流程的持續性。 下列程序包含執行此作業的步驟。  

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>若要啟用自我裝載工作流程的持續性

1.  加入 System.Activites.DurableInstancing.dll 的參考。  
  
2.  在原始程式檔最上方現有的 "using" 陳述式後方，加入下列陳述式。  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  建構 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 並將它指派給 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 的 <xref:System.Activities.WorkflowApplication>，如下列程式碼範例所示。
  
    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```
  
   > [!NOTE]
   > 依據您的 SQL Server 版本，連接字串伺服器名稱可能有所不同。  
  
4. 叫用 <xref:System.Activities.WorkflowApplication.Persist%2A> 物件上的 <xref:System.Activities.WorkflowApplication> 方法以保存工作流程，或叫用 <xref:System.Activities.WorkflowApplication.Unload%2A> 以保存及卸載工作流程。 您也可以處理由 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 物件引發的 <xref:System.Activities.WorkflowApplication> 事件，並傳回 <xref:System.Activities.PersistableIdleAction.Persist> 的適當 (<xref:System.Activities.PersistableIdleAction.Unload> 或 <xref:System.Activities.PersistableIdleAction>) 成員。  
  
   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> 請參閱[保存工作流程應用程式](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md)範例，以[持續性](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)啟用持續性工作流程使用的範例，如<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，和[How to： 建立及執行長時間執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)的步驟[入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)的逐步指示。  

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>啟用使用 WorkflowServiceHost 之自我裝載工作流程服務的持續性

您可以使用 <xref:System.ServiceModel.WorkflowServiceHost> 類別或 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 類別，啟用以程式設計方式使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 之自我裝載工作流程服務的持續性。  

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>使用 SqlWorkflowInstanceStoreBehavior 類別  

以下程序包含使用 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 類別以啟用自我裝載工作流程服務之持續性的步驟。  

##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>若要啟用使用 SqlWorkflowInstanceStoreBehavior 的持續性

1.  加入 System.ServiceModel.dll 的參考。  
  
2.  在原始程式檔最上方現有的 "using" 陳述式後方，加入下列陳述式。  
  
    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3.  建立 `WorkflowServiceHost` 的執行個體，並加入工作流程服務的端點。  
  
    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ``` 

4.  建構 `SqlWorkflowInstanceStoreBehavior` 物件並設定該行為物件的屬性。  
  
    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5.  開啟工作流程服務主機。

    ```csharp
    host.Open();
    ```

> [!IMPORTANT]
> 請參閱[內建的組態](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md)範例，以[持續性](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)如需啟用工作流程服務使用的持續性的範例`SqlWorkflowInstanceStoreBehavior`類別。  

### <a name="using-the-durableinstancingoptions-property"></a>使用 DurableInstancingOptions 屬性

當套用 `SqlWorkflowInstanceStoreBehavior` 時，會將 `DurableInstancingOptions.InstanceStore` 上的 `WorkflowServiceHost` 設定為使用組態值建立的 `SqlWorkflowInstanceStore` 物件。 您同樣可以使用程式設計方式，在不必使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 類別的情況下，設定 `WorkflowServiceHost` 的 `SqlWorkflowInstanceStoreBehavior` 屬性，如下列程式碼範例所示。  

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>使用組態檔啟用使用 WorkflowServiceHost 之 WAS 裝載工作流程服務的持續性

您可以使用組態檔，啟用自我裝載或 Windows Process Activation Service (WAS) 裝載之工作流程服務的持續性。 WAS 裝載的工作流程服務會使用 WorkflowServiceHost，如同自我裝載的工作流程服務一樣。  
  
`SqlWorkflowInstanceStoreBehavior`，可讓您輕鬆地變更服務行為[SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)透過 XML 組態屬性。 如果是 WAS 裝載的工作流程服務，請使用 Web.config 檔。 下列組態範例示範如何使用組態檔中的 `sqlWorkflowInstanceStore` 行為項目來設定 SQL 工作流程執行個體存放區。  
  
```xml  
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore 
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30" 
                    runnableInstancesDetectionPeriod="00:00:05">

        <sqlWorkflowInstanceStore/>
    </behavior>
</serviceBehaviors>
```
  
如果您並未設定 `connectionString` 或 `connectionStringName` 屬性的值，SQL 工作流程執行個體存放區就會使用預設命名的連接字串 `DefaultSqlWorkflowInstanceStoreConnectionString`。  
  
當套用 `SqlWorkflowInstanceStoreBehavior` 時，會將 `DurableInstancingOptions.InstanceStore` 上的 `WorkflowServiceHost` 設定為使用組態值建立的 `SqlWorkflowInstanceStore` 物件。 您同樣可以使用程式設計方式，在不必使用服務行為項目的情況下，搭配 `SqlWorkflowInstanceStore` 來使用 `WorkflowServiceHost`。  
  
```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```
  
> [!IMPORTANT]
> 建議您不要將敏感資訊 (例如，使用者名稱和密碼) 儲存在 Web.config 檔案中。 如果要將敏感資訊儲存在 Web.config 檔案中，則應使用檔案系統存取控制清單 (ACL) 來保護存取 Web.config 檔的安全性。 此外，您也可以保護的組態檔內組態值中所述[組態加密組態資訊使用受保護的](https://go.microsoft.com/fwlink/?LinkId=178419)。

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>與 SQL 工作流程執行個體存放區功能相關的 Machine.config 項目

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安裝會將下列與 SQL 工作流程執行個體存放區功能相關的項目加入至 Machine.config 檔：  

-   將以下行為延伸項目加入至 Machine.config 檔，這樣您就可以使用組態檔中的 <`sqlWorkflowInstanceStore`> 服務行為項目來設定服務的持續性。

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        <system.serviceModel>
    <configuration>
    ```
