---
title: "屬性促銷活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd8356927ad7cb4c24cc278fcb901cc543c6d7b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="property-promotion-activity"></a><span data-ttu-id="0714a-102">屬性促銷活動</span><span class="sxs-lookup"><span data-stu-id="0714a-102">Property Promotion Activity</span></span>
<span data-ttu-id="0714a-103">此範例提供了端對端方案，此方案會將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 提升功能直接整合到工作流程撰寫經驗。</span><span class="sxs-lookup"><span data-stu-id="0714a-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="0714a-104">將會提供組態元素、工作流程活動、可簡化使用提升功能之工作流程延伸模組的集合。</span><span class="sxs-lookup"><span data-stu-id="0714a-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="0714a-105">此外，此範例也包含一個簡單的工作流程，可示範如何使用這個集合。</span><span class="sxs-lookup"><span data-stu-id="0714a-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0714a-106">範例只供教育目的之用。</span><span class="sxs-lookup"><span data-stu-id="0714a-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="0714a-107">不能用於實際執行環境，而且從來沒有在實際執行環境中測試過。</span><span class="sxs-lookup"><span data-stu-id="0714a-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="0714a-108">Microsoft 不提供對這些範例的技術支援。</span><span class="sxs-lookup"><span data-stu-id="0714a-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0714a-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="0714a-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="0714a-110">初始化的 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 資料庫</span><span class="sxs-lookup"><span data-stu-id="0714a-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="0714a-111">範例專案</span><span class="sxs-lookup"><span data-stu-id="0714a-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="0714a-112">**PropertyPromotionActivity**專案包含了有關提升特有的組態項目、 工作流程活動和工作流程延伸模組檔案。</span><span class="sxs-lookup"><span data-stu-id="0714a-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="0714a-113">**CounterServiceApplication**專案包含使用的範例工作流程**SqlWorkflowInstanceStorePromotion**專案。</span><span class="sxs-lookup"><span data-stu-id="0714a-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="0714a-114">必須針對 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 資料庫執行的 SQL 指令碼 (PropertyPromotionActivitySQLSample.sql)。</span><span class="sxs-lookup"><span data-stu-id="0714a-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="0714a-115">連結兩個 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 專案的方案檔案 (`PropertyPromotionActivity.sln`)。</span><span class="sxs-lookup"><span data-stu-id="0714a-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="0714a-116">若要設定及執行範例</span><span class="sxs-lookup"><span data-stu-id="0714a-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="0714a-117">初始化工作流程持續性資料庫。</span><span class="sxs-lookup"><span data-stu-id="0714a-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="0714a-118">巡覽至範例目錄 (\WF\Basic\Persistence\PropertyPromotionActivity)，並執行 CreateInstanceStore.cmd。</span><span class="sxs-lookup"><span data-stu-id="0714a-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="0714a-119">如果未提供系統管理員權限，請建立 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="0714a-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="0714a-120">在 SQL Server Management Studio，請移至**安全性**，**登入**。</span><span class="sxs-lookup"><span data-stu-id="0714a-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="0714a-121">以滑鼠右鍵按一下**登入**並建立新的登入。</span><span class="sxs-lookup"><span data-stu-id="0714a-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="0714a-122">將 ACL 使用者加入至 SQL 角色，藉由開啟**資料庫**， **InstanceStore**，**安全性**。</span><span class="sxs-lookup"><span data-stu-id="0714a-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="0714a-123">以滑鼠右鍵按一下**使用者**選取**新使用者**。</span><span class="sxs-lookup"><span data-stu-id="0714a-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="0714a-124">設定**登入名稱**上面建立的使用者。</span><span class="sxs-lookup"><span data-stu-id="0714a-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="0714a-125">將使用者加入至資料庫角色成員資格 System.Activities.DurableInstancing.InstanceStoreUsers (和其他成員資格)。</span><span class="sxs-lookup"><span data-stu-id="0714a-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="0714a-126">請注意，使用者可能已存在 (例如 dbo 使用者)。</span><span class="sxs-lookup"><span data-stu-id="0714a-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="0714a-127">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 PropertyPromotionActivity.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="0714a-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="0714a-128">如果您在 SQL Server Express 本機安裝以外的資料庫中建立執行個體存放區，您必須更新資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="0714a-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="0714a-129">更改 App.config 檔案下的**CounterServiceApplication**所設定的值`connectionString`屬性`sqlWorkflowInstanceStorePromotion`節點，讓它指向已初始化的持續性資料庫中步驟 1。</span><span class="sxs-lookup"><span data-stu-id="0714a-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="0714a-130">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="0714a-130">Build and run the solution.</span></span> <span data-ttu-id="0714a-131">這樣會啟動計數器 WF 服務，並自動啟動工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="0714a-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="0714a-132">在持續性資料庫中快速選取 [dbo].[CounterService] 檢視表中的所有資料列 (這個檢視表是藉由執行步驟 1 的 CreateInstanceStore.cmd 所加入)。</span><span class="sxs-lookup"><span data-stu-id="0714a-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="0714a-133">您將會看到類似下面的結果集：</span><span class="sxs-lookup"><span data-stu-id="0714a-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="0714a-134">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0714a-134">InstanceId</span></span>|<span data-ttu-id="0714a-135">CounterValue</span><span class="sxs-lookup"><span data-stu-id="0714a-135">CounterValue</span></span>|<span data-ttu-id="0714a-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="0714a-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="0714a-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="0714a-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="0714a-138">12</span><span class="sxs-lookup"><span data-stu-id="0714a-138">12</span></span>|<span data-ttu-id="0714a-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="0714a-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="0714a-140">在您持續重新整理檢視表時，您會注意到 CounterValue 和 CounterValueLastUpdated 每隔兩秒鐘就會變更。</span><span class="sxs-lookup"><span data-stu-id="0714a-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="0714a-141">這是計數器更新自己的間隔。</span><span class="sxs-lookup"><span data-stu-id="0714a-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="0714a-142">CounterValue 和 CounterValueLastUpdated 代表這個工作流程的提升屬性。</span><span class="sxs-lookup"><span data-stu-id="0714a-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="0714a-143">若要移除範例</span><span class="sxs-lookup"><span data-stu-id="0714a-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="0714a-144">執行範例目錄 (\WF\Basic\Persistence\PropertyPromotionActivity) 中的 RemoveInstanceStore.cmd。</span><span class="sxs-lookup"><span data-stu-id="0714a-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="0714a-145">了解這個範例</span><span class="sxs-lookup"><span data-stu-id="0714a-145">Understanding This Sample</span></span>  
 <span data-ttu-id="0714a-146">此範例包含兩個專案和一個 SQL 檔案：</span><span class="sxs-lookup"><span data-stu-id="0714a-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="0714a-147">**CounterServiceApplication**是裝載簡單計數器 WF 服務的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0714a-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="0714a-148">一旦透過 `Start` 端點收到單向訊息之後，工作流程就會從 0 開始算到 29，每隔兩秒鐘累加計數器變數。</span><span class="sxs-lookup"><span data-stu-id="0714a-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="0714a-149">在每次累加計數器之後，工作流程會保存而提升屬性則會在 [dbo].[CounterService] 檢視表中更新。</span><span class="sxs-lookup"><span data-stu-id="0714a-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="0714a-150">當執行主控台應用程式時，它會裝載 WF 服務並將訊息傳送給 `Start` 端點，以建立計數器 WF 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0714a-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="0714a-151">**PropertyPromotionActivity**是一個類別庫包含組態項目、 工作流程活動和工作流程延伸模組， **CounterServiceApplication**使用。</span><span class="sxs-lookup"><span data-stu-id="0714a-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="0714a-152">**PropertyPromotionActivitySQLSample.sql**建立，並將檢視 [dbo]。 [CounterService] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0714a-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="0714a-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="0714a-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="0714a-154">使用 SqlWorkflowInstanceStorePromotion 組態元素</span><span class="sxs-lookup"><span data-stu-id="0714a-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="0714a-155">`SqlWorkflowInstanceStorePromotion` 組態元素繼承自 `SqlWorkflowInstanceStore` 組態元素，而且會加入稱為 `promotionSets` 的其他組態元素。</span><span class="sxs-lookup"><span data-stu-id="0714a-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="0714a-156">`promotionSets` 元素可讓使用者透過組態指定提升屬性。</span><span class="sxs-lookup"><span data-stu-id="0714a-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="0714a-157">這是範例所使用的組態檔：</span><span class="sxs-lookup"><span data-stu-id="0714a-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="0714a-158">檢查 [dbo].[CounterService] 檢視表的定義。</span><span class="sxs-lookup"><span data-stu-id="0714a-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="0714a-159">當保存工作流程執行個體時，將會針對組態中定義的每一個 `InstancePromotedProperties`，將一個資料列插入 `PromotionSet` 檢視表中。</span><span class="sxs-lookup"><span data-stu-id="0714a-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="0714a-160">這個資料列包含 `PromotionSet` 的所有提升屬性 (一個資料行一個提升屬性)。</span><span class="sxs-lookup"><span data-stu-id="0714a-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="0714a-161">這個 `PromotionSet` 是由 Tuple 當做索引鍵：`InstanceId, PromotionName`。</span><span class="sxs-lookup"><span data-stu-id="0714a-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="0714a-162">在此範例中，組態中已定義一個 `PromotionSet`，而它的名稱屬性為 `CounterService`。</span><span class="sxs-lookup"><span data-stu-id="0714a-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="0714a-163">請注意，`PromotionName` 資料行值為何等於 `PromotionSet` 元素的名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="0714a-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="0714a-164">`promotedValue` 元素的順序與提升屬性在 `InstancePromotedProperties` 檢視中的位置相關。</span><span class="sxs-lookup"><span data-stu-id="0714a-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="0714a-165">`Count` 是第一個 `promotedValue` 元素。</span><span class="sxs-lookup"><span data-stu-id="0714a-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="0714a-166">因此，它會對應到 `Value1` 檢視表中的 `InstancePromotedProperties` 資料行。</span><span class="sxs-lookup"><span data-stu-id="0714a-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="0714a-167">`LastIncrementedAt` 是第二個 `promotedValue` 元素。</span><span class="sxs-lookup"><span data-stu-id="0714a-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="0714a-168">因此，它會對應到 `Value2` 檢視表中的 `InstancePromotedProperties` 資料行。</span><span class="sxs-lookup"><span data-stu-id="0714a-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="0714a-169">使用 PromoteValue 活動</span><span class="sxs-lookup"><span data-stu-id="0714a-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="0714a-170">在 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] 設計工具中檢查 CounterService.xamlx 檔案。</span><span class="sxs-lookup"><span data-stu-id="0714a-170">Examine the CounterService.xamlx file in the [!INCLUDE[wf2](../../../../includes/wf2-md.md)] Designer.</span></span> <span data-ttu-id="0714a-171">請注意 WF 定義中有兩個特殊活動：`PromoteValue<DateTime>` 和 `PromoteValue<Int32>`。</span><span class="sxs-lookup"><span data-stu-id="0714a-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="0714a-172">`PromoteValue<Int32>` 活動將它的 `Name` 成員定義為 `Count`。</span><span class="sxs-lookup"><span data-stu-id="0714a-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="0714a-173">這會符合組態中的第一個 `promotedValue` 元素，並將其 `Value` 定義為 `Counter` 工作流程變數。</span><span class="sxs-lookup"><span data-stu-id="0714a-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="0714a-174">當保存此工作流程時，`Counter` 工作流程變數會當做提升屬性保存到 `Value1` 檢視表的 `InstancePromotedProperties` 資料行中。</span><span class="sxs-lookup"><span data-stu-id="0714a-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="0714a-175">`PromoteValue<DateTime>` 活動將它的 `Name` 成員定義為 `LastIncrementedAt`。</span><span class="sxs-lookup"><span data-stu-id="0714a-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="0714a-176">這會符合組態中的第二個 `promotedValue` 元素，並將其 `Value` 定義為 `TimeLastIncremented` 工作流程變數。</span><span class="sxs-lookup"><span data-stu-id="0714a-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="0714a-177">這表示當保存此工作流程時，`TimeLastIncremented` 工作流程變數的值將會當做提升屬性保存到 `Value2` 檢視表的 `InstancePromotedProperties` 資料行中。</span><span class="sxs-lookup"><span data-stu-id="0714a-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="0714a-178">請注意，`PromotedValue` 活動也有一個名為 `ClearExistingPromotedData` 的布林成員。</span><span class="sxs-lookup"><span data-stu-id="0714a-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="0714a-179">當這個成員設定為 `true` 時，這會在工作流程中清除到該點為止的所有提升屬性值。</span><span class="sxs-lookup"><span data-stu-id="0714a-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="0714a-180">例如，如果序列活動定義如下：</span><span class="sxs-lookup"><span data-stu-id="0714a-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="0714a-181">PromoteValue {Name ="Count"，值 = 3}</span><span class="sxs-lookup"><span data-stu-id="0714a-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="0714a-182">PromoteValue {Name ="LastIncrementedAt"，值 = 1-1-2000年}</span><span class="sxs-lookup"><span data-stu-id="0714a-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="0714a-183">保存</span><span class="sxs-lookup"><span data-stu-id="0714a-183">Persist</span></span>  
  
4.  <span data-ttu-id="0714a-184">PromoteValue {Name ="Count"，值 = 4，ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="0714a-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="0714a-185">保存</span><span class="sxs-lookup"><span data-stu-id="0714a-185">Persist</span></span>  
  
 <span data-ttu-id="0714a-186">在第二個保存中，`Count` 的提升值將會是 4。</span><span class="sxs-lookup"><span data-stu-id="0714a-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="0714a-187">不過的提升的值`LastIncrementedAt`將`NULL`。</span><span class="sxs-lookup"><span data-stu-id="0714a-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="0714a-188">如果 `ClearExistingPromotedData` 在步驟 4 未設定為 `true`，則在第二個保存之後，Count 的提升值會是 4。</span><span class="sxs-lookup"><span data-stu-id="0714a-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="0714a-189">因此，`LastIncrementedAt` 的提升值仍然是 1-1-2000。</span><span class="sxs-lookup"><span data-stu-id="0714a-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="0714a-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="0714a-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="0714a-191">此類別庫包含下列公用類別，以簡化 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 提升功能的使用。</span><span class="sxs-lookup"><span data-stu-id="0714a-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="0714a-192">PromoteValue 類別</span><span class="sxs-lookup"><span data-stu-id="0714a-192">PromoteValue Class</span></span>  
 <span data-ttu-id="0714a-193">這個類別會提升一個屬性。</span><span class="sxs-lookup"><span data-stu-id="0714a-193">This class promotes one property.</span></span> <span data-ttu-id="0714a-194">提升屬性 (Property) 的名稱應該符合組態中 `promotedValue` 元素的名稱屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="0714a-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="0714a-195">這個活動可在工作流程設計工具中使用。</span><span class="sxs-lookup"><span data-stu-id="0714a-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="0714a-196">請參閱 CounterServiceApplication 以了解範例的使用。</span><span class="sxs-lookup"><span data-stu-id="0714a-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="0714a-197">ClearExistingPromotedData (Bool)</span><span class="sxs-lookup"><span data-stu-id="0714a-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="0714a-198">清除在這個活動之前提升的所有值。</span><span class="sxs-lookup"><span data-stu-id="0714a-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="0714a-199">Name (string)</span><span class="sxs-lookup"><span data-stu-id="0714a-199">Name (string)</span></span>  
 <span data-ttu-id="0714a-200">代表這個屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="0714a-200">The name that represents this property.</span></span> <span data-ttu-id="0714a-201">這應該符合的名稱屬性\<promotedValue > 組態中的項目。</span><span class="sxs-lookup"><span data-stu-id="0714a-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="0714a-202">值 (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="0714a-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="0714a-203">您想要儲存在資料行中的變數 / 值。</span><span class="sxs-lookup"><span data-stu-id="0714a-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="0714a-204">PromoteValues 類別</span><span class="sxs-lookup"><span data-stu-id="0714a-204">PromoteValues Class</span></span>  
 <span data-ttu-id="0714a-205">提升多個屬性。</span><span class="sxs-lookup"><span data-stu-id="0714a-205">Promotes multiple properties.</span></span> <span data-ttu-id="0714a-206">提升屬性 (Property) 的名稱應該符合組態中 `promotedValue` 元素內的所有名稱屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="0714a-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="0714a-207">其用法類似於 `PromoteValue` 活動，除了多個屬性將會同時提升的事實以外。</span><span class="sxs-lookup"><span data-stu-id="0714a-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="0714a-208">這個活動不能在工作流程設計工具中使用。</span><span class="sxs-lookup"><span data-stu-id="0714a-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="0714a-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="0714a-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="0714a-210">衍生自 `SqlWorkflowInstanceStoreBehavior`。</span><span class="sxs-lookup"><span data-stu-id="0714a-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="0714a-211">這個衍生類別會加入自訂持續性參與者 (也是這個程式庫的一部分) 當做工作流程延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0714a-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="0714a-212">之前兩個工作流程活動的實作取決於這個自訂持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="0714a-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="0714a-213">此類別庫也包含 `ConfigurationElement` 的 `SqlWorkflowInstanceStorePromotionElement` 實作，以及之前的提升活動所使用的自訂持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="0714a-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="0714a-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="0714a-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="0714a-215">這個 SQL 檔案除了 `[dbo].[CounterService]` 檢視表以外也會建立 `[InstancePromotedProperties]` 檢視表，以便查詢已設定 CounterService Promotion 的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="0714a-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0714a-216">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0714a-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0714a-217">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="0714a-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0714a-218">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="0714a-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0714a-219">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="0714a-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="0714a-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0714a-220">See Also</span></span>  
 [<span data-ttu-id="0714a-221">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="0714a-221">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
