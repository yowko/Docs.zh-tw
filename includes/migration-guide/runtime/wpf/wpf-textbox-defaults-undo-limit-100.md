---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496181"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="ca657-101">WPF TextBox 的預設復原限制為 100</span><span class="sxs-lookup"><span data-stu-id="ca657-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="ca657-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ca657-102">Details</span></span>

<span data-ttu-id="ca657-103">在 .NET Framework 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET Framework 4.0 中則沒有限制)</span><span class="sxs-lookup"><span data-stu-id="ca657-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca657-104">建議</span><span class="sxs-lookup"><span data-stu-id="ca657-104">Suggestion</span></span>

<span data-ttu-id="ca657-105">如果 100 的復原限制太低，可以使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 明確設定此限制</span><span class="sxs-lookup"><span data-stu-id="ca657-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="ca657-106">名稱</span><span class="sxs-lookup"><span data-stu-id="ca657-106">Name</span></span>    | <span data-ttu-id="ca657-107">值</span><span class="sxs-lookup"><span data-stu-id="ca657-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca657-108">範圍</span><span class="sxs-lookup"><span data-stu-id="ca657-108">Scope</span></span>   |<span data-ttu-id="ca657-109">Edge</span><span class="sxs-lookup"><span data-stu-id="ca657-109">Edge</span></span>|
|<span data-ttu-id="ca657-110">版本</span><span class="sxs-lookup"><span data-stu-id="ca657-110">Version</span></span>|<span data-ttu-id="ca657-111">4.5</span><span class="sxs-lookup"><span data-stu-id="ca657-111">4.5</span></span>|
|<span data-ttu-id="ca657-112">類型</span><span class="sxs-lookup"><span data-stu-id="ca657-112">Type</span></span>|<span data-ttu-id="ca657-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="ca657-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ca657-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ca657-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
