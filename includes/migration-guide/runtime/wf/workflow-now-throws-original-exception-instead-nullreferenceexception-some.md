---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621101"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>在某些情況下，工作流程現在會擲回原始例外狀況，而不是 NullReferenceException

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 和舊版中，工作流程活動的 Execute 方法擲回 <xref:System.Exception.Message> 屬性為 <code>null</code> 值的例外狀況時，System.Activities 工作流程執行階段會擲回 <xref:System.NullReferenceException?displayProperty=fullName>，進而遮罩原始的例外狀況。在 .NET Framework 4.7 中，會擲回之前遮罩的例外狀況。

#### <a name="suggestion"></a>建議

如果您的程式碼依賴處理 <xref:System.NullReferenceException?displayProperty=fullName>，請將它變更為攔截可能會從自訂活動擲回的例外狀況。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.7|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
