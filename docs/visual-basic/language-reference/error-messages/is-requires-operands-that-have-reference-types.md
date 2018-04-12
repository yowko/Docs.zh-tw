---
title: '&#39; 是 &#39;需要運算元有參考類型，但此運算元擁有實值型別 &#39;&lt;typename&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28d017a566fdc1e55cb53ce907641d6bccfb354c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="46628-102">&#39; 是 &#39;需要運算元有參考類型，但此運算元擁有實值型別 &#39;&lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="46628-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="46628-103">`Is`比較運算子會判斷兩個物件變數是否參考相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="46628-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="46628-104">這項比較是未定義實值類型。</span><span class="sxs-lookup"><span data-stu-id="46628-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="46628-105">**錯誤 ID:** BC30020</span><span class="sxs-lookup"><span data-stu-id="46628-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46628-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="46628-106">To correct this error</span></span>  
  
-   <span data-ttu-id="46628-107">使用適當的算術比較運算子或`Like`運算子來比較兩個實值類型。</span><span class="sxs-lookup"><span data-stu-id="46628-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46628-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46628-108">See Also</span></span>  
 [<span data-ttu-id="46628-109">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="46628-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="46628-110">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="46628-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="46628-111">比較運算子</span><span class="sxs-lookup"><span data-stu-id="46628-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
