---
title: 在 ML.NET 處理期間檢查中繼資料
description: 了解如何在 ML.NET 中，於 ML.NET 機器學習服務管線載入、處理和模型定型步驟期間檢查中繼資料。
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: d6ddeb523fb229eb0ebc9c2f22809312060e4266
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402381"
---
# <a name="inspect-intermediate-data-during-processing"></a>在處理期間檢查中繼資料

了解如何在 ML.NET 中，於載入、處理和模型定型步驟期間檢查中繼資料。 中繼資料是機器學習服務管線中每個階段的輸出。

您可以在 ML.NET 中透過各種方式檢查與以下內容相似且會載入 [`IDataView`](xref:Microsoft.ML.IDataView) 的中繼資料。
 
```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a>將 IDataView 轉換成 IEnumerable

其中一個檢查 [`IDataView`](xref:Microsoft.ML.IDataView) 最快速的方式便是將它轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)。 若要將 [`IDataView`](xref:Microsoft.ML.IDataView) 轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)，請使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 方法。 

若要最佳化效能，請將 `reuseRowObject` 設為 `true`。 如此會使用目前資料列的資料，在評估時才延遲填入相同的物件，而非為資料集中的每個資料列建立新物件。

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

## <a name="accessing-specific-indices-with-ienumerable"></a>使用 IEnumerable 存取特定索引

若您只需要存取一部分的資料或特定索引，請使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)，並將 `reuseRowObject` 參數的值設為 `false`，為資料集中所要求的每個資料列建立新物件。 接著，將 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 轉換成陣列或清單。

> [!WARNING]
> 將 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 的結果轉換成陣列或清單，會將所有要求的 [`IDataView`](xref:Microsoft.ML.IDataView) 資料列載入記憶體，而這可能會影響效能。

一旦所有集合都已建立完成，您便可以在資料上執行作業。 以下程式碼片段會擷取資料集中的前三個資料列，並計算目前的平均價格。

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
``` 

## <a name="inspect-values-in-a-single-column"></a>檢查單一資料行中的值

在模型建置流程的任何一個時間點，[`IDataView`](xref:Microsoft.ML.IDataView) 單一資料行中的值可透過使用 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 方法進行存取。 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 方法會將單一資料行中的所有值作為 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 傳回。

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>一次檢查一列 IDataView 值

[`IDataView`](xref:Microsoft.ML.IDataView) 會延遲評估。 若要逐一查看 [`IDataView`](xref:Microsoft.ML.IDataView)，而不將其轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)(如本文件先前章節所示範)，請使用 [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) 方法並將您 [`IDataView`](xref:Microsoft.ML.IDataView) 的 [DataViewSchema](xref:Microsoft.ML.DataViewSchema) 作為參數傳遞，來建立 [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor)。 然後，若要逐一查看資料列，請使用 [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) 指標方法，搭配 [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) 委派來從每個資料行擷取個別的值。

> [!IMPORTANT]
> 基於效能考量，ML.NET 中的向量會使用 [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601)，而非原生集合類型 (即 `Vector`、`float[]` 等)。 

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);
    
    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>預覽預先處理結果或針對資料子集的定型結果

> [!WARNING]
> 請不要在生產程式碼中使用 `Preview`，因為它旨在用於偵錯，可能會降低效能。

模型建置流程是實驗性且反覆性的。 若要預覽預先處理之後或針對資料子集定型機器學習模型之後資料的結果，請使用 [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) 方法，該方法會傳回 [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)。 結果是一個具備 `ColumnView` 和 `RowView` 屬性的物件，這兩個屬性都是 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)，且包含特定資料行或資料列中的值。 使用 `maxRows` 參數指定要套用轉換的資料列數。

![資料偵錯工具預覽物件](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

檢查 [`IDataView`](xref:Microsoft.ML.IDataView) 的結果看起來會與下列內容相似：

![資料偵錯工具預覽資料列檢視](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
