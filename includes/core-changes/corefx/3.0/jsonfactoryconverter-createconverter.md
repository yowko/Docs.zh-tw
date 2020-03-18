---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147558"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactory轉換器.創建轉換器簽名已更改

為方便類的<xref:System.Text.Json.Serialization.JsonConverterFactory>組成，<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A>該方法已公開，並給出了第二個類型<xref:System.Text.Json.JsonSerializerOptions>參數。

#### <a name="change-description"></a>變更描述

在 .NET `CreateConverter` Core 版本 3.0 預覽版 8 之前，該方法的簽名是：

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

在 .NET 核心 3.0 預覽版 8 和更高版本中，它是：

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

在這種變化之前，很難組成密封的工廠轉換器，因為沒有簡單的方法來<xref:System.Text.Json.Serialization.JsonConverter%601>得到它。 使工廠方法公開，也傳遞電流<xref:System.Text.Json.JsonSerializerOptions>允許更靈活的組合。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 8

#### <a name="recommended-action"></a>建議的動作

派生類需要更新和重新編譯。

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
