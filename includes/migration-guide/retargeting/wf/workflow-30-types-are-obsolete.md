---
ms.openlocfilehash: 70acbb571921c5f72ecaa26b26136a77532ad220
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774367"
---
### <a name="workflow-30-types-are-obsolete"></a>WorkFlow 3.0 類型已淘汰

|   |   |
|---|---|
|詳細資料|Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 命名空間中的 API) 現在已淘汰。|
|建議|您應該改用新的 WWF 4.0 API (在 System.Activities 中)。 您可以在[這裡](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的範例，並在[這裡](https://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)取得進一步指引。 此外，由於仍然支援 WWF 3.0 API，因此可使用這些 API，並藉由隱藏建置階段警告或使用舊版編譯器來避免出現警告。|
|範圍|主要|
|版本|4.5|
|類型|正在重定目標|
