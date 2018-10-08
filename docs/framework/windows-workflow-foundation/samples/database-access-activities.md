---
title: 資料庫存取活動
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: efcdd25ee3e6b86d87d551623b166eab4fa76845
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850396"
---
# <a name="database-access-activities"></a><span data-ttu-id="31563-102">資料庫存取活動</span><span class="sxs-lookup"><span data-stu-id="31563-102">Database Access Activities</span></span>
<span data-ttu-id="31563-103">資料庫存取活動可讓您存取工作流程內的資料庫。</span><span class="sxs-lookup"><span data-stu-id="31563-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="31563-104">這些活動可讓您存取資料庫以擷取或修改資訊以及使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)來存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="31563-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31563-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="31563-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31563-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="31563-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="31563-107">如果此目錄不存在，請移至 （下載頁面） 以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="31563-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31563-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="31563-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="31563-109">資料庫活動</span><span class="sxs-lookup"><span data-stu-id="31563-109">Database Activities</span></span>
 <span data-ttu-id="31563-110">下列各節詳細說明此範例中包含的活動清單。</span><span class="sxs-lookup"><span data-stu-id="31563-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="31563-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="31563-111">DbUpdate</span></span>
 <span data-ttu-id="31563-112">執行 SQL 查詢，該查詢會產生資料庫修改 (插入、更新、刪除和其他修改)。</span><span class="sxs-lookup"><span data-stu-id="31563-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="31563-113">這個類別會以非同步方式執行其工作 (它衍生自 <xref:System.Activities.AsyncCodeActivity> 並且使用其非同步功能)。</span><span class="sxs-lookup"><span data-stu-id="31563-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="31563-114">透過設定提供者非變異名稱 (`ProviderName`) 和連接字串 (`ConnectionString`)，或僅使用來自應用程式組態檔的連接字串組態名稱 (`ConfigFileSectionName`)，即可設定連接資訊。</span><span class="sxs-lookup"><span data-stu-id="31563-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="31563-115">要執行的查詢是在其 `Sql` 屬性中設定，而參數是透過 `Parameters` 集合傳遞。</span><span class="sxs-lookup"><span data-stu-id="31563-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="31563-116">在 `DbUpdate` 執行之後，受影響的記錄數目會在 `AffectedRecords` 屬性中傳回。</span><span class="sxs-lookup"><span data-stu-id="31563-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="31563-117">引數</span><span class="sxs-lookup"><span data-stu-id="31563-117">Argument</span></span>|<span data-ttu-id="31563-118">描述</span><span class="sxs-lookup"><span data-stu-id="31563-118">Description</span></span>|
|-|-|
|<span data-ttu-id="31563-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="31563-119">ProviderName</span></span>|<span data-ttu-id="31563-120">ADO.NET 提供者的非變異名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="31563-121">如果設定這個引數，則同樣必須設定 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="31563-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="31563-122">ConnectionString</span></span>|<span data-ttu-id="31563-123">連接至資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="31563-123">Connection string to connect to the database.</span></span> <span data-ttu-id="31563-124">如果設定這個引數，則同樣必須設定 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="31563-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="31563-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="31563-125">ConfigName</span></span>|<span data-ttu-id="31563-126">儲存連接資訊之組態檔區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="31563-127">如果設定這個引數，則不需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="31563-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="31563-128">CommandType</span></span>|<span data-ttu-id="31563-129">要執行之 <xref:System.Data.Common.DbCommand> 的型別。</span><span class="sxs-lookup"><span data-stu-id="31563-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="31563-130">Sql</span><span class="sxs-lookup"><span data-stu-id="31563-130">Sql</span></span>|<span data-ttu-id="31563-131">要執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="31563-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="31563-132">參數</span><span class="sxs-lookup"><span data-stu-id="31563-132">Parameters</span></span>|<span data-ttu-id="31563-133">SQL 查詢的參數集合。</span><span class="sxs-lookup"><span data-stu-id="31563-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="31563-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="31563-134">AffectedRecords</span></span>|<span data-ttu-id="31563-135">受上一次作業影響的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="31563-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="31563-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="31563-136">DbQueryScalar</span></span>
 <span data-ttu-id="31563-137">執行從資料庫擷取單一值的查詢。</span><span class="sxs-lookup"><span data-stu-id="31563-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="31563-138">這個類別會以非同步方式執行其工作 (它衍生自 <xref:System.Activities.AsyncCodeActivity%601> 並且使用其非同步功能)。</span><span class="sxs-lookup"><span data-stu-id="31563-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="31563-139">透過設定提供者非變異名稱 (`ProviderName`) 和連接字串 (`ConnectionString`)，或僅使用來自應用程式組態檔的連接字串組態名稱 (`ConfigFileSectionName`)，即可設定連接資訊。</span><span class="sxs-lookup"><span data-stu-id="31563-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="31563-140">要執行的查詢是在其 `Sql` 屬性中設定，而參數是透過 `Parameters` 集合傳遞。</span><span class="sxs-lookup"><span data-stu-id="31563-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="31563-141">之後`DbQueryScalar`會執行，會傳回純量中`Result``out`引數 (型別的`TResult`，也就是在基底類別中定義<xref:System.Activities.AsyncCodeActivity%601>)。</span><span class="sxs-lookup"><span data-stu-id="31563-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="31563-142">引數</span><span class="sxs-lookup"><span data-stu-id="31563-142">Argument</span></span>|<span data-ttu-id="31563-143">描述</span><span class="sxs-lookup"><span data-stu-id="31563-143">Description</span></span>|
|-|-|
|<span data-ttu-id="31563-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="31563-144">ProviderName</span></span>|<span data-ttu-id="31563-145">ADO.NET 提供者的非變異名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="31563-146">如果設定這個引數，則同樣必須設定 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="31563-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="31563-147">ConnectionString</span></span>|<span data-ttu-id="31563-148">連接至資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="31563-148">Connection string to connect to the database.</span></span> <span data-ttu-id="31563-149">如果設定這個引數，則同樣必須設定 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="31563-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="31563-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="31563-150">ConfigName</span></span>|<span data-ttu-id="31563-151">儲存連接資訊之組態檔區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="31563-152">如果設定這個引數，則不需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="31563-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="31563-153">CommandType</span></span>|<span data-ttu-id="31563-154">要執行之 <xref:System.Data.Common.DbCommand> 的型別。</span><span class="sxs-lookup"><span data-stu-id="31563-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="31563-155">Sql</span><span class="sxs-lookup"><span data-stu-id="31563-155">Sql</span></span>|<span data-ttu-id="31563-156">要執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="31563-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="31563-157">參數</span><span class="sxs-lookup"><span data-stu-id="31563-157">Parameters</span></span>|<span data-ttu-id="31563-158">SQL 查詢的參數集合。</span><span class="sxs-lookup"><span data-stu-id="31563-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="31563-159">結果</span><span class="sxs-lookup"><span data-stu-id="31563-159">Result</span></span>|<span data-ttu-id="31563-160">查詢執行之後取得的純量。</span><span class="sxs-lookup"><span data-stu-id="31563-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="31563-161">這個引數的型別為 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="31563-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="31563-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="31563-162">DbQuery</span></span>
 <span data-ttu-id="31563-163">執行擷取物件清單的查詢。</span><span class="sxs-lookup"><span data-stu-id="31563-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="31563-164">執行查詢之後，會執行對應的函式 (它可以是<xref:System.Func%601> < `DbDataReader`， `TResult`> 或有<xref:System.Activities.ActivityFunc%601> < `DbDataReader`， `TResult`>)。</span><span class="sxs-lookup"><span data-stu-id="31563-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="31563-165">這個對應的函式會取得 `DbDataReader` 中的記錄，並且將它對應至要傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="31563-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="31563-166">透過設定提供者非變異名稱 (`ProviderName`) 和連接字串 (`ConnectionString`)，或僅使用來自應用程式組態檔的連接字串組態名稱 (`ConfigFileSectionName`)，即可設定連接資訊。</span><span class="sxs-lookup"><span data-stu-id="31563-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="31563-167">要執行的查詢是在其 `Sql` 屬性中設定，而參數是透過 `Parameters` 集合傳遞。</span><span class="sxs-lookup"><span data-stu-id="31563-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="31563-168">SQL 查詢的結果會使用 `DbDataReader` 擷取。</span><span class="sxs-lookup"><span data-stu-id="31563-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="31563-169">活動會逐一查看 `DbDataReader`，並且將 `DbDataReader` 中的資料列對應至 `TResult` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="31563-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="31563-170">使用者`DbQuery`必須提供對應程式碼，可在兩種方式： 使用<xref:System.Func%601> < `DbDataReader`， `TResult`> 或<xref:System.Activities.ActivityFunc%601> < `DbDataReader`， `TResult`>。</span><span class="sxs-lookup"><span data-stu-id="31563-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="31563-171">在第一個案例中，對應會在單一執行 Pulse 中完成。</span><span class="sxs-lookup"><span data-stu-id="31563-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="31563-172">因此這種方式速度較快，但是無法序列化為 XAML。</span><span class="sxs-lookup"><span data-stu-id="31563-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="31563-173">在第二個案例中，對應是在多次 Pulse 中執行。</span><span class="sxs-lookup"><span data-stu-id="31563-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="31563-174">因此，這種方式的速度較慢，但是可以序列化為 XAML，並且以宣告方式編寫 (任何存在的活動都可以參與對應)。</span><span class="sxs-lookup"><span data-stu-id="31563-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="31563-175">引數</span><span class="sxs-lookup"><span data-stu-id="31563-175">Argument</span></span>|<span data-ttu-id="31563-176">描述</span><span class="sxs-lookup"><span data-stu-id="31563-176">Description</span></span>|
|-|-|
|<span data-ttu-id="31563-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="31563-177">ProviderName</span></span>|<span data-ttu-id="31563-178">ADO.NET 提供者的非變異名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="31563-179">如果設定這個引數，則同樣必須設定 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="31563-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="31563-180">ConnectionString</span></span>|<span data-ttu-id="31563-181">連接至資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="31563-181">Connection string to connect to the database.</span></span> <span data-ttu-id="31563-182">如果設定這個引數，則同樣必須設定 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="31563-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="31563-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="31563-183">ConfigName</span></span>|<span data-ttu-id="31563-184">儲存連接資訊之組態檔區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="31563-185">如果設定這個引數，則不需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="31563-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="31563-186">CommandType</span></span>|<span data-ttu-id="31563-187">要執行之 <xref:System.Data.Common.DbCommand> 的型別。</span><span class="sxs-lookup"><span data-stu-id="31563-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="31563-188">Sql</span><span class="sxs-lookup"><span data-stu-id="31563-188">Sql</span></span>|<span data-ttu-id="31563-189">要執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="31563-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="31563-190">參數</span><span class="sxs-lookup"><span data-stu-id="31563-190">Parameters</span></span>|<span data-ttu-id="31563-191">SQL 查詢的參數集合。</span><span class="sxs-lookup"><span data-stu-id="31563-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="31563-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="31563-192">Mapper</span></span>|<span data-ttu-id="31563-193">對應函式 (<xref:System.Func%601><`DbDataReader`， `TResult`>) 會採用記錄`DataReader`執行查詢而取得，並傳回型別的物件的執行個體`TResult`加入`Result`集合。</span><span class="sxs-lookup"><span data-stu-id="31563-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="31563-194">在此案例中，對應是在單一執行 Pulse 中完成，但是無法使用設計工具以宣告方式邊寫。</span><span class="sxs-lookup"><span data-stu-id="31563-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="31563-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="31563-195">MapperFunc</span></span>|<span data-ttu-id="31563-196">對應函式 (<xref:System.Activities.ActivityFunc%601><`DbDataReader`， `TResult`>) 會採用記錄`DataReader`執行查詢而取得，並傳回型別的物件的執行個體`TResult`加入`Result`集合。</span><span class="sxs-lookup"><span data-stu-id="31563-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="31563-197">在此案例中，對應會在多個執行 Pulse 中完成。</span><span class="sxs-lookup"><span data-stu-id="31563-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="31563-198">此函式可以序列化為 XAML，並且以宣告方式編寫 (任何存在的活動都可以參與對應)。</span><span class="sxs-lookup"><span data-stu-id="31563-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="31563-199">結果</span><span class="sxs-lookup"><span data-stu-id="31563-199">Result</span></span>|<span data-ttu-id="31563-200">物件清單，該清單是執行查詢以及針對 `DataReader` 中的每項記錄執行對應函式而取得。</span><span class="sxs-lookup"><span data-stu-id="31563-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="31563-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="31563-201">DbQueryDataSet</span></span>
 <span data-ttu-id="31563-202">執行傳回 <xref:System.Data.DataSet> 的查詢。</span><span class="sxs-lookup"><span data-stu-id="31563-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="31563-203">這個類別會以非同步方式執行其工作。</span><span class="sxs-lookup"><span data-stu-id="31563-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="31563-204">它衍生自<xref:System.Activities.AsyncCodeActivity> < `TResult`> 並且使用其非同步功能。</span><span class="sxs-lookup"><span data-stu-id="31563-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="31563-205">透過設定提供者非變異名稱 (`ProviderName`) 和連接字串 (`ConnectionString`)，或僅使用來自應用程式組態檔的連接字串組態名稱 (`ConfigFileSectionName`)，即可設定連接資訊。</span><span class="sxs-lookup"><span data-stu-id="31563-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="31563-206">要執行的查詢是在其 `Sql` 屬性中設定，而參數是透過 `Parameters` 集合傳遞。</span><span class="sxs-lookup"><span data-stu-id="31563-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="31563-207">之後`DbQueryDataSet`會執行`DataSet`會傳回`Result``out`引數 (型別的`TResult`，也就是基底類別中定義<xref:System.Activities.AsyncCodeActivity%601>)。</span><span class="sxs-lookup"><span data-stu-id="31563-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="31563-208">引數</span><span class="sxs-lookup"><span data-stu-id="31563-208">Argument</span></span>|<span data-ttu-id="31563-209">描述</span><span class="sxs-lookup"><span data-stu-id="31563-209">Description</span></span>|
|-|-|
|<span data-ttu-id="31563-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="31563-210">ProviderName</span></span>|<span data-ttu-id="31563-211">ADO.NET 提供者的非變異名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="31563-212">如果設定這個引數，則同樣必須設定 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="31563-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="31563-213">ConnectionString</span></span>|<span data-ttu-id="31563-214">連接至資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="31563-214">Connection string to connect to the database.</span></span> <span data-ttu-id="31563-215">如果設定這個引數，則同樣必須設定 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="31563-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="31563-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="31563-216">ConfigName</span></span>|<span data-ttu-id="31563-217">儲存連接資訊之組態檔區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="31563-218">如果設定這個引數，則不需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="31563-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="31563-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="31563-219">CommandType</span></span>|<span data-ttu-id="31563-220">要執行之 <xref:System.Data.Common.DbCommand> 的型別。</span><span class="sxs-lookup"><span data-stu-id="31563-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="31563-221">Sql</span><span class="sxs-lookup"><span data-stu-id="31563-221">Sql</span></span>|<span data-ttu-id="31563-222">要執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="31563-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="31563-223">參數</span><span class="sxs-lookup"><span data-stu-id="31563-223">Parameters</span></span>|<span data-ttu-id="31563-224">SQL 查詢的參數集合。</span><span class="sxs-lookup"><span data-stu-id="31563-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="31563-225">結果</span><span class="sxs-lookup"><span data-stu-id="31563-225">Result</span></span>|<span data-ttu-id="31563-226">查詢執行之後取得的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="31563-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="31563-227">設定連接資訊</span><span class="sxs-lookup"><span data-stu-id="31563-227">Configuring Connection Information</span></span>
 <span data-ttu-id="31563-228">所有 DbActivities 會共用相同的組態參數。</span><span class="sxs-lookup"><span data-stu-id="31563-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="31563-229">您可以透過兩種方式加以設定：</span><span class="sxs-lookup"><span data-stu-id="31563-229">They can be configured in two ways:</span></span>

-   <span data-ttu-id="31563-230">`ConnectionString + InvariantName`：設定 ADO.NET 提供者非變異名稱和連接字串。</span><span class="sxs-lookup"><span data-stu-id="31563-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

-   <span data-ttu-id="31563-231">`ConfigName`：設定包含連接資訊的組態區段名稱。</span><span class="sxs-lookup"><span data-stu-id="31563-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   <span data-ttu-id="31563-232">在活動中：</span><span class="sxs-lookup"><span data-stu-id="31563-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="31563-233">執行這個範例</span><span class="sxs-lookup"><span data-stu-id="31563-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="31563-234">安裝指示</span><span class="sxs-lookup"><span data-stu-id="31563-234">Setup instructions</span></span>
 <span data-ttu-id="31563-235">這個範例會使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="31563-235">This sample uses a database.</span></span> <span data-ttu-id="31563-236">範例中提供 set-up 和 load 指令碼 (Setup.cmd)。</span><span class="sxs-lookup"><span data-stu-id="31563-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="31563-237">您必須使用命令提示字元執行該檔案。</span><span class="sxs-lookup"><span data-stu-id="31563-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="31563-238">Setup.cmd 指令碼會叫用 CreateDb.sql 指令碼檔，該檔案中包含的 SQL 命令會執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="31563-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

-   <span data-ttu-id="31563-239">建立名為 DbActivitiesSample 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="31563-239">Creates a database called DbActivitiesSample.</span></span>

-   <span data-ttu-id="31563-240">建立 Roles 資料表。</span><span class="sxs-lookup"><span data-stu-id="31563-240">Creates the Roles table.</span></span>

-   <span data-ttu-id="31563-241">建立 Employees 資料表。</span><span class="sxs-lookup"><span data-stu-id="31563-241">Creates Employees table.</span></span>

-   <span data-ttu-id="31563-242">將三個記錄插入至 Roles 資料表。</span><span class="sxs-lookup"><span data-stu-id="31563-242">Inserts three records into the Roles table.</span></span>

-   <span data-ttu-id="31563-243">將十二個記錄插入至 Employees 資料表。</span><span class="sxs-lookup"><span data-stu-id="31563-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="31563-244">若要執行 Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="31563-244">To run Setup.cmd</span></span>

1.  <span data-ttu-id="31563-245">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="31563-245">Open a command prompt.</span></span>

2.  <span data-ttu-id="31563-246">移至 DbActivities 範例資料夾。</span><span class="sxs-lookup"><span data-stu-id="31563-246">Go to the DbActivities sample folder.</span></span>

3.  <span data-ttu-id="31563-247">輸入"setup.cmd"，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="31563-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="31563-248">Setup.cmd 會嘗試在本機電腦 SqlExpress 執行個體中安裝範例。</span><span class="sxs-lookup"><span data-stu-id="31563-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="31563-249">如果您想要將它安裝到其他 SQL Server 執行個體中，請使用新的執行個體名稱編輯 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="31563-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="31563-250">若要解除安裝範例資料庫</span><span class="sxs-lookup"><span data-stu-id="31563-250">To uninstall the sample database</span></span>

1.  <span data-ttu-id="31563-251">在命令提示字元中從相同資料夾執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="31563-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="31563-252">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="31563-252">To run the sample</span></span>

1.  <span data-ttu-id="31563-253">在 Visual Studio 2010 中開啟方案</span><span class="sxs-lookup"><span data-stu-id="31563-253">Open the solution in Visual Studio 2010</span></span>

2.  <span data-ttu-id="31563-254">若要編譯方案，請按下 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="31563-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="31563-255">若要執行範例但不進行偵錯，請按 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="31563-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="31563-256">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="31563-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31563-257">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="31563-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="31563-258">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="31563-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31563-259">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="31563-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
