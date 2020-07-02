---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619989"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a><span data-ttu-id="ad475-101">System.URI 逸出現在支援 RFC 3986</span><span class="sxs-lookup"><span data-stu-id="ad475-101">System.Uri escaping now supports RFC 3986</span></span>

#### <a name="details"></a><span data-ttu-id="ad475-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ad475-102">Details</span></span>

<span data-ttu-id="ad475-103">URI 逸出在 .NET Framework 4.5 中已變更，可支援 [RFC 3986](https://tools.ietf.org/html/rfc3986)。</span><span class="sxs-lookup"><span data-stu-id="ad475-103">URI escaping has changed in .NET Framework 4.5 to support [RFC 3986](https://tools.ietf.org/html/rfc3986).</span></span> <span data-ttu-id="ad475-104">特定變更包括：</span><span class="sxs-lookup"><span data-stu-id="ad475-104">Specific changes include:</span></span><ul><li><span data-ttu-id="ad475-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> 會根據 RFC 3986 逸出保留字元。</span><span class="sxs-lookup"><span data-stu-id="ad475-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> escapes reserved characters based on RFC 3986.</span></span></li><li><span data-ttu-id="ad475-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> 不會逸出保留字元。</span><span class="sxs-lookup"><span data-stu-id="ad475-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> does not escape reserved characters.</span></span></li><li><span data-ttu-id="ad475-107">如果 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> 遇到無效的逸出序列，則不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ad475-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> does not throw an exception if it encounters an invalid escape sequence.</span></span></li><li><span data-ttu-id="ad475-108">非保留的逸出字元不逸出。</span><span class="sxs-lookup"><span data-stu-id="ad475-108">Unreserved escaped characters are un-escaped.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="ad475-109">建議</span><span class="sxs-lookup"><span data-stu-id="ad475-109">Suggestion</span></span>

<ul><li><span data-ttu-id="ad475-110">請更新應用程式，以便在逸出序列無效時，不依賴 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> 擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ad475-110">Update applications to not rely on <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> to throw in the case of an invalid escape sequence.</span></span> <span data-ttu-id="ad475-111">現在必須直接偵測這類序列。</span><span class="sxs-lookup"><span data-stu-id="ad475-111">Such sequences must be detected directly now.</span></span></li><li><span data-ttu-id="ad475-112">同樣地，逸出和未逸出 URI 以及資料字串可能會因 .NET Framework 4.0 和 .NET Framework 4.5 而有所不同，因此不應該在不同的 .NET 版本之間直接進行比較。</span><span class="sxs-lookup"><span data-stu-id="ad475-112">Similarly, expect that Escaped and Unescaped URI and Data strings may vary from .NET Framework 4.0 and .NET Framework 4.5 and should not be compared across .NET versions directly.</span></span> <span data-ttu-id="ad475-113">相反地，應該將這些字串剖析和正規化為單一 .NET 版本，再進行任何比較。</span><span class="sxs-lookup"><span data-stu-id="ad475-113">Instead, they should be parsed and normalized in a single .NET version before any comparisons are made.</span></span></li></ul>

| <span data-ttu-id="ad475-114">名稱</span><span class="sxs-lookup"><span data-stu-id="ad475-114">Name</span></span>    | <span data-ttu-id="ad475-115">值</span><span class="sxs-lookup"><span data-stu-id="ad475-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ad475-116">影響範圍</span><span class="sxs-lookup"><span data-stu-id="ad475-116">Scope</span></span>   |<span data-ttu-id="ad475-117">Minor</span><span class="sxs-lookup"><span data-stu-id="ad475-117">Minor</span></span>|
|<span data-ttu-id="ad475-118">版本</span><span class="sxs-lookup"><span data-stu-id="ad475-118">Version</span></span>|<span data-ttu-id="ad475-119">4.5</span><span class="sxs-lookup"><span data-stu-id="ad475-119">4.5</span></span>|
|<span data-ttu-id="ad475-120">類型</span><span class="sxs-lookup"><span data-stu-id="ad475-120">Type</span></span>|<span data-ttu-id="ad475-121">執行階段</span><span class="sxs-lookup"><span data-stu-id="ad475-121">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad475-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ad475-122">Affected APIs</span></span>

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
