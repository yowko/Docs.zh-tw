---
title: 常見問題集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 4b06ebd5b77331d63fc250a91a72c553ec2b737f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950350"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="74283-102">常見問題集</span><span class="sxs-lookup"><span data-stu-id="74283-102">Frequently Asked Questions</span></span>
<span data-ttu-id="74283-103">下列各節將解答實作 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 時可能會遇到的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="74283-103">The following sections answer some common issues that you might encounter when you implement [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="74283-104">[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)中有其他問題可解決。</span><span class="sxs-lookup"><span data-stu-id="74283-104">Additional issues are addressed in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="cannot-connect"></a><span data-ttu-id="74283-105">無法連接</span><span class="sxs-lookup"><span data-stu-id="74283-105">Cannot Connect</span></span>  
 <span data-ttu-id="74283-106">問：</span><span class="sxs-lookup"><span data-stu-id="74283-106">Q.</span></span> <span data-ttu-id="74283-107">我無法連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="74283-107">I cannot connect to my database.</span></span>  
  
 <span data-ttu-id="74283-108">答：</span><span class="sxs-lookup"><span data-stu-id="74283-108">A.</span></span> <span data-ttu-id="74283-109">請確定您的連接字串正確, 且您的 SQL Server 實例正在執行。</span><span class="sxs-lookup"><span data-stu-id="74283-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="74283-110">另外也請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 需要具名管道 (Named Pipe) 通訊協定才能啟用。</span><span class="sxs-lookup"><span data-stu-id="74283-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="74283-111">如需詳細資訊, 請參閱[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-111">For more information, see [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
## <a name="changes-to-database-lost"></a><span data-ttu-id="74283-112">遺失對資料庫所做的變更</span><span class="sxs-lookup"><span data-stu-id="74283-112">Changes to Database Lost</span></span>  
 <span data-ttu-id="74283-113">問：</span><span class="sxs-lookup"><span data-stu-id="74283-113">Q.</span></span> <span data-ttu-id="74283-114">我變更了資料庫中的資料，但重新執行應用程式時，變更不見了。</span><span class="sxs-lookup"><span data-stu-id="74283-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>  
  
 <span data-ttu-id="74283-115">答：</span><span class="sxs-lookup"><span data-stu-id="74283-115">A.</span></span> <span data-ttu-id="74283-116">請確定您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 來儲存結果到資料庫。</span><span class="sxs-lookup"><span data-stu-id="74283-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>  
  
## <a name="database-connection-open-how-long"></a><span data-ttu-id="74283-117">資料庫連接:要開啟多久？</span><span class="sxs-lookup"><span data-stu-id="74283-117">Database Connection: Open How Long?</span></span>  
 <span data-ttu-id="74283-118">問：</span><span class="sxs-lookup"><span data-stu-id="74283-118">Q.</span></span> <span data-ttu-id="74283-119">我的資料庫連接會維持開啟的狀態多久？</span><span class="sxs-lookup"><span data-stu-id="74283-119">How long does my database connection remain open?</span></span>  
  
 <span data-ttu-id="74283-120">答：</span><span class="sxs-lookup"><span data-stu-id="74283-120">A.</span></span> <span data-ttu-id="74283-121">連接通常會一直維持開啟的狀態，直到您使用查詢結果為止。</span><span class="sxs-lookup"><span data-stu-id="74283-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="74283-122">如果您預期會花時間處理所有結果，而且也不反對快取結果，請將 <xref:System.Linq.Enumerable.ToList%2A> 套用到查詢。</span><span class="sxs-lookup"><span data-stu-id="74283-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="74283-123">在每個物件只處理一次的常見情況中，在 `DataReader` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中使用資料流 (Streaming) 模型較有利。</span><span class="sxs-lookup"><span data-stu-id="74283-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="74283-124">連接使用方式的確切詳細資訊會取決於下列各項：</span><span class="sxs-lookup"><span data-stu-id="74283-124">The exact details of connection usage depend on the following:</span></span>  
  
- <span data-ttu-id="74283-125">連接狀態 (如果 <xref:System.Data.Linq.DataContext> 是使用連接物件建構的)。</span><span class="sxs-lookup"><span data-stu-id="74283-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>  
  
- <span data-ttu-id="74283-126">連接字串設定 (例如，啟用 Multiple Active Result Set (MARS)。</span><span class="sxs-lookup"><span data-stu-id="74283-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="74283-127">如需詳細資訊，請參閱 [Multiple Active Result Sets (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-127">For more information, see [Multiple Active Result Sets (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).</span></span>  
  
## <a name="updating-without-querying"></a><span data-ttu-id="74283-128">更新但不查詢</span><span class="sxs-lookup"><span data-stu-id="74283-128">Updating Without Querying</span></span>  
 <span data-ttu-id="74283-129">問：</span><span class="sxs-lookup"><span data-stu-id="74283-129">Q.</span></span> <span data-ttu-id="74283-130">我可以不先查詢資料庫，就更新資料表資料嗎？</span><span class="sxs-lookup"><span data-stu-id="74283-130">Can I update table data without first querying the database?</span></span>  
  
 <span data-ttu-id="74283-131">答：</span><span class="sxs-lookup"><span data-stu-id="74283-131">A.</span></span> <span data-ttu-id="74283-132">雖然 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 沒有以設定為基礎的更新命令，不過您可以使用下列其中一種方式，就可以不先查詢即更新。</span><span class="sxs-lookup"><span data-stu-id="74283-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>  
  
- <span data-ttu-id="74283-133">使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 傳送 SQL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="74283-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>  
  
- <span data-ttu-id="74283-134">建立物件的新執行個體，然後初始化所有影響更新的目前值 (欄位)。</span><span class="sxs-lookup"><span data-stu-id="74283-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="74283-135">接著使用 <xref:System.Data.Linq.DataContext> 附加物件至 <xref:System.Data.Linq.Table%601.Attach%2A>，然後修改要變更的欄位。</span><span class="sxs-lookup"><span data-stu-id="74283-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>  
  
## <a name="unexpected-query-results"></a><span data-ttu-id="74283-136">未預期的查詢結果</span><span class="sxs-lookup"><span data-stu-id="74283-136">Unexpected Query Results</span></span>  
 <span data-ttu-id="74283-137">問：</span><span class="sxs-lookup"><span data-stu-id="74283-137">Q.</span></span> <span data-ttu-id="74283-138">我的查詢傳回未預期的結果。</span><span class="sxs-lookup"><span data-stu-id="74283-138">My query is returning unexpected results.</span></span> <span data-ttu-id="74283-139">我該如何檢查發生了什麼狀況？</span><span class="sxs-lookup"><span data-stu-id="74283-139">How can I inspect what is occurring?</span></span>  
  
 <span data-ttu-id="74283-140">答：</span><span class="sxs-lookup"><span data-stu-id="74283-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="74283-141">提供多項工具來檢查它所產生的 SQL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="74283-141">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="74283-142">最重要的其中一項工具就是 <xref:System.Data.Linq.DataContext.Log%2A>。</span><span class="sxs-lookup"><span data-stu-id="74283-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="74283-143">如需詳細資訊, 請參閱[偵錯工具支援](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-143">For more information, see [Debugging Support](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).</span></span>  
  
## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="74283-144">未預期的預存程序結果</span><span class="sxs-lookup"><span data-stu-id="74283-144">Unexpected Stored Procedure Results</span></span>  
 <span data-ttu-id="74283-145">問：</span><span class="sxs-lookup"><span data-stu-id="74283-145">Q.</span></span> <span data-ttu-id="74283-146">我有一個預存程序，它的傳回值是由 `MAX()` 計算的。</span><span class="sxs-lookup"><span data-stu-id="74283-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="74283-147">當我將預存程式拖曳至 O/R 設計工具介面時, 傳回值不正確。</span><span class="sxs-lookup"><span data-stu-id="74283-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>  
  
 <span data-ttu-id="74283-148">答：</span><span class="sxs-lookup"><span data-stu-id="74283-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="74283-149">提供兩種方式來藉由預存程序傳回資料庫產生的值。</span><span class="sxs-lookup"><span data-stu-id="74283-149">provides two ways to return database-generated values by way of stored procedures:</span></span>  
  
- <span data-ttu-id="74283-150">藉由命名輸出結果。</span><span class="sxs-lookup"><span data-stu-id="74283-150">By naming the output result.</span></span>  
  
- <span data-ttu-id="74283-151">藉由明確指定輸出參數。</span><span class="sxs-lookup"><span data-stu-id="74283-151">By explicitly specifying an output parameter.</span></span>  
  
 <span data-ttu-id="74283-152">下面是輸出不正確的範例。</span><span class="sxs-lookup"><span data-stu-id="74283-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="74283-153">由於 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法對應結果，因此永遠會傳回 0：</span><span class="sxs-lookup"><span data-stu-id="74283-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 <span data-ttu-id="74283-154">下面是使用輸出參數時，輸出正確的範例：</span><span class="sxs-lookup"><span data-stu-id="74283-154">The following is an example of correct output by using an output parameter:</span></span>  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 <span data-ttu-id="74283-155">下面是藉由命名輸出結果，輸出正確的範例：</span><span class="sxs-lookup"><span data-stu-id="74283-155">The following is an example of correct output by naming the output result:</span></span>  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 <span data-ttu-id="74283-156">如需詳細資訊, 請參閱[使用預存程式自訂作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-156">For more information, see [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).</span></span>  
  
## <a name="serialization-errors"></a><span data-ttu-id="74283-157">序列化錯誤</span><span class="sxs-lookup"><span data-stu-id="74283-157">Serialization Errors</span></span>  
 <span data-ttu-id="74283-158">問：</span><span class="sxs-lookup"><span data-stu-id="74283-158">Q.</span></span> <span data-ttu-id="74283-159">當我嘗試序列化時, 收到下列錯誤:"ChangeTracker + 別 standardchangetracker" 的 "Type..。未標示為可序列化。」</span><span class="sxs-lookup"><span data-stu-id="74283-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>  
  
 <span data-ttu-id="74283-160">答：</span><span class="sxs-lookup"><span data-stu-id="74283-160">A.</span></span> <span data-ttu-id="74283-161">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的程式碼產生支援 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="74283-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="74283-162">但不支援 <xref:System.Xml.Serialization.XmlSerializer> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>。</span><span class="sxs-lookup"><span data-stu-id="74283-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="74283-163">如需詳細資訊，請參閱[序列化](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-163">For more information, see [Serialization](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>  
  
## <a name="multiple-dbml-files"></a><span data-ttu-id="74283-164">多個 DBML 檔案</span><span class="sxs-lookup"><span data-stu-id="74283-164">Multiple DBML Files</span></span>  
 <span data-ttu-id="74283-165">問：</span><span class="sxs-lookup"><span data-stu-id="74283-165">Q.</span></span> <span data-ttu-id="74283-166">當有多個 DBML 檔案共用一些資料表時，會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="74283-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>  
  
 <span data-ttu-id="74283-167">答：</span><span class="sxs-lookup"><span data-stu-id="74283-167">A.</span></span> <span data-ttu-id="74283-168">將 [**內容命名空間**] 和 [**實體命名空間**] 屬性從物件關聯式設計工具設定為每個 DBML 檔案的相異值。</span><span class="sxs-lookup"><span data-stu-id="74283-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="74283-169">這就可避免名稱/命名空間發生衝突。</span><span class="sxs-lookup"><span data-stu-id="74283-169">This approach eliminates the name/namespace collision.</span></span>  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="74283-170">避免在插入或更新時明確設定資料庫產生的值</span><span class="sxs-lookup"><span data-stu-id="74283-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>  
 <span data-ttu-id="74283-171">問：</span><span class="sxs-lookup"><span data-stu-id="74283-171">Q.</span></span> <span data-ttu-id="74283-172">我的資料庫資料表有個 `DateCreated` 資料行，它預設為 SQL `Getdate()`。</span><span class="sxs-lookup"><span data-stu-id="74283-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="74283-173">當我嘗試使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 插入新的資料錄時，值會設成 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="74283-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="74283-174">但我本來預期它會設成資料庫預設值。</span><span class="sxs-lookup"><span data-stu-id="74283-174">I would expect it to be set to the database default.</span></span>  
  
 <span data-ttu-id="74283-175">答：</span><span class="sxs-lookup"><span data-stu-id="74283-175">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="74283-176">會自動針對識別 (自動遞增)、rowguidcol (資料庫產生的 GUID) 和時間戳記資料行處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="74283-176">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="74283-177">在其他情況下, 您應該手動<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>設定<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = `true` =和<xref:System.Data.Linq.Mapping.AutoSync.Always> / 屬性。/ <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate></span><span class="sxs-lookup"><span data-stu-id="74283-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>  
  
## <a name="multiple-dataloadoptions"></a><span data-ttu-id="74283-178">多個 DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="74283-178">Multiple DataLoadOptions</span></span>  
 <span data-ttu-id="74283-179">問：</span><span class="sxs-lookup"><span data-stu-id="74283-179">Q.</span></span> <span data-ttu-id="74283-180">我可以指定其他載入選項，而不覆寫第一個載入選項嗎？</span><span class="sxs-lookup"><span data-stu-id="74283-180">Can I specify additional load options without overwriting the first?</span></span>  
  
 <span data-ttu-id="74283-181">答：</span><span class="sxs-lookup"><span data-stu-id="74283-181">A.</span></span> <span data-ttu-id="74283-182">是的。</span><span class="sxs-lookup"><span data-stu-id="74283-182">Yes.</span></span> <span data-ttu-id="74283-183">如下列範例所示，第一個選項不會被覆寫：</span><span class="sxs-lookup"><span data-stu-id="74283-183">The first is not overwritten, as in the following example:</span></span>  
  
```vb  
Dim dlo As New DataLoadOptions()  
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)  
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)  
```  
  
```csharp  
DataLoadOptions dlo = new DataLoadOptions();  
dlo.LoadWith<Order>(o => o.Customer);  
dlo.LoadWith<Order>(o => o.OrderDetails);  
```  
  
## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="74283-184">使用 SQL Compact 3.5 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="74283-184">Errors Using SQL Compact 3.5</span></span>  
 <span data-ttu-id="74283-185">問：</span><span class="sxs-lookup"><span data-stu-id="74283-185">Q.</span></span> <span data-ttu-id="74283-186">當我將資料表從 SQL Server Compact 3.5 資料庫拖曳出來時, 出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="74283-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>  
  
 <span data-ttu-id="74283-187">答：</span><span class="sxs-lookup"><span data-stu-id="74283-187">A.</span></span> <span data-ttu-id="74283-188">雖然[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]執行時間會執行, 但物件關聯式設計工具不支援 SQL Server Compact 3.5。</span><span class="sxs-lookup"><span data-stu-id="74283-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="74283-189">在此情況下，您必須建立自己的實體類別，然後加入適當的屬性。</span><span class="sxs-lookup"><span data-stu-id="74283-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>  
  
## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="74283-190">繼承關係發生錯誤</span><span class="sxs-lookup"><span data-stu-id="74283-190">Errors in Inheritance Relationships</span></span>  
 <span data-ttu-id="74283-191">問：</span><span class="sxs-lookup"><span data-stu-id="74283-191">Q.</span></span> <span data-ttu-id="74283-192">我使用物件關聯式設計工具中的 [工具箱繼承] 圖形來連接兩個實體, 但卻收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="74283-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>  
  
 <span data-ttu-id="74283-193">答：</span><span class="sxs-lookup"><span data-stu-id="74283-193">A.</span></span> <span data-ttu-id="74283-194">光是建立關係還不夠。</span><span class="sxs-lookup"><span data-stu-id="74283-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="74283-195">您還必須提供資訊，例如鑑別子資料行、基底類別鑑別子值以及衍生類別鑑別子值。</span><span class="sxs-lookup"><span data-stu-id="74283-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>  
  
## <a name="provider-model"></a><span data-ttu-id="74283-196">提供者模型</span><span class="sxs-lookup"><span data-stu-id="74283-196">Provider Model</span></span>  
 <span data-ttu-id="74283-197">問：</span><span class="sxs-lookup"><span data-stu-id="74283-197">Q.</span></span> <span data-ttu-id="74283-198">是否有公用提供者模型可供使用？</span><span class="sxs-lookup"><span data-stu-id="74283-198">Is a public provider model available?</span></span>  
  
 <span data-ttu-id="74283-199">答：</span><span class="sxs-lookup"><span data-stu-id="74283-199">A.</span></span> <span data-ttu-id="74283-200">沒有公用提供者模型可以使用。</span><span class="sxs-lookup"><span data-stu-id="74283-200">No public provider model is available.</span></span> <span data-ttu-id="74283-201">目前僅[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援 SQL Server 和 SQL Server Compact 3.5。</span><span class="sxs-lookup"><span data-stu-id="74283-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>  
  
## <a name="sql-injection-attacks"></a><span data-ttu-id="74283-202">SQL 插入攻擊</span><span class="sxs-lookup"><span data-stu-id="74283-202">SQL-Injection Attacks</span></span>  
 <span data-ttu-id="74283-203">問：</span><span class="sxs-lookup"><span data-stu-id="74283-203">Q.</span></span> <span data-ttu-id="74283-204">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何保護不受 SQL 插入攻擊？</span><span class="sxs-lookup"><span data-stu-id="74283-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>  
  
 <span data-ttu-id="74283-205">答：</span><span class="sxs-lookup"><span data-stu-id="74283-205">A.</span></span> <span data-ttu-id="74283-206">對於以串連使用者輸入形成的傳統 SQL 查詢來說，SQL 插入一直是相當重大的風險。</span><span class="sxs-lookup"><span data-stu-id="74283-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="74283-207">藉由在查詢中使用 <xref:System.Data.SqlClient.SqlParameter>，可避免這類插入。</span><span class="sxs-lookup"><span data-stu-id="74283-207">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="74283-208">使用者輸入會轉換成參數值。</span><span class="sxs-lookup"><span data-stu-id="74283-208">User input is turned into parameter values.</span></span> <span data-ttu-id="74283-209">如此一來，惡意命令就無法藉由客戶輸入來使用。</span><span class="sxs-lookup"><span data-stu-id="74283-209">This approach prevents malicious commands from being used from customer input.</span></span>  
  
## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="74283-210">變更 DBML 檔案中的唯讀旗標</span><span class="sxs-lookup"><span data-stu-id="74283-210">Changing Read-only Flag in DBML Files</span></span>  
 <span data-ttu-id="74283-211">問：</span><span class="sxs-lookup"><span data-stu-id="74283-211">Q.</span></span> <span data-ttu-id="74283-212">從 DBML 檔案建立物件模型時，要如何排除部分屬性的 setter？</span><span class="sxs-lookup"><span data-stu-id="74283-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>  
  
 <span data-ttu-id="74283-213">答：</span><span class="sxs-lookup"><span data-stu-id="74283-213">A.</span></span> <span data-ttu-id="74283-214">在這種進階案例中，請採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="74283-214">Take the following steps for this advanced scenario:</span></span>  
  
1. <span data-ttu-id="74283-215">在 .dbml 檔案中，藉由將 <xref:System.Data.Linq.ITable.IsReadOnly%2A> 旗標變更為 `True`，以修改屬性。</span><span class="sxs-lookup"><span data-stu-id="74283-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>  
  
2. <span data-ttu-id="74283-216">加入部分類別。</span><span class="sxs-lookup"><span data-stu-id="74283-216">Add a partial class.</span></span> <span data-ttu-id="74283-217">針對唯讀成員建立含參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="74283-217">Create a constructor with parameters for the read-only members.</span></span>  
  
3. <span data-ttu-id="74283-218">檢視預設 <xref:System.Data.Linq.Mapping.UpdateCheck> 值 (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>)，判斷它是否為應用程式的正確值。</span><span class="sxs-lookup"><span data-stu-id="74283-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="74283-219">如果您在 Visual Studio 中使用物件關聯式設計工具, 您的變更可能會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="74283-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>  
  
## <a name="aptca"></a><span data-ttu-id="74283-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="74283-220">APTCA</span></span>  
 <span data-ttu-id="74283-221">問：</span><span class="sxs-lookup"><span data-stu-id="74283-221">Q.</span></span> <span data-ttu-id="74283-222">System.Data.Linq 是否標示為供部分信任的程式碼使用？</span><span class="sxs-lookup"><span data-stu-id="74283-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>  
  
 <span data-ttu-id="74283-223">答：</span><span class="sxs-lookup"><span data-stu-id="74283-223">A.</span></span> <span data-ttu-id="74283-224">是, system.object 元件是以<xref:System.Security.AllowPartiallyTrustedCallersAttribute>屬性標記的 .NET Framework 元件中。</span><span class="sxs-lookup"><span data-stu-id="74283-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="74283-225">若沒有這個標記, .NET Framework 中的元件僅供完全信任的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="74283-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>  
  
 <span data-ttu-id="74283-226">中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]允許部分信任的呼叫端的主要案例, 是為了[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]讓該元件能夠從 Web 應用程式存取, 其中的*信任*設定為「中」。</span><span class="sxs-lookup"><span data-stu-id="74283-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>  
  
## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="74283-227">對應多個資料表的資料</span><span class="sxs-lookup"><span data-stu-id="74283-227">Mapping Data from Multiple Tables</span></span>  
 <span data-ttu-id="74283-228">問：</span><span class="sxs-lookup"><span data-stu-id="74283-228">Q.</span></span> <span data-ttu-id="74283-229">我的實體中的資料來自於多個資料表。</span><span class="sxs-lookup"><span data-stu-id="74283-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="74283-230">我該如何對應這些資料？</span><span class="sxs-lookup"><span data-stu-id="74283-230">How do I map it?</span></span>  
  
 <span data-ttu-id="74283-231">答：</span><span class="sxs-lookup"><span data-stu-id="74283-231">A.</span></span> <span data-ttu-id="74283-232">您可以在資料庫中建立檢視，然後將實體對應到該檢視。</span><span class="sxs-lookup"><span data-stu-id="74283-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="74283-233">會針對檢視產生與資料表相同的 SQL。</span><span class="sxs-lookup"><span data-stu-id="74283-233">generates the same SQL for views as it does for tables.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74283-234">在這種情況下使用檢視會有限制。</span><span class="sxs-lookup"><span data-stu-id="74283-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="74283-235">此方式在基礎檢視支援 <xref:System.Data.Linq.Table%601> 上所執行的作業時最安全。</span><span class="sxs-lookup"><span data-stu-id="74283-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="74283-236">只有您才知道會執行哪些作業。</span><span class="sxs-lookup"><span data-stu-id="74283-236">Only you know which operations are intended.</span></span> <span data-ttu-id="74283-237">例如, 大部分的應用程式都是唯讀的, 而另一個相當大`Create`號碼只會針對 views 使用預存程式來執行/ / `Update` `Delete`作業。</span><span class="sxs-lookup"><span data-stu-id="74283-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="74283-238">連接共用</span><span class="sxs-lookup"><span data-stu-id="74283-238">Connection Pooling</span></span>  
 <span data-ttu-id="74283-239">問：</span><span class="sxs-lookup"><span data-stu-id="74283-239">Q.</span></span> <span data-ttu-id="74283-240">是否有可方便 <xref:System.Data.Linq.DataContext> 共用的建構？</span><span class="sxs-lookup"><span data-stu-id="74283-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>  
  
 <span data-ttu-id="74283-241">答：</span><span class="sxs-lookup"><span data-stu-id="74283-241">A.</span></span> <span data-ttu-id="74283-242">請不要嘗試重複使用 <xref:System.Data.Linq.DataContext> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="74283-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="74283-243">每個 <xref:System.Data.Linq.DataContext> 都會維持某一個特定編輯/查詢工作階段的狀態 (包括識別快取)。</span><span class="sxs-lookup"><span data-stu-id="74283-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="74283-244">若要取得以資料庫目前狀態為基礎的新執行個體，請使用新的 <xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="74283-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="74283-245">您仍然可以使用基礎 ADO.NET 連接共用。</span><span class="sxs-lookup"><span data-stu-id="74283-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="74283-246">如需詳細資訊，請參閱 [SQL Server 連共用ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="74283-247">第二個 DataContext 未更新</span><span class="sxs-lookup"><span data-stu-id="74283-247">Second DataContext Is Not Updated</span></span>  
 <span data-ttu-id="74283-248">問：</span><span class="sxs-lookup"><span data-stu-id="74283-248">Q.</span></span> <span data-ttu-id="74283-249">我使用一個 <xref:System.Data.Linq.DataContext> 執行個體來儲存資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="74283-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="74283-250">但是，相同資料庫上的第二個 <xref:System.Data.Linq.DataContext> 卻未反映更新的值。</span><span class="sxs-lookup"><span data-stu-id="74283-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="74283-251">第二個 <xref:System.Data.Linq.DataContext> 執行個體似乎傳回快取的值。</span><span class="sxs-lookup"><span data-stu-id="74283-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>  
  
 <span data-ttu-id="74283-252">答：</span><span class="sxs-lookup"><span data-stu-id="74283-252">A.</span></span> <span data-ttu-id="74283-253">這種行為是設計上的預期行為。</span><span class="sxs-lookup"><span data-stu-id="74283-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="74283-254">會繼續傳回您在第一個執行個體中看到的相同執行個體/值。</span><span class="sxs-lookup"><span data-stu-id="74283-254">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="74283-255">當您進行更新時，會使用開放式並行存取。</span><span class="sxs-lookup"><span data-stu-id="74283-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="74283-256">這時會使用原始資料來檢查目前資料庫狀態，以確認它實際上是否仍未變更。</span><span class="sxs-lookup"><span data-stu-id="74283-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="74283-257">如果變更，就會發生衝突，而應用程式必須解決此衝突。</span><span class="sxs-lookup"><span data-stu-id="74283-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="74283-258">應用程式可選擇的其中一種做法是將原始狀態重設為目前資料庫狀態，然後嘗試再次更新。</span><span class="sxs-lookup"><span data-stu-id="74283-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="74283-259">如需詳細資訊，請參閱[如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="74283-259">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="74283-260">您也可以將 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 false，以關閉快取和變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="74283-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="74283-261">這樣每次查詢時，就能擷取最新的值。</span><span class="sxs-lookup"><span data-stu-id="74283-261">You can then retrieve the latest values every time that you query.</span></span>  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="74283-262">無法在唯讀模式下呼叫 SubmitChanges</span><span class="sxs-lookup"><span data-stu-id="74283-262">Cannot Call SubmitChanges in Read-only Mode</span></span>  
 <span data-ttu-id="74283-263">問：</span><span class="sxs-lookup"><span data-stu-id="74283-263">Q.</span></span> <span data-ttu-id="74283-264">當我嘗試在唯讀模式下呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="74283-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>  
  
 <span data-ttu-id="74283-265">答：</span><span class="sxs-lookup"><span data-stu-id="74283-265">A.</span></span> <span data-ttu-id="74283-266">內容在唯讀模式下無法追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="74283-266">Read-only mode turns off the ability of the context to track changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74283-267">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74283-267">See also</span></span>

- [<span data-ttu-id="74283-268">參考資料</span><span class="sxs-lookup"><span data-stu-id="74283-268">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="74283-269">疑難排解</span><span class="sxs-lookup"><span data-stu-id="74283-269">Troubleshooting</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)
- [<span data-ttu-id="74283-270">LINQ to SQL 中的安全性</span><span class="sxs-lookup"><span data-stu-id="74283-270">Security in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
