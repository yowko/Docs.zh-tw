---
title: 陣列
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 11c1d23af4cf599ba632144634947520a1647ae7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701389"
---
# <a name="arrays"></a><span data-ttu-id="1e227-102">陣列</span><span class="sxs-lookup"><span data-stu-id="1e227-102">Arrays</span></span>

<span data-ttu-id="1e227-103">✔️想要在公用 Api 中使用集合，而不是陣列。</span><span class="sxs-lookup"><span data-stu-id="1e227-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="1e227-104">[ [集合](guidelines-for-collections.md) ] 區段提供如何在集合和陣列之間進行選擇的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1e227-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="1e227-105">❌ 請勿使用唯讀陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="1e227-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="1e227-106">欄位本身是唯讀的，而且無法變更，但陣列中的元素可以變更。</span><span class="sxs-lookup"><span data-stu-id="1e227-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="1e227-107">✔️考慮使用不規則陣列，而不是多維陣列。</span><span class="sxs-lookup"><span data-stu-id="1e227-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="1e227-108">不規則陣列是陣列，其元素也是陣列。</span><span class="sxs-lookup"><span data-stu-id="1e227-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="1e227-109">組成專案的陣列可以是不同的大小，導致某些資料集的空間浪費較少， (例如，相較于多維陣列，疏鬆陣列) 。</span><span class="sxs-lookup"><span data-stu-id="1e227-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="1e227-110">此外，CLR 會將不規則陣列的索引作業優化，因此在某些情況下，它們可能會表現出更好的執行時間效能。</span><span class="sxs-lookup"><span data-stu-id="1e227-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="1e227-111">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="1e227-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1e227-112">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="1e227-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1e227-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e227-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="1e227-114">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="1e227-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1e227-115">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="1e227-115">Usage Guidelines</span></span>](usage-guidelines.md)
