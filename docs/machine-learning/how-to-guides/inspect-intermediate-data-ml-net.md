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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="dd3bb-103">在處理期間檢查中繼資料</span><span class="sxs-lookup"><span data-stu-id="dd3bb-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="dd3bb-104">了解如何在 ML.NET 中，於載入、處理和模型定型步驟期間檢查中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="dd3bb-105">中繼資料是機器學習服務管線中每個階段的輸出。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="dd3bb-106">可以通過各種方式以ML.NET檢查中間資料，如下面表示[`IDataView`](xref:Microsoft.ML.IDataView)的資料，該資料載入到 中所示。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="dd3bb-107">將 IDataView 轉換成 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="dd3bb-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="dd3bb-108">檢查 的最快方法之一[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)是將轉換為 。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="dd3bb-109">轉換 以[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="dd3bb-110">若要最佳化效能，請將 `reuseRowObject` 設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="dd3bb-111">如此會使用目前資料列的資料，在評估時才延遲填入相同的物件，而非為資料集中的每個資料列建立新物件。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="dd3bb-112">使用 IEnumerable 存取特定索引</span><span class="sxs-lookup"><span data-stu-id="dd3bb-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="dd3bb-113">如果只需要訪問資料或特定索引的一部分，請使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)參數值並將其設置為`reuseRowObject``false`，以便為資料集中的每個請求行創建新物件。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="dd3bb-114">然後，將[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)轉換為數組或清單。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="dd3bb-115">將 的結果[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)轉換為數組或清單會將所有請求[`IDataView`](xref:Microsoft.ML.IDataView)的行載入到可能影響性能的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="dd3bb-116">一旦所有集合都已建立完成，您便可以在資料上執行作業。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="dd3bb-117">以下程式碼片段會擷取資料集中的前三個資料列，並計算目前的平均價格。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="dd3bb-118">檢查單一資料行中的值</span><span class="sxs-lookup"><span data-stu-id="dd3bb-118">Inspect values in a single column</span></span>

<span data-ttu-id="dd3bb-119">在模型構建過程中的任意點，[`IDataView`](xref:Microsoft.ML.IDataView)可以使用[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*)方法訪問</span><span class="sxs-lookup"><span data-stu-id="dd3bb-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="dd3bb-120">該方法[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*)將單個列中的所有值作為 返回[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="dd3bb-121">一次檢查一列 IDataView 值</span><span class="sxs-lookup"><span data-stu-id="dd3bb-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="dd3bb-122">[`IDataView`](xref:Microsoft.ML.IDataView)是懶惰的評估。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="dd3bb-123">要反覆運算 的[`IDataView`](xref:Microsoft.ML.IDataView)行，而不轉換為 本文檔前面各節中[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)所示的 行，請使用[`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor)[`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*)方法並傳入 資料[DataViewSchema](xref:Microsoft.ML.DataViewSchema)[`IDataView`](xref:Microsoft.ML.IDataView)視圖架構作為參數創建 。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="dd3bb-124">然後，要反覆運算行，請使用[`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*)游標方法以及[`ValueGetter`](xref:Microsoft.ML.ValueGetter%601)委託從每個列中提取相應的值。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd3bb-125">出於性能目的，ML.NET中的向量使用[`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601)而不是本機集合類型（即`Vector`。`float[]`</span><span class="sxs-lookup"><span data-stu-id="dd3bb-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="dd3bb-126">預覽預先處理結果或針對資料子集的定型結果</span><span class="sxs-lookup"><span data-stu-id="dd3bb-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="dd3bb-127">請不要在生產程式碼中使用 `Preview`，因為它旨在用於偵錯，可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="dd3bb-128">模型建置流程是實驗性且反覆性的。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="dd3bb-129">要預覽在資料子集上預處理或訓練機器學習模型後資料的外觀，請使用 返回[`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*)的方法[`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)返回 。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="dd3bb-130">結果是具有`ColumnView`和`RowView`屬性的物件，該物件既是[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)和 屬性，也包含特定列或行中的值。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="dd3bb-131">使用 `maxRows` 參數指定要套用轉換的資料列數。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![資料偵錯工具預覽物件](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="dd3bb-133">檢查 的結果[`IDataView`](xref:Microsoft.ML.IDataView)類似于以下內容：</span><span class="sxs-lookup"><span data-stu-id="dd3bb-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![資料偵錯工具預覽資料列檢視](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
