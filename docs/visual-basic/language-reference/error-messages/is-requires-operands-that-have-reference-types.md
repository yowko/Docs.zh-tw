---
title: '&#39;是&#39;需要運算元有參考型別，但此運算元擁有實值型別&#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 0b3f80e98087e455ec730dea8c57478528e9259c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722916"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="1745c-102">&#39;是&#39;需要運算元有參考型別，但此運算元擁有實值型別&#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="1745c-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="1745c-103">`Is`比較運算子會判斷兩個物件變數是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1745c-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="1745c-104">這項比較未定義實值型別。</span><span class="sxs-lookup"><span data-stu-id="1745c-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="1745c-105">**錯誤 ID:** BC30020</span><span class="sxs-lookup"><span data-stu-id="1745c-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1745c-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1745c-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1745c-107">使用適當的算術比較運算子或`Like`運算子來比較兩個實值型別。</span><span class="sxs-lookup"><span data-stu-id="1745c-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1745c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1745c-108">See also</span></span>
- [<span data-ttu-id="1745c-109">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="1745c-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="1745c-110">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="1745c-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="1745c-111">比較運算子</span><span class="sxs-lookup"><span data-stu-id="1745c-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
