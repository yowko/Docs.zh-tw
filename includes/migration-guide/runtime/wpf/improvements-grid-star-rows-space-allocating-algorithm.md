---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621951"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="545b4-101">格線含星號資料列空間配置演算法的改進</span><span class="sxs-lookup"><span data-stu-id="545b4-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="545b4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="545b4-102">Details</span></span>

<span data-ttu-id="545b4-103">已修正 <xref:System.Windows.Controls.Grid> (於 .NET Framework 4.7 推出) 中[配置大小至 ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) 的演算法錯誤 (Bug)。</span><span class="sxs-lookup"><span data-stu-id="545b4-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="545b4-104">在某些情況下，例如含 <code>Height=&quot;Auto&quot;</code> 與空白資料列的格線，資料列會排列在錯誤的位置，可能會全部擠在格線外。</span><span class="sxs-lookup"><span data-stu-id="545b4-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="545b4-105">建議</span><span class="sxs-lookup"><span data-stu-id="545b4-105">Suggestion</span></span>

<span data-ttu-id="545b4-106">若要讓應用程式受益於這些變更，您必須在 .NET Framework 4.8 或更新版本上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="545b4-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="545b4-107">名稱</span><span class="sxs-lookup"><span data-stu-id="545b4-107">Name</span></span>    | <span data-ttu-id="545b4-108">值</span><span class="sxs-lookup"><span data-stu-id="545b4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="545b4-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="545b4-109">Scope</span></span>   |<span data-ttu-id="545b4-110">主要</span><span class="sxs-lookup"><span data-stu-id="545b4-110">Major</span></span>|
|<span data-ttu-id="545b4-111">版本</span><span class="sxs-lookup"><span data-stu-id="545b4-111">Version</span></span>|<span data-ttu-id="545b4-112">4.8</span><span class="sxs-lookup"><span data-stu-id="545b4-112">4.8</span></span>|
|<span data-ttu-id="545b4-113">類型</span><span class="sxs-lookup"><span data-stu-id="545b4-113">Type</span></span>|<span data-ttu-id="545b4-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="545b4-114">Runtime</span></span>|
