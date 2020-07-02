---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621101"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="2eb26-101">在某些情況下，工作流程現在會擲回原始例外狀況，而不是 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="2eb26-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="2eb26-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2eb26-102">Details</span></span>

<span data-ttu-id="2eb26-103">在 .NET Framework 4.6.2 和舊版中，工作流程活動的 Execute 方法擲回 <xref:System.Exception.Message> 屬性為 <code>null</code> 值的例外狀況時，System.Activities 工作流程執行階段會擲回 <xref:System.NullReferenceException?displayProperty=fullName>，進而遮罩原始的例外狀況。在 .NET Framework 4.7 中，會擲回之前遮罩的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2eb26-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2eb26-104">建議</span><span class="sxs-lookup"><span data-stu-id="2eb26-104">Suggestion</span></span>

<span data-ttu-id="2eb26-105">如果您的程式碼依賴處理 <xref:System.NullReferenceException?displayProperty=fullName>，請將它變更為攔截可能會從自訂活動擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2eb26-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="2eb26-106">名稱</span><span class="sxs-lookup"><span data-stu-id="2eb26-106">Name</span></span>    | <span data-ttu-id="2eb26-107">值</span><span class="sxs-lookup"><span data-stu-id="2eb26-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2eb26-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="2eb26-108">Scope</span></span>   |<span data-ttu-id="2eb26-109">Minor</span><span class="sxs-lookup"><span data-stu-id="2eb26-109">Minor</span></span>|
|<span data-ttu-id="2eb26-110">版本</span><span class="sxs-lookup"><span data-stu-id="2eb26-110">Version</span></span>|<span data-ttu-id="2eb26-111">4.7</span><span class="sxs-lookup"><span data-stu-id="2eb26-111">4.7</span></span>|
|<span data-ttu-id="2eb26-112">類型</span><span class="sxs-lookup"><span data-stu-id="2eb26-112">Type</span></span>|<span data-ttu-id="2eb26-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="2eb26-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2eb26-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2eb26-114">Affected APIs</span></span>

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
