---
title: 從檔案和其他來源載入資料
description: 此操作說明教學會示範如何將資料載入 ML.NET 以進行處理和定型。 資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 4008f38bf4a20113a3f5c865e38222e5b82f2acc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991368"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="c7331-104">從檔案和其他來源載入資料</span><span class="sxs-lookup"><span data-stu-id="c7331-104">Load data from files and other sources</span></span>

<span data-ttu-id="c7331-105">此操作說明教學會示範如何將資料載入 ML.NET 以進行處理和定型。</span><span class="sxs-lookup"><span data-stu-id="c7331-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="c7331-106">資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="c7331-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="c7331-107">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="c7331-107">Create the data model</span></span>

<span data-ttu-id="c7331-108">ML.NET 可讓您透過類別定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="c7331-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="c7331-109">例如，假設有下列的輸入資料：</span><span class="sxs-lookup"><span data-stu-id="c7331-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="c7331-110">建立資料模型以表示以下的程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="c7331-110">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="c7331-111">使用資料行屬性標註資料模型</span><span class="sxs-lookup"><span data-stu-id="c7331-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="c7331-112">屬性可提供 ML.NET 更多關於資料模型和資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="c7331-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="c7331-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 屬性會指定您屬性的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="c7331-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7331-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 只有在從檔案載入資料時才需要。</span><span class="sxs-lookup"><span data-stu-id="c7331-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="c7331-115">將資料行作為以下項目載入：</span><span class="sxs-lookup"><span data-stu-id="c7331-115">Load columns as:</span></span>

- <span data-ttu-id="c7331-116">個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。</span><span class="sxs-lookup"><span data-stu-id="c7331-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="c7331-117">以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。</span><span class="sxs-lookup"><span data-stu-id="c7331-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="c7331-118">若您擁有向量屬性，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用到您資料模型中的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7331-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="c7331-119">請務必注意，向量中的所有項目都必須是相同類型。</span><span class="sxs-lookup"><span data-stu-id="c7331-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="c7331-120">將資料行保持分離可讓您更輕易且具備彈性地進行特徵工程，但針對極為大量的資料行，在每一個資料行上進行作業會影響定型速度。</span><span class="sxs-lookup"><span data-stu-id="c7331-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="c7331-121">ML.NET 會透過資料行名稱運作。</span><span class="sxs-lookup"><span data-stu-id="c7331-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="c7331-122">若您想要將資料行名稱變更為屬性名稱之外的名稱，請使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="c7331-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="c7331-123">在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。</span><span class="sxs-lookup"><span data-stu-id="c7331-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="c7331-124">但是，針對資料處理和建置機器學習模型，ML.NET 會使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性中提供的值來覆寫及參考屬性。</span><span class="sxs-lookup"><span data-stu-id="c7331-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="c7331-125">從單一檔案載入資料</span><span class="sxs-lookup"><span data-stu-id="c7331-125">Load data from a single file</span></span>

<span data-ttu-id="c7331-126">若要從檔案載入資料，請搭配要載入其資料的資料模型使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法。</span><span class="sxs-lookup"><span data-stu-id="c7331-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="c7331-127">因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。</span><span class="sxs-lookup"><span data-stu-id="c7331-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="c7331-128">若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。</span><span class="sxs-lookup"><span data-stu-id="c7331-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="c7331-129">從多個檔案載入資料</span><span class="sxs-lookup"><span data-stu-id="c7331-129">Load data from multiple files</span></span>

<span data-ttu-id="c7331-130">您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。</span><span class="sxs-lookup"><span data-stu-id="c7331-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="c7331-131">從單一目錄中的檔案載入</span><span class="sxs-lookup"><span data-stu-id="c7331-131">Load from files in a single directory</span></span>

<span data-ttu-id="c7331-132">當您所有的資料檔案都位於相同目錄時，請在 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c7331-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="c7331-133">載入多個目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="c7331-133">Load from files in multiple directories</span></span>

<span data-ttu-id="c7331-134">若要從多個目錄載入資料，請使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) 方法來建立 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)。</span><span class="sxs-lookup"><span data-stu-id="c7331-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="c7331-135">然後，請使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) 方法並指定個別檔案路徑 (無法使用萬用字元)。</span><span class="sxs-lookup"><span data-stu-id="c7331-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="c7331-136">從關係資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="c7331-136">Load data from a relational database</span></span>

> [!NOTE]
> <span data-ttu-id="c7331-137">DatabaseLoader 目前為預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="c7331-137">DatabaseLoader is currently in preview.</span></span> <span data-ttu-id="c7331-138">它可以藉由參考[SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet[套件的方式](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview)來使用。</span><span class="sxs-lookup"><span data-stu-id="c7331-138">It can be used by referencing the [Microsoft.ML.Experimental](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) and [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet packages.</span></span>

<span data-ttu-id="c7331-139">ML.NET 支援從支援[`System.Data`](xref:System.Data)的各種關係資料庫載入資料，其中包括 SQL Server、Azure SQL Database、Oracle、SQLite、于 postgresql、進度、IBM DB2 及其他許多。</span><span class="sxs-lookup"><span data-stu-id="c7331-139">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

<span data-ttu-id="c7331-140">假設資料庫具有名為`House`的資料表和下列架構：</span><span class="sxs-lookup"><span data-stu-id="c7331-140">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] int NOT NULL IDENTITY,
    [Size] real NOT NULL,
    [Price] real NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="c7331-141">資料可由 `HouseData` 等類別建立模型。</span><span class="sxs-lookup"><span data-stu-id="c7331-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="c7331-142">然後，在您的應用程式內建立`DatabaseLoader`。</span><span class="sxs-lookup"><span data-stu-id="c7331-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="c7331-143">定義您的連接字串，以及要在資料庫上執行的 SQL 命令，並建立`DatabaseSource`實例。</span><span class="sxs-lookup"><span data-stu-id="c7331-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="c7331-144">這個範例會使用具有檔案路徑的 LocalDB SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7331-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="c7331-145">不過，DatabaseLoader 會針對內部部署和雲端中的資料庫支援任何其他有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c7331-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size,Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance,connectionString,sqlCommand);
```

<span data-ttu-id="c7331-146">最後，使用`Load`方法將資料載入[`IDataView`](xref:Microsoft.ML.IDataView)中。</span><span class="sxs-lookup"><span data-stu-id="c7331-146">Finally, use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="c7331-147">從其他來源載入資料</span><span class="sxs-lookup"><span data-stu-id="c7331-147">Load data from other sources</span></span>

<span data-ttu-id="c7331-148">除了載入儲存在檔案中的資料，ML.NET 支援從其他來源載入資料，其中包含但不限於：</span><span class="sxs-lookup"><span data-stu-id="c7331-148">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="c7331-149">記憶體內集合</span><span class="sxs-lookup"><span data-stu-id="c7331-149">In-memory collections</span></span>
- <span data-ttu-id="c7331-150">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="c7331-150">JSON/XML</span></span>

<span data-ttu-id="c7331-151">請注意，當使用串流來源時，ML.NET 預期輸入的形式為記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="c7331-151">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="c7331-152">因此，當使用像是 JSON/XML 等來源時，請務必將資料格式化成記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="c7331-152">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="c7331-153">假設有下列記憶體內部集合：</span><span class="sxs-lookup"><span data-stu-id="c7331-153">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="c7331-154">請使用 [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 方法將記憶體內部集合載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="c7331-154">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7331-155">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 假設它載入的 [`IEnumerable`](xref:System.Collections.IEnumerable) 是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="c7331-155">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
