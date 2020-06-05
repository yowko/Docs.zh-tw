---
title: 在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: aa3e1d6281af22b301a4697b265ed3fbf23e3de4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373910"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="c3f72-102">在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果</span><span class="sxs-lookup"><span data-stu-id="c3f72-102">Using the iteration variable in a lambda expression may have unexpected results</span></span>
<span data-ttu-id="c3f72-103">在 lambda 運算式中使用反覆運算變數可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="c3f72-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="c3f72-104">相反地，請在迴圈內建立區域變數，並將反覆運算變數的值指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="c3f72-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>  
  
 <span data-ttu-id="c3f72-105">當您在迴圈內宣告的 lambda 運算式中使用迴圈反覆運算變數時，就會出現這個警告。</span><span class="sxs-lookup"><span data-stu-id="c3f72-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="c3f72-106">例如，下列範例會使警告出現。</span><span class="sxs-lookup"><span data-stu-id="c3f72-106">For example, the following example causes the warning to appear.</span></span>  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 <span data-ttu-id="c3f72-107">下列範例會顯示可能發生的非預期結果。</span><span class="sxs-lookup"><span data-stu-id="c3f72-107">The following example shows the unexpected results that might occur.</span></span>  
  
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
  
 <span data-ttu-id="c3f72-108">`For`迴圈會建立 lambda 運算式的陣列，其中每一個都會傳回迴圈反覆運算變數的值 `i` 。</span><span class="sxs-lookup"><span data-stu-id="c3f72-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="c3f72-109">在迴圈中評估 lambda 運算式時 `For Each` ，您可能會預期會在迴圈中顯示0、1、2、3和4的連續值 `i` `For` 。</span><span class="sxs-lookup"><span data-stu-id="c3f72-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="c3f72-110">相反地，您會看到顯示的最後一個值 `i` 五次：</span><span class="sxs-lookup"><span data-stu-id="c3f72-110">Instead, you see the final value of `i` displayed five times:</span></span>  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 <span data-ttu-id="c3f72-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="c3f72-111">By default, this message is a warning.</span></span> <span data-ttu-id="c3f72-112">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="c3f72-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c3f72-113">**錯誤識別碼：** BC42324</span><span class="sxs-lookup"><span data-stu-id="c3f72-113">**Error ID:** BC42324</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3f72-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c3f72-114">To correct this error</span></span>  
  
- <span data-ttu-id="c3f72-115">將反覆運算變數的值指派給本機變數，並在 lambda 運算式中使用區域變數。</span><span class="sxs-lookup"><span data-stu-id="c3f72-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3f72-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3f72-116">See also</span></span>

- [<span data-ttu-id="c3f72-117">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c3f72-117">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
