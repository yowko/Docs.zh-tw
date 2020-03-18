---
title: C# 委派 - C# 語言教學課程
description: 了解使用 C# 委派進行的晚期繫結
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159165"
---
# <a name="delegates"></a><span data-ttu-id="5d986-103">委派</span><span class="sxs-lookup"><span data-stu-id="5d986-103">Delegates</span></span>

<span data-ttu-id="5d986-104">「委派型別」\*\*\*\*\*\* 代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="5d986-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="5d986-105">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="5d986-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="5d986-106">委託類似于在其他一些語言中找到的函數指標的概念。</span><span class="sxs-lookup"><span data-stu-id="5d986-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="5d986-107">與函數指標不同，委託是物件導向的和型別安全的。</span><span class="sxs-lookup"><span data-stu-id="5d986-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="5d986-108">下列範例會宣告並使用名為 `Function` 的委派型別。</span><span class="sxs-lookup"><span data-stu-id="5d986-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="5d986-109">`Function` 委派型別的執行個體可以參考任何採用 `double` 引數並傳回 `double` 值的方法。</span><span class="sxs-lookup"><span data-stu-id="5d986-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="5d986-110">`Apply` 方法會將指定的函式套用到 `double[]` 的元素，其中會傳回含有結果的 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="5d986-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="5d986-111">在 `Main` 方法中，是使用 `Apply` 將三個不同的函式套用到 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="5d986-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="5d986-112">委派可以參考靜態方法 (例如上一個範例中的 `Square` 或 `Math.Sin`)，或是參考執行個體方法 (例如上一個範例中的 `m.Multiply`)。</span><span class="sxs-lookup"><span data-stu-id="5d986-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="5d986-113">參考執行個體方法的委派也會參考特定的物件，而且透過委派來叫用執行個體方法時，該物件就會變成叫用中的 `this`。</span><span class="sxs-lookup"><span data-stu-id="5d986-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="5d986-114">還可以使用匿名函數創建委託，匿名函數是在聲明時創建的"內聯方法"。</span><span class="sxs-lookup"><span data-stu-id="5d986-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="5d986-115">匿名函式可以看見周圍方法的區域變數。</span><span class="sxs-lookup"><span data-stu-id="5d986-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="5d986-116">以下示例不創建類：</span><span class="sxs-lookup"><span data-stu-id="5d986-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="5d986-117">委託不知道或不關心它引用的方法的類;重要的是引用的方法具有與委託相同的參數和返回類型。</span><span class="sxs-lookup"><span data-stu-id="5d986-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d986-118">[上一個](interfaces.md)
>[下一個](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="5d986-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
