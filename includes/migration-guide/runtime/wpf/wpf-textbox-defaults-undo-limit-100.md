---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235120"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="c3816-101">WPF TextBox 的預設復原限制為 100</span><span class="sxs-lookup"><span data-stu-id="c3816-101">WPF TextBox defaults to undo limit of 100</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c3816-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3816-102">Details</span></span>|<span data-ttu-id="c3816-103">在 .NET Framework 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET Framework 4.0 中則沒有限制)</span><span class="sxs-lookup"><span data-stu-id="c3816-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>|
|<span data-ttu-id="c3816-104">建議</span><span class="sxs-lookup"><span data-stu-id="c3816-104">Suggestion</span></span>|<span data-ttu-id="c3816-105">如果 100 的復原限制太低，此限制可以明確設定 (使用</span><span class="sxs-lookup"><span data-stu-id="c3816-105">If an undo limit of 100 is too low, the limit can be set explicitly with</span></span> <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|<span data-ttu-id="c3816-106">範圍</span><span class="sxs-lookup"><span data-stu-id="c3816-106">Scope</span></span>|<span data-ttu-id="c3816-107">Edge</span><span class="sxs-lookup"><span data-stu-id="c3816-107">Edge</span></span>|
|<span data-ttu-id="c3816-108">版本</span><span class="sxs-lookup"><span data-stu-id="c3816-108">Version</span></span>|<span data-ttu-id="c3816-109">4.5</span><span class="sxs-lookup"><span data-stu-id="c3816-109">4.5</span></span>|
|<span data-ttu-id="c3816-110">類型</span><span class="sxs-lookup"><span data-stu-id="c3816-110">Type</span></span>|<span data-ttu-id="c3816-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="c3816-111">Runtime</span></span>|
|<span data-ttu-id="c3816-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c3816-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
