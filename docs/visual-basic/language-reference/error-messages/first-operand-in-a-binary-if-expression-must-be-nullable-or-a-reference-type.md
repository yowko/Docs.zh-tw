---
title: 二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249522"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="6ad7a-102">二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型</span><span class="sxs-lookup"><span data-stu-id="6ad7a-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="6ad7a-103">運算式`If`可以採用兩個或三個參數。</span><span class="sxs-lookup"><span data-stu-id="6ad7a-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="6ad7a-104">僅發送兩個參數時，第一個參數必須是參考型別或空數值型別。</span><span class="sxs-lookup"><span data-stu-id="6ad7a-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="6ad7a-105">如果第一個參數計算為`Nothing`以外的任何內容，則返回其值。</span><span class="sxs-lookup"><span data-stu-id="6ad7a-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="6ad7a-106">如果第一個參數計算到`Nothing`，則計算並返回第二個參數。</span><span class="sxs-lookup"><span data-stu-id="6ad7a-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="6ad7a-107">例如，以下代碼包含兩`If`個運算式，一個包含三個參數，一個包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="6ad7a-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="6ad7a-108">運算式計算並返回相同的值。</span><span class="sxs-lookup"><span data-stu-id="6ad7a-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="6ad7a-109">以下運算式導致此錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ad7a-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="6ad7a-110">**錯誤 ID：** BC33107</span><span class="sxs-lookup"><span data-stu-id="6ad7a-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ad7a-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6ad7a-111">To correct this error</span></span>  
  
- <span data-ttu-id="6ad7a-112">如果無法更改代碼，以便第一個參數是空數值型別或參考型別，請考慮轉換為三個參數`If`運算式或語句。 `If...Then...Else`</span><span class="sxs-lookup"><span data-stu-id="6ad7a-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ad7a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad7a-113">See also</span></span>

- [<span data-ttu-id="6ad7a-114">If 運算子</span><span class="sxs-lookup"><span data-stu-id="6ad7a-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="6ad7a-115">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="6ad7a-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="6ad7a-116">空數值型別</span><span class="sxs-lookup"><span data-stu-id="6ad7a-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
