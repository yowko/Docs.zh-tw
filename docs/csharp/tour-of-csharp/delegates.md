---
title: "C# 委派 - C# 語言教學課程"
description: "了解使用 C# 委派進行的晚期繫結"
keywords: ".NET, csharp, 委派, lambda, 晚期繫結"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="delegates"></a><span data-ttu-id="9bf40-104">委派</span><span class="sxs-lookup"><span data-stu-id="9bf40-104">Delegates</span></span>

<span data-ttu-id="9bf40-105">「委派型別」代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9bf40-105">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="9bf40-106">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="9bf40-106">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="9bf40-107">委派就類似其他程式設計語言中的函式指標，但與函式指標的不同之處是，委派是物件導向且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="9bf40-107">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="9bf40-108">下列範例會宣告並使用名為 `Function` 的委派型別。</span><span class="sxs-lookup"><span data-stu-id="9bf40-108">The following example declares and uses a delegate type named `Function`.</span></span>

<span data-ttu-id="9bf40-109">[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]</span><span class="sxs-lookup"><span data-stu-id="9bf40-109">[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]</span></span>

<span data-ttu-id="9bf40-110">`Function` 委派型別的執行個體可以參考任何採用 `double` 引數並傳回 `double` 值的方法。</span><span class="sxs-lookup"><span data-stu-id="9bf40-110">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="9bf40-111">`Apply` 方法會將指定的函式套用到 `double[]` 的元素，其中會傳回含有結果的 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="9bf40-111">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="9bf40-112">在 `Main` 方法中，是使用 `Apply` 將三個不同的函式套用到 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="9bf40-112">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="9bf40-113">委派可以參考靜態方法 (例如上一個範例中的 `Square` 或 `Math.Sin`)，或是參考執行個體方法 (例如上一個範例中的 `m.Multiply`)。</span><span class="sxs-lookup"><span data-stu-id="9bf40-113">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="9bf40-114">參考執行個體方法的委派也會參考特定的物件，而且透過委派來叫用執行個體方法時，該物件就會變成叫用中的 `this`。</span><span class="sxs-lookup"><span data-stu-id="9bf40-114">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="9bf40-115">您也可以使用匿名函式來建立委派，這些函式是動態建立的「內嵌方法」。</span><span class="sxs-lookup"><span data-stu-id="9bf40-115">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="9bf40-116">匿名函式可以看見周圍方法的區域變數。</span><span class="sxs-lookup"><span data-stu-id="9bf40-116">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="9bf40-117">因此，可以更輕鬆地覆寫上面的乘數範例，而不需使用 Multiplier 類別：</span><span class="sxs-lookup"><span data-stu-id="9bf40-117">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

<span data-ttu-id="9bf40-118">[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]</span><span class="sxs-lookup"><span data-stu-id="9bf40-118">[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]</span></span>

<span data-ttu-id="9bf40-119">委派有一個有趣且實用的屬性，就是它並不知道或並不在乎所參考方法的類別；唯一重要的是所參考的方法具有與委派相同的參數和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9bf40-119">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="9bf40-120">[上一頁](enums.md)
[下一頁](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="9bf40-120">[Previous](enums.md)
[Next](attributes.md)</span></span>

