---
title: 從檔案和其他來源載入資料
description: 此操作說明教學會示範如何將資料載入 ML.NET 以進行處理和定型。 資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。
ms.date: 06/25/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: fafbe3fed9e3f0b509eda4f9d8967965bde19767
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397737"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="31576-104">從檔案和其他來源載入資料</span><span class="sxs-lookup"><span data-stu-id="31576-104">Load data from files and other sources</span></span>

<span data-ttu-id="31576-105">此操作說明教學會示範如何將資料載入 ML.NET 以進行處理和定型。</span><span class="sxs-lookup"><span data-stu-id="31576-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="31576-106">資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="31576-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="31576-107">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="31576-107">Create the data model</span></span>

<span data-ttu-id="31576-108">ML.NET 可讓您透過類別定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="31576-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="31576-109">例如，假設有下列的輸入資料：</span><span class="sxs-lookup"><span data-stu-id="31576-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="31576-110">建立資料模型以表示以下的程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="31576-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="31576-111">使用資料行屬性標註資料模型</span><span class="sxs-lookup"><span data-stu-id="31576-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="31576-112">屬性可提供 ML.NET 更多關於資料模型和資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="31576-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="31576-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 屬性會指定您屬性的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="31576-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31576-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 只有在從檔案載入資料時才需要。</span><span class="sxs-lookup"><span data-stu-id="31576-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="31576-115">將資料行作為以下項目載入：</span><span class="sxs-lookup"><span data-stu-id="31576-115">Load columns as:</span></span> 
- <span data-ttu-id="31576-116">個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。</span><span class="sxs-lookup"><span data-stu-id="31576-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="31576-117">以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。</span><span class="sxs-lookup"><span data-stu-id="31576-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="31576-118">若您擁有向量屬性，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用到您資料模型中的屬性。</span><span class="sxs-lookup"><span data-stu-id="31576-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="31576-119">請務必注意，向量中的所有項目都必須是相同類型。</span><span class="sxs-lookup"><span data-stu-id="31576-119">It's important to note that all of the elements in the vector need to be the same type.</span></span>

<span data-ttu-id="31576-120">ML.NET 會透過資料行名稱運作。</span><span class="sxs-lookup"><span data-stu-id="31576-120">ML.NET Operates through column names.</span></span> <span data-ttu-id="31576-121">若您想要將資料行名稱變更為屬性名稱之外的名稱，請使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="31576-121">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="31576-122">在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。</span><span class="sxs-lookup"><span data-stu-id="31576-122">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="31576-123">但是，針對資料處理和建置機器學習模型，ML.NET 會使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性中提供的值來覆寫及參考屬性。</span><span class="sxs-lookup"><span data-stu-id="31576-123">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="31576-124">從單一檔案載入資料</span><span class="sxs-lookup"><span data-stu-id="31576-124">Load data from a single file</span></span>

<span data-ttu-id="31576-125">若要從檔案載入資料，請搭配要載入其資料的資料模型使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法。</span><span class="sxs-lookup"><span data-stu-id="31576-125">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="31576-126">因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。</span><span class="sxs-lookup"><span data-stu-id="31576-126">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="31576-127">若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。</span><span class="sxs-lookup"><span data-stu-id="31576-127">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="31576-128">從多個檔案載入資料</span><span class="sxs-lookup"><span data-stu-id="31576-128">Load data from multiple files</span></span>

<span data-ttu-id="31576-129">您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。</span><span class="sxs-lookup"><span data-stu-id="31576-129">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="31576-130">從單一目錄中的檔案載入</span><span class="sxs-lookup"><span data-stu-id="31576-130">Load from files in a single directory</span></span>

<span data-ttu-id="31576-131">當您所有的資料檔案都位於相同目錄時，請在 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="31576-131">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="31576-132">載入多個目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="31576-132">Load from files in multiple directories</span></span>

<span data-ttu-id="31576-133">若要從多個目錄載入資料，請使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) 方法來建立 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)。</span><span class="sxs-lookup"><span data-stu-id="31576-133">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="31576-134">然後，請使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) 方法並指定個別檔案路徑 (無法使用萬用字元)。</span><span class="sxs-lookup"><span data-stu-id="31576-134">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="31576-135">從其他來源載入資料</span><span class="sxs-lookup"><span data-stu-id="31576-135">Load data from other sources</span></span>

<span data-ttu-id="31576-136">除了載入儲存在檔案中的資料，ML.NET 支援從其他來源載入資料，其中包含但不限於：</span><span class="sxs-lookup"><span data-stu-id="31576-136">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="31576-137">記憶體內集合</span><span class="sxs-lookup"><span data-stu-id="31576-137">In-memory collections</span></span>
- <span data-ttu-id="31576-138">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="31576-138">JSON/XML</span></span>
- <span data-ttu-id="31576-139">資料庫</span><span class="sxs-lookup"><span data-stu-id="31576-139">Databases</span></span>

<span data-ttu-id="31576-140">請注意，當使用串流來源時，ML.NET 預期輸入的形式為記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="31576-140">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="31576-141">因此，當使用像是 JSON/XML 等來源時，請務必將資料格式化成記憶體內部集合。</span><span class="sxs-lookup"><span data-stu-id="31576-141">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="31576-142">假設有下列記憶體內部集合：</span><span class="sxs-lookup"><span data-stu-id="31576-142">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="31576-143">請使用 [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 方法將記憶體內部集合載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="31576-143">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
