---
title: 在 ML.NET 處理期間檢查中繼資料
description: 了解如何在 ML.NET 中，於 ML.NET 機器學習服務管線載入、處理和模型定型步驟期間檢查中繼資料。
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977094"
---
# <a name="inspect-intermediate-data-during-processing"></a>在處理期間檢查中繼資料

了解如何在 ML.NET 中，於載入、處理和模型定型步驟期間檢查中繼資料。 中繼資料是機器學習服務管線中每個階段的輸出。

可以通過各種方式以ML.NET檢查中間資料，如下面表示[`IDataView`](xref:Microsoft.ML.IDataView)的資料，該資料載入到 中所示。

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

檢查 的最快方法之一[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)是將轉換為 。 轉換 以[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法。

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

如果只需要訪問資料或特定索引的一部分，請使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)參數值並將其設置為`reuseRowObject``false`，以便為資料集中的每個請求行創建新物件。 然後，將[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)轉換為數組或清單。

> [!WARNING]
> 將 的結果[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)轉換為數組或清單會將所有請求[`IDataView`](xref:Microsoft.ML.IDataView)的行載入到可能影響性能的記憶體中。

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

在模型構建過程中的任意點，[`IDataView`](xref:Microsoft.ML.IDataView)可以使用[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*)方法訪問 該方法[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*)將單個列中的所有值作為 返回[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)。

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>一次檢查一列 IDataView 值

[`IDataView`](xref:Microsoft.ML.IDataView)是懶惰的評估。 要反覆運算 的[`IDataView`](xref:Microsoft.ML.IDataView)行，而不轉換為 本文檔前面各節中[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)所示的 行，請使用[`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor)[`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*)方法並傳入 資料[DataViewSchema](xref:Microsoft.ML.DataViewSchema)[`IDataView`](xref:Microsoft.ML.IDataView)視圖架構作為參數創建 。 然後，要反覆運算行，請使用[`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*)游標方法以及[`ValueGetter`](xref:Microsoft.ML.ValueGetter%601)委託從每個列中提取相應的值。

> [!IMPORTANT]
> 出於性能目的，ML.NET中的向量使用[`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601)而不是本機集合類型（即`Vector`。`float[]`

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

模型建置流程是實驗性且反覆性的。 要預覽在資料子集上預處理或訓練機器學習模型後資料的外觀，請使用 返回[`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*)的方法[`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)返回 。 結果是具有`ColumnView`和`RowView`屬性的物件，該物件既是[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)和 屬性，也包含特定列或行中的值。 使用 `maxRows` 參數指定要套用轉換的資料列數。

![資料偵錯工具預覽物件](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

檢查 的結果[`IDataView`](xref:Microsoft.ML.IDataView)類似于以下內容：

![資料偵錯工具預覽資料列檢視](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
