---
title: 陣列
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741800"
---
# <a name="arrays"></a><span data-ttu-id="ffaea-102">陣列</span><span class="sxs-lookup"><span data-stu-id="ffaea-102">Arrays</span></span>
<span data-ttu-id="ffaea-103">✔️偏好在公用 Api 中使用陣列的集合。</span><span class="sxs-lookup"><span data-stu-id="ffaea-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="ffaea-104">[[集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)] 區段提供如何在集合和陣列之間進行選擇的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ffaea-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="ffaea-105">❌ 不要使用唯讀陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="ffaea-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="ffaea-106">欄位本身是唯讀的，而且無法變更，但陣列中的元素可以變更。</span><span class="sxs-lookup"><span data-stu-id="ffaea-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="ffaea-107">✔️考慮使用不規則陣列，而不是多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="ffaea-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="ffaea-108">不規則陣列是一種陣列，其中包含同時也是陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="ffaea-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="ffaea-109">組成元素的陣列可以是不同的大小，因此，某些資料集（例如，疏鬆陣列）相較于多維度陣列，會浪費更少的空間。</span><span class="sxs-lookup"><span data-stu-id="ffaea-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="ffaea-110">此外，CLR 會優化不規則陣列上的索引作業，因此在某些情況下可能會表現出更佳的執行時間效能。</span><span class="sxs-lookup"><span data-stu-id="ffaea-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="ffaea-111">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="ffaea-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ffaea-112">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="ffaea-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ffaea-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffaea-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="ffaea-114">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ffaea-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ffaea-115">用法方針</span><span class="sxs-lookup"><span data-stu-id="ffaea-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
