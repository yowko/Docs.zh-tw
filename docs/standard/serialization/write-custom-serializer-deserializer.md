---
title: 如何使用撰寫自訂序列化程式和還原序列化程式 System.Text.Json
description: 瞭解如何使用命名空間撰寫 JSON 的自訂序列化程式和還原序列化程式 System.Text.Json 。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a01d3c8dd18c114ea1c3aabc402bc841a6025ffe
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439937"
---
# <a name="how-to-write-custom-serializers-and-deserializers-with-no-locsystemtextjson"></a><span data-ttu-id="61a5a-103">如何使用撰寫自訂序列化程式和還原序列化程式 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="61a5a-103">How to write custom serializers and deserializers with System.Text.Json</span></span>

<span data-ttu-id="61a5a-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器，可從 `ReadOnlySpan<byte>` 或讀取 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="61a5a-105">`Utf8JsonReader`是低層級的型別，可用來建立自訂剖析器和還原序列化程式。</span><span class="sxs-lookup"><span data-stu-id="61a5a-105">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="61a5a-106"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonReader` 幕後。</span><span class="sxs-lookup"><span data-stu-id="61a5a-106">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="61a5a-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（如、和）撰寫 UTF-8 編碼的 JSON 文字 `String` `Int32` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="61a5a-108">寫入器是一種低層級的型別，可用來建立自訂序列化程式。</span><span class="sxs-lookup"><span data-stu-id="61a5a-108">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="61a5a-109"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonWriter` 幕後。</span><span class="sxs-lookup"><span data-stu-id="61a5a-109">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="61a5a-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用建立唯讀檔案物件模型 (DOM) 的功能 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="61a5a-111">DOM 提供 JSON 承載中資料的隨機存取。</span><span class="sxs-lookup"><span data-stu-id="61a5a-111">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="61a5a-112">撰寫承載的 JSON 專案可以透過型別存取 <xref:System.Text.Json.JsonElement> 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-112">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="61a5a-113">此 `JsonElement` 類型提供陣列和物件列舉值以及 api，以將 JSON 文字轉換成常見的 .net 類型。</span><span class="sxs-lookup"><span data-stu-id="61a5a-113">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="61a5a-114">`JsonDocument` 公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。</span><span class="sxs-lookup"><span data-stu-id="61a5a-114">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="61a5a-115">下列各節說明如何使用這些工具來讀取和寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="61a5a-115">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="61a5a-116">使用 JsonDocument 存取資料</span><span class="sxs-lookup"><span data-stu-id="61a5a-116">Use JsonDocument for access to data</span></span>

<span data-ttu-id="61a5a-117">下列範例示範如何使用 <xref:System.Text.Json.JsonDocument> 類別，隨機存取 JSON 字串中的資料：</span><span class="sxs-lookup"><span data-stu-id="61a5a-117">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::

<span data-ttu-id="61a5a-118">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="61a5a-118">The preceding code:</span></span>

* <span data-ttu-id="61a5a-119">假設要分析的 JSON 是在名為的字串中 `jsonString` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-119">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="61a5a-120">計算陣列中具有屬性之物件的平均等級 `Students` `Grade` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-120">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="61a5a-121">針對沒有等級的學生指派預設等級70。</span><span class="sxs-lookup"><span data-stu-id="61a5a-121">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="61a5a-122">依每個反復專案遞增變數來計算學生數目 `count` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-122">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="61a5a-123">替代方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="61a5a-123">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::

<span data-ttu-id="61a5a-124">以下是此程式碼處理的 JSON 範例：</span><span class="sxs-lookup"><span data-stu-id="61a5a-124">Here's an example of the JSON that this code processes:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="61a5a-125">使用 JsonDocument 撰寫 JSON</span><span class="sxs-lookup"><span data-stu-id="61a5a-125">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="61a5a-126">下列範例顯示如何從撰寫 JSON <xref:System.Text.Json.JsonDocument> ：</span><span class="sxs-lookup"><span data-stu-id="61a5a-126">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::

<span data-ttu-id="61a5a-127">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="61a5a-127">The preceding code:</span></span>

* <span data-ttu-id="61a5a-128">讀取 JSON 檔案、將資料載入中 `JsonDocument` ，然後將格式化 (美觀的) JSON 寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="61a5a-128">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="61a5a-129">使用 <xref:System.Text.Json.JsonDocumentOptions> 指定允許但忽略輸入 JSON 中的批註。</span><span class="sxs-lookup"><span data-stu-id="61a5a-129">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="61a5a-130">完成時，會 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> 在寫入器上呼叫。</span><span class="sxs-lookup"><span data-stu-id="61a5a-130">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="61a5a-131">替代方式是讓寫入器在處置時自動清除。</span><span class="sxs-lookup"><span data-stu-id="61a5a-131">An alternative is to let the writer auto-flush when it's disposed.</span></span>

<span data-ttu-id="61a5a-132">以下是範例程式碼要處理的 JSON 輸入範例：</span><span class="sxs-lookup"><span data-stu-id="61a5a-132">Here's an example of JSON input to be processed by the example code:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

<span data-ttu-id="61a5a-133">結果會是下列整齊列印的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="61a5a-133">The result is the following pretty-printed JSON output:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="61a5a-134">使用 Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="61a5a-134">Use Utf8JsonWriter</span></span>

<span data-ttu-id="61a5a-135">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：</span><span class="sxs-lookup"><span data-stu-id="61a5a-135">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::

## <a name="use-utf8jsonreader"></a><span data-ttu-id="61a5a-136">使用 Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="61a5a-136">Use Utf8JsonReader</span></span>

<span data-ttu-id="61a5a-137">下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：</span><span class="sxs-lookup"><span data-stu-id="61a5a-137">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::

<span data-ttu-id="61a5a-138">上述程式碼假設 `jsonUtf8` 變數是一個位元組陣列，其中包含編碼為 utf-8 的有效 JSON。</span><span class="sxs-lookup"><span data-stu-id="61a5a-138">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="61a5a-139">使用 Utf8JsonReader 篩選資料</span><span class="sxs-lookup"><span data-stu-id="61a5a-139">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="61a5a-140">下列範例示範如何以同步方式讀取檔案，並搜尋值。</span><span class="sxs-lookup"><span data-stu-id="61a5a-140">The following example shows how to synchronously read a file, and search for a value.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::

<span data-ttu-id="61a5a-141">如需此範例的非同步版本，請參閱 [.net 範例 JSON 專案](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs)。</span><span class="sxs-lookup"><span data-stu-id="61a5a-141">For an asynchronous version of this example, see [.NET samples JSON project](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).</span></span>

<span data-ttu-id="61a5a-142">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="61a5a-142">The preceding code:</span></span>

* <span data-ttu-id="61a5a-143">假設 JSON 包含物件的陣列，而且每個物件都可以包含字串類型的 "name" 屬性。</span><span class="sxs-lookup"><span data-stu-id="61a5a-143">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="61a5a-144">計算以 "大學" 結尾的物件和 "name" 屬性值。</span><span class="sxs-lookup"><span data-stu-id="61a5a-144">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="61a5a-145">假設檔案是以 UTF-16 編碼，並將它轉碼為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="61a5a-145">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="61a5a-146">您可以 `ReadOnlySpan<byte>` 使用下列程式碼，將編碼為 utf-8 的檔案直接讀入中：</span><span class="sxs-lookup"><span data-stu-id="61a5a-146">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="61a5a-147">如果檔案包含 UTF-8 位元組順序標記 (BOM) ，請先將其移除，再將位元組傳遞給 `Utf8JsonReader` ，因為讀取器預期文字。</span><span class="sxs-lookup"><span data-stu-id="61a5a-147">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="61a5a-148">否則，會將 BOM 視為不正確 JSON，而讀取器會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61a5a-148">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="61a5a-149">以下是上述程式碼可以讀取的 JSON 範例。</span><span class="sxs-lookup"><span data-stu-id="61a5a-149">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="61a5a-150">產生的摘要訊息是「2個以上的名稱的結尾是 ' 大學 '」：</span><span class="sxs-lookup"><span data-stu-id="61a5a-150">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="61a5a-151">使用 Utf8JsonReader 從串流讀取</span><span class="sxs-lookup"><span data-stu-id="61a5a-151">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="61a5a-152">當讀取大型檔案 (gb 或更大的大小時，例如) ，您可能會想要避免必須一次將整個檔案載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="61a5a-152">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="61a5a-153">在此案例中，您可以使用 <xref:System.IO.FileStream> 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-153">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="61a5a-154">使用 `Utf8JsonReader` 從資料流程讀取時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="61a5a-154">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="61a5a-155">包含部分 JSON 承載的緩衝區必須至少與它內最大的 JSON 權杖一樣大，讓讀取器可以進行向前的進度。</span><span class="sxs-lookup"><span data-stu-id="61a5a-155">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="61a5a-156">緩衝區至少必須和 JSON 內的最大泛空白字元順序一樣大。</span><span class="sxs-lookup"><span data-stu-id="61a5a-156">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="61a5a-157">讀取器不會追蹤已讀取的資料，直到它完全讀取 JSON 承載中的下一個 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-157">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="61a5a-158">因此，當緩衝區中有剩餘的位元組時，您必須再次將它們傳遞給讀取器。</span><span class="sxs-lookup"><span data-stu-id="61a5a-158">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="61a5a-159">您可以使用 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> 來判斷剩餘的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="61a5a-159">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="61a5a-160">下列程式碼說明如何從資料流程讀取。</span><span class="sxs-lookup"><span data-stu-id="61a5a-160">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="61a5a-161">此範例會顯示 <xref:System.IO.MemoryStream> 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-161">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="61a5a-162">類似的程式碼可搭配使用 <xref:System.IO.FileStream> ，但在 `FileStream` 開始時包含 utf-8 BOM 時除外。</span><span class="sxs-lookup"><span data-stu-id="61a5a-162">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="61a5a-163">在這種情況下，您必須先從緩衝區中去除這三個位元組，再將剩餘的位元組傳遞給 `Utf8JsonReader` 。</span><span class="sxs-lookup"><span data-stu-id="61a5a-163">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="61a5a-164">否則，讀取器會擲回例外狀況，因為 BOM 不會被視為 JSON 的有效部分。</span><span class="sxs-lookup"><span data-stu-id="61a5a-164">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="61a5a-165">範例程式碼的開頭為 4 KB 的緩衝區，每次發現大小不夠大而無法容納完整的 JSON 權杖時，便會將緩衝區大小加倍，讓讀取器在 JSON 承載上進行向前處理。</span><span class="sxs-lookup"><span data-stu-id="61a5a-165">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="61a5a-166">只有當您設定非常小的初始緩衝區大小（例如10個位元組）時，程式碼片段中提供的 JSON 範例才會觸發緩衝區大小的增加。</span><span class="sxs-lookup"><span data-stu-id="61a5a-166">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="61a5a-167">如果您將初始緩衝區大小設定為10，則 `Console.WriteLine` 語句會說明緩衝區大小增加的原因和影響。</span><span class="sxs-lookup"><span data-stu-id="61a5a-167">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="61a5a-168">在 4 KB 的初始緩衝區大小中，會顯示整個範例 JSON `Console.WriteLine` ，而且永遠不需要增加緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="61a5a-168">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::

<span data-ttu-id="61a5a-169">先前的範例不會對緩衝區所能成長的大小設定限制。</span><span class="sxs-lookup"><span data-stu-id="61a5a-169">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="61a5a-170">如果權杖大小太大，程式碼可能會失敗併發生 <xref:System.OutOfMemoryException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61a5a-170">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="61a5a-171">如果 JSON 包含的權杖大約是 1 GB 或更大的大小，就會發生這種情況，因為 1 GB 的大小加倍會導致大小太大而無法放入 `int32` 緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="61a5a-171">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="see-also"></a><span data-ttu-id="61a5a-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61a5a-172">See also</span></span>

* [<span data-ttu-id="61a5a-173">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="61a5a-173">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="61a5a-174">如何自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="61a5a-174">How to customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="61a5a-175">如何撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="61a5a-175">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="61a5a-176">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="61a5a-176">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
