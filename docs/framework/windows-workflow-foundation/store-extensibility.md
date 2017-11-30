---
title: "存放區擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6700fe67d151e78c8b216d93a4cd7098ed6401d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="store-extensibility"></a>存放區擴充性
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 可讓使用者提升應用程式專屬的自訂屬性，用來查詢持續性資料庫中的執行個體。 提升屬性的動作會讓值用於資料庫中的特殊檢視表。 這些提升屬性 (可用於使用者查詢中的屬性) 可以屬於簡單型別 (例如 Int64、GUID、String 及 DateTime)，也可以屬於序列化的二進位型別 (byte[])。  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 類別具有 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> 方法，可讓您將屬性提升為可在查詢中使用的屬性。 下列範例為存放區擴充性的端對端範例。  
  
1.  在這個範例案例中，文件處理 (DP) 應用程式具有工作流程，其中每個工作流程均使用自訂活動來處理文件。 這些工作流程具有一組狀態變數，需要向使用者顯示。 為了達到這個目的，DP 應用程式提供型別 <xref:System.Activities.Persistence.PersistenceParticipant> 的執行個體擴充，可由任何活動用於提供狀態變數。  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  接著新延伸會加入至主機。  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     如需有關加入自訂持續性參與者的詳細資訊，請參閱[持續性參與者](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)範例。  
  
3.  DP 應用程式中的自訂活動擴展中的各種狀態欄位**Execute**方法。  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  當工作流程執行個體達到保存點， **CollectValues**方法**Collectvalues**持續性參與者會將這些屬性儲存至持續性資料集合。  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
    ```  
  
    > [!NOTE]
    >  所有這些屬性會傳遞至**SqlWorkflowInstanceStore**持續性架構會透過**Sqlworkflowinstancestore**集合。  
  
5.  DP 應用程式初始化 SQL 工作流程執行個體存放區，並叫用**升階**來提升這個資料的方法。  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     根據這項提升資訊， **SqlWorkflowInstanceStore**置於的資料行的資料屬性[InstancePromotedProperties](#InstancePromotedProperties)檢視。
  
6.  為了要查詢提升表中的資料子集，DP 應用程式會將自訂檢視加入到提升檢視上方。  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
##  <a name="InstancePromotedProperties"></a>[System.Activities.DurableInstancing.InstancePromotedProperties] 檢視  
  
|資料行名稱|資料行型別|描述|  
|-----------------|-----------------|-----------------|  
|InstanceId|GUID|這項提升所屬的工作流程執行個體。|  
|PromotionName|nvarchar(400)|提升本身的名稱。|  
|Value1, Value2, Value3,..,Value32|sql_variant|受提升之屬性本身的值。 Most SQL 基本資料型別 (長度超過 8000 位元組的二進位 Blob 和字串除外) 均適合 sql_variant。|  
|Value33, Value34, Value35, …, Value64|varbinary(max)|明確宣告為 varbinary(max) 之受提升屬性的值。|
