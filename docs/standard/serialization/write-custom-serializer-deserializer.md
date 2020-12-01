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
# <a name="how-to-write-custom-serializers-and-deserializers-with-no-locsystemtextjson"></a>如何使用撰寫自訂序列化程式和還原序列化程式 System.Text.Json

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> 是適用于 UTF-8 編碼 JSON 文字的高效能、低配置、順向讀取器，可從 `ReadOnlySpan<byte>` 或讀取 `ReadOnlySequence<byte>` 。 `Utf8JsonReader`是低層級的型別，可用來建立自訂剖析器和還原序列化程式。 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonReader` 幕後。

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> 是一種高效能的方式，可從常見的 .NET 類型（如、和）撰寫 UTF-8 編碼的 JSON 文字 `String` `Int32` `DateTime` 。 寫入器是一種低層級的型別，可用來建立自訂序列化程式。 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>方法會使用在 `Utf8JsonWriter` 幕後。

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> 提供使用建立唯讀檔案物件模型 (DOM) 的功能 `Utf8JsonReader` 。 DOM 提供 JSON 承載中資料的隨機存取。 撰寫承載的 JSON 專案可以透過型別存取 <xref:System.Text.Json.JsonElement> 。 此 `JsonElement` 類型提供陣列和物件列舉值以及 api，以將 JSON 文字轉換成常見的 .net 類型。 `JsonDocument` 公開 <xref:System.Text.Json.JsonDocument.RootElement> 屬性。

下列各節說明如何使用這些工具來讀取和寫入 JSON。

## <a name="use-jsondocument-for-access-to-data"></a>使用 JsonDocument 存取資料

下列範例示範如何使用 <xref:System.Text.Json.JsonDocument> 類別，隨機存取 JSON 字串中的資料：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::

上述程式碼：

* 假設要分析的 JSON 是在名為的字串中 `jsonString` 。
* 計算陣列中具有屬性之物件的平均等級 `Students` `Grade` 。
* 針對沒有等級的學生指派預設等級70。
* 依每個反復專案遞增變數來計算學生數目 `count` 。 替代方法是呼叫 <xref:System.Text.Json.JsonElement.GetArrayLength%2A> ，如下列範例所示：

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::

以下是此程式碼處理的 JSON 範例：

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a>使用 JsonDocument 撰寫 JSON

下列範例顯示如何從撰寫 JSON <xref:System.Text.Json.JsonDocument> ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::

上述程式碼：

* 讀取 JSON 檔案、將資料載入中 `JsonDocument` ，然後將格式化 (美觀的) JSON 寫入檔案。
* 使用 <xref:System.Text.Json.JsonDocumentOptions> 指定允許但忽略輸入 JSON 中的批註。
* 完成時，會 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> 在寫入器上呼叫。 替代方式是讓寫入器在處置時自動清除。

以下是範例程式碼要處理的 JSON 輸入範例：

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

結果會是下列整齊列印的 JSON 輸出：

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a>使用 Utf8JsonWriter

下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonWriter> 類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::

## <a name="use-utf8jsonreader"></a>使用 Utf8JsonReader

下列範例顯示如何使用 <xref:System.Text.Json.Utf8JsonReader> 類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::

上述程式碼假設 `jsonUtf8` 變數是一個位元組陣列，其中包含編碼為 utf-8 的有效 JSON。

### <a name="filter-data-using-utf8jsonreader"></a>使用 Utf8JsonReader 篩選資料

下列範例示範如何以同步方式讀取檔案，並搜尋值。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::

如需此範例的非同步版本，請參閱 [.net 範例 JSON 專案](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs)。

上述程式碼：

* 假設 JSON 包含物件的陣列，而且每個物件都可以包含字串類型的 "name" 屬性。
* 計算以 "大學" 結尾的物件和 "name" 屬性值。
* 假設檔案是以 UTF-16 編碼，並將它轉碼為 UTF-8。 您可以 `ReadOnlySpan<byte>` 使用下列程式碼，將編碼為 utf-8 的檔案直接讀入中：

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  如果檔案包含 UTF-8 位元組順序標記 (BOM) ，請先將其移除，再將位元組傳遞給 `Utf8JsonReader` ，因為讀取器預期文字。 否則，會將 BOM 視為不正確 JSON，而讀取器會擲回例外狀況。

以下是上述程式碼可以讀取的 JSON 範例。 產生的摘要訊息是「2個以上的名稱的結尾是 ' 大學 '」：

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a>使用 Utf8JsonReader 從串流讀取

當讀取大型檔案 (gb 或更大的大小時，例如) ，您可能會想要避免必須一次將整個檔案載入記憶體中。 在此案例中，您可以使用 <xref:System.IO.FileStream> 。

使用 `Utf8JsonReader` 從資料流程讀取時，適用下列規則：

* 包含部分 JSON 承載的緩衝區必須至少與它內最大的 JSON 權杖一樣大，讓讀取器可以進行向前的進度。
* 緩衝區至少必須和 JSON 內的最大泛空白字元順序一樣大。
* 讀取器不會追蹤已讀取的資料，直到它完全讀取 JSON 承載中的下一個 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> 。 因此，當緩衝區中有剩餘的位元組時，您必須再次將它們傳遞給讀取器。 您可以使用 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> 來判斷剩餘的位元組數目。

下列程式碼說明如何從資料流程讀取。 此範例會顯示 <xref:System.IO.MemoryStream> 。 類似的程式碼可搭配使用 <xref:System.IO.FileStream> ，但在 `FileStream` 開始時包含 utf-8 BOM 時除外。 在這種情況下，您必須先從緩衝區中去除這三個位元組，再將剩餘的位元組傳遞給 `Utf8JsonReader` 。 否則，讀取器會擲回例外狀況，因為 BOM 不會被視為 JSON 的有效部分。

範例程式碼的開頭為 4 KB 的緩衝區，每次發現大小不夠大而無法容納完整的 JSON 權杖時，便會將緩衝區大小加倍，讓讀取器在 JSON 承載上進行向前處理。 只有當您設定非常小的初始緩衝區大小（例如10個位元組）時，程式碼片段中提供的 JSON 範例才會觸發緩衝區大小的增加。 如果您將初始緩衝區大小設定為10，則 `Console.WriteLine` 語句會說明緩衝區大小增加的原因和影響。 在 4 KB 的初始緩衝區大小中，會顯示整個範例 JSON `Console.WriteLine` ，而且永遠不需要增加緩衝區大小。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::

先前的範例不會對緩衝區所能成長的大小設定限制。 如果權杖大小太大，程式碼可能會失敗併發生 <xref:System.OutOfMemoryException> 例外狀況。 如果 JSON 包含的權杖大約是 1 GB 或更大的大小，就會發生這種情況，因為 1 GB 的大小加倍會導致大小太大而無法放入 `int32` 緩衝區中。

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [如何自訂字元編碼](system-text-json-character-encoding.md)
* [如何撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
