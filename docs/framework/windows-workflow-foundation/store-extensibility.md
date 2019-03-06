---
title: 存放區擴充性
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 8f317e8e0864dd6c4595ac669611594c843b277c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375424"
---
# <a name="store-extensibility"></a><span data-ttu-id="7f82b-102">存放區擴充性</span><span class="sxs-lookup"><span data-stu-id="7f82b-102">Store Extensibility</span></span>
<span data-ttu-id="7f82b-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 可讓使用者提升應用程式專屬的自訂屬性，用來查詢持續性資料庫中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f82b-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="7f82b-104">提升屬性的動作會讓值用於資料庫中的特殊檢視表。</span><span class="sxs-lookup"><span data-stu-id="7f82b-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="7f82b-105">這些提升屬性 (可用於使用者查詢中的屬性) 可以屬於簡單型別 (例如 Int64、GUID、String 及 DateTime)，也可以屬於序列化的二進位型別 (byte[])。</span><span class="sxs-lookup"><span data-stu-id="7f82b-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="7f82b-106"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 類別具有 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> 方法，可讓您將屬性提升為可在查詢中使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="7f82b-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="7f82b-107">下列範例為存放區擴充性的端對端範例。</span><span class="sxs-lookup"><span data-stu-id="7f82b-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="7f82b-108">在這個範例案例中，文件處理 (DP) 應用程式具有工作流程，其中每個工作流程均使用自訂活動來處理文件。</span><span class="sxs-lookup"><span data-stu-id="7f82b-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="7f82b-109">這些工作流程具有一組狀態變數，需要向使用者顯示。</span><span class="sxs-lookup"><span data-stu-id="7f82b-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="7f82b-110">為了達到這個目的，DP 應用程式提供型別 <xref:System.Activities.Persistence.PersistenceParticipant> 的執行個體擴充，可由任何活動用於提供狀態變數。</span><span class="sxs-lookup"><span data-stu-id="7f82b-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="7f82b-111">接著新延伸會加入至主機。</span><span class="sxs-lookup"><span data-stu-id="7f82b-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="7f82b-112">如需有關加入自訂持續性參與者的詳細資訊，請參閱 <<c0> [ 持續性參與者](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)範例。</span><span class="sxs-lookup"><span data-stu-id="7f82b-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="7f82b-113">DP 應用程式中的自訂活動填入中的各種狀態欄位**Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="7f82b-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
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
  
4.  <span data-ttu-id="7f82b-114">當工作流程執行個體達到保存點， **CollectValues**方法**Collectvalues**持續性參與者會將這些屬性儲存至持續性資料集合。</span><span class="sxs-lookup"><span data-stu-id="7f82b-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
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
    >  <span data-ttu-id="7f82b-115">所有這些屬性會傳遞給**SqlWorkflowInstanceStore**持續性架構會透過**Sqlworkflowinstancestore**集合。</span><span class="sxs-lookup"><span data-stu-id="7f82b-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="7f82b-116">DP 應用程式初始化 SQL 工作流程執行個體存放區，並叫用**升階**來提升這個資料的方法。</span><span class="sxs-lookup"><span data-stu-id="7f82b-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
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
  
     <span data-ttu-id="7f82b-117">根據這項提升資訊， **SqlWorkflowInstanceStore**將資料屬性的資料行中放[InstancePromotedProperties](#InstancePromotedProperties)檢視。</span><span class="sxs-lookup"><span data-stu-id="7f82b-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="7f82b-118">為了要查詢提升表中的資料子集，DP 應用程式會將自訂檢視加入到提升檢視上方。</span><span class="sxs-lookup"><span data-stu-id="7f82b-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
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
  
## <a name="InstancePromotedProperties"></a> <span data-ttu-id="7f82b-119">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span><span class="sxs-lookup"><span data-stu-id="7f82b-119">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="7f82b-120">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="7f82b-120">Column Name</span></span>|<span data-ttu-id="7f82b-121">資料行型別</span><span class="sxs-lookup"><span data-stu-id="7f82b-121">Column Type</span></span>|<span data-ttu-id="7f82b-122">描述</span><span class="sxs-lookup"><span data-stu-id="7f82b-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="7f82b-123">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f82b-123">InstanceId</span></span>|<span data-ttu-id="7f82b-124">GUID</span><span class="sxs-lookup"><span data-stu-id="7f82b-124">GUID</span></span>|<span data-ttu-id="7f82b-125">這項提升所屬的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f82b-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="7f82b-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="7f82b-126">PromotionName</span></span>|<span data-ttu-id="7f82b-127">nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="7f82b-127">nvarchar(400)</span></span>|<span data-ttu-id="7f82b-128">提升本身的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f82b-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="7f82b-129">Value1, Value2, Value3,..,Value32</span><span class="sxs-lookup"><span data-stu-id="7f82b-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="7f82b-130">sql_variant</span><span class="sxs-lookup"><span data-stu-id="7f82b-130">sql_variant</span></span>|<span data-ttu-id="7f82b-131">受提升之屬性本身的值。</span><span class="sxs-lookup"><span data-stu-id="7f82b-131">The value of the promoted property itself.</span></span> <span data-ttu-id="7f82b-132">Most SQL 基本資料型別 (長度超過 8000 位元組的二進位 Blob 和字串除外) 均適合 sql_variant。</span><span class="sxs-lookup"><span data-stu-id="7f82b-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="7f82b-133">Value33, Value34, Value35, …, Value64</span><span class="sxs-lookup"><span data-stu-id="7f82b-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="7f82b-134">varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="7f82b-134">varbinary(max)</span></span>|<span data-ttu-id="7f82b-135">明確宣告為 varbinary(max) 之受提升屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7f82b-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
