---
title: 在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 358c7a988ae95c2326a26bc048f5436e11acb340
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641586"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="0721f-102">在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果</span><span class="sxs-lookup"><span data-stu-id="0721f-102">Using the iteration variable in a lambda expression may have unexpected results</span></span>
<span data-ttu-id="0721f-103">Lambda 運算式中使用反覆運算變數可能會非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="0721f-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="0721f-104">相反地，建立迴圈內的區域變數，並將它指派反覆項目變數的值。</span><span class="sxs-lookup"><span data-stu-id="0721f-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>  
  
 <span data-ttu-id="0721f-105">當您在迴圈內宣告的 lambda 運算式中使用迴圈反覆項目變數時，就會顯示此警告。</span><span class="sxs-lookup"><span data-stu-id="0721f-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="0721f-106">例如，下列範例會顯示警告。</span><span class="sxs-lookup"><span data-stu-id="0721f-106">For example, the following example causes the warning to appear.</span></span>  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 <span data-ttu-id="0721f-107">下列範例顯示可能會發生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="0721f-107">The following example shows the unexpected results that might occur.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0721f-108">`For`迴圈會建立其中每個傳回的值，迴圈反覆運算變數的 lambda 運算式的陣列`i`。</span><span class="sxs-lookup"><span data-stu-id="0721f-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="0721f-109">Lambda 運算式以進行評估`For Each`迴圈中，您可能會看到 0、 1、 2、 3 和 4 顯示，後續的值`i`在`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="0721f-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="0721f-110">相反地，您會看到的最終值`i`顯示五次：</span><span class="sxs-lookup"><span data-stu-id="0721f-110">Instead, you see the final value of `i` displayed five times:</span></span>  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 <span data-ttu-id="0721f-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="0721f-111">By default, this message is a warning.</span></span> <span data-ttu-id="0721f-112">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="0721f-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0721f-113">**錯誤 ID:** BC42324</span><span class="sxs-lookup"><span data-stu-id="0721f-113">**Error ID:** BC42324</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0721f-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0721f-114">To correct this error</span></span>  
  
-   <span data-ttu-id="0721f-115">反覆項目變數的值指派給本機變數，並使用 lambda 運算式中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="0721f-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="0721f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0721f-116">See also</span></span>
- [<span data-ttu-id="0721f-117">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="0721f-117">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
