---
title: 陣列
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54f5d68a343f473c67484e9e806551eb115bac36
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="arrays"></a><span data-ttu-id="066c9-102">陣列</span><span class="sxs-lookup"><span data-stu-id="066c9-102">Arrays</span></span>
<span data-ttu-id="066c9-103">**✓ 不要**偏好使用透過公用應用程式開發介面中的陣列的集合。</span><span class="sxs-lookup"><span data-stu-id="066c9-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="066c9-104">[集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md)> 一節提供有關如何選擇集合和陣列的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="066c9-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="066c9-105">**X 不**使用唯讀陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="066c9-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="066c9-106">欄位為唯讀且無法變更，但是可以變更在陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="066c9-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="066c9-107">**✓ 考慮**使用不規則的陣列，而不要使用多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="066c9-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="066c9-108">不規則的陣列是也是陣列的元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="066c9-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="066c9-109">組成元素的陣列可以是不同的大小，相較於多維陣列的某些資料 （例如疏鬆矩陣） 集而言較不浪費空間。</span><span class="sxs-lookup"><span data-stu-id="066c9-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="066c9-110">此外，CLR 最佳化不規則的陣列索引作業，讓它們可能會出現在某些情況下更好的執行階段效能。</span><span class="sxs-lookup"><span data-stu-id="066c9-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="066c9-111">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="066c9-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="066c9-112">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="066c9-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066c9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="066c9-113">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="066c9-114">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="066c9-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="066c9-115">用法方針</span><span class="sxs-lookup"><span data-stu-id="066c9-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
