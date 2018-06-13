---
title: '&#39;IsNot&#39;類型的運算元&#39;typename&#39;可以只相較於&#39;Nothing&#39;，因為&#39;typename&#39;是可為 null 的型別'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 44cc17c73b476e5e322b9b58b021bc7bcd63167f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587592"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="7d242-102">&#39;IsNot&#39;類型的運算元&#39;typename&#39;可以只相較於&#39;Nothing&#39;，因為&#39;typename&#39;是可為 null 的型別</span><span class="sxs-lookup"><span data-stu-id="7d242-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="7d242-103">宣告為可為 null 的變數已被的運算式進行比較以外`Nothing`使用`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="7d242-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="7d242-104">**錯誤 ID:** BC32128</span><span class="sxs-lookup"><span data-stu-id="7d242-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d242-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7d242-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="7d242-106">要比較的運算式可為 null 的類型以外`Nothing`使用`IsNot`運算子，請呼叫`GetType`方法可為 null 的類型和比較結果與運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7d242-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d242-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d242-107">See Also</span></span>  
 [<span data-ttu-id="7d242-108">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="7d242-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="7d242-109">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="7d242-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
