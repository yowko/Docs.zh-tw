---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117131"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter. CreateConverter 簽章已變更

為了簡化<xref:System.Text.Json.Serialization.JsonConverterFactory>類別的撰寫，已將<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A>方法設為公用，並提供類型<xref:System.Text.Json.JsonSerializerOptions>的第二個引數。

#### <a name="details"></a>詳細資料

版本 3.0 Preview 8 之前 .net Core 中方法的簽章為：`CreateConverter` 

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

在此變更之前，很難撰寫密封的 factory 轉換器，因為沒有簡單的<xref:System.Text.Json.Serialization.JsonConverter%601>方法可以從它取得。 將 factory 方法設為公用，同時傳遞目前<xref:System.Text.Json.JsonSerializerOptions>的允許更具彈性的組合。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

衍生類別需要更新並重新編譯。

#### <a name="affected-apis"></a>受影響的 API

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
