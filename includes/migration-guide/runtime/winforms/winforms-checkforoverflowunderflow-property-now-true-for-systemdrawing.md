---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496414"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="1059a-101">WinForm 的 CheckForOverflowUnderflow 屬性對於 System.Drawing 現在是 true</span><span class="sxs-lookup"><span data-stu-id="1059a-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="1059a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1059a-102">Details</span></span>

<span data-ttu-id="1059a-103">System.Drawing.dll 組件的 CheckForOverflowUnderflow 屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="1059a-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1059a-104">建議</span><span class="sxs-lookup"><span data-stu-id="1059a-104">Suggestion</span></span>

<span data-ttu-id="1059a-105">以往發生溢位時，結果會以無訊息模式截斷。</span><span class="sxs-lookup"><span data-stu-id="1059a-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="1059a-106">現在則會擲回 <xref:System.OverflowException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1059a-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="1059a-107">名稱</span><span class="sxs-lookup"><span data-stu-id="1059a-107">Name</span></span>    | <span data-ttu-id="1059a-108">值</span><span class="sxs-lookup"><span data-stu-id="1059a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1059a-109">範圍</span><span class="sxs-lookup"><span data-stu-id="1059a-109">Scope</span></span>   |<span data-ttu-id="1059a-110">Edge</span><span class="sxs-lookup"><span data-stu-id="1059a-110">Edge</span></span>|
|<span data-ttu-id="1059a-111">版本</span><span class="sxs-lookup"><span data-stu-id="1059a-111">Version</span></span>|<span data-ttu-id="1059a-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1059a-112">4.5</span></span>|
|<span data-ttu-id="1059a-113">類型</span><span class="sxs-lookup"><span data-stu-id="1059a-113">Type</span></span>|<span data-ttu-id="1059a-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="1059a-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1059a-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1059a-115">Affected APIs</span></span>

<span data-ttu-id="1059a-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="1059a-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
