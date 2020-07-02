---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617143"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="25ebc-101">某些工作流程拖放 API 已淘汰</span><span class="sxs-lookup"><span data-stu-id="25ebc-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="25ebc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25ebc-102">Details</span></span>

<span data-ttu-id="25ebc-103">此工作流程拖放 API 已淘汰；如果針對 4.5 重建應用程式，就會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="25ebc-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25ebc-104">建議</span><span class="sxs-lookup"><span data-stu-id="25ebc-104">Suggestion</span></span>

<span data-ttu-id="25ebc-105">您應該改用支援操作多個物件的新 <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> API。</span><span class="sxs-lookup"><span data-stu-id="25ebc-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="25ebc-106">或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。</span><span class="sxs-lookup"><span data-stu-id="25ebc-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="25ebc-107">這些 API 仍受到支援。</span><span class="sxs-lookup"><span data-stu-id="25ebc-107">The APIs are still supported.</span></span>

| <span data-ttu-id="25ebc-108">名稱</span><span class="sxs-lookup"><span data-stu-id="25ebc-108">Name</span></span>    | <span data-ttu-id="25ebc-109">值</span><span class="sxs-lookup"><span data-stu-id="25ebc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25ebc-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="25ebc-110">Scope</span></span>   | <span data-ttu-id="25ebc-111">Minor</span><span class="sxs-lookup"><span data-stu-id="25ebc-111">Minor</span></span>       |
| <span data-ttu-id="25ebc-112">版本</span><span class="sxs-lookup"><span data-stu-id="25ebc-112">Version</span></span> | <span data-ttu-id="25ebc-113">4.5</span><span class="sxs-lookup"><span data-stu-id="25ebc-113">4.5</span></span>         |
| <span data-ttu-id="25ebc-114">類型</span><span class="sxs-lookup"><span data-stu-id="25ebc-114">Type</span></span>    | <span data-ttu-id="25ebc-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="25ebc-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="25ebc-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="25ebc-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
