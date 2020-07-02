---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614321"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="1208e-101">允許在 URI 中使用 Unicode 雙向控制字元</span><span class="sxs-lookup"><span data-stu-id="1208e-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="1208e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1208e-102">Details</span></span>

<span data-ttu-id="1208e-103">Unicode 會指定數個特殊控制字元，用來指定文字的方向。</span><span class="sxs-lookup"><span data-stu-id="1208e-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="1208e-104">在舊版的 .NET Framework 中，這些字元會從所有 URI 中不正確地移除，即使它們存在於自己的百分比編碼中。</span><span class="sxs-lookup"><span data-stu-id="1208e-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="1208e-105">為進一步遵循 [RFC 3987](https://tools.ietf.org/html/rfc3987)，我們現在允許在 URI 中使用這些字元。</span><span class="sxs-lookup"><span data-stu-id="1208e-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="1208e-106">在 URI 找到未編碼的內容時，它們是百分比編碼的。</span><span class="sxs-lookup"><span data-stu-id="1208e-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="1208e-107">找到百分比編碼的內容時，它們會保持現況。</span><span class="sxs-lookup"><span data-stu-id="1208e-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1208e-108">建議</span><span class="sxs-lookup"><span data-stu-id="1208e-108">Suggestion</span></span>

<span data-ttu-id="1208e-109">以 .NET Framework 4.7.2 版開始為目標的應用程式，預設啟用對 Unicode 雙向字元的支援。</span><span class="sxs-lookup"><span data-stu-id="1208e-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="1208e-110">如果不需要這項變更，您可以在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數來停用此變更：</span><span class="sxs-lookup"><span data-stu-id="1208e-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="1208e-111">對於以舊版 .NET Framework 為目標，但執行版本低於 .NET Framework 4.7.2 (含) 的應用程式，預設停用對 Unicode 雙向字元的支援。</span><span class="sxs-lookup"><span data-stu-id="1208e-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="1208e-112">您可以在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數停用它：</span><span class="sxs-lookup"><span data-stu-id="1208e-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="1208e-113">名稱</span><span class="sxs-lookup"><span data-stu-id="1208e-113">Name</span></span>    | <span data-ttu-id="1208e-114">值</span><span class="sxs-lookup"><span data-stu-id="1208e-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1208e-115">影響範圍</span><span class="sxs-lookup"><span data-stu-id="1208e-115">Scope</span></span>   | <span data-ttu-id="1208e-116">Minor</span><span class="sxs-lookup"><span data-stu-id="1208e-116">Minor</span></span>       |
| <span data-ttu-id="1208e-117">版本</span><span class="sxs-lookup"><span data-stu-id="1208e-117">Version</span></span> | <span data-ttu-id="1208e-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1208e-118">4.7.2</span></span>       |
| <span data-ttu-id="1208e-119">類型</span><span class="sxs-lookup"><span data-stu-id="1208e-119">Type</span></span>    | <span data-ttu-id="1208e-120">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="1208e-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1208e-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1208e-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
