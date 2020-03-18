---
title: 從檔案和其他來源載入資料
description: 瞭解如何使用 API 將資料處理和培訓載入到ML.NET。 資料存儲在檔、資料庫、JSON、XML 或記憶體中集合中。
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344747"
---
# <a name="load-data-from-files-and-other-sources"></a>從檔案和其他來源載入資料

瞭解如何使用 API 將資料處理和培訓載入到ML.NET。 資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。

如果使用模型產生器，請參閱[將訓練資料載入到模型產生器](load-data-model-builder.md)中。

## <a name="create-the-data-model"></a>建立資料模型

ML.NET 可讓您透過類別定義資料模型。 例如，假設有下列的輸入資料：

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

建立資料模型以表示以下的程式碼片段：

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

### <a name="annotating-the-data-model-with-column-attributes"></a>使用資料行屬性標註資料模型

屬性可提供 ML.NET 更多關於資料模型和資料來源的資訊。

該[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)屬性指定屬性的列索引。

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)僅在從檔載入資料時才需要。

將資料行作為以下項目載入：

- 個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。
- 以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。

如果您有向量屬性，請將[`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute)該屬性應用於資料模型中的屬性。 請務必注意，向量中的所有項目都必須是相同類型。 將資料行保持分離可讓您更輕易且具備彈性地進行特徵工程，但針對極為大量的資料行，在每一個資料行上進行作業會影響定型速度。

ML.NET 會透過資料行名稱運作。 如果要將列的名稱更改為屬性名稱以外的內容，請使用 屬性[`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute)。 在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。 但是，對於資料處理和構建機器學習模型，ML.NET重寫和引用屬性中提供[`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute)的值。

## <a name="load-data-from-a-single-file"></a>從單一檔案載入資料

要從檔載入資料，[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*)請使用 該方法以及要載入的資料的資料模型。 因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。 若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>從多個檔案載入資料

您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。

### <a name="load-from-files-in-a-single-directory"></a>從單一目錄中的檔案載入

當所有資料檔案都在同一目錄中時，請使用 方法中的[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*)萬用字元。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>載入多個目錄中的檔案

要從多個目錄載入資料，[`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*)請使用 方法創建 。 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) 然後，使用[`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*)方法並指定各個檔路徑（無法使用萬用字元）。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>從關係資料庫載入資料

ML.NET 支援從 SQL Server、Azure SQL[`System.Data`](xref:System.Data)資料庫、Oracle、SQLite、PostgreSQL、進度、IBM DB2 等支援的各種關係資料庫載入資料。

> [!NOTE]
> 要使用`DatabaseLoader`，請參閱[系統.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet 包。

給定一個資料庫，其中具有`House`名為的表和以下架構：

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

資料可由 `HouseData` 等類別建立模型。

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

然後，在應用程式內部，創建 一`DatabaseLoader`個 。

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

定義連接字串以及要在資料庫上執行的 SQL 命令並創建`DatabaseSource`實例。 此示例使用具有檔路徑的本地 DB SQL Server 資料庫。 但是，DatabaseLoader 支援本地和雲中資料庫的任何其他有效連接字串。

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

類型類型的數位[`Real`](xref:System.Data.SqlDbType)資料必須轉換為[`Real`](xref:System.Data.SqlDbType)。 該[`Real`](xref:System.Data.SqlDbType)類型表示為單精確度浮點值或[`Single`](xref:System.Single)，ML.NET演算法預期的輸入類型。 在此示例中，`NumBed`列是資料庫中的整數。 `CAST`使用內建函數，它將轉換為[`Real`](xref:System.Data.SqlDbType)。 由於`Price`該屬性已為類型[`Real`](xref:System.Data.SqlDbType)，因此按現在的形式載入該屬性。

使用`Load`方法將資料載入到 中[`IDataView`](xref:Microsoft.ML.IDataView)。

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>從其他來源載入資料

除了載入儲存在檔案中的資料，ML.NET 支援從其他來源載入資料，其中包含但不限於：

- 記憶體內集合
- JSON/XML

請注意，當使用串流來源時，ML.NET 預期輸入的形式為記憶體內部集合。 因此，當使用像是 JSON/XML 等來源時，請務必將資料格式化成記憶體內部集合。

假設有下列記憶體內部集合：

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

使用 方法將記憶體中集合載入[`IDataView`](xref:Microsoft.ML.IDataView)到[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)中：

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)假定[`IEnumerable`](xref:System.Collections.IEnumerable)它載入的執行緒安全。

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>後續步驟

- 要清理或以其他方式處理資料，請參閱[準備用於構建模型的資料](prepare-data-ml-net.md)。
- 準備好構建模型時，請參閱[訓練和評估模型](train-machine-learning-model-ml-net.md)。
