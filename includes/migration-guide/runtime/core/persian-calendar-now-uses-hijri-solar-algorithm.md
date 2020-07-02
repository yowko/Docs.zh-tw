---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621120"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="4daa0-101">波斯曆現在會使用回教陽曆演算法</span><span class="sxs-lookup"><span data-stu-id="4daa0-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="4daa0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4daa0-102">Details</span></span>

<span data-ttu-id="4daa0-103">從 .NET Framework 4.6 開始，<xref:System.Globalization.PersianCalendar?displayProperty=fullName> 類別會使用回教陽曆演算法。</span><span class="sxs-lookup"><span data-stu-id="4daa0-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="4daa0-104">從 .NET Framework 4.6 開始，針對 1800 年以前的日期或 2023 年以後的日期 (西曆)，在 <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 與其他日曆之間轉換這些日期可能會產生稍微不同的結果。此外，<xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> 現在是 <code>March 22, 0622</code>，而不是 <code>March 21, 0622</code>。</span><span class="sxs-lookup"><span data-stu-id="4daa0-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4daa0-105">建議</span><span class="sxs-lookup"><span data-stu-id="4daa0-105">Suggestion</span></span>

<span data-ttu-id="4daa0-106">請注意，在 .NET Framework 4.6 中使用 PersianCalendar 時，某些較早或較晚的日期可能會稍微不同。</span><span class="sxs-lookup"><span data-stu-id="4daa0-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="4daa0-107">此外，在不同 .NET Framework 版本上執行的處理序之間序列化日期，不會將日期儲存為 PersianCalendar 日期字串 (因為這些值可能不同)。</span><span class="sxs-lookup"><span data-stu-id="4daa0-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="4daa0-108">名稱</span><span class="sxs-lookup"><span data-stu-id="4daa0-108">Name</span></span>    | <span data-ttu-id="4daa0-109">值</span><span class="sxs-lookup"><span data-stu-id="4daa0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4daa0-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="4daa0-110">Scope</span></span>   |<span data-ttu-id="4daa0-111">Minor</span><span class="sxs-lookup"><span data-stu-id="4daa0-111">Minor</span></span>|
|<span data-ttu-id="4daa0-112">版本</span><span class="sxs-lookup"><span data-stu-id="4daa0-112">Version</span></span>|<span data-ttu-id="4daa0-113">4.6</span><span class="sxs-lookup"><span data-stu-id="4daa0-113">4.6</span></span>|
|<span data-ttu-id="4daa0-114">類型</span><span class="sxs-lookup"><span data-stu-id="4daa0-114">Type</span></span>|<span data-ttu-id="4daa0-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="4daa0-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4daa0-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4daa0-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
