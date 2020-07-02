---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617147"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="d219e-101">WorkFlow 3.0 類型已淘汰</span><span class="sxs-lookup"><span data-stu-id="d219e-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="d219e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d219e-102">Details</span></span>

<span data-ttu-id="d219e-103">Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 命名空間中的 API) 現在已淘汰。</span><span class="sxs-lookup"><span data-stu-id="d219e-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d219e-104">建議</span><span class="sxs-lookup"><span data-stu-id="d219e-104">Suggestion</span></span>

<span data-ttu-id="d219e-105">您應該改用新的 WWF 4.0 API (在 System.Activities 中)。</span><span class="sxs-lookup"><span data-stu-id="d219e-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="d219e-106">您可以在[這裡](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的範例，並在[這裡](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5)取得進一步指引。</span><span class="sxs-lookup"><span data-stu-id="d219e-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="d219e-107">此外，由於仍然支援 WWF 3.0 API，因此可使用這些 API，並藉由隱藏建置階段警告或使用舊版編譯器來避免出現警告。</span><span class="sxs-lookup"><span data-stu-id="d219e-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="d219e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="d219e-108">Name</span></span>    | <span data-ttu-id="d219e-109">值</span><span class="sxs-lookup"><span data-stu-id="d219e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d219e-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d219e-110">Scope</span></span>   | <span data-ttu-id="d219e-111">主要</span><span class="sxs-lookup"><span data-stu-id="d219e-111">Major</span></span>       |
| <span data-ttu-id="d219e-112">版本</span><span class="sxs-lookup"><span data-stu-id="d219e-112">Version</span></span> | <span data-ttu-id="d219e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d219e-113">4.5</span></span>         |
| <span data-ttu-id="d219e-114">類型</span><span class="sxs-lookup"><span data-stu-id="d219e-114">Type</span></span>    | <span data-ttu-id="d219e-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d219e-115">Retargeting</span></span> |
