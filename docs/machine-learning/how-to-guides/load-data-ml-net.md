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
# <a name="load-data-from-files-and-other-sources"></a>從檔案和其他來源載入資料

瞭解如何使用 API 將資料載入至 ML.NET，以進行處理和定型。 資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。

如果您是使用模型建立器，請參閱將 [定型資料載入模型](load-data-model-builder.md)產生器。

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

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)屬性會指定屬性的資料行索引。

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 只有從檔案載入資料時才需要。

將資料行作為以下項目載入：

- 個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。
- 以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。

如果您有 vector 屬性，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用至資料模型中的屬性。 請務必注意，向量中的所有項目都必須是相同類型。 將資料行保持分離可讓您更輕易且具備彈性地進行特徵工程，但針對極為大量的資料行，在每一個資料行上進行作業會影響定型速度。

ML.NET 會透過資料行名稱運作。 如果您想要將資料行的名稱變更為屬性名稱以外的名稱，請使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性。 在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。 但是，對於資料處理和建立機器學習模型，ML.NET 會使用屬性中提供的值來覆寫及參考屬性 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 。

## <a name="load-data-from-a-single-file"></a>從單一檔案載入資料

若要從檔案載入資料，請使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 方法以及要載入之資料的資料模型。 因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。 若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>從多個檔案載入資料

您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。

### <a name="load-from-files-in-a-single-directory"></a>從單一目錄中的檔案載入

當所有的資料檔案都在相同的目錄中時，在方法中使用萬用字元 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>載入多個目錄中的檔案

若要從多個目錄載入資料，請使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) 方法來建立 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) 。 然後，使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) 方法，並指定個別的檔案路徑， (無法使用萬用字元) 。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>從關係資料庫載入資料

ML.NET 支援從所支援的各種關係資料庫載入資料， [`System.Data`](xref:System.Data) 包括 SQL Server、Azure SQL Database、Oracle、SQLite、于 postgresql、進度、IBM DB2 等等。

> [!NOTE]
> 若要使用 `DatabaseLoader` ，請參考 [SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet 套件。

假設資料庫具有名為的資料表 `House` 和下列架構：

```sql
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

然後，在您的應用程式內建立 `DatabaseLoader` 。

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

定義您的連接字串，以及要在資料庫上執行的 SQL 命令，並建立 `DatabaseSource` 實例。 這個範例會使用 LocalDB SQL Server 資料庫與檔案路徑。 不過，DatabaseLoader 對內部部署和雲端中的資料庫支援任何其他有效的連接字串。

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

不是類型的數值資料必須 [`Real`](xref:System.Data.SqlDbType) 轉換成 [`Real`](xref:System.Data.SqlDbType) 。 此 [`Real`](xref:System.Data.SqlDbType) 類型會表示為單精確度浮點數或 [`Single`](xref:System.Single) ML.NET 演算法預期的輸入類型。 在此範例中， `NumBed` 資料行是資料庫中的整數。 使用 `CAST` 內建函數，它會轉換成 [`Real`](xref:System.Data.SqlDbType) 。 因為屬性已經是型別，所以 `Price` [`Real`](xref:System.Data.SqlDbType) 會依原樣載入。

您 `Load` 可以使用方法，將資料載入至 [`IDataView`](xref:Microsoft.ML.IDataView) 。

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

使用方法將記憶體中的集合載入中 [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) ：

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) 假設 [`IEnumerable`](xref:System.Collections.IEnumerable) 它載入自的是安全線程。

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>後續步驟

- 若要清除或以其他方式處理資料，請參閱 [準備用來建立模型的資料](prepare-data-ml-net.md)。
- 當您準備好建立模型時，請參閱 [定型和評估模型](train-machine-learning-model-ml-net.md)。
