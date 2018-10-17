---
title: 數值與比較運算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 733c1e494c29f04aa06a4159c3b1dae219f01b44
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372326"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="34029-102">數值與比較運算子</span><span class="sxs-lookup"><span data-stu-id="34029-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="34029-103">除了下列幾點以外，在 Common Language Runtime (CLR) 中算術和比較運算子都會如預期運作：</span><span class="sxs-lookup"><span data-stu-id="34029-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="34029-104">SQL 不支援浮點數值 (Floating-Point Number) 的模數運算子。</span><span class="sxs-lookup"><span data-stu-id="34029-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="34029-105">SQL 不支援不檢查的算術。</span><span class="sxs-lookup"><span data-stu-id="34029-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="34029-106">當您在無法於 SQL 中複寫因而不受支援的運算式中使用遞增和遞減運算子時，這些運算子會造成副作用。</span><span class="sxs-lookup"><span data-stu-id="34029-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="34029-107">支援的運算子</span><span class="sxs-lookup"><span data-stu-id="34029-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="34029-108">支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="34029-108">supports the following operators.</span></span>  
  
-   <span data-ttu-id="34029-109">基本算術運算子：</span><span class="sxs-lookup"><span data-stu-id="34029-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="34029-110">`-` (減法)</span><span class="sxs-lookup"><span data-stu-id="34029-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="34029-111">Visual Basic 整數除法 (`\`)</span><span class="sxs-lookup"><span data-stu-id="34029-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="34029-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="34029-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="34029-113">`-` (一元否定運算)</span><span class="sxs-lookup"><span data-stu-id="34029-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="34029-114">基本比較運算子：</span><span class="sxs-lookup"><span data-stu-id="34029-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="34029-115">Visual Basic `=` 和 C# `==`</span><span class="sxs-lookup"><span data-stu-id="34029-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="34029-116">Visual Basic `<>` 和 C# `!=`</span><span class="sxs-lookup"><span data-stu-id="34029-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="34029-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="34029-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="34029-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34029-118">See Also</span></span>  
 [<span data-ttu-id="34029-119">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="34029-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="34029-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="34029-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="34029-121">運算子</span><span class="sxs-lookup"><span data-stu-id="34029-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
