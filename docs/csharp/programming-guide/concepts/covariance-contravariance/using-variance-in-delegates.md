---
title: 在委派中使用變異數 (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 980caf8d5e4699115d203a89fab7994d18cc1707
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168350"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="9ac9e-102">在委派中使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac9e-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="9ac9e-103">當您將方法指派給委派時，「共變數」  和「反變數」  可讓您彈性地比對委派類型和方法簽章。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="9ac9e-104">共變數允許某個方法的傳回型別與定義於委派中的傳回型別相比，其衍生程度較大。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="9ac9e-105">反變數允許某個方法的參數類型與委派類型中的參數類型相比，其衍生程度較小。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="9ac9e-106">範例 1：共變數</span><span class="sxs-lookup"><span data-stu-id="9ac9e-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="9ac9e-107">說明</span><span class="sxs-lookup"><span data-stu-id="9ac9e-107">Description</span></span>  
 <span data-ttu-id="9ac9e-108">此範例示範如何搭配其傳回型別衍生自委派簽章中傳回型別的方法使用委派。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="9ac9e-109">`DogsHandler` 所傳回的資料類型是 `Dogs` 類型，該類型衍生自定義於委派中的 `Mammals` 類型。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9ac9e-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="9ac9e-110">Code</span></span>  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="9ac9e-111">範例 2：反變數</span><span class="sxs-lookup"><span data-stu-id="9ac9e-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="9ac9e-112">說明</span><span class="sxs-lookup"><span data-stu-id="9ac9e-112">Description</span></span>

<span data-ttu-id="9ac9e-113">此範例示範如何搭配其參數類型為委派簽章參數類型的基底類型方法來使用委派。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="9ac9e-114">透過反變數，您可以使用一個事件處理常式，而不是不同的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="9ac9e-115">下列範例會使用兩個委派：</span><span class="sxs-lookup"><span data-stu-id="9ac9e-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="9ac9e-116"><xref:System.Windows.Forms.KeyEventHandler> 委派會定義 [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) 事件的簽章。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="9ac9e-117">其簽章為：</span><span class="sxs-lookup"><span data-stu-id="9ac9e-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="9ac9e-118"><xref:System.Windows.Forms.MouseEventHandler> 委派會定義 [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) 事件的簽章。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="9ac9e-119">其簽章為：</span><span class="sxs-lookup"><span data-stu-id="9ac9e-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="9ac9e-120">此範例以 <xref:System.EventArgs> 參數定義事件處理常式，然後使用它來處理 `Button.KeyDown` 和 `Button.MouseClick` 事件。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="9ac9e-121">由於 <xref:System.EventArgs> 同時是 <xref:System.Windows.Forms.KeyEventArgs> 和 <xref:System.Windows.Forms.MouseEventArgs> 的基底類型，因此可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="9ac9e-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span> 
  
### <a name="code"></a><span data-ttu-id="9ac9e-122">程式碼</span><span class="sxs-lookup"><span data-stu-id="9ac9e-122">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ac9e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac9e-123">See also</span></span>

- [<span data-ttu-id="9ac9e-124">委派中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac9e-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="9ac9e-125">針對 Func 與 Action 泛型委派使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac9e-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
