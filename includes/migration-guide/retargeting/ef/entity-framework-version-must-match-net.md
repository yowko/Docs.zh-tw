---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234650"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="bf9bd-101">Entity Framework 版本必須符合 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="bf9bd-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bf9bd-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bf9bd-102">Details</span></span>|<span data-ttu-id="bf9bd-103">Entity Framework 版本應該符合 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="bf9bd-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="bf9bd-104">建議針對 .NET Framework 4.5 使用 Entity Framework 5。</span><span class="sxs-lookup"><span data-stu-id="bf9bd-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="bf9bd-105">.NET Framework 4.5 專案中，已知 EF 4.x 有一些 <xref:System.ComponentModel.DataAnnotations> 相關問題。</span><span class="sxs-lookup"><span data-stu-id="bf9bd-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="bf9bd-106">在 .NET 4.5 中，這些已移至不同的組件，因此決定要使用哪些註解時會有問題。</span><span class="sxs-lookup"><span data-stu-id="bf9bd-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="bf9bd-107">建議</span><span class="sxs-lookup"><span data-stu-id="bf9bd-107">Suggestion</span></span>|<span data-ttu-id="bf9bd-108">針對 .NET Framework 4.5 升級至 Entity Framework 5</span><span class="sxs-lookup"><span data-stu-id="bf9bd-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="bf9bd-109">範圍</span><span class="sxs-lookup"><span data-stu-id="bf9bd-109">Scope</span></span>|<span data-ttu-id="bf9bd-110">主要</span><span class="sxs-lookup"><span data-stu-id="bf9bd-110">Major</span></span>|
|<span data-ttu-id="bf9bd-111">版本</span><span class="sxs-lookup"><span data-stu-id="bf9bd-111">Version</span></span>|<span data-ttu-id="bf9bd-112">4.5</span><span class="sxs-lookup"><span data-stu-id="bf9bd-112">4.5</span></span>|
|<span data-ttu-id="bf9bd-113">類型</span><span class="sxs-lookup"><span data-stu-id="bf9bd-113">Type</span></span>|<span data-ttu-id="bf9bd-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="bf9bd-114">Retargeting</span></span>|
