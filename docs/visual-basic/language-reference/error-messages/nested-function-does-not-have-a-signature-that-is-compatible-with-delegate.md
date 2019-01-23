---
title: 巢狀函式沒有與委派相容的簽章&#39;&lt;委派名稱&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: abfda4ee6064ec9ea54b8a3c383d10f8263a1458
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506403"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="5d828-102">巢狀函式沒有與委派相容的簽章&#39;&lt;委派名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="5d828-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="5d828-103">Lambda 運算式已指派給具有不相容的簽章的委派。</span><span class="sxs-lookup"><span data-stu-id="5d828-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="5d828-104">例如，下列程式碼中，委派`Del`有兩個整數參數。</span><span class="sxs-lookup"><span data-stu-id="5d828-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="5d828-105">如果具有一個引數的 lambda 運算式宣告為類型，就會引發錯誤`Del`:</span><span class="sxs-lookup"><span data-stu-id="5d828-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="5d828-106">**錯誤 ID:** BC36532</span><span class="sxs-lookup"><span data-stu-id="5d828-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d828-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5d828-107">To correct this error</span></span>  
  
-   <span data-ttu-id="5d828-108">調整委派定義或指派的 lambda 運算式，使簽章相容。</span><span class="sxs-lookup"><span data-stu-id="5d828-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d828-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d828-109">See also</span></span>
- [<span data-ttu-id="5d828-110">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="5d828-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="5d828-111">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="5d828-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
