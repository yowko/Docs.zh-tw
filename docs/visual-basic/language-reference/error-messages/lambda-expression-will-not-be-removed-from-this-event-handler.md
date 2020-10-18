---
title: Lambda 運算式將不會從這個事件處理常式中移除
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 5a30e63044b51f8176dfeebdcc9eb8fd517739ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163112"
---
# <a name="bc42326-lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="0e72e-102">BC42326： Lambda 運算式將不會從這個事件處理常式中移除</span><span class="sxs-lookup"><span data-stu-id="0e72e-102">BC42326: Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="0e72e-103">Lambda 運算式將不會從這個事件處理常式中移除。</span><span class="sxs-lookup"><span data-stu-id="0e72e-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="0e72e-104">將 lambda 運算式指派給變數，並使用變數來加入和移除事件。</span><span class="sxs-lookup"><span data-stu-id="0e72e-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="0e72e-105">當 lambda 運算式與事件處理常式搭配使用時，您可能看不到您預期的行為。</span><span class="sxs-lookup"><span data-stu-id="0e72e-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="0e72e-106">編譯器會為每個 lambda 運算式定義產生新的方法，即使它們相同也是一樣。</span><span class="sxs-lookup"><span data-stu-id="0e72e-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="0e72e-107">因此，會顯示下列程式碼 `False` 。</span><span class="sxs-lookup"><span data-stu-id="0e72e-107">Therefore, the following code displays `False`.</span></span>

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

<span data-ttu-id="0e72e-108">當 lambda 運算式與事件處理常式搭配使用時，這可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="0e72e-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="0e72e-109">在下列範例中， `AddHandler` 語句不會移除新增的 lambda 運算式 `RemoveHandler` 。</span><span class="sxs-lookup"><span data-stu-id="0e72e-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

<span data-ttu-id="0e72e-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="0e72e-110">By default, this message is a warning.</span></span> <span data-ttu-id="0e72e-111">如需如何隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="0e72e-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="0e72e-112">**錯誤識別碼：** BC42326</span><span class="sxs-lookup"><span data-stu-id="0e72e-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0e72e-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0e72e-113">To correct this error</span></span>

<span data-ttu-id="0e72e-114">若要避免警告並移除 lambda 運算式，請將 lambda 運算式指派給變數，並在和語句中使用變數 `AddHandler` `RemoveHandler` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0e72e-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="0e72e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e72e-115">See also</span></span>

- [<span data-ttu-id="0e72e-116">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="0e72e-116">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="0e72e-117">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="0e72e-117">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="0e72e-118">事件</span><span class="sxs-lookup"><span data-stu-id="0e72e-118">Events</span></span>](../../programming-guide/language-features/events/index.md)
