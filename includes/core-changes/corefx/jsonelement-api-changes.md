---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119300"
---
### <a name="jsonelement-api-changes"></a>JsonElement API 變更

從 .net Core 3.0 Preview 7 開始，某些<xref:System.Text.Json.JsonElement> api 已變更為允許更輕鬆的探索和更高的可用性。

#### <a name="change-description"></a>變更描述

在 .net Core 3.0 Preview 7 中<xref:System.Text.Json.JsonElement> ，api 已依照下列方式變更，以允許更容易探索及使用更高的可用性。

1. 已`WriteProperty` 從<xref:System.Text.Json.JsonElement>移除所有方法多載。 這會影響程式碼，如下所示：

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

1. `WriteValue`已重新命名<xref:System.Text.Json.JsonElement.WriteTo%2A>為。 這會影響程式碼，如下所示：

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>現在， `null`當其方法參數為時，會擲回。 <xref:System.ArgumentNullException>

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 7

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼受到這些變更的影響，您可以執行下列動作：

- `WriteProperty` 中<xref:System.Text.Json.JsonElement>的多載沒有替代 API。 相反地，您可以呼叫其中一個<xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType>多載以及<xref:System.Text.Json.JsonElement.WriteTo%2A>方法，以達到相同的結果。 例如：

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- 將方法重新命名<xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>為。 `WriteValue` 方法參數會保持不變。 例如，先前的程式碼應該變更為下列內容：

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <xref:System.ArgumentNullException>在<xref:System.Text.Json.JsonElement.WriteTo%2A>方法的呼叫中處理。

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
