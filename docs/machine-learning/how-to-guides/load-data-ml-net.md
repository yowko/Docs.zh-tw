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
# <a name="load-data-from-files-and-other-sources"></a>從檔案和其他來源載入資料

此操作說明教學會示範如何將資料載入 ML.NET 以進行處理和定型。 資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。

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

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 屬性會指定您屬性的資料行索引。

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 只有在從檔案載入資料時才需要。

將資料行作為以下項目載入：

- 個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。
- 以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。

若您擁有向量屬性，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用到您資料模型中的屬性。 請務必注意，向量中的所有項目都必須是相同類型。 將資料行保持分離可讓您更輕易且具備彈性地進行特徵工程，但針對極為大量的資料行，在每一個資料行上進行作業會影響定型速度。

ML.NET 會透過資料行名稱運作。 若您想要將資料行名稱變更為屬性名稱之外的名稱，請使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性。 在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。 但是，針對資料處理和建置機器學習模型，ML.NET 會使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性中提供的值來覆寫及參考屬性。

## <a name="load-data-from-a-single-file"></a>從單一檔案載入資料

若要從檔案載入資料，請搭配要載入其資料的資料模型使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法。 因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。 若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>從多個檔案載入資料

您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。

### <a name="load-from-files-in-a-single-directory"></a>從單一目錄中的檔案載入

當您所有的資料檔案都位於相同目錄時，請在 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法中使用萬用字元。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>載入多個目錄中的檔案

若要從多個目錄載入資料，請使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) 方法來建立 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)。 然後，請使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) 方法並指定個別檔案路徑 (無法使用萬用字元)。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>從關係資料庫載入資料

> [!NOTE]
> DatabaseLoader 目前為預覽狀態。 它可以藉由參考[SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet[套件的方式](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview)來使用。

ML.NET 支援從支援[`System.Data`](xref:System.Data)的各種關係資料庫載入資料，其中包括 SQL Server、Azure SQL Database、Oracle、SQLite、于 postgresql、進度、IBM DB2 及其他許多。

假設資料庫具有名為`House`的資料表和下列架構：

```SQL
CREATE TABLE [House] (
    [HouseId] int NOT NULL IDENTITY,
    [Size] real NOT NULL,
    [Price] real NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

資料可由 `HouseData` 等類別建立模型。

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float Price { get; set; }
}
```

然後，在您的應用程式內建立`DatabaseLoader`。

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

定義您的連接字串，以及要在資料庫上執行的 SQL 命令，並建立`DatabaseSource`實例。 這個範例會使用具有檔案路徑的 LocalDB SQL Server 資料庫。 不過，DatabaseLoader 會針對內部部署和雲端中的資料庫支援任何其他有效的連接字串。

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size,Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance,connectionString,sqlCommand);
```

最後，使用`Load`方法將資料載入[`IDataView`](xref:Microsoft.ML.IDataView)中。

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

請使用 [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 方法將記憶體內部集合載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 假設它載入的 [`IEnumerable`](xref:System.Collections.IEnumerable) 是安全執行緒。

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
