---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617147"
---
### <a name="workflow-30-types-are-obsolete"></a>WorkFlow 3.0 類型已淘汰

#### <a name="details"></a>詳細資料

Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 命名空間中的 API) 現在已淘汰。

#### <a name="suggestion"></a>建議

您應該改用新的 WWF 4.0 API (在 System.Activities 中)。 您可以在[這裡](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的範例，並在[這裡](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5)取得進一步指引。 此外，由於仍然支援 WWF 3.0 API，因此可使用這些 API，並藉由隱藏建置階段警告或使用舊版編譯器來避免出現警告。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |
