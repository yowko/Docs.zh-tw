---
ms.openlocfilehash: 1f85b1ce95ca07329aff77af4ec894622e0818d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606756"
---
### <a name="workflow-30-types-are-obsolete"></a>WorkFlow 3.0 類型已淘汰

#### <a name="details"></a>詳細資料

Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 命名空間中的 API) 現在已淘汰。

#### <a name="suggestion"></a>建議

您應該改用新的 WWF 4.0 API (在 System.Activities 中)。 您可以在[這裡](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的範例，並在[這裡](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5)取得進一步指引。 此外，由於仍然支援 WWF 3.0 API，因此可使用這些 API，並藉由隱藏建置階段警告或使用舊版編譯器來避免出現警告。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | 主要       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |
