---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617140"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="7e0be-101">System.Uri 剖析遵守 RFC 3987</span><span class="sxs-lookup"><span data-stu-id="7e0be-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="7e0be-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7e0be-102">Details</span></span>

<span data-ttu-id="7e0be-103">URI 剖析在 .NET Framework 4.5 中已做了幾項變更。</span><span class="sxs-lookup"><span data-stu-id="7e0be-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="7e0be-104">不過請注意，這些變更只會影響以 .NET Framework 4.5 為目標的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7e0be-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="7e0be-105">如果某個二進位檔是以 .NET Framework 4.0 為目標，則會遵守舊版行為。</span><span class="sxs-lookup"><span data-stu-id="7e0be-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="7e0be-106">.NET Framework 4.5 中的 URI 剖析變更包括：</span><span class="sxs-lookup"><span data-stu-id="7e0be-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="7e0be-107">URI 剖析將會根據 RFC 3987 中最新的 IRI 規則來執行正規化和字元檢查。</span><span class="sxs-lookup"><span data-stu-id="7e0be-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="7e0be-108">只會在 URI 的主機部分執行 Unicode 正規化格式 C。</span><span class="sxs-lookup"><span data-stu-id="7e0be-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="7e0be-109">無效的 mailto: URI 現在會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e0be-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="7e0be-110">現在會保留路徑線段結尾的後置點。</span><span class="sxs-lookup"><span data-stu-id="7e0be-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="7e0be-111">`file://` URI 不會逸出 `?` 字元。</span><span class="sxs-lookup"><span data-stu-id="7e0be-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="7e0be-112">不支援 Unicode 控制字元 `U+0080` 至 `U+009F`。</span><span class="sxs-lookup"><span data-stu-id="7e0be-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="7e0be-113">逗號字元 `,` 或 `%2c` 不會自動設為未逸出。</span><span class="sxs-lookup"><span data-stu-id="7e0be-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7e0be-114">建議</span><span class="sxs-lookup"><span data-stu-id="7e0be-114">Suggestion</span></span>

<span data-ttu-id="7e0be-115">如果需要舊版 .NET Framework 4.0 URI 剖析語意 (通常不需要)，藉由設定 .NET Framework 4.0 目標即可使用。</span><span class="sxs-lookup"><span data-stu-id="7e0be-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="7e0be-116">您可以在組件上使用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>，或透過 Visual Studio 專案系統 UI 的 [專案屬性] 頁面來完成此作業。</span><span class="sxs-lookup"><span data-stu-id="7e0be-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="7e0be-117">名稱</span><span class="sxs-lookup"><span data-stu-id="7e0be-117">Name</span></span>    | <span data-ttu-id="7e0be-118">值</span><span class="sxs-lookup"><span data-stu-id="7e0be-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7e0be-119">影響範圍</span><span class="sxs-lookup"><span data-stu-id="7e0be-119">Scope</span></span>   | <span data-ttu-id="7e0be-120">主要</span><span class="sxs-lookup"><span data-stu-id="7e0be-120">Major</span></span>       |
| <span data-ttu-id="7e0be-121">版本</span><span class="sxs-lookup"><span data-stu-id="7e0be-121">Version</span></span> | <span data-ttu-id="7e0be-122">4.5</span><span class="sxs-lookup"><span data-stu-id="7e0be-122">4.5</span></span>         |
| <span data-ttu-id="7e0be-123">類型</span><span class="sxs-lookup"><span data-stu-id="7e0be-123">Type</span></span>    | <span data-ttu-id="7e0be-124">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="7e0be-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7e0be-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7e0be-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
