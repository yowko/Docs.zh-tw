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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="02ea7-103">在處理期間檢查中繼資料</span><span class="sxs-lookup"><span data-stu-id="02ea7-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="02ea7-104">了解如何在 ML.NET 中，於載入、處理和模型定型步驟期間檢查中繼資料。</span><span class="sxs-lookup"><span data-stu-id="02ea7-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="02ea7-105">中繼資料是機器學習服務管線中每個階段的輸出。</span><span class="sxs-lookup"><span data-stu-id="02ea7-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="02ea7-106">您 [`IDataView`](xref:Microsoft.ML.IDataView) 可以在 ML.NET 中以各種方式檢查中繼資料（如下所示），並將其載入至。</span><span class="sxs-lookup"><span data-stu-id="02ea7-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="02ea7-107">將 IDataView 轉換成 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="02ea7-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="02ea7-108">其中一個最快的檢查方式 [`IDataView`](xref:Microsoft.ML.IDataView) 是將它轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 。</span><span class="sxs-lookup"><span data-stu-id="02ea7-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="02ea7-109">轉換會 [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 方法。</span><span class="sxs-lookup"><span data-stu-id="02ea7-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method.</span></span>

<span data-ttu-id="02ea7-110">若要最佳化效能，請將 `reuseRowObject` 設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="02ea7-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="02ea7-111">如此會使用目前資料列的資料，在評估時才延遲填入相同的物件，而非為資料集中的每個資料列建立新物件。</span><span class="sxs-lookup"><span data-stu-id="02ea7-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="02ea7-112">使用 IEnumerable 存取特定索引</span><span class="sxs-lookup"><span data-stu-id="02ea7-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="02ea7-113">如果您只需要存取部分資料或特定的索引，請使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 並將 `reuseRowObject` 參數值設定為，以 `false` 針對資料集中每個要求的資料列建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="02ea7-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="02ea7-114">然後，將轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 陣列或清單。</span><span class="sxs-lookup"><span data-stu-id="02ea7-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="02ea7-115">將的結果轉換成 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 陣列或清單，會將所有要求的資料 [`IDataView`](xref:Microsoft.ML.IDataView) 列載入記憶體中，而這可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="02ea7-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="02ea7-116">一旦所有集合都已建立完成，您便可以在資料上執行作業。</span><span class="sxs-lookup"><span data-stu-id="02ea7-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="02ea7-117">以下程式碼片段會擷取資料集中的前三個資料列，並計算目前的平均價格。</span><span class="sxs-lookup"><span data-stu-id="02ea7-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="02ea7-118">檢查單一資料行中的值</span><span class="sxs-lookup"><span data-stu-id="02ea7-118">Inspect values in a single column</span></span>

<span data-ttu-id="02ea7-119">在模型建立程式中的任何時間點， [`IDataView`](xref:Microsoft.ML.IDataView) 都可以使用方法來存取單一資料行中的值 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) 。</span><span class="sxs-lookup"><span data-stu-id="02ea7-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) method.</span></span> <span data-ttu-id="02ea7-120">方法會傳回 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) 單一資料行中的所有值做為 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 。</span><span class="sxs-lookup"><span data-stu-id="02ea7-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="02ea7-121">一次檢查一列 IDataView 值</span><span class="sxs-lookup"><span data-stu-id="02ea7-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="02ea7-122">[`IDataView`](xref:Microsoft.ML.IDataView) 延遲評估。</span><span class="sxs-lookup"><span data-stu-id="02ea7-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="02ea7-123">若要逐一查看的資料列 [`IDataView`](xref:Microsoft.ML.IDataView) ，而不是轉換為 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，如本檔先前章節所示，請使用方法來建立， [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) 並將您的 [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor%2A) [DataViewSchema](xref:Microsoft.ML.DataViewSchema) 傳入 [`IDataView`](xref:Microsoft.ML.IDataView) 做為參數。</span><span class="sxs-lookup"><span data-stu-id="02ea7-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor%2A) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="02ea7-124">然後，若要逐一查看資料列，請使用 [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext%2A) cursor 方法和 [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) 委派，從每個資料行中解壓縮各自的值。</span><span class="sxs-lookup"><span data-stu-id="02ea7-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext%2A) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02ea7-125">基於效能考慮，ML.NET 中的向量 [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) 會使用，而不是原生集合類型 (也就是 `Vector` `float[]`) 。</span><span class="sxs-lookup"><span data-stu-id="02ea7-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="02ea7-126">預覽預先處理結果或針對資料子集的定型結果</span><span class="sxs-lookup"><span data-stu-id="02ea7-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="02ea7-127">請不要在生產程式碼中使用 `Preview`，因為它旨在用於偵錯，可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="02ea7-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="02ea7-128">模型建置流程是實驗性且反覆性的。</span><span class="sxs-lookup"><span data-stu-id="02ea7-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="02ea7-129">若要在預先處理或定型資料子集上的機器學習模型之後，預覽哪些資料看起來像這樣，請使用傳回的 [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) 方法 [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview) 。</span><span class="sxs-lookup"><span data-stu-id="02ea7-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="02ea7-130">結果是具有和屬性的物件， `ColumnView` `RowView` 這些屬性都是 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，而且會包含特定資料行或資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="02ea7-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="02ea7-131">使用 `maxRows` 參數指定要套用轉換的資料列數。</span><span class="sxs-lookup"><span data-stu-id="02ea7-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![資料偵錯工具預覽物件](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="02ea7-133">檢查的結果 [`IDataView`](xref:Microsoft.ML.IDataView) 看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="02ea7-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![資料偵錯工具預覽資料列檢視](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
