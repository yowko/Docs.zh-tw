---
title: 從檔案和其他來源載入資料
description: 瞭解如何使用 API 將資料載入至 ML.NET，以進行處理和定型。 資料會儲存在檔案、資料庫、JSON、XML 或記憶體中的集合中。
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: edcb1c4d00a09ba8404b08ddc3ca3447a52a81b6
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679582"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="1f517-104">從檔案和其他來源載入資料</span><span class="sxs-lookup"><span data-stu-id="1f517-104">Load data from files and other sources</span></span>

<span data-ttu-id="1f517-105">瞭解如何使用 API 將資料載入至 ML.NET，以進行處理和定型。</span><span class="sxs-lookup"><span data-stu-id="1f517-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="1f517-106">資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="1f517-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="1f517-107">如果您是使用模型建立器，請參閱將 [定型資料載入模型](load-data-model-builder.md)產生器。</span><span class="sxs-lookup"><span data-stu-id="1f517-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="1f517-108">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="1f517-108">Create the data model</span></span>

<span data-ttu-id="1f517-109">ML.NET 可讓您透過類別定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="1f517-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="1f517-110">例如，假設有下列的輸入資料：</span><span class="sxs-lookup"><span data-stu-id="1f517-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="1f517-111">建立資料模型以表示以下的程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="1f517-111">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="1f517-112">使用資料行屬性標註資料模型</span><span class="sxs-lookup"><span data-stu-id="1f517-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="1f517-113">屬性可提供 ML.NET 更多關於資料模型和資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="1f517-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="1f517-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)屬性會指定屬性的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="1f517-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f517-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 只有從檔案載入資料時才需要。</span><span class="sxs-lookup"><span data-stu-id="1f517-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="1f517-116">將資料行作為以下項目載入：</span><span class="sxs-lookup"><span data-stu-id="1f517-116">Load columns as:</span></span>

- <span data-ttu-id="1f517-117">個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。</span><span class="sxs-lookup"><span data-stu-id="1f517-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="1f517-118">以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。</span><span class="sxs-lookup"><span data-stu-id="1f517-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="1f517-119">如果您有 vector 屬性，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用至資料模型中的屬性。</span><span class="sxs-lookup"><span data-stu-id="1f517-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="1f517-120">請務必注意，向量中的所有項目都必須是相同類型。</span><span class="sxs-lookup"><span data-stu-id="1f517-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="1f517-121">將資料行保持分離可讓您更輕易且具備彈性地進行特徵工程，但針對極為大量的資料行，在每一個資料行上進行作業會影響定型速度。</span><span class="sxs-lookup"><span data-stu-id="1f517-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="1f517-122">ML.NET 會透過資料行名稱運作。</span><span class="sxs-lookup"><span data-stu-id="1f517-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="1f517-123">如果您想要將資料行的名稱變更為屬性名稱以外的名稱，請使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="1f517-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="1f517-124">在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。</span><span class="sxs-lookup"><span data-stu-id="1f517-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="1f517-125">但是，對於資料處理和建立機器學習模型，ML.NET 會使用屬性中提供的值來覆寫及參考屬性 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="1f517-126">從單一檔案載入資料</span><span class="sxs-lookup"><span data-stu-id="1f517-126">Load data from a single file</span></span>

<span data-ttu-id="1f517-127">若要從檔案載入資料，請使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 方法以及要載入之資料的資料模型。</span><span class="sxs-lookup"><span data-stu-id="1f517-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="1f517-128">因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。</span><span class="sxs-lookup"><span data-stu-id="1f517-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="1f517-129">若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。</span><span class="sxs-lookup"><span data-stu-id="1f517-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="1f517-130">從多個檔案載入資料</span><span class="sxs-lookup"><span data-stu-id="1f517-130">Load data from multiple files</span></span>

<span data-ttu-id="1f517-131">您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。</span><span class="sxs-lookup"><span data-stu-id="1f517-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="1f517-132">從單一目錄中的檔案載入</span><span class="sxs-lookup"><span data-stu-id="1f517-132">Load from files in a single directory</span></span>

<span data-ttu-id="1f517-133">當所有的資料檔案都在相同的目錄中時，在方法中使用萬用字元 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="1f517-134">載入多個目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="1f517-134">Load from files in multiple directories</span></span>

<span data-ttu-id="1f517-135">若要從多個目錄載入資料，請使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) 方法來建立 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="1f517-136">然後，使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) 方法，並指定個別的檔案路徑， (無法使用萬用字元) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="1f517-137">從關係資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="1f517-137">Load data from a relational database</span></span>

<span data-ttu-id="1f517-138">ML.NET 支援從所支援的各種關係資料庫載入資料， [`System.Data`](xref:System.Data) 包括 SQL Server、Azure SQL Database、Oracle、SQLite、于 postgresql、進度、IBM DB2 等等。</span><span class="sxs-lookup"><span data-stu-id="1f517-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="1f517-139">若要使用 `DatabaseLoader` ，請參考 [SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="1f517-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="1f517-140">假設資料庫具有名為的資料表 `House` 和下列架構：</span><span class="sxs-lookup"><span data-stu-id="1f517-140">Given a database with a table named `House` and the following schema:</span></span>

```sql
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="1f517-141">資料可由 `HouseData` 等類別建立模型。</span><span class="sxs-lookup"><span data-stu-id="1f517-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="1f517-142">然後，在您的應用程式內建立 `DatabaseLoader` 。</span><span class="sxs-lookup"><span data-stu-id="1f517-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="1f517-143">定義您的連接字串，以及要在資料庫上執行的 SQL 命令，並建立 `DatabaseSource` 實例。</span><span class="sxs-lookup"><span data-stu-id="1f517-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="1f517-144">這個範例會使用 LocalDB SQL Server 資料庫與檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="1f517-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="1f517-145">不過，DatabaseLoader 對內部部署和雲端中的資料庫支援任何其他有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="1f517-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="1f517-146">不是類型的數值資料必須 [`Real`](xref:System.Data.SqlDbType) 轉換成 [`Real`](xref:System.Data.SqlDbType) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="1f517-147">此 [`Real`](xref:System.Data.SqlDbType) 類型會表示為單精確度浮點數或 [`Single`](xref:System.Single) ML.NET 演算法預期的輸入類型。</span><span class="sxs-lookup"><span data-stu-id="1f517-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="1f517-148">在此範例中， `NumBed` 資料行是資料庫中的整數。</span><span class="sxs-lookup"><span data-stu-id="1f517-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="1f517-149">使用 `CAST` 內建函數，它會轉換成 [`Real`](xref:System.Data.SqlDbType) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="1f517-150">因為屬性已經是型別，所以 `Price` [`Real`](xref:System.Data.SqlDbType) 會依原樣載入。</span><span class="sxs-lookup"><span data-stu-id="1f517-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="1f517-151">您 `Load` 可以使用方法，將資料載入至 [`IDataView`](xref:Microsoft.ML.IDataView) 。</span><span class="sxs-lookup"><span data-stu-id="1f517-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="1f517-152">從其他來源載入資料</span><span class="sxs-lookup"><span data-stu-id="1f517-152">Load data from other sources</span></span>

<span data-ttu-id="1f517-153">除了載入儲存在檔案中的資料，ML.NET 支援從其他來源載入資料，其中包含但不限於：</span><span class="sxs-lookup"><span data-stu-id="1f517-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="1f517-154">記憶體內集合</span><span class="sxs-lookup"><span data-stu-id="1f517-154">In-memory collections</span></span>
- <span data-ttu-id="1f517-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="1f517-155">JSON/XML</span></span>

<span data-ttu-id="1f517-156">請注意，當使用串流來源時，ML.NET 預期輸入的形式為記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="1f517-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="1f517-157">因此，當使用像是 JSON/XML 等來源時，請務必將資料格式化成記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="1f517-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="1f517-158">假設有下列記憶體內部集合：</span><span class="sxs-lookup"><span data-stu-id="1f517-158">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="1f517-159">使用方法將記憶體中的集合載入中 [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) ：</span><span class="sxs-lookup"><span data-stu-id="1f517-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f517-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) 假設 [`IEnumerable`](xref:System.Collections.IEnumerable) 它載入自的是安全線程。</span><span class="sxs-lookup"><span data-stu-id="1f517-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="1f517-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1f517-161">Next steps</span></span>

- <span data-ttu-id="1f517-162">若要清除或以其他方式處理資料，請參閱 [準備用來建立模型的資料](prepare-data-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="1f517-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="1f517-163">當您準備好建立模型時，請參閱 [定型和評估模型](train-machine-learning-model-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="1f517-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
