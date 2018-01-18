---
title: "數值與比較運算子"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56558e790b8aee300da0a75ade7c0ac451a0eca1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="22e1f-102">數值與比較運算子</span><span class="sxs-lookup"><span data-stu-id="22e1f-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="22e1f-103">除了下列幾點以外，在 Common Language Runtime (CLR) 中算術和比較運算子都會如預期運作：</span><span class="sxs-lookup"><span data-stu-id="22e1f-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="22e1f-104">SQL 不支援浮點數值 (Floating-Point Number) 的模數運算子。</span><span class="sxs-lookup"><span data-stu-id="22e1f-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="22e1f-105">SQL 不支援不檢查的算術。</span><span class="sxs-lookup"><span data-stu-id="22e1f-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="22e1f-106">當您在無法於 SQL 中複寫因而不受支援的運算式中使用遞增和遞減運算子時，這些運算子會造成副作用。</span><span class="sxs-lookup"><span data-stu-id="22e1f-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="22e1f-107">支援的運算子</span><span class="sxs-lookup"><span data-stu-id="22e1f-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="22e1f-108"> 支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="22e1f-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="22e1f-109">基本算術運算子：</span><span class="sxs-lookup"><span data-stu-id="22e1f-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="22e1f-110">`-` (減法)</span><span class="sxs-lookup"><span data-stu-id="22e1f-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="22e1f-111">Visual Basic 整數除法 (`\`)</span><span class="sxs-lookup"><span data-stu-id="22e1f-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="22e1f-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="22e1f-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="22e1f-113">`-` (一元否定運算)</span><span class="sxs-lookup"><span data-stu-id="22e1f-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="22e1f-114">基本比較運算子：</span><span class="sxs-lookup"><span data-stu-id="22e1f-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="22e1f-115">Visual Basic `=` 和 C# `==`</span><span class="sxs-lookup"><span data-stu-id="22e1f-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="22e1f-116">Visual Basic `<>` 和 C# `!=`</span><span class="sxs-lookup"><span data-stu-id="22e1f-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="22e1f-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="22e1f-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="22e1f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="22e1f-118">See Also</span></span>  
 [<span data-ttu-id="22e1f-119">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="22e1f-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="22e1f-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="22e1f-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="22e1f-121">運算子</span><span class="sxs-lookup"><span data-stu-id="22e1f-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
