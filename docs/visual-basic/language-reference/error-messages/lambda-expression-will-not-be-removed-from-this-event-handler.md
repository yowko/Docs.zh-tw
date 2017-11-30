---
title: "Lambda 運算式將不會從這個事件處理常式中移除"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords: BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a4c57d1f8f41d2d9ebb645d3f2628c32a2c4e4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="aedcc-102">Lambda 運算式將不會從這個事件處理常式中移除</span><span class="sxs-lookup"><span data-stu-id="aedcc-102">Lambda expression will not be removed from this event handler</span></span>
<span data-ttu-id="aedcc-103">Lambda 運算式不會移除這個事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="aedcc-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="aedcc-104">Lambda 運算式指派給變數，並使用變數來加入和移除事件。</span><span class="sxs-lookup"><span data-stu-id="aedcc-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>  
  
 <span data-ttu-id="aedcc-105">當事件處理常式使用 lambda 運算式時，您可能無法看見預期的行為。</span><span class="sxs-lookup"><span data-stu-id="aedcc-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="aedcc-106">編譯器會產生新的方法，每個 lambda 運算式定義，即使它們完全相同。</span><span class="sxs-lookup"><span data-stu-id="aedcc-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="aedcc-107">因此，下列程式碼顯示`False`。</span><span class="sxs-lookup"><span data-stu-id="aedcc-107">Therefore, the following code displays `False`.</span></span>  
  
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
  
 <span data-ttu-id="aedcc-108">當事件處理常式使用 lambda 運算式時，這可能會造成非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="aedcc-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="aedcc-109">在下列範例中，lambda 運算式加入`AddHandler`不會移除`RemoveHandler`陳述式。</span><span class="sxs-lookup"><span data-stu-id="aedcc-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>  
  
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
  
 <span data-ttu-id="aedcc-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="aedcc-110">By default, this message is a warning.</span></span> <span data-ttu-id="aedcc-111">如需如何隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="aedcc-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="aedcc-112">**錯誤 ID:** BC42326</span><span class="sxs-lookup"><span data-stu-id="aedcc-112">**Error ID:** BC42326</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aedcc-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="aedcc-113">To correct this error</span></span>  
  
-   <span data-ttu-id="aedcc-114">若要避免這個警告，並移除 lambda 運算式，指派給變數的 lambda 運算式，兩者中使用變數`AddHandler`和`RemoveHandler`陳述式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aedcc-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aedcc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aedcc-115">See Also</span></span>  
 [<span data-ttu-id="aedcc-116">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="aedcc-116">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="aedcc-117">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="aedcc-117">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="aedcc-118">事件</span><span class="sxs-lookup"><span data-stu-id="aedcc-118">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
