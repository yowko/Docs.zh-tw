---
title: C# 委派 - C# 語言教學課程
description: 了解使用 C# 委派進行的晚期繫結
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 35a1e212b50e77eb43271a657c8abb21eb6cfb4a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634626"
---
# <a name="delegates"></a><span data-ttu-id="17cc2-103">委派</span><span class="sxs-lookup"><span data-stu-id="17cc2-103">Delegates</span></span>

<span data-ttu-id="17cc2-104">「委派型別」代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="17cc2-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="17cc2-105">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="17cc2-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="17cc2-106">委派就類似其他程式設計語言中的函式指標，但與函式指標的不同之處是，委派是物件導向且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="17cc2-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="17cc2-107">下列範例會宣告並使用名為 `Function` 的委派型別。</span><span class="sxs-lookup"><span data-stu-id="17cc2-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="17cc2-108">`Function` 委派型別的執行個體可以參考任何採用 `double` 引數並傳回 `double` 值的方法。</span><span class="sxs-lookup"><span data-stu-id="17cc2-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="17cc2-109">`Apply` 方法會將指定的函式套用到 `double[]` 的元素，其中會傳回含有結果的 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="17cc2-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="17cc2-110">在 `Main` 方法中，是使用 `Apply` 將三個不同的函式套用到 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="17cc2-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="17cc2-111">委派可以參考靜態方法 (例如上一個範例中的 `Square` 或 `Math.Sin`)，或是參考執行個體方法 (例如上一個範例中的 `m.Multiply`)。</span><span class="sxs-lookup"><span data-stu-id="17cc2-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="17cc2-112">參考執行個體方法的委派也會參考特定的物件，而且透過委派來叫用執行個體方法時，該物件就會變成叫用中的 `this`。</span><span class="sxs-lookup"><span data-stu-id="17cc2-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="17cc2-113">您也可以使用匿名函式來建立委派，這些函式是動態建立的「內嵌方法」。</span><span class="sxs-lookup"><span data-stu-id="17cc2-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="17cc2-114">匿名函式可以看見周圍方法的區域變數。</span><span class="sxs-lookup"><span data-stu-id="17cc2-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="17cc2-115">因此，可以更輕鬆地覆寫上面的乘數範例，而不需使用 Multiplier 類別：</span><span class="sxs-lookup"><span data-stu-id="17cc2-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="17cc2-116">委派有一個有趣且實用的屬性，就是它並不知道或並不在乎所參考方法的類別；唯一重要的是所參考的方法具有與委派相同的參數和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="17cc2-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="17cc2-117">[上一頁](enums.md)
>[下一頁](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="17cc2-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
