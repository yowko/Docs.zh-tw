---
title: Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512737"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="e4b37-102">Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中</span><span class="sxs-lookup"><span data-stu-id="e4b37-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="e4b37-103">您未`WithEvents` `Handles`在子句中提供變數。</span><span class="sxs-lookup"><span data-stu-id="e4b37-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="e4b37-104">程式宣告結尾的`WithEvents` 關鍵字會使其處理使用關鍵字宣告之物件變數所引發的事件。`Handles`</span><span class="sxs-lookup"><span data-stu-id="e4b37-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>
  
 <span data-ttu-id="e4b37-105">**錯誤識別碼:** BC30506</span><span class="sxs-lookup"><span data-stu-id="e4b37-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e4b37-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e4b37-106">To correct this error</span></span>
  
- <span data-ttu-id="e4b37-107">提供必要`WithEvents`的變數。</span><span class="sxs-lookup"><span data-stu-id="e4b37-107">Supply the necessary `WithEvents` variable.</span></span>
  
## <a name="example"></a><span data-ttu-id="e4b37-108">範例</span><span class="sxs-lookup"><span data-stu-id="e4b37-108">Example</span></span>

<span data-ttu-id="e4b37-109">在下列範例中, Visual Basic 會產生編譯器`BC30506`錯誤, 因為在<xref:System.Timers.Timer?displayProperty=nameWithType>實例的定義中不會使用[WithEvents](../modifiers/withevents.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e4b37-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}
    
    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

<span data-ttu-id="e4b37-110">下列範例會成功編譯, 因為`_timer1`變數是`WithEvents`以關鍵字定義的:</span><span class="sxs-lookup"><span data-stu-id="e4b37-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a><span data-ttu-id="e4b37-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4b37-111">See also</span></span>

- [<span data-ttu-id="e4b37-112">Handles</span><span class="sxs-lookup"><span data-stu-id="e4b37-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
