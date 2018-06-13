---
title: 巢狀函式沒有與委派相容的簽章&#39;&lt;委派名稱&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594467"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="91a46-102">巢狀函式沒有與委派相容的簽章&#39;&lt;委派名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="91a46-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="91a46-103">Lambda 運算式已被指派至具有相容簽章的委派。</span><span class="sxs-lookup"><span data-stu-id="91a46-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="91a46-104">例如，下列程式碼中，委派`Del`有兩個整數參數。</span><span class="sxs-lookup"><span data-stu-id="91a46-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="91a46-105">如果有一個引數的 lambda 運算式宣告為類型將會引發錯誤`Del`:</span><span class="sxs-lookup"><span data-stu-id="91a46-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="91a46-106">**錯誤 ID:** BC36532</span><span class="sxs-lookup"><span data-stu-id="91a46-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="91a46-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="91a46-107">To correct this error</span></span>  
  
-   <span data-ttu-id="91a46-108">調整委派定義或指派的 lambda 運算式的簽章是不相容。</span><span class="sxs-lookup"><span data-stu-id="91a46-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a46-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91a46-109">See Also</span></span>  
 [<span data-ttu-id="91a46-110">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="91a46-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="91a46-111">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="91a46-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
