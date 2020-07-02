---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615624"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a><span data-ttu-id="182b7-101">如果使用 EntityDeploySplit 或 EntityClean 工作，以 Visual Studio 2013 建置 Entity Framework edmx 可能會失敗，並出現錯誤 MSB4062</span><span class="sxs-lookup"><span data-stu-id="182b7-101">Building an Entity Framework edmx with Visual Studio 2013 can fail with error MSB4062 if using the EntityDeploySplit or EntityClean tasks</span></span>

#### <a name="details"></a><span data-ttu-id="182b7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="182b7-102">Details</span></span>

<span data-ttu-id="182b7-103">MSBuild 12.0 工具 (隨附於 Visual Studio 2013) 已變更 MSBuild 檔案位置，導致舊版 Entity Framework 的目標檔案無效。</span><span class="sxs-lookup"><span data-stu-id="182b7-103">MSBuild 12.0 tools (included in Visual Studio 2013) changed MSBuild file locations, causing older Entity Framework targets files to be invalid.</span></span> <span data-ttu-id="182b7-104">結果是 `EntityDeploySplit` 和 `EntityClean` 工作會失敗，因為找不到 `Microsoft.Data.Entity.Build.Tasks.dll`。</span><span class="sxs-lookup"><span data-stu-id="182b7-104">The result is that `EntityDeploySplit` and `EntityClean` tasks fail because they are unable to find `Microsoft.Data.Entity.Build.Tasks.dll`.</span></span> <span data-ttu-id="182b7-105">請注意，造成此中斷的原因是工具組 (MSBuild/VS) 變更，而不是 .NET Framework 變更。</span><span class="sxs-lookup"><span data-stu-id="182b7-105">Note that this break is because of a toolset (MSBuild/VS) change, not because of a .NET Framework change.</span></span> <span data-ttu-id="182b7-106">只有在升級開發人員工具時才會發生此情況，若只是升級 .NET Framework 則不會發生。</span><span class="sxs-lookup"><span data-stu-id="182b7-106">It will only occur when upgrading developer tools, not when merely upgrading the .NET Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="182b7-107">建議</span><span class="sxs-lookup"><span data-stu-id="182b7-107">Suggestion</span></span>

<span data-ttu-id="182b7-108">Entity Framework 的目標檔案已修正，從 .NET Framework 4.6 開始，可搭配新的 MSBuild 配置使用。</span><span class="sxs-lookup"><span data-stu-id="182b7-108">Entity Framework targets files are fixed to work with the new MSBuild layout beginning in the .NET Framework 4.6.</span></span> <span data-ttu-id="182b7-109">升級至該版 Framework 將會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="182b7-109">Upgrading to that version of the Framework will fix this issue.</span></span> <span data-ttu-id="182b7-110">或者，您也可以使用[此因應措施](https://stackoverflow.com/a/24249247/131944)來直接修補目標檔案。</span><span class="sxs-lookup"><span data-stu-id="182b7-110">Alternatively, [this workaround](https://stackoverflow.com/a/24249247/131944) can be used to patch the targets files directly.</span></span>

| <span data-ttu-id="182b7-111">名稱</span><span class="sxs-lookup"><span data-stu-id="182b7-111">Name</span></span>    | <span data-ttu-id="182b7-112">值</span><span class="sxs-lookup"><span data-stu-id="182b7-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="182b7-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="182b7-113">Scope</span></span>   | <span data-ttu-id="182b7-114">主要</span><span class="sxs-lookup"><span data-stu-id="182b7-114">Major</span></span>       |
| <span data-ttu-id="182b7-115">版本</span><span class="sxs-lookup"><span data-stu-id="182b7-115">Version</span></span> | <span data-ttu-id="182b7-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="182b7-116">4.5.1</span></span>       |
| <span data-ttu-id="182b7-117">類型</span><span class="sxs-lookup"><span data-stu-id="182b7-117">Type</span></span>    | <span data-ttu-id="182b7-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="182b7-118">Retargeting</span></span> |
