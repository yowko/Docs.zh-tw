---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568101"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="0f99a-101">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="0f99a-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="0f99a-102">為了簡化 <xref:System.Text.Json.Serialization.JsonConverterFactory> 類別的撰寫，<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> 方法已設為公用，並提供類型 <xref:System.Text.Json.JsonSerializerOptions>的第二個引數。</span><span class="sxs-lookup"><span data-stu-id="0f99a-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f99a-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0f99a-103">Change description</span></span>

<span data-ttu-id="0f99a-104">在 3.0 Preview 8 之前的 .NET Core 中，`CreateConverter` 方法的簽章為：</span><span class="sxs-lookup"><span data-stu-id="0f99a-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="0f99a-105">在 .NET Core 3.0 Preview 8 和更新版本中，它是：</span><span class="sxs-lookup"><span data-stu-id="0f99a-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="0f99a-106">在此變更之前，很難撰寫密封的 factory 轉換器，因為沒有簡單的方法可以從它取得 <xref:System.Text.Json.Serialization.JsonConverter%601>。</span><span class="sxs-lookup"><span data-stu-id="0f99a-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="0f99a-107">將 factory 方法設為公用，同時傳遞目前的 <xref:System.Text.Json.JsonSerializerOptions> 允許更具彈性的組合。</span><span class="sxs-lookup"><span data-stu-id="0f99a-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f99a-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0f99a-108">Version introduced</span></span>

<span data-ttu-id="0f99a-109">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0f99a-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f99a-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0f99a-110">Recommended action</span></span>

<span data-ttu-id="0f99a-111">衍生類別需要更新並重新編譯。</span><span class="sxs-lookup"><span data-stu-id="0f99a-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f99a-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0f99a-112">Affected APIs</span></span>

<span data-ttu-id="0f99a-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0f99a-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
