---
title: 在委派中使用變異數 (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 46c09da9adac7ed47c32b1fed4311dfedbf5764e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="9e750-102">在委派中使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="9e750-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="9e750-103">當您將方法指派給委派時，「共變數」和「反變數」可讓您彈性地比對委派類型和方法簽章。</span><span class="sxs-lookup"><span data-stu-id="9e750-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="9e750-104">共變數允許某個方法的傳回型別與定義於委派中的傳回型別相比，其衍生程度較大。</span><span class="sxs-lookup"><span data-stu-id="9e750-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="9e750-105">反變數允許某個方法的參數類型與委派類型中的參數類型相比，其衍生程度較小。</span><span class="sxs-lookup"><span data-stu-id="9e750-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="9e750-106">範例 1︰共變數</span><span class="sxs-lookup"><span data-stu-id="9e750-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="9e750-107">描述</span><span class="sxs-lookup"><span data-stu-id="9e750-107">Description</span></span>  
 <span data-ttu-id="9e750-108">此範例示範如何搭配其傳回型別衍生自委派簽章中傳回型別的方法使用委派。</span><span class="sxs-lookup"><span data-stu-id="9e750-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="9e750-109">`DogsHandler` 所傳回的資料類型是 `Dogs` 類型，該類型衍生自定義於委派中的 `Mammals` 類型。</span><span class="sxs-lookup"><span data-stu-id="9e750-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9e750-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="9e750-110">Code</span></span>  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="9e750-111">範例 2：反變數</span><span class="sxs-lookup"><span data-stu-id="9e750-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="9e750-112">描述</span><span class="sxs-lookup"><span data-stu-id="9e750-112">Description</span></span>  
 <span data-ttu-id="9e750-113">此範例示範如何搭配其參數類型為委派簽章參數類型之基底類型的方法使用委派。</span><span class="sxs-lookup"><span data-stu-id="9e750-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="9e750-114">透過反變數，您可以使用一個事件處理常式，而不是不同的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9e750-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="9e750-115">例如，您可以建立一個事件處理常式，該事件處理常式接受 `EventArgs` 輸入參數，並使用它來搭配將 `MouseEventArgs` 類型作為參數傳送的 `Button.MouseClick` 事件，以及搭配傳送 `KeyEventArgs` 參數的 `TextBox.KeyDown` 事件。</span><span class="sxs-lookup"><span data-stu-id="9e750-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9e750-116">程式碼</span><span class="sxs-lookup"><span data-stu-id="9e750-116">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e750-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e750-117">See Also</span></span>  
 [<span data-ttu-id="9e750-118">委派中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="9e750-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="9e750-119">針對 Func 與 Action 泛型委派使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="9e750-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
