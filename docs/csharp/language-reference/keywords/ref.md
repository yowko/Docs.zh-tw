---
title: "ref (C# 參考)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 427045317e9d7d0fe3435a486b9f761908ab5e78
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="ref-c-reference"></a><span data-ttu-id="89b5b-102">ref (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="89b5b-102">ref (C# Reference)</span></span>

<span data-ttu-id="89b5b-103">`ref` 關鍵字指出以傳址方式傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="89b5b-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="89b5b-104">它用於三個不同的內容：</span><span class="sxs-lookup"><span data-stu-id="89b5b-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="89b5b-105">在方法簽章和方法呼叫中，以傳址方式將引數傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="89b5b-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="89b5b-106">如需詳細資訊，請參閱[以傳址方式傳遞引數](#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="89b5b-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="89b5b-107">在方法簽章中，以傳址方式將值傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="89b5b-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="89b5b-108">如需詳細資訊，請參閱[參考傳回值](#reference-return-values)。</span><span class="sxs-lookup"><span data-stu-id="89b5b-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="89b5b-109">在成員主體中，指出參考傳回值儲存在本機作為呼叫者想要修改的參考。</span><span class="sxs-lookup"><span data-stu-id="89b5b-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="89b5b-110">如需詳細資訊，請參閱 [ref 區域變數](#ref-locals)。</span><span class="sxs-lookup"><span data-stu-id="89b5b-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="89b5b-111">以傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="89b5b-111">Passing an argument by reference</span></span>

<span data-ttu-id="89b5b-112">用於方法的參數清單時，`ref` 關鍵字指出以傳址方式傳遞引數，而不是以傳值方式。</span><span class="sxs-lookup"><span data-stu-id="89b5b-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="89b5b-113">以傳址方式傳遞的效果是已呼叫方法中引數的任何變更都會反映在呼叫方法中。</span><span class="sxs-lookup"><span data-stu-id="89b5b-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="89b5b-114">例如，如果呼叫者傳遞區域變數運算式或陣列元素存取運算式，而且已呼叫方法取代 ref 參數所參考的物件，則在傳回方法時，呼叫者的區域變數或陣列元素現在會參考新的物件。</span><span class="sxs-lookup"><span data-stu-id="89b5b-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="89b5b-115">請勿將參考傳遞的概念與參考類型的概念相混淆。</span><span class="sxs-lookup"><span data-stu-id="89b5b-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="89b5b-116">兩個概念並不相同。</span><span class="sxs-lookup"><span data-stu-id="89b5b-116">The two concepts are not the same.</span></span> <span data-ttu-id="89b5b-117">方法參數可以由 `ref` 修改，而不論其是否為實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="89b5b-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="89b5b-118">當實值類型由參考傳遞時，沒有 boxing。</span><span class="sxs-lookup"><span data-stu-id="89b5b-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="89b5b-119">若要使用 `ref` 參數，方法定義和呼叫方法都必須明確使用 `ref` 關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="89b5b-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="89b5b-120">傳遞至 `ref` 或 `in` 參數的引數，必須在傳遞之前先初始化。</span><span class="sxs-lookup"><span data-stu-id="89b5b-120">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="89b5b-121">這與 [out](out-parameter-modifier.md) 參數不同，其引數不需要在傳遞之前先明確初始化。</span><span class="sxs-lookup"><span data-stu-id="89b5b-121">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="89b5b-122">類別的成員的簽章，不能只有在 `ref`、`in` 或 `out` 部分不同。</span><span class="sxs-lookup"><span data-stu-id="89b5b-122">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="89b5b-123">如果類型的兩個成員之間，唯一的區別在於其中一個有 `ref` 參數，而另一個有 `out` 或 `in` 參數，則會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="89b5b-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="89b5b-124">例如，下列程式碼不會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="89b5b-124">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
<span data-ttu-id="89b5b-125">但如果一種方法有 `ref`、`in` 或 `out` 參數，而另一種方法有實值參數，則可以對方法進行多載，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="89b5b-125">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="89b5b-126">其他需要簽章比對的情況 (像是隱藏或覆寫)，`in`、`ref` 及 `out` 是簽章的一部分，但彼此不相符。</span><span class="sxs-lookup"><span data-stu-id="89b5b-126">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="89b5b-127">屬性不是變數。</span><span class="sxs-lookup"><span data-stu-id="89b5b-127">Properties are not variables.</span></span> <span data-ttu-id="89b5b-128">它們都是方法，且不能傳遞給 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="89b5b-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="89b5b-129">如需如何傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="89b5b-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="89b5b-130">您不可為下列幾種方法使用 `ref`、`in` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="89b5b-130">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="89b5b-131">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="89b5b-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
- <span data-ttu-id="89b5b-132">迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="89b5b-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="89b5b-133">以傳址方式傳遞引數：範例</span><span class="sxs-lookup"><span data-stu-id="89b5b-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="89b5b-134">先前的範例會以傳址方式傳遞實值型別。</span><span class="sxs-lookup"><span data-stu-id="89b5b-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="89b5b-135">您也可以使用 `ref` 關鍵字，以傳址方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="89b5b-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="89b5b-136">以傳址方式傳遞參考型別，可讓已呼叫方法取代參考參數在呼叫者中所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="89b5b-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="89b5b-137">物件的儲存位置會以參考參數值的方式，傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="89b5b-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="89b5b-138">如果您變更參數儲存位置中的值 (指向新的物件)，則也會變更呼叫端所參考的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="89b5b-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="89b5b-139">下列範例會以 `ref` 參數，傳遞參考類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="89b5b-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="89b5b-140">如需如何依傳值和依傳址方式來傳遞參考類型的詳細資訊，請參閱[傳遞參考類型參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="89b5b-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="89b5b-141">參考傳回值</span><span class="sxs-lookup"><span data-stu-id="89b5b-141">Reference return values</span></span>

<span data-ttu-id="89b5b-142">參考傳回值 (或 ref 傳回值) 是方法以傳址方式傳回給呼叫者的值。</span><span class="sxs-lookup"><span data-stu-id="89b5b-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="89b5b-143">也就是說，呼叫者可以修改方法所傳回的值，而且該變更會反映在包含方法的物件狀態中。</span><span class="sxs-lookup"><span data-stu-id="89b5b-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="89b5b-144">參考傳回值是使用 `ref` 關鍵字所定義：</span><span class="sxs-lookup"><span data-stu-id="89b5b-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="89b5b-145">在方法簽章中。</span><span class="sxs-lookup"><span data-stu-id="89b5b-145">In the method signature.</span></span> <span data-ttu-id="89b5b-146">例如，下列方法簽章指出 `GetCurrentPrice` 方法以傳址方式傳回 <xref:System.Decimal> 值。</span><span class="sxs-lookup"><span data-stu-id="89b5b-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="89b5b-147">`return` 權杖與方法之 `return` 陳述式中所傳回變數之間。</span><span class="sxs-lookup"><span data-stu-id="89b5b-147">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="89b5b-148">例如: </span><span class="sxs-lookup"><span data-stu-id="89b5b-148">For example:</span></span>
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

<span data-ttu-id="89b5b-149">為了讓呼叫者修改物件的狀態，參考傳回值必須儲存至明確定義為 [ref 區域變數](#ref-locals)的變數。</span><span class="sxs-lookup"><span data-stu-id="89b5b-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="89b5b-150">如需範例，請參閱 [ref 傳回值和 ref 區域變數範例](#a-ref-returns-and-ref-locals-example)。</span><span class="sxs-lookup"><span data-stu-id="89b5b-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="89b5b-151">ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="89b5b-151">Ref locals</span></span>

<span data-ttu-id="89b5b-152">ref 區域變數用來參考使用 `return ref` 所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="89b5b-152">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="89b5b-153">ref 區域變數必須初始化並指派給 ref 傳回值。</span><span class="sxs-lookup"><span data-stu-id="89b5b-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="89b5b-154">任何對 ref 區域變數值進行的修改，都會反映在其方法以傳址方式傳回值之物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="89b5b-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="89b5b-155">定義 ref 區域變數的方式是在變數宣告前面使用 `ref` 關鍵字，並且緊接在以傳址方式傳回值的方法呼叫前面。</span><span class="sxs-lookup"><span data-stu-id="89b5b-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="89b5b-156">例如，下列陳述式定義名為 `GetEstimatedValue` 之方法所傳回的 ref 區域變數值：</span><span class="sxs-lookup"><span data-stu-id="89b5b-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="89b5b-157">請注意，`ref` 關鍵字必須用在兩個位置，或者編譯器會產生錯誤 CS8172「無法使用值將傳址變數初始化」。</span><span class="sxs-lookup"><span data-stu-id="89b5b-157">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="89b5b-158">ref 傳回值和 ref 區域變數範例</span><span class="sxs-lookup"><span data-stu-id="89b5b-158">A ref returns and ref locals example</span></span>

<span data-ttu-id="89b5b-159">下面範例會定義具有 `Title` 和 `Author` 這兩個 <xref:System.String> 欄位的 `Book` 類別。</span><span class="sxs-lookup"><span data-stu-id="89b5b-159">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="89b5b-160">它也會定義 `BookCollection` 類別，以包含 `Book` 物件的私用陣列。</span><span class="sxs-lookup"><span data-stu-id="89b5b-160">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="89b5b-161">以傳址方式傳回個別書籍物件，方法是呼叫其 `GetBookByTitle` 方法。</span><span class="sxs-lookup"><span data-stu-id="89b5b-161">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="89b5b-162">呼叫者將 `GetBookByTitle` 方法所傳回的值儲存為 ref 區域變數時，呼叫者對傳回值進行的變更會反映在 `BookCollection` 物件中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="89b5b-162">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="89b5b-163">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="89b5b-163">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="89b5b-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="89b5b-164">See Also</span></span>  
 [<span data-ttu-id="89b5b-165">C# 參考</span><span class="sxs-lookup"><span data-stu-id="89b5b-165">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="89b5b-166">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="89b5b-166">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="89b5b-167">傳遞參數</span><span class="sxs-lookup"><span data-stu-id="89b5b-167">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="89b5b-168">方法參數</span><span class="sxs-lookup"><span data-stu-id="89b5b-168">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="89b5b-169">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="89b5b-169">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
