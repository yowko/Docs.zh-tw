---
title: "Lambda 運算式不是有效的第一個運算式中 &#39;選取案例 &#39;陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords: BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="762a4-102">Lambda 運算式不是有效的第一個運算式中 &#39;選取案例 &#39;陳述式</span><span class="sxs-lookup"><span data-stu-id="762a4-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="762a4-103">您無法使用 lambda 運算式中的測試運算式`Select Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="762a4-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="762a4-104">Lambda 運算式定義傳回函式和測試運算式的`Select Case`陳述式必須是基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="762a4-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="762a4-105">下列程式碼會造成這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="762a4-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="762a4-106">**錯誤 ID:** BC36635</span><span class="sxs-lookup"><span data-stu-id="762a4-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="762a4-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="762a4-107">To correct this error</span></span>  
  
-   <span data-ttu-id="762a4-108">檢查您的程式碼，以判斷不同的條件式建構 (例如 `If...Then...Else` 陳述式) 是否可行。</span><span class="sxs-lookup"><span data-stu-id="762a4-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="762a4-109">您可能想要呼叫的函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="762a4-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="762a4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="762a4-110">See Also</span></span>  
 [<span data-ttu-id="762a4-111">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="762a4-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="762a4-112">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="762a4-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="762a4-113">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="762a4-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
