---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614373"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="46a1c-101">DataContractJsonSerializer 的控制字元序列化現在與 ECMAScript V6 和 V8 相容</span><span class="sxs-lookup"><span data-stu-id="46a1c-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="46a1c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="46a1c-102">Details</span></span>

<span data-ttu-id="46a1c-103">在 .NET Framework 4.6.2 和舊版中，並未 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> 以與 ECMAScript V6 和 V8 標準相容的方式序列化某些特殊控制字元，例如 \b、\f 和 \t。</span><span class="sxs-lookup"><span data-stu-id="46a1c-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="46a1c-104">從 .NET Framework 4.7 開始，這些控制字元的序列化會與 ECMAScript V6 和 V8 相容。</span><span class="sxs-lookup"><span data-stu-id="46a1c-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="46a1c-105">建議</span><span class="sxs-lookup"><span data-stu-id="46a1c-105">Suggestion</span></span>

<span data-ttu-id="46a1c-106">若為以 .NET Framework 4.7 為目標的應用程式，會預設啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="46a1c-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="46a1c-107">如果不需要此行為，您可將下列程式行加入至 app.config 或 web.config 檔案的 `<runtime>` 區段，以選擇退出此功能：</span><span class="sxs-lookup"><span data-stu-id="46a1c-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="46a1c-108">名稱</span><span class="sxs-lookup"><span data-stu-id="46a1c-108">Name</span></span>    | <span data-ttu-id="46a1c-109">值</span><span class="sxs-lookup"><span data-stu-id="46a1c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="46a1c-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="46a1c-110">Scope</span></span>   | <span data-ttu-id="46a1c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="46a1c-111">Edge</span></span>        |
| <span data-ttu-id="46a1c-112">版本</span><span class="sxs-lookup"><span data-stu-id="46a1c-112">Version</span></span> | <span data-ttu-id="46a1c-113">4.7</span><span class="sxs-lookup"><span data-stu-id="46a1c-113">4.7</span></span>         |
| <span data-ttu-id="46a1c-114">類型</span><span class="sxs-lookup"><span data-stu-id="46a1c-114">Type</span></span>    | <span data-ttu-id="46a1c-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="46a1c-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="46a1c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="46a1c-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
