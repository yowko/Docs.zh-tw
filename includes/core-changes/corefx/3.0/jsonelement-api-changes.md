---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568253"
---
### <a name="jsonelement-api-changes"></a>JsonElement API 更改

從 .NET 核心 3.0 預覽<xref:System.Text.Json.JsonElement>7 開始，一些 API 已更改，以便更輕鬆地發現和增強可用性。

#### <a name="change-description"></a>變更描述

在 .NET 核心 3.0<xref:System.Text.Json.JsonElement>預覽 7 中，API 已更改如下，以便更輕鬆地發現和增強可用性。

1. 從`WriteProperty`<xref:System.Text.Json.JsonElement>中刪除了所有方法重載。 這會影響以下代碼：

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

1. `WriteValue`被重命名為<xref:System.Text.Json.JsonElement.WriteTo%2A>。 這會影響以下代碼：

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>現在，當它<xref:System.ArgumentNullException>的方法參數為`null`時引發 。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 7

#### <a name="recommended-action"></a>建議的動作

如果代碼受到這些更改的影響，您可以執行以下操作：

- 中沒有`WriteProperty`替換超載的<xref:System.Text.Json.JsonElement>API。 相反，您可以調用其中一個<xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType>重載以及<xref:System.Text.Json.JsonElement.WriteTo%2A>方法來實現相同的結果。 例如：

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- 將`WriteValue`方法重命名為<xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>。 方法參數保持不變。 例如，以前的代碼應更改為以下內容：

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- 處理對<xref:System.ArgumentNullException>方法的<xref:System.Text.Json.JsonElement.WriteTo%2A>調用。

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
