---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147558"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="e82d9-101">JsonFactory轉換器.創建轉換器簽名已更改</span><span class="sxs-lookup"><span data-stu-id="e82d9-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="e82d9-102">為方便類的<xref:System.Text.Json.Serialization.JsonConverterFactory>組成，<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A>該方法已公開，並給出了第二個類型<xref:System.Text.Json.JsonSerializerOptions>參數。</span><span class="sxs-lookup"><span data-stu-id="e82d9-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e82d9-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="e82d9-103">Change description</span></span>

<span data-ttu-id="e82d9-104">在 .NET `CreateConverter` Core 版本 3.0 預覽版 8 之前，該方法的簽名是：</span><span class="sxs-lookup"><span data-stu-id="e82d9-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="e82d9-105">在 .NET 核心 3.0 預覽版 8 和更高版本中，它是：</span><span class="sxs-lookup"><span data-stu-id="e82d9-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="e82d9-106">在這種變化之前，很難組成密封的工廠轉換器，因為沒有簡單的方法來<xref:System.Text.Json.Serialization.JsonConverter%601>得到它。</span><span class="sxs-lookup"><span data-stu-id="e82d9-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="e82d9-107">使工廠方法公開，也傳遞電流<xref:System.Text.Json.JsonSerializerOptions>允許更靈活的組合。</span><span class="sxs-lookup"><span data-stu-id="e82d9-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e82d9-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="e82d9-108">Version introduced</span></span>

<span data-ttu-id="e82d9-109">3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="e82d9-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e82d9-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e82d9-110">Recommended action</span></span>

<span data-ttu-id="e82d9-111">派生類需要更新和重新編譯。</span><span class="sxs-lookup"><span data-stu-id="e82d9-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e82d9-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e82d9-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
