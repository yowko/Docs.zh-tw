---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803463"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="fdafc-101">在某些情況下，工作流程現在會擲回原始例外狀況，而不是 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="fdafc-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fdafc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fdafc-102">Details</span></span>|<span data-ttu-id="fdafc-103">在 .NET Framework 4.6.2 和舊版中，工作流程活動的 Execute 方法擲回 <xref:System.Exception.Message> 屬性為 <code>null</code> 值的例外狀況時，System.Activities 工作流程執行階段會擲回 <xref:System.NullReferenceException?displayProperty=name>，進而遮罩原始的例外狀況。在 .NET Framework 4.7 中，會擲回之前遮罩的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fdafc-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="fdafc-104">建議</span><span class="sxs-lookup"><span data-stu-id="fdafc-104">Suggestion</span></span>|<span data-ttu-id="fdafc-105">如果您的程式碼依賴處理 <xref:System.NullReferenceException?displayProperty=name>，請將它變更為攔截可能會從自訂活動擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fdafc-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="fdafc-106">範圍</span><span class="sxs-lookup"><span data-stu-id="fdafc-106">Scope</span></span>|<span data-ttu-id="fdafc-107">次要</span><span class="sxs-lookup"><span data-stu-id="fdafc-107">Minor</span></span>|
|<span data-ttu-id="fdafc-108">版本</span><span class="sxs-lookup"><span data-stu-id="fdafc-108">Version</span></span>|<span data-ttu-id="fdafc-109">4.7</span><span class="sxs-lookup"><span data-stu-id="fdafc-109">4.7</span></span>|
|<span data-ttu-id="fdafc-110">類型</span><span class="sxs-lookup"><span data-stu-id="fdafc-110">Type</span></span>|<span data-ttu-id="fdafc-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="fdafc-111">Runtime</span></span>|
|<span data-ttu-id="fdafc-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fdafc-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
