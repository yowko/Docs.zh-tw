---
title: 數值與比較運算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 9b31fd2d819afbb1e589ad74f23ec139830c68b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212163"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="283ac-102">數值與比較運算子</span><span class="sxs-lookup"><span data-stu-id="283ac-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="283ac-103">除了下列幾點以外，在 Common Language Runtime (CLR) 中算術和比較運算子都會如預期運作：</span><span class="sxs-lookup"><span data-stu-id="283ac-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="283ac-104">SQL 不支援浮點數值 (Floating-Point Number) 的模數運算子。</span><span class="sxs-lookup"><span data-stu-id="283ac-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="283ac-105">SQL 不支援不檢查的算術。</span><span class="sxs-lookup"><span data-stu-id="283ac-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="283ac-106">當您在無法於 SQL 中複寫因而不受支援的運算式中使用遞增和遞減運算子時，這些運算子會造成副作用。</span><span class="sxs-lookup"><span data-stu-id="283ac-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="283ac-107">支援的運算子</span><span class="sxs-lookup"><span data-stu-id="283ac-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="283ac-108">支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="283ac-108">supports the following operators.</span></span>  
  
-   <span data-ttu-id="283ac-109">基本算術運算子：</span><span class="sxs-lookup"><span data-stu-id="283ac-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="283ac-110">`-` (減法)</span><span class="sxs-lookup"><span data-stu-id="283ac-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="283ac-111">Visual Basic 整數除法 (`\`)</span><span class="sxs-lookup"><span data-stu-id="283ac-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="283ac-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="283ac-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="283ac-113">`-` (一元否定運算)</span><span class="sxs-lookup"><span data-stu-id="283ac-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="283ac-114">基本比較運算子：</span><span class="sxs-lookup"><span data-stu-id="283ac-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="283ac-115">Visual Basic `=` 和 C# `==`</span><span class="sxs-lookup"><span data-stu-id="283ac-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="283ac-116">Visual Basic `<>` 和 C# `!=`</span><span class="sxs-lookup"><span data-stu-id="283ac-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="283ac-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="283ac-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="283ac-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="283ac-118">See also</span></span>

- [<span data-ttu-id="283ac-119">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="283ac-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [<span data-ttu-id="283ac-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="283ac-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)
- [<span data-ttu-id="283ac-121">運算子</span><span class="sxs-lookup"><span data-stu-id="283ac-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
