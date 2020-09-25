---
title: 空間函式
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7d0979b5166c847244cbeec97acf4fa4f745a259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169579"
---
# <a name="spatial-functions"></a><span data-ttu-id="094a5-102">空間函式</span><span class="sxs-lookup"><span data-stu-id="094a5-102">Spatial Functions</span></span>

<span data-ttu-id="094a5-103">空間型別沒有任何常值格式。</span><span class="sxs-lookup"><span data-stu-id="094a5-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="094a5-104">不過，您可以使用標準 Entity Framework 函式 (使用 Well-Known Text 格式的字串所呼叫)。</span><span class="sxs-lookup"><span data-stu-id="094a5-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="094a5-105">例如，下列函式呼叫可建立幾何點：</span><span class="sxs-lookup"><span data-stu-id="094a5-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="094a5-106">這些 <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> 方法都有所有空間標準 Entity Framework 方法。</span><span class="sxs-lookup"><span data-stu-id="094a5-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="094a5-107">按一下相關方法，以查看應將哪些參數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="094a5-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
