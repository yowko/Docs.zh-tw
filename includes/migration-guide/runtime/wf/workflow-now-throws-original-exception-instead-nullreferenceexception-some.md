---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496894"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="2e7fa-101">在某些情況下，工作流程現在會擲回原始例外狀況，而不是 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="2e7fa-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="2e7fa-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2e7fa-102">Details</span></span>

<span data-ttu-id="2e7fa-103">在 .NET Framework 4.6.2 和舊版中，工作流程活動的 Execute 方法擲回 <xref:System.Exception.Message> 屬性為 <code>null</code> 值的例外狀況時，System.Activities 工作流程執行階段會擲回 <xref:System.NullReferenceException?displayProperty=fullName>，進而遮罩原始的例外狀況。在 .NET Framework 4.7 中，會擲回之前遮罩的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e7fa-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2e7fa-104">建議</span><span class="sxs-lookup"><span data-stu-id="2e7fa-104">Suggestion</span></span>

<span data-ttu-id="2e7fa-105">如果您的程式碼依賴處理 <xref:System.NullReferenceException?displayProperty=fullName>，請將它變更為攔截可能會從自訂活動擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e7fa-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="2e7fa-106">名稱</span><span class="sxs-lookup"><span data-stu-id="2e7fa-106">Name</span></span>    | <span data-ttu-id="2e7fa-107">值</span><span class="sxs-lookup"><span data-stu-id="2e7fa-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e7fa-108">範圍</span><span class="sxs-lookup"><span data-stu-id="2e7fa-108">Scope</span></span>   |<span data-ttu-id="2e7fa-109">Minor</span><span class="sxs-lookup"><span data-stu-id="2e7fa-109">Minor</span></span>|
|<span data-ttu-id="2e7fa-110">版本</span><span class="sxs-lookup"><span data-stu-id="2e7fa-110">Version</span></span>|<span data-ttu-id="2e7fa-111">4.7</span><span class="sxs-lookup"><span data-stu-id="2e7fa-111">4.7</span></span>|
|<span data-ttu-id="2e7fa-112">類型</span><span class="sxs-lookup"><span data-stu-id="2e7fa-112">Type</span></span>|<span data-ttu-id="2e7fa-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="2e7fa-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2e7fa-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2e7fa-114">Affected APIs</span></span>

- <xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)`
- `M:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)`
- ``M:System.Activities.AsyncCodeActivity`1.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)``
- `M:System.Activities.WorkflowInvoker.Invoke`

-->
