---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497016"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="a04d0-101">StaysOpen=False 時的鏈結快顯視窗</span><span class="sxs-lookup"><span data-stu-id="a04d0-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="a04d0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a04d0-102">Details</span></span>

<span data-ttu-id="a04d0-103">當您按一下 StaysOpen=False 快顯視窗的外部時，該快顯視窗應該要關閉。</span><span class="sxs-lookup"><span data-stu-id="a04d0-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="a04d0-104">當兩個或多個這類快顯視窗鏈結在一起 (也就是其中一個包含另一個) 時，會發生許多問題，包括：</span><span class="sxs-lookup"><span data-stu-id="a04d0-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="a04d0-105">開啟兩個層級，按一下 P2 外部 (但在 P1 內部)。</span><span class="sxs-lookup"><span data-stu-id="a04d0-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="a04d0-106">沒有發生任何事。</span><span class="sxs-lookup"><span data-stu-id="a04d0-106">Nothing happens.</span></span></li><li><span data-ttu-id="a04d0-107">開啟兩個層級，按一下 P1 外部。</span><span class="sxs-lookup"><span data-stu-id="a04d0-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="a04d0-108">這兩個快顯視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="a04d0-108">Both popups close.</span></span></li><li><span data-ttu-id="a04d0-109">開啟及關閉兩個層級。</span><span class="sxs-lookup"><span data-stu-id="a04d0-109">Open and close two levels.</span></span>  <span data-ttu-id="a04d0-110">然後嘗試再次開啟 P2。</span><span class="sxs-lookup"><span data-stu-id="a04d0-110">Then try to open P2 again.</span></span>  <span data-ttu-id="a04d0-111">沒有發生任何事。</span><span class="sxs-lookup"><span data-stu-id="a04d0-111">Nothing happens.</span></span></li><li><span data-ttu-id="a04d0-112">嘗試開啟三個層級。</span><span class="sxs-lookup"><span data-stu-id="a04d0-112">Try to open three levels.</span></span>  <span data-ttu-id="a04d0-113">你無此權限。</span><span class="sxs-lookup"><span data-stu-id="a04d0-113">You can't.</span></span>  <span data-ttu-id="a04d0-114"> (不會發生任何事，或是前兩個層級關閉，視您按一下的位置而定。 ) 這些案例 (和其他變異) 現在可如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="a04d0-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="a04d0-115">名稱</span><span class="sxs-lookup"><span data-stu-id="a04d0-115">Name</span></span>    | <span data-ttu-id="a04d0-116">值</span><span class="sxs-lookup"><span data-stu-id="a04d0-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a04d0-117">範圍</span><span class="sxs-lookup"><span data-stu-id="a04d0-117">Scope</span></span>   |<span data-ttu-id="a04d0-118">Edge</span><span class="sxs-lookup"><span data-stu-id="a04d0-118">Edge</span></span>|
|<span data-ttu-id="a04d0-119">版本</span><span class="sxs-lookup"><span data-stu-id="a04d0-119">Version</span></span>|<span data-ttu-id="a04d0-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="a04d0-120">4.7.1</span></span>|
|<span data-ttu-id="a04d0-121">類型</span><span class="sxs-lookup"><span data-stu-id="a04d0-121">Type</span></span>|<span data-ttu-id="a04d0-122">執行階段</span><span class="sxs-lookup"><span data-stu-id="a04d0-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a04d0-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a04d0-123">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
