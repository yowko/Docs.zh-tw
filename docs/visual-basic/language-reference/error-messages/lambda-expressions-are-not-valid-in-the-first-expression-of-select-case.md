---
title: Lambda 運算式不是有效的第一個運算式中&#39;Select Case&#39;陳述式
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: afefa821f9695dbbfe2a96aee5afd3171ae5b1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700217"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="82439-102">Lambda 運算式不是有效的第一個運算式中&#39;Select Case&#39;陳述式</span><span class="sxs-lookup"><span data-stu-id="82439-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="82439-103">您無法使用 lambda 運算式中的測試運算式`Select Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="82439-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="82439-104">Lambda 運算式定義傳回函式和測試運算式`Select Case`陳述式必須是基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="82439-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="82439-105">下列程式碼會造成這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="82439-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="82439-106">**錯誤 ID:** BC36635</span><span class="sxs-lookup"><span data-stu-id="82439-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82439-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="82439-107">To correct this error</span></span>  
  
-   <span data-ttu-id="82439-108">檢查您的程式碼，以判斷不同的條件式建構 (例如 `If...Then...Else` 陳述式) 是否可行。</span><span class="sxs-lookup"><span data-stu-id="82439-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="82439-109">您可能想要呼叫的函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="82439-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="82439-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82439-110">See also</span></span>
- [<span data-ttu-id="82439-111">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="82439-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="82439-112">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="82439-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="82439-113">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="82439-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
