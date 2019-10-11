---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237314"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="01832-101">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="01832-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="01832-102">為了簡化 @no__t 0 類別的組合，已將 @no__t 1 方法設為公用，並提供類型 <xref:System.Text.Json.JsonSerializerOptions> 的第二個引數。</span><span class="sxs-lookup"><span data-stu-id="01832-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="01832-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="01832-103">Change description</span></span>

<span data-ttu-id="01832-104">3\.0 Preview 8 之前的 .NET Core 中，`CreateConverter` 方法的簽章為：</span><span class="sxs-lookup"><span data-stu-id="01832-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="01832-105">在 .NET Core 3.0 Preview 8 和更新版本中，它是：</span><span class="sxs-lookup"><span data-stu-id="01832-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="01832-106">在此變更之前，很難撰寫密封的 factory 轉換器，因為沒有簡單的方法可以從它取得 <xref:System.Text.Json.Serialization.JsonConverter%601>。</span><span class="sxs-lookup"><span data-stu-id="01832-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="01832-107">將 factory 方法設為公用，同時傳遞目前的 <xref:System.Text.Json.JsonSerializerOptions> 允許更具彈性的組合。</span><span class="sxs-lookup"><span data-stu-id="01832-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01832-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="01832-108">Version introduced</span></span>

<span data-ttu-id="01832-109">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="01832-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01832-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="01832-110">Recommended action</span></span>

<span data-ttu-id="01832-111">衍生類別需要更新並重新編譯。</span><span class="sxs-lookup"><span data-stu-id="01832-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01832-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="01832-112">Affected APIs</span></span>

<span data-ttu-id="01832-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01832-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
