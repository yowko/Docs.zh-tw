---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614332"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="20802-101">確定 System.Uri 使用一致的保留字集</span><span class="sxs-lookup"><span data-stu-id="20802-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="20802-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="20802-102">Details</span></span>

<span data-ttu-id="20802-103">在 <xref:System.Uri?displayProperty=fullName> 中，某些有時已解碼的百分比編碼字元，現在一致保持編碼。</span><span class="sxs-lookup"><span data-stu-id="20802-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="20802-104">這發生在存取 URI 的路徑、查詢、片段或使用者資訊元件的屬性和方法之間。</span><span class="sxs-lookup"><span data-stu-id="20802-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="20802-105">行為只有在下列兩項都符合時才會變更：</span><span class="sxs-lookup"><span data-stu-id="20802-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="20802-106">URI 包含下列任一保留字元的編碼格式：`:`、`'`、`(`、`)`、`!` 或 `*`。</span><span class="sxs-lookup"><span data-stu-id="20802-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="20802-107">URI 包含 Unicode 或編碼的非保留字元。</span><span class="sxs-lookup"><span data-stu-id="20802-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="20802-108">如果符合上述兩項，則編碼的保留字元會保持編碼。</span><span class="sxs-lookup"><span data-stu-id="20802-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="20802-109">在舊版的 .NET Framework 中，它們是解碼的。</span><span class="sxs-lookup"><span data-stu-id="20802-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20802-110">建議</span><span class="sxs-lookup"><span data-stu-id="20802-110">Suggestion</span></span>

<span data-ttu-id="20802-111">對於以 .NET Framework 4.7.2 版開始為目標的應用程式，預設會啟用新的解碼行為。</span><span class="sxs-lookup"><span data-stu-id="20802-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="20802-112">如果不需要這項變更，您可以在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數來停用此變更：</span><span class="sxs-lookup"><span data-stu-id="20802-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="20802-113">對於以舊版 .NET Framework 為目標，但執行版本低於 .NET Framework 4.7.2 (含) 的應用程式，預設會停用新的解碼行為。</span><span class="sxs-lookup"><span data-stu-id="20802-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="20802-114">您可以藉由在[AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` 應用程式佈建檔的區段中新增下列 AppCoNtextSwitchOverrides 參數來啟用它：</span><span class="sxs-lookup"><span data-stu-id="20802-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="20802-115">名稱</span><span class="sxs-lookup"><span data-stu-id="20802-115">Name</span></span>    | <span data-ttu-id="20802-116">值</span><span class="sxs-lookup"><span data-stu-id="20802-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20802-117">影響範圍</span><span class="sxs-lookup"><span data-stu-id="20802-117">Scope</span></span>   | <span data-ttu-id="20802-118">Minor</span><span class="sxs-lookup"><span data-stu-id="20802-118">Minor</span></span>       |
| <span data-ttu-id="20802-119">版本</span><span class="sxs-lookup"><span data-stu-id="20802-119">Version</span></span> | <span data-ttu-id="20802-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="20802-120">4.7.2</span></span>       |
| <span data-ttu-id="20802-121">類型</span><span class="sxs-lookup"><span data-stu-id="20802-121">Type</span></span>    | <span data-ttu-id="20802-122">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="20802-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="20802-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="20802-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
