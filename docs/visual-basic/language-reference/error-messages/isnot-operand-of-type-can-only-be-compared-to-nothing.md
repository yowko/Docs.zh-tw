---
title: '&#39;IsNot&#39;類型運算元的&#39;typename&#39;可以只相較於&#39;Nothing&#39;，因為&#39;typename&#39;是可為 null 的型別'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 65b04c85bccd169bbb2eea847d7b8af96c1a292f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505714"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="be9db-102">&#39;IsNot&#39;類型運算元的&#39;typename&#39;可以只相較於&#39;Nothing&#39;，因為&#39;typename&#39;是可為 null 的型別</span><span class="sxs-lookup"><span data-stu-id="be9db-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="be9db-103">宣告為可為 null 的變數已經做過比較運算式以外`Nothing`使用`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="be9db-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="be9db-104">**錯誤 ID:** BC32128</span><span class="sxs-lookup"><span data-stu-id="be9db-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be9db-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="be9db-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="be9db-106">若要使用 `Nothing` 運算子，將可為 Null 的類型與 `IsNot` 以外的運算式進行比較，請在可為 Null 的類型上呼叫 `GetType` 方法，並將結果與運算式進行比較，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="be9db-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="be9db-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be9db-107">See also</span></span>
- [<span data-ttu-id="be9db-108">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="be9db-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="be9db-109">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="be9db-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
