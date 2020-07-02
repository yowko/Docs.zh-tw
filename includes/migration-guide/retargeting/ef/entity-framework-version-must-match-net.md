---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617138"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="8bab5-101">Entity Framework 版本必須符合 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="8bab5-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="8bab5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8bab5-102">Details</span></span>

<span data-ttu-id="8bab5-103">Entity Framework （EF）版本應該與 .NET Framework 版本相符。</span><span class="sxs-lookup"><span data-stu-id="8bab5-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="8bab5-104">建議針對 .NET Framework 4.5 使用 Entity Framework 5。</span><span class="sxs-lookup"><span data-stu-id="8bab5-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="8bab5-105">.NET Framework 4.5 專案中，已知 EF 4.x 有一些 <xref:System.ComponentModel.DataAnnotations> 相關問題。</span><span class="sxs-lookup"><span data-stu-id="8bab5-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="8bab5-106">在 .NET Framework 4.5 中，這些已移至不同的元件，因此在決定要使用的注釋時，會發生問題。</span><span class="sxs-lookup"><span data-stu-id="8bab5-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8bab5-107">建議</span><span class="sxs-lookup"><span data-stu-id="8bab5-107">Suggestion</span></span>

<span data-ttu-id="8bab5-108">針對 .NET Framework 4.5 升級至 Entity Framework 5</span><span class="sxs-lookup"><span data-stu-id="8bab5-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="8bab5-109">名稱</span><span class="sxs-lookup"><span data-stu-id="8bab5-109">Name</span></span>    | <span data-ttu-id="8bab5-110">值</span><span class="sxs-lookup"><span data-stu-id="8bab5-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8bab5-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8bab5-111">Scope</span></span>   | <span data-ttu-id="8bab5-112">主要</span><span class="sxs-lookup"><span data-stu-id="8bab5-112">Major</span></span>       |
| <span data-ttu-id="8bab5-113">版本</span><span class="sxs-lookup"><span data-stu-id="8bab5-113">Version</span></span> | <span data-ttu-id="8bab5-114">4.5</span><span class="sxs-lookup"><span data-stu-id="8bab5-114">4.5</span></span>         |
| <span data-ttu-id="8bab5-115">類型</span><span class="sxs-lookup"><span data-stu-id="8bab5-115">Type</span></span>    | <span data-ttu-id="8bab5-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8bab5-116">Retargeting</span></span> |
