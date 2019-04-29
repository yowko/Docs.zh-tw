---
title: 空間函式
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 09402633c5e7f591a534992fc92655e6a2d1d88d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797692"
---
# <a name="spatial-functions"></a><span data-ttu-id="ad9bb-102">空間函式</span><span class="sxs-lookup"><span data-stu-id="ad9bb-102">Spatial Functions</span></span>
<span data-ttu-id="ad9bb-103">空間型別沒有任何常值格式。</span><span class="sxs-lookup"><span data-stu-id="ad9bb-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="ad9bb-104">不過，您可以使用標準 Entity Framework 函式 (使用 Well-Known Text 格式的字串所呼叫)。</span><span class="sxs-lookup"><span data-stu-id="ad9bb-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="ad9bb-105">例如，下列函式呼叫可建立幾何點：</span><span class="sxs-lookup"><span data-stu-id="ad9bb-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="ad9bb-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>方法具有所有空間標準 Entity Framework 方法。</span><span class="sxs-lookup"><span data-stu-id="ad9bb-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="ad9bb-107">按一下相關方法，以查看應將哪些參數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="ad9bb-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
