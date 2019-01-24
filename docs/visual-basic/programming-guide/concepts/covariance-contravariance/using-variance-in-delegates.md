---
title: 使用委派 (Visual Basic) 中的變異數
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: e0b0df354c6c31eed41ead2bb0b2a1aaa4ac9922
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690822"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="cb1c6-102">使用委派 (Visual Basic) 中的變異數</span><span class="sxs-lookup"><span data-stu-id="cb1c6-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="cb1c6-103">當您將方法指派給委派時，「共變數」和「反變數」可讓您彈性地比對委派類型和方法簽章。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="cb1c6-104">共變數允許某個方法的傳回型別與定義於委派中的傳回型別相比，其衍生程度較大。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="cb1c6-105">反變數允許某個方法的參數類型與委派類型中的參數類型相比，其衍生程度較小。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="cb1c6-106">範例 1:共變數</span><span class="sxs-lookup"><span data-stu-id="cb1c6-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb1c6-107">描述</span><span class="sxs-lookup"><span data-stu-id="cb1c6-107">Description</span></span>  
 <span data-ttu-id="cb1c6-108">此範例示範如何搭配其傳回型別衍生自委派簽章中傳回型別的方法使用委派。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="cb1c6-109">`DogsHandler` 所傳回的資料類型是 `Dogs` 類型，該類型衍生自定義於委派中的 `Mammals` 類型。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb1c6-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="cb1c6-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="cb1c6-111">範例 2:反變數</span><span class="sxs-lookup"><span data-stu-id="cb1c6-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb1c6-112">描述</span><span class="sxs-lookup"><span data-stu-id="cb1c6-112">Description</span></span>  
 <span data-ttu-id="cb1c6-113">此範例示範如何搭配其參數類型為委派簽章參數類型之基底類型的方法使用委派。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="cb1c6-114">透過反變數，您可以使用一個事件處理常式，而不是不同的處理常式。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="cb1c6-115">例如，您可以建立一個事件處理常式，該事件處理常式接受 `EventArgs` 輸入參數，並使用它來搭配將 `MouseEventArgs` 類型作為參數傳送的 `Button.MouseClick` 事件，以及搭配傳送 `KeyEventArgs` 參數的 `TextBox.KeyDown` 事件。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb1c6-116">程式碼</span><span class="sxs-lookup"><span data-stu-id="cb1c6-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb1c6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb1c6-117">See also</span></span>
- [<span data-ttu-id="cb1c6-118">委派中的變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb1c6-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="cb1c6-119">針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb1c6-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
