---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804664"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="d2014-101">WorkflowDesigner.Load 不會移除符號屬性</span><span class="sxs-lookup"><span data-stu-id="d2014-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d2014-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d2014-102">Details</span></span>|<span data-ttu-id="d2014-103">如果工作流程設計工具是以 .NET Framework 4.5 為目標，並使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法載入重新裝載的 3.5 工作流程，則會在儲存工作流程時擲回 <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="d2014-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="d2014-104">建議</span><span class="sxs-lookup"><span data-stu-id="d2014-104">Suggestion</span></span>|<span data-ttu-id="d2014-105">只有在工作流程設計工具是以 .NET Framework 4.5 為目標時才會出現此 Bug，因此可藉由將 <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> 設定為 .NET Framework 4.0 來解決。或者，可以使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> 方法載入工作流桯來避免問題，而不要使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load>。</span><span class="sxs-lookup"><span data-stu-id="d2014-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="d2014-106">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d2014-106">Scope</span></span>|<span data-ttu-id="d2014-107">主要</span><span class="sxs-lookup"><span data-stu-id="d2014-107">Major</span></span>|
|<span data-ttu-id="d2014-108">版本</span><span class="sxs-lookup"><span data-stu-id="d2014-108">Version</span></span>|<span data-ttu-id="d2014-109">4.5</span><span class="sxs-lookup"><span data-stu-id="d2014-109">4.5</span></span>|
|<span data-ttu-id="d2014-110">類型</span><span class="sxs-lookup"><span data-stu-id="d2014-110">Type</span></span>|<span data-ttu-id="d2014-111">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d2014-111">Retargeting</span></span>|
|<span data-ttu-id="d2014-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d2014-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
