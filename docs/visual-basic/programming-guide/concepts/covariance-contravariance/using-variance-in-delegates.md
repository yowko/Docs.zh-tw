---
title: 在委派中使用變異數（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169073"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="ecdc2-102">在委派中使用變異數（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ecdc2-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="ecdc2-103">當您將方法指派給委派時，「共變數」和「反變數」可讓您彈性地比對委派類型和方法簽章。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="ecdc2-104">共變數允許某個方法的傳回型別與定義於委派中的傳回型別相比，其衍生程度較大。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="ecdc2-105">反變數允許某個方法的參數類型與委派類型中的參數類型相比，其衍生程度較小。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="ecdc2-106">範例 1：共變數</span><span class="sxs-lookup"><span data-stu-id="ecdc2-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="ecdc2-107">描述</span><span class="sxs-lookup"><span data-stu-id="ecdc2-107">Description</span></span>

<span data-ttu-id="ecdc2-108">此範例示範如何搭配其傳回型別衍生自委派簽章中傳回型別的方法使用委派。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="ecdc2-109">`DogsHandler` 所傳回的資料類型是 `Dogs` 類型，該類型衍生自定義於委派中的 `Mammals` 類型。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="ecdc2-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="ecdc2-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="ecdc2-111">範例 2：反變數</span><span class="sxs-lookup"><span data-stu-id="ecdc2-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="ecdc2-112">描述</span><span class="sxs-lookup"><span data-stu-id="ecdc2-112">Description</span></span>

<span data-ttu-id="ecdc2-113">此範例示範如何搭配其參數類型為委派簽章參數類型的基底類型方法來使用委派。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="ecdc2-114">透過反變數，您可以使用一個事件處理常式，而不是不同的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="ecdc2-115">下列範例會使用兩個委派：</span><span class="sxs-lookup"><span data-stu-id="ecdc2-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="ecdc2-116"><xref:System.Windows.Forms.KeyEventHandler> 委派會定義 [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) 事件的簽章。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="ecdc2-117">其簽章為：</span><span class="sxs-lookup"><span data-stu-id="ecdc2-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="ecdc2-118"><xref:System.Windows.Forms.MouseEventHandler> 委派會定義 [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) 事件的簽章。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="ecdc2-119">其簽章為：</span><span class="sxs-lookup"><span data-stu-id="ecdc2-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="ecdc2-120">此範例以 <xref:System.EventArgs> 參數定義事件處理常式，然後使用它來處理 `Button.KeyDown` 和 `Button.MouseClick` 事件。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="ecdc2-121">由於 <xref:System.EventArgs> 同時是 <xref:System.Windows.Forms.KeyEventArgs> 和 <xref:System.Windows.Forms.MouseEventArgs> 的基底類型，因此可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="ecdc2-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="ecdc2-122">程式碼</span><span class="sxs-lookup"><span data-stu-id="ecdc2-122">Code</span></span>

```vb
' Event handler that accepts a parameter of the EventArgs type.
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

## <a name="see-also"></a><span data-ttu-id="ecdc2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecdc2-123">See also</span></span>

- [<span data-ttu-id="ecdc2-124">委派中的變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecdc2-124">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="ecdc2-125">針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecdc2-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
