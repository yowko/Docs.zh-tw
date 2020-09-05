---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496829"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="256a3-101">ContentDisposition DateTimes 會傳回稍微不同的字串</span><span class="sxs-lookup"><span data-stu-id="256a3-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="256a3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="256a3-102">Details</span></span>

<span data-ttu-id="256a3-103"><xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> 的字串表示已更新，從 4.6 開始，一律會以兩個位數表示 <xref:System.DateTime?displayProperty=fullName> 的小時元件。</span><span class="sxs-lookup"><span data-stu-id="256a3-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="256a3-104">這是為了遵守 [RFC822](https://www.ietf.org/rfc/rfc0822.txt) 和 [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)。</span><span class="sxs-lookup"><span data-stu-id="256a3-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="256a3-105">這會導致 <xref:System.Net.Mime.ContentDisposition.ToString> 在 4.6 中傳回稍微不同的字串，例如，當其中一個配置的時間項目早於上午 10:00 時。</span><span class="sxs-lookup"><span data-stu-id="256a3-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="256a3-106">請注意，ContentDispositions 有時會透過轉換成字串來進行序列化，因此應檢閱任何 <xref:System.Net.Mime.ContentDisposition.ToString> 作業、序列化或 GetHashCode 呼叫。</span><span class="sxs-lookup"><span data-stu-id="256a3-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="256a3-107">建議</span><span class="sxs-lookup"><span data-stu-id="256a3-107">Suggestion</span></span>

<span data-ttu-id="256a3-108">在不同的 .NET Framework 版本中，ContentDispositions 的字串表示不會正確地相互比較。</span><span class="sxs-lookup"><span data-stu-id="256a3-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="256a3-109">如果可能的話，請將字串轉換回 ContentDispositions，再進行比較。</span><span class="sxs-lookup"><span data-stu-id="256a3-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="256a3-110">名稱</span><span class="sxs-lookup"><span data-stu-id="256a3-110">Name</span></span>    | <span data-ttu-id="256a3-111">值</span><span class="sxs-lookup"><span data-stu-id="256a3-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="256a3-112">範圍</span><span class="sxs-lookup"><span data-stu-id="256a3-112">Scope</span></span>   |<span data-ttu-id="256a3-113">Minor</span><span class="sxs-lookup"><span data-stu-id="256a3-113">Minor</span></span>|
|<span data-ttu-id="256a3-114">版本</span><span class="sxs-lookup"><span data-stu-id="256a3-114">Version</span></span>|<span data-ttu-id="256a3-115">4.6</span><span class="sxs-lookup"><span data-stu-id="256a3-115">4.6</span></span>|
|<span data-ttu-id="256a3-116">類型</span><span class="sxs-lookup"><span data-stu-id="256a3-116">Type</span></span>|<span data-ttu-id="256a3-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="256a3-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="256a3-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="256a3-118">Affected APIs</span></span>

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
