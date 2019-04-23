---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774388"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="0bcce-101">WorkflowDesigner.Load 不會移除符號屬性</span><span class="sxs-lookup"><span data-stu-id="0bcce-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0bcce-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0bcce-102">Details</span></span>|<span data-ttu-id="0bcce-103">如果工作流程設計工具是以 .NET Framework 4.5 為目標，並使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法載入重新裝載的 3.5 工作流程，則會在儲存工作流程時擲回 <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="0bcce-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="0bcce-104">建議</span><span class="sxs-lookup"><span data-stu-id="0bcce-104">Suggestion</span></span>|<span data-ttu-id="0bcce-105">只有在工作流程設計工具是以 .NET Framework 4.5 為目標時才會出現此 Bug，因此可藉由將 <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> 設定為 .NET Framework 4.0 來解決。或者，可以使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> 方法載入工作流桯來避免問題，而不要使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load>。</span><span class="sxs-lookup"><span data-stu-id="0bcce-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="0bcce-106">範圍</span><span class="sxs-lookup"><span data-stu-id="0bcce-106">Scope</span></span>|<span data-ttu-id="0bcce-107">主要</span><span class="sxs-lookup"><span data-stu-id="0bcce-107">Major</span></span>|
|<span data-ttu-id="0bcce-108">版本</span><span class="sxs-lookup"><span data-stu-id="0bcce-108">Version</span></span>|<span data-ttu-id="0bcce-109">4.5</span><span class="sxs-lookup"><span data-stu-id="0bcce-109">4.5</span></span>|
|<span data-ttu-id="0bcce-110">類型</span><span class="sxs-lookup"><span data-stu-id="0bcce-110">Type</span></span>|<span data-ttu-id="0bcce-111">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="0bcce-111">Retargeting</span></span>|
|<span data-ttu-id="0bcce-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0bcce-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
