---
title: "使用委派 (Visual Basic) 中的變異數 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 620fd61000e42d68f566e441d023d73a036000ae
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="08219-102">使用委派 (Visual Basic) 中的變異數</span><span class="sxs-lookup"><span data-stu-id="08219-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="08219-103">當您指派給委派的方法*共變數*和*反變數*進行比對方法簽章與委派型別提供的彈性。</span><span class="sxs-lookup"><span data-stu-id="08219-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="08219-104">共變數允許的方法有更多衍生於所定義的委派中的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="08219-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="08219-105">反變數允許具有較少衍生比委派型別中的參數類型的方法。</span><span class="sxs-lookup"><span data-stu-id="08219-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="08219-106">範例 1︰ 共變數</span><span class="sxs-lookup"><span data-stu-id="08219-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="08219-107">描述</span><span class="sxs-lookup"><span data-stu-id="08219-107">Description</span></span>  
 <span data-ttu-id="08219-108">這個範例會示範如何使用委派的傳回型別衍生自委派簽章中的傳回類型的方法。</span><span class="sxs-lookup"><span data-stu-id="08219-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="08219-109">傳回的資料型別`DogsHandler`的型別`Dogs`，衍生自`Mammals`定義在委派中的型別。</span><span class="sxs-lookup"><span data-stu-id="08219-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="08219-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="08219-110">Code</span></span>  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="08219-111">範例 2︰ 反變數</span><span class="sxs-lookup"><span data-stu-id="08219-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="08219-112">描述</span><span class="sxs-lookup"><span data-stu-id="08219-112">Description</span></span>  
 <span data-ttu-id="08219-113">這個範例會示範如何使用委派的參數類型的委派簽章的參數型別的基底型別的方法。</span><span class="sxs-lookup"><span data-stu-id="08219-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="08219-114">與反變數，您可以使用一個事件處理常式，而不是個別的處理常式。</span><span class="sxs-lookup"><span data-stu-id="08219-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="08219-115">例如，您可以建立事件處理常式可接受`EventArgs`輸入參數，並將它與`Button.MouseClick`所傳送的事件`MouseEventArgs`類型做為參數，也可以與`TextBox.KeyDown`所傳送的事件`KeyEventArgs`參數。</span><span class="sxs-lookup"><span data-stu-id="08219-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="08219-116">程式碼</span><span class="sxs-lookup"><span data-stu-id="08219-116">Code</span></span>  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="08219-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08219-117">See Also</span></span>  
 <span data-ttu-id="08219-118">[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="08219-118">[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span></span>  
<span data-ttu-id="08219-119"> [針對 Func 與 Action 委派 (Visual Basic) 中使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="08219-119"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
