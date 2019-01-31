---
title: 二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: cb47670e8417e903b2886887394b972d1ac138b0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284631"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="2a81d-102">二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型</span><span class="sxs-lookup"><span data-stu-id="2a81d-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="2a81d-103">`If`運算式可以接受兩個或三個引數。</span><span class="sxs-lookup"><span data-stu-id="2a81d-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="2a81d-104">當您傳送僅兩個引數時，第一個引數必須是參考型別或可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="2a81d-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="2a81d-105">如果第一個引數評估為任何項目以外的其他`Nothing`，其值會傳回。</span><span class="sxs-lookup"><span data-stu-id="2a81d-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="2a81d-106">如果第一個引數評估為`Nothing`，評估並傳回第二個引數。</span><span class="sxs-lookup"><span data-stu-id="2a81d-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="2a81d-107">例如，下列程式碼包含兩個`If`運算式、 一個具有三個引數和一個具有兩個引數。</span><span class="sxs-lookup"><span data-stu-id="2a81d-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="2a81d-108">運算式會計算並傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="2a81d-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="2a81d-109">下列運算式會造成這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="2a81d-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="2a81d-110">**錯誤 ID:** BC33107</span><span class="sxs-lookup"><span data-stu-id="2a81d-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2a81d-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2a81d-111">To correct this error</span></span>  
  
-   <span data-ttu-id="2a81d-112">如果您無法變更程式碼，使第一個引數是 null 的型別或參考型別，請考慮將轉換成三個引數`If`運算式，或`If...Then...Else`陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a81d-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a81d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a81d-113">See also</span></span>
- [<span data-ttu-id="2a81d-114">If 運算子</span><span class="sxs-lookup"><span data-stu-id="2a81d-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="2a81d-115">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="2a81d-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="2a81d-116">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="2a81d-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
