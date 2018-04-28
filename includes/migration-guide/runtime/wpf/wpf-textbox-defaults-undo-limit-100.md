### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="00336-101">WPF TextBox 的預設復原限制為 100</span><span class="sxs-lookup"><span data-stu-id="00336-101">WPF TextBox defaults to undo limit of 100</span></span>

|   |   |
|---|---|
|<span data-ttu-id="00336-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00336-102">Details</span></span>|<span data-ttu-id="00336-103">在 .NET 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET 4.0 中則沒有限制)</span><span class="sxs-lookup"><span data-stu-id="00336-103">In .NET 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET 4.0)</span></span>|
|<span data-ttu-id="00336-104">建議</span><span class="sxs-lookup"><span data-stu-id="00336-104">Suggestion</span></span>|<span data-ttu-id="00336-105">如果 100 的復原限制太低，可以使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 明確設定此限制</span><span class="sxs-lookup"><span data-stu-id="00336-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>|
|<span data-ttu-id="00336-106">範圍</span><span class="sxs-lookup"><span data-stu-id="00336-106">Scope</span></span>|<span data-ttu-id="00336-107">Edge</span><span class="sxs-lookup"><span data-stu-id="00336-107">Edge</span></span>|
|<span data-ttu-id="00336-108">版本</span><span class="sxs-lookup"><span data-stu-id="00336-108">Version</span></span>|<span data-ttu-id="00336-109">4.5</span><span class="sxs-lookup"><span data-stu-id="00336-109">4.5</span></span>|
|<span data-ttu-id="00336-110">類型</span><span class="sxs-lookup"><span data-stu-id="00336-110">Type</span></span>|<span data-ttu-id="00336-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="00336-111">Runtime</span></span>|
|<span data-ttu-id="00336-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="00336-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

