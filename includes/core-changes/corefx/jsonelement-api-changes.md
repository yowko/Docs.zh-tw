---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237316"
---
### <a name="jsonelement-api-changes"></a>JsonElement API 變更

從 .NET Core 3.0 Preview 7 開始，部分 @no__t 0 Api 已變更為允許更輕鬆的探索和更高的可用性。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.0 Preview 7 中，<xref:System.Text.Json.JsonElement> Api 已依照下列方式變更，以允許更容易探索及使用更高的可用性。

1. 已從 <xref:System.Text.Json.JsonElement> 移除所有的 `WriteProperty` 方法多載。 這會影響程式碼，如下所示：

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. `WriteValue` 已重新命名為 <xref:System.Text.Json.JsonElement.WriteTo%2A>。 這會影響程式碼，如下所示：

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> 現在會在其方法參數 `null` 時擲回 <xref:System.ArgumentNullException>。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 7

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼受到這些變更的影響，您可以執行下列動作：

- @No__t-1 中沒有適用于 @no__t 0 多載的替代 API。 相反地，您可以呼叫其中一個 <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> 多載以及 <xref:System.Text.Json.JsonElement.WriteTo%2A> 方法，以達到相同的結果。 例如:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- 將 `WriteValue` 方法重新命名為 <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>。 方法參數會保持不變。 例如，先前的程式碼應該變更為下列內容：

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- 處理 <xref:System.Text.Json.JsonElement.WriteTo%2A> 方法的呼叫中的 <xref:System.ArgumentNullException>。

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
