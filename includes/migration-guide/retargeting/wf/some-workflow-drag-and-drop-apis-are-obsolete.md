---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617143"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>某些工作流程拖放 API 已淘汰

#### <a name="details"></a>詳細資料

此工作流程拖放 API 已淘汰；如果針對 4.5 重建應用程式，就會產生編譯器警告。

#### <a name="suggestion"></a>建議

您應該改用支援操作多個物件的新 <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> API。 或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。 這些 API 仍受到支援。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
