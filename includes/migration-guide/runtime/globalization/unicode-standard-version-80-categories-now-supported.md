---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857601"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="69af9-101">現在支援 Unicode 標準 8.0 版分類</span><span class="sxs-lookup"><span data-stu-id="69af9-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="69af9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="69af9-102">Details</span></span>|<span data-ttu-id="69af9-103">在 .NET Framework 4.6.2 中，Unicode 資料已從 Unicode 標準 6.3 版升級至 8.0 版。</span><span class="sxs-lookup"><span data-stu-id="69af9-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="69af9-104">在 .NET Framework 4.6.2 中要求 Unicode 字元分類時，某些結果可能不符合舊版 .NET Framework 中的結果。</span><span class="sxs-lookup"><span data-stu-id="69af9-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="69af9-105">這項變更主要會影響柴羅基文音節和新傣文母音符號和音調標記。</span><span class="sxs-lookup"><span data-stu-id="69af9-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="69af9-106">建議</span><span class="sxs-lookup"><span data-stu-id="69af9-106">Suggestion</span></span>|<span data-ttu-id="69af9-107">請檢閱程式碼，並移除/變更仰賴硬式編碼的 Unicode 字元分類的邏輯。</span><span class="sxs-lookup"><span data-stu-id="69af9-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="69af9-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="69af9-108">Scope</span></span>|<span data-ttu-id="69af9-109">Minor</span><span class="sxs-lookup"><span data-stu-id="69af9-109">Minor</span></span>|
|<span data-ttu-id="69af9-110">版本</span><span class="sxs-lookup"><span data-stu-id="69af9-110">Version</span></span>|<span data-ttu-id="69af9-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="69af9-111">4.6.2</span></span>|
|<span data-ttu-id="69af9-112">類型</span><span class="sxs-lookup"><span data-stu-id="69af9-112">Type</span></span>|<span data-ttu-id="69af9-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="69af9-113">Runtime</span></span>|
|<span data-ttu-id="69af9-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="69af9-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
