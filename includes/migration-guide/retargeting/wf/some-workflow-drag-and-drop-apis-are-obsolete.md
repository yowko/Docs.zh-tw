---
ms.openlocfilehash: 297af393e86c65e84ea7271d98eab36dbc6dbb0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774387"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="5d17f-101">某些工作流程拖放 API 已淘汰</span><span class="sxs-lookup"><span data-stu-id="5d17f-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5d17f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d17f-102">Details</span></span>|<span data-ttu-id="5d17f-103">此工作流程拖放 API 已淘汰；如果針對 4.5 重建應用程式，就會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="5d17f-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>|
|<span data-ttu-id="5d17f-104">建議</span><span class="sxs-lookup"><span data-stu-id="5d17f-104">Suggestion</span></span>|<span data-ttu-id="5d17f-105">您應該改用支援操作多個物件的新 <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> API。</span><span class="sxs-lookup"><span data-stu-id="5d17f-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="5d17f-106">或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。</span><span class="sxs-lookup"><span data-stu-id="5d17f-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="5d17f-107">這些 API 仍受到支援。</span><span class="sxs-lookup"><span data-stu-id="5d17f-107">The APIs are still supported.</span></span>|
|<span data-ttu-id="5d17f-108">範圍</span><span class="sxs-lookup"><span data-stu-id="5d17f-108">Scope</span></span>|<span data-ttu-id="5d17f-109">次要</span><span class="sxs-lookup"><span data-stu-id="5d17f-109">Minor</span></span>|
|<span data-ttu-id="5d17f-110">版本</span><span class="sxs-lookup"><span data-stu-id="5d17f-110">Version</span></span>|<span data-ttu-id="5d17f-111">4.5</span><span class="sxs-lookup"><span data-stu-id="5d17f-111">4.5</span></span>|
|<span data-ttu-id="5d17f-112">類型</span><span class="sxs-lookup"><span data-stu-id="5d17f-112">Type</span></span>|<span data-ttu-id="5d17f-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="5d17f-113">Retargeting</span></span>|
|<span data-ttu-id="5d17f-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5d17f-114">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
