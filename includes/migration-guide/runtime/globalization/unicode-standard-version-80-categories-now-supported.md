---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621072"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="efc0e-101">現在支援 Unicode 標準 8.0 版分類</span><span class="sxs-lookup"><span data-stu-id="efc0e-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="efc0e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="efc0e-102">Details</span></span>

<span data-ttu-id="efc0e-103">在 .NET Framework 4.6.2 中，Unicode 資料已從 Unicode 標準 6.3 版升級至 8.0 版。</span><span class="sxs-lookup"><span data-stu-id="efc0e-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="efc0e-104">在 .NET Framework 4.6.2 中要求 Unicode 字元分類時，某些結果可能不符合舊版 .NET Framework 中的結果。</span><span class="sxs-lookup"><span data-stu-id="efc0e-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="efc0e-105">這項變更主要會影響柴羅基文音節和新傣文母音符號和音調標記。</span><span class="sxs-lookup"><span data-stu-id="efc0e-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="efc0e-106">建議</span><span class="sxs-lookup"><span data-stu-id="efc0e-106">Suggestion</span></span>

<span data-ttu-id="efc0e-107">請檢閱程式碼，並移除/變更仰賴硬式編碼的 Unicode 字元分類的邏輯。</span><span class="sxs-lookup"><span data-stu-id="efc0e-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="efc0e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="efc0e-108">Name</span></span>    | <span data-ttu-id="efc0e-109">值</span><span class="sxs-lookup"><span data-stu-id="efc0e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="efc0e-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="efc0e-110">Scope</span></span>   |<span data-ttu-id="efc0e-111">Minor</span><span class="sxs-lookup"><span data-stu-id="efc0e-111">Minor</span></span>|
|<span data-ttu-id="efc0e-112">版本</span><span class="sxs-lookup"><span data-stu-id="efc0e-112">Version</span></span>|<span data-ttu-id="efc0e-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="efc0e-113">4.6.2</span></span>|
|<span data-ttu-id="efc0e-114">類型</span><span class="sxs-lookup"><span data-stu-id="efc0e-114">Type</span></span>|<span data-ttu-id="efc0e-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="efc0e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efc0e-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="efc0e-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
