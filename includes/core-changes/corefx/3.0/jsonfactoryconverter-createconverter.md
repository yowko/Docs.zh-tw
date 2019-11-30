---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568101"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter. CreateConverter 簽章已變更

為了簡化 <xref:System.Text.Json.Serialization.JsonConverterFactory> 類別的撰寫，<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> 方法已設為公用，並提供類型 <xref:System.Text.Json.JsonSerializerOptions>的第二個引數。

#### <a name="change-description"></a>變更描述

在 3.0 Preview 8 之前的 .NET Core 中，`CreateConverter` 方法的簽章為：

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

在 .NET Core 3.0 Preview 8 和更新版本中，它是：

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

在此變更之前，很難撰寫密封的 factory 轉換器，因為沒有簡單的方法可以從它取得 <xref:System.Text.Json.Serialization.JsonConverter%601>。 將 factory 方法設為公用，同時傳遞目前的 <xref:System.Text.Json.JsonSerializerOptions> 允許更具彈性的組合。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

衍生類別需要更新並重新編譯。

#### <a name="affected-apis"></a>受影響的 API

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>。

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
