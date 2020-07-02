---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621107"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="0850b-101">StaysOpen=False 時的鏈結快顯視窗</span><span class="sxs-lookup"><span data-stu-id="0850b-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="0850b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0850b-102">Details</span></span>

<span data-ttu-id="0850b-103">當您按一下 StaysOpen=False 快顯視窗的外部時，該快顯視窗應該要關閉。</span><span class="sxs-lookup"><span data-stu-id="0850b-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="0850b-104">當兩個或多個這類快顯視窗鏈結在一起 (也就是其中一個包含另一個) 時，會發生許多問題，包括：</span><span class="sxs-lookup"><span data-stu-id="0850b-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="0850b-105">開啟兩個層級，按一下 P2 外部 (但在 P1 內部)。</span><span class="sxs-lookup"><span data-stu-id="0850b-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="0850b-106">不會發生任何情況。</span><span class="sxs-lookup"><span data-stu-id="0850b-106">Nothing happens.</span></span></li><li><span data-ttu-id="0850b-107">開啟兩個層級，按一下 P1 外部。</span><span class="sxs-lookup"><span data-stu-id="0850b-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="0850b-108">這兩個快顯視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="0850b-108">Both popups close.</span></span></li><li><span data-ttu-id="0850b-109">開啟及關閉兩個層級。</span><span class="sxs-lookup"><span data-stu-id="0850b-109">Open and close two levels.</span></span>  <span data-ttu-id="0850b-110">然後嘗試再次開啟 P2。</span><span class="sxs-lookup"><span data-stu-id="0850b-110">Then try to open P2 again.</span></span>  <span data-ttu-id="0850b-111">不會發生任何情況。</span><span class="sxs-lookup"><span data-stu-id="0850b-111">Nothing happens.</span></span></li><li><span data-ttu-id="0850b-112">嘗試開啟三個層級。</span><span class="sxs-lookup"><span data-stu-id="0850b-112">Try to open three levels.</span></span>  <span data-ttu-id="0850b-113">您無法。</span><span class="sxs-lookup"><span data-stu-id="0850b-113">You can't.</span></span>  <span data-ttu-id="0850b-114">（視您按一下的位置而定，不會發生任何事，或前兩個層級關閉）。這些案例（和其他變異）現在會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="0850b-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="0850b-115">名稱</span><span class="sxs-lookup"><span data-stu-id="0850b-115">Name</span></span>    | <span data-ttu-id="0850b-116">值</span><span class="sxs-lookup"><span data-stu-id="0850b-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0850b-117">影響範圍</span><span class="sxs-lookup"><span data-stu-id="0850b-117">Scope</span></span>   |<span data-ttu-id="0850b-118">Edge</span><span class="sxs-lookup"><span data-stu-id="0850b-118">Edge</span></span>|
|<span data-ttu-id="0850b-119">版本</span><span class="sxs-lookup"><span data-stu-id="0850b-119">Version</span></span>|<span data-ttu-id="0850b-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0850b-120">4.7.1</span></span>|
|<span data-ttu-id="0850b-121">類型</span><span class="sxs-lookup"><span data-stu-id="0850b-121">Type</span></span>|<span data-ttu-id="0850b-122">執行階段</span><span class="sxs-lookup"><span data-stu-id="0850b-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0850b-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0850b-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
