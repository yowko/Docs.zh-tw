---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620103"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="7fc07-101">WPF TextBox 的預設復原限制為 100</span><span class="sxs-lookup"><span data-stu-id="7fc07-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="7fc07-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7fc07-102">Details</span></span>

<span data-ttu-id="7fc07-103">在 .NET Framework 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET Framework 4.0 中則沒有限制)</span><span class="sxs-lookup"><span data-stu-id="7fc07-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7fc07-104">建議</span><span class="sxs-lookup"><span data-stu-id="7fc07-104">Suggestion</span></span>

<span data-ttu-id="7fc07-105">如果 100 的復原限制太低，可以使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 明確設定此限制</span><span class="sxs-lookup"><span data-stu-id="7fc07-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="7fc07-106">名稱</span><span class="sxs-lookup"><span data-stu-id="7fc07-106">Name</span></span>    | <span data-ttu-id="7fc07-107">值</span><span class="sxs-lookup"><span data-stu-id="7fc07-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7fc07-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="7fc07-108">Scope</span></span>   |<span data-ttu-id="7fc07-109">Edge</span><span class="sxs-lookup"><span data-stu-id="7fc07-109">Edge</span></span>|
|<span data-ttu-id="7fc07-110">版本</span><span class="sxs-lookup"><span data-stu-id="7fc07-110">Version</span></span>|<span data-ttu-id="7fc07-111">4.5</span><span class="sxs-lookup"><span data-stu-id="7fc07-111">4.5</span></span>|
|<span data-ttu-id="7fc07-112">類型</span><span class="sxs-lookup"><span data-stu-id="7fc07-112">Type</span></span>|<span data-ttu-id="7fc07-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="7fc07-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7fc07-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7fc07-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
