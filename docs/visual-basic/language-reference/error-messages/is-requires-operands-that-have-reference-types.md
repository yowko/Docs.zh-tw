---
title: "'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: fbd0011e76ccecc605b0355025b7ca131e44724e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263926"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="9e216-102">'Is' 需要有參考類型的運算元，但此運算元擁有實值型別 '\<類型名稱 >'</span><span class="sxs-lookup"><span data-stu-id="9e216-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>
<span data-ttu-id="9e216-103">`Is`比較運算子會判斷兩個物件變數是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e216-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="9e216-104">這項比較未定義實值型別。</span><span class="sxs-lookup"><span data-stu-id="9e216-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="9e216-105">**錯誤 ID:** BC30020</span><span class="sxs-lookup"><span data-stu-id="9e216-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e216-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9e216-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9e216-107">使用適當的算術比較運算子或`Like`運算子來比較兩個實值型別。</span><span class="sxs-lookup"><span data-stu-id="9e216-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e216-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e216-108">See also</span></span>
- [<span data-ttu-id="9e216-109">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="9e216-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="9e216-110">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="9e216-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="9e216-111">比較運算子</span><span class="sxs-lookup"><span data-stu-id="9e216-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
