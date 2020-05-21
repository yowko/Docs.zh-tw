---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721533"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="ce30d-101">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="ce30d-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="ce30d-102">為了簡化類別的撰寫 <xref:System.Text.Json.Serialization.JsonConverterFactory> ，已將 <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> 方法設為公用，並提供類型的第二個引數 <xref:System.Text.Json.JsonSerializerOptions> 。</span><span class="sxs-lookup"><span data-stu-id="ce30d-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ce30d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ce30d-103">Change description</span></span>

<span data-ttu-id="ce30d-104">`CreateConverter`版本 3.0 Preview 8 之前 .Net Core 中方法的簽章為：</span><span class="sxs-lookup"><span data-stu-id="ce30d-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="ce30d-105">在 .NET Core 3.0 Preview 8 和更新版本中，它是：</span><span class="sxs-lookup"><span data-stu-id="ce30d-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="ce30d-106">在此變更之前，很難撰寫密封的 factory 轉換器，因為沒有簡單的方法可以 <xref:System.Text.Json.Serialization.JsonConverter%601> 從它取得。</span><span class="sxs-lookup"><span data-stu-id="ce30d-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="ce30d-107">將 factory 方法設為公用，同時傳遞目前的 <xref:System.Text.Json.JsonSerializerOptions> 允許更具彈性的組合。</span><span class="sxs-lookup"><span data-stu-id="ce30d-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ce30d-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ce30d-108">Version introduced</span></span>

<span data-ttu-id="ce30d-109">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="ce30d-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ce30d-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ce30d-110">Recommended action</span></span>

<span data-ttu-id="ce30d-111">衍生類別需要更新並重新編譯。</span><span class="sxs-lookup"><span data-stu-id="ce30d-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ce30d-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ce30d-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
