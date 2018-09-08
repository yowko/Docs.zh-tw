---
title: 空間函式
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133950"
---
# <a name="spatial-functions"></a><span data-ttu-id="dbe15-102">空間函式</span><span class="sxs-lookup"><span data-stu-id="dbe15-102">Spatial Functions</span></span>
<span data-ttu-id="dbe15-103">空間型別沒有任何常值格式。</span><span class="sxs-lookup"><span data-stu-id="dbe15-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="dbe15-104">不過，您可以使用標準 Entity Framework 函式 (使用 Well-Known Text 格式的字串所呼叫)。</span><span class="sxs-lookup"><span data-stu-id="dbe15-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="dbe15-105">例如，下列函式呼叫可建立幾何點：</span><span class="sxs-lookup"><span data-stu-id="dbe15-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="dbe15-106">[SpatialEdmFunctions 方法](https://msdn.microsoft.com/library/hh749531.aspx)頁面會列出所有空間標準 Entity Framework 方法。</span><span class="sxs-lookup"><span data-stu-id="dbe15-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="dbe15-107">按一下相關方法，以查看應將哪些參數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="dbe15-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
