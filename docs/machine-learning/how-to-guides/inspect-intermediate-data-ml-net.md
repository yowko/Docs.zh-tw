---
title: 在 ML.NET 處理期間檢查中繼資料
description: 了解如何在 ML.NET 中，於 ML.NET 機器學習服務管線載入、處理和模型定型步驟期間檢查中繼資料。
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4f168653297594a604e6f381947f31cba5376178
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679621"
---
# <a name="inspect-intermediate-data-during-processing"></a>在處理期間檢查中繼資料

了解如何在 ML.NET 中，於載入、處理和模型定型步驟期間檢查中繼資料。 中繼資料是機器學習服務管線中每個階段的輸出。

您 [`IDataView`](xref:Microsoft.ML.IDataView) 可以在 ML.NET 中以各種方式檢查中繼資料（如下所示），並將其載入至。

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

其中一個最快的檢查方式 [`IDataView`](xref:Microsoft.ML.IDataView) 是將它轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 。 轉換會 [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 方法。

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

如果您只需要存取部分資料或特定的索引，請使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 並將 `reuseRowObject` 參數值設定為，以 `false` 針對資料集中每個要求的資料列建立新的物件。 然後，將轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 陣列或清單。

> [!WARNING]
> 將的結果轉換成 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 陣列或清單，會將所有要求的資料 [`IDataView`](xref:Microsoft.ML.IDataView) 列載入記憶體中，而這可能會影響效能。

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

在模型建立程式中的任何時間點， [`IDataView`](xref:Microsoft.ML.IDataView) 都可以使用方法來存取單一資料行中的值 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) 。 方法會傳回 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) 單一資料行中的所有值做為 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 。

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>一次檢查一列 IDataView 值

[`IDataView`](xref:Microsoft.ML.IDataView) 延遲評估。 若要逐一查看的資料列 [`IDataView`](xref:Microsoft.ML.IDataView) ，而不是轉換為 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，如本檔先前章節所示，請使用方法來建立， [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) 並將您的 [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor%2A) [DataViewSchema](xref:Microsoft.ML.DataViewSchema) 傳入 [`IDataView`](xref:Microsoft.ML.IDataView) 做為參數。 然後，若要逐一查看資料列，請使用 [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext%2A) cursor 方法和 [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) 委派，從每個資料行中解壓縮各自的值。

> [!IMPORTANT]
> 基於效能考慮，ML.NET 中的向量 [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) 會使用，而不是原生集合類型 (也就是 `Vector` `float[]`) 。

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

模型建置流程是實驗性且反覆性的。 若要在預先處理或定型資料子集上的機器學習模型之後，預覽哪些資料看起來像這樣，請使用傳回的 [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) 方法 [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview) 。 結果是具有和屬性的物件， `ColumnView` `RowView` 這些屬性都是 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，而且會包含特定資料行或資料列中的值。 使用 `maxRows` 參數指定要套用轉換的資料列數。

![資料偵錯工具預覽物件](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

檢查的結果 [`IDataView`](xref:Microsoft.ML.IDataView) 看起來會如下所示：

![資料偵錯工具預覽資料列檢視](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
