---
title: 陣列
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: KrzysztofCwalina
ms.openlocfilehash: dd30cdee0440553a9f955f0b3f4ee420e938b9ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864113"
---
# <a name="arrays"></a><span data-ttu-id="80dcb-102">陣列</span><span class="sxs-lookup"><span data-stu-id="80dcb-102">Arrays</span></span>
<span data-ttu-id="80dcb-103">**✓ DO** 偏好使用透過公用應用程式開發介面中的陣列的集合。</span><span class="sxs-lookup"><span data-stu-id="80dcb-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="80dcb-104">[集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)節提供有關如何選擇集合和陣列的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80dcb-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="80dcb-105">**X DO NOT** 使用唯讀陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="80dcb-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="80dcb-106">欄位本身是唯讀的而且無法變更，但是可以變更陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="80dcb-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="80dcb-107">**✓ CONSIDER** 使用不規則的陣列，而不要使用多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="80dcb-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="80dcb-108">不規則的陣列是也是陣列的元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="80dcb-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="80dcb-109">產生的項目陣列可以是不同的大小，導致相較於多維陣列的某些資料集的資料 （例如，疏鬆矩陣） 較不會浪費空間。</span><span class="sxs-lookup"><span data-stu-id="80dcb-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="80dcb-110">此外，CLR 最佳化不規則的陣列索引作業，因此它們可能會表現出更好的執行階段效能，在某些情況下。</span><span class="sxs-lookup"><span data-stu-id="80dcb-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="80dcb-111">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="80dcb-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="80dcb-112">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="80dcb-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80dcb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80dcb-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="80dcb-114">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="80dcb-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="80dcb-115">用法方針</span><span class="sxs-lookup"><span data-stu-id="80dcb-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
