---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234675"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="09ff9-101">WorkflowDesigner.Load 不會移除符號屬性</span><span class="sxs-lookup"><span data-stu-id="09ff9-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="09ff9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="09ff9-102">Details</span></span>|<span data-ttu-id="09ff9-103">如果工作流程設計工具是以 .NET Framework 4.5 為目標，並使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法載入重新裝載的 3.5 工作流程，則會在儲存工作流程時擲回 <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="09ff9-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="09ff9-104">建議</span><span class="sxs-lookup"><span data-stu-id="09ff9-104">Suggestion</span></span>|<span data-ttu-id="09ff9-105">只有在工作流程設計工具是以 .NET Framework 4.5 為目標時才會出現此 Bug，因此可藉由將 <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> 設定為 .NET Framework 4.0 來解決。或者，可以使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> 方法載入工作流桯來避免問題，而不要使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load>。</span><span class="sxs-lookup"><span data-stu-id="09ff9-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="09ff9-106">範圍</span><span class="sxs-lookup"><span data-stu-id="09ff9-106">Scope</span></span>|<span data-ttu-id="09ff9-107">主要</span><span class="sxs-lookup"><span data-stu-id="09ff9-107">Major</span></span>|
|<span data-ttu-id="09ff9-108">版本</span><span class="sxs-lookup"><span data-stu-id="09ff9-108">Version</span></span>|<span data-ttu-id="09ff9-109">4.5</span><span class="sxs-lookup"><span data-stu-id="09ff9-109">4.5</span></span>|
|<span data-ttu-id="09ff9-110">類型</span><span class="sxs-lookup"><span data-stu-id="09ff9-110">Type</span></span>|<span data-ttu-id="09ff9-111">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="09ff9-111">Retargeting</span></span>|
|<span data-ttu-id="09ff9-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="09ff9-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
