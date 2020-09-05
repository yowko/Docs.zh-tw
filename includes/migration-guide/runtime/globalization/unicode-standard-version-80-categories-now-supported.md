---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496926"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="c4a5c-101">現在支援 Unicode 標準 8.0 版分類</span><span class="sxs-lookup"><span data-stu-id="c4a5c-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="c4a5c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4a5c-102">Details</span></span>

<span data-ttu-id="c4a5c-103">在 .NET Framework 4.6.2 中，Unicode 資料已從 Unicode 標準 6.3 版升級至 8.0 版。</span><span class="sxs-lookup"><span data-stu-id="c4a5c-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="c4a5c-104">在 .NET Framework 4.6.2 中要求 Unicode 字元分類時，某些結果可能不符合舊版 .NET Framework 中的結果。</span><span class="sxs-lookup"><span data-stu-id="c4a5c-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="c4a5c-105">這項變更主要會影響柴羅基文音節和新傣文母音符號和音調標記。</span><span class="sxs-lookup"><span data-stu-id="c4a5c-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c4a5c-106">建議</span><span class="sxs-lookup"><span data-stu-id="c4a5c-106">Suggestion</span></span>

<span data-ttu-id="c4a5c-107">請檢閱程式碼，並移除/變更仰賴硬式編碼的 Unicode 字元分類的邏輯。</span><span class="sxs-lookup"><span data-stu-id="c4a5c-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="c4a5c-108">名稱</span><span class="sxs-lookup"><span data-stu-id="c4a5c-108">Name</span></span>    | <span data-ttu-id="c4a5c-109">值</span><span class="sxs-lookup"><span data-stu-id="c4a5c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c4a5c-110">範圍</span><span class="sxs-lookup"><span data-stu-id="c4a5c-110">Scope</span></span>   |<span data-ttu-id="c4a5c-111">Minor</span><span class="sxs-lookup"><span data-stu-id="c4a5c-111">Minor</span></span>|
|<span data-ttu-id="c4a5c-112">版本</span><span class="sxs-lookup"><span data-stu-id="c4a5c-112">Version</span></span>|<span data-ttu-id="c4a5c-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c4a5c-113">4.6.2</span></span>|
|<span data-ttu-id="c4a5c-114">類型</span><span class="sxs-lookup"><span data-stu-id="c4a5c-114">Type</span></span>|<span data-ttu-id="c4a5c-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="c4a5c-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c4a5c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c4a5c-116">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
