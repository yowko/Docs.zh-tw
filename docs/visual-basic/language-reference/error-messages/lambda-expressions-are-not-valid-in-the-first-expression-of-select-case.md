---
title: Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: d56515093020a4c987d132491957ce6db9e21683
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287790"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="bc7f9-102">Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效</span><span class="sxs-lookup"><span data-stu-id="bc7f9-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>
<span data-ttu-id="bc7f9-103">您無法使用 lambda 運算式中的測試運算式`Select Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="bc7f9-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="bc7f9-104">Lambda 運算式定義傳回函式和測試運算式`Select Case`陳述式必須是基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="bc7f9-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="bc7f9-105">下列程式碼會造成這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="bc7f9-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="bc7f9-106">**錯誤 ID:** BC36635</span><span class="sxs-lookup"><span data-stu-id="bc7f9-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc7f9-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bc7f9-107">To correct this error</span></span>  
  
-   <span data-ttu-id="bc7f9-108">檢查您的程式碼，以判斷不同的條件式建構 (例如 `If...Then...Else` 陳述式) 是否可行。</span><span class="sxs-lookup"><span data-stu-id="bc7f9-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="bc7f9-109">您可能想要呼叫的函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="bc7f9-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc7f9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc7f9-110">See also</span></span>
- [<span data-ttu-id="bc7f9-111">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="bc7f9-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="bc7f9-112">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="bc7f9-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="bc7f9-113">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="bc7f9-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
