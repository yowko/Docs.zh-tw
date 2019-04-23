---
title: ref 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 1faebe2ce1a59798621888e3a518900234720be5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116252"
---
# <a name="ref-c-reference"></a><span data-ttu-id="1af94-102">ref (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1af94-102">ref (C# Reference)</span></span>

<span data-ttu-id="1af94-103">`ref` 關鍵字指出以傳參考方式傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="1af94-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="1af94-104">它用於三個不同的內容：</span><span class="sxs-lookup"><span data-stu-id="1af94-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="1af94-105">在方法簽章和方法呼叫中，以傳參考方式將引數傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="1af94-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="1af94-106">如需詳細資訊，請參閱[以傳址方式傳遞引數](#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="1af94-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="1af94-107">在方法簽章中，以傳參考方式將值傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="1af94-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="1af94-108">如需詳細資訊，請參閱[參考傳回值](#reference-return-values)。</span><span class="sxs-lookup"><span data-stu-id="1af94-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="1af94-109">在成員主體中，指出參考傳回值儲存在本機作為呼叫者想要修改的參考，或是一般而言，以參考存取另一個值的區域變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="1af94-110">如需詳細資訊，請參閱 [ref 區域變數](#ref-locals)。</span><span class="sxs-lookup"><span data-stu-id="1af94-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="1af94-111">在 `struct` 宣告中來宣告 `ref struct` 或 `ref readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="1af94-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="1af94-112">如需詳細資訊，請參閱 [ref struct 型別](#ref-struct-types)。</span><span class="sxs-lookup"><span data-stu-id="1af94-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="1af94-113">以傳參考方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="1af94-113">Passing an argument by reference</span></span>

<span data-ttu-id="1af94-114">用於方法的參數清單時，`ref` 關鍵字指出以傳參考方式傳遞引數，而不是以傳值方式。</span><span class="sxs-lookup"><span data-stu-id="1af94-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="1af94-115">`ref` 關鍵字會使形式參數成為引數的別名，其必須為變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="1af94-116">換句話說，參數上的任何作業都會在引數上進行。</span><span class="sxs-lookup"><span data-stu-id="1af94-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="1af94-117">例如，如果呼叫者傳遞區域變數運算式或陣列元素存取運算式，而且已呼叫方法取代 ref 參數所參考的物件，則在傳回方法時，呼叫者的區域變數或陣列元素現在會參考新的物件。</span><span class="sxs-lookup"><span data-stu-id="1af94-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="1af94-118">請勿將參考傳遞的概念與參考類型的概念相混淆。</span><span class="sxs-lookup"><span data-stu-id="1af94-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="1af94-119">兩個概念並不相同。</span><span class="sxs-lookup"><span data-stu-id="1af94-119">The two concepts are not the same.</span></span> <span data-ttu-id="1af94-120">方法參數可以由 `ref` 修改，而不論其是否為實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="1af94-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="1af94-121">當實值類型由參考傳遞時，沒有 boxing。</span><span class="sxs-lookup"><span data-stu-id="1af94-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="1af94-122">若要使用 `ref` 參數，方法定義和呼叫方法都必須明確使用 `ref` 關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1af94-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="1af94-123">傳遞至 `ref` 或 `in` 參數的引數，必須在傳遞之前先初始化。</span><span class="sxs-lookup"><span data-stu-id="1af94-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="1af94-124">這與 [out](out-parameter-modifier.md) 參數不同，其引數不需要在傳遞之前先明確初始化。</span><span class="sxs-lookup"><span data-stu-id="1af94-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="1af94-125">類別的成員的簽章，不能只有在 `ref`、`in` 或 `out` 部分不同。</span><span class="sxs-lookup"><span data-stu-id="1af94-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="1af94-126">如果類型的兩個成員之間，唯一的區別在於其中一個有 `ref` 參數，而另一個有 `out` 或 `in` 參數，則會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="1af94-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="1af94-127">例如，下列程式碼不會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="1af94-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="1af94-128">但如果一種方法有 `ref`、`in` 或 `out` 參數，而另一種方法有實值參數，則可以對方法進行多載，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="1af94-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="1af94-129">其他需要簽章比對的情況 (像是隱藏或覆寫)，`in`、`ref` 及 `out` 是簽章的一部分，但彼此不相符。</span><span class="sxs-lookup"><span data-stu-id="1af94-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="1af94-130">屬性不是變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-130">Properties are not variables.</span></span> <span data-ttu-id="1af94-131">它們都是方法，且不能傳遞給 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="1af94-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="1af94-132">您不可為下列幾種方法使用 `ref`、`in` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="1af94-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="1af94-133">使用 [async](async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="1af94-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="1af94-134">迭代器方法，其包括 [yield return](yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1af94-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="1af94-135">以傳址方式傳遞引數：範例</span><span class="sxs-lookup"><span data-stu-id="1af94-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="1af94-136">先前的範例會以傳參考方式傳遞實值型別。</span><span class="sxs-lookup"><span data-stu-id="1af94-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="1af94-137">您也可以使用 `ref` 關鍵字，以傳參考方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="1af94-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="1af94-138">以傳參考方式傳遞參考型別，可讓已呼叫方法取代參考參數在呼叫者中所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="1af94-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="1af94-139">物件的儲存位置會以參考參數值的方式，傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="1af94-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="1af94-140">如果您變更參數儲存位置中的值 (指向新的物件)，則也會變更呼叫端所參考的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="1af94-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="1af94-141">下列範例會以 `ref` 參數，傳遞參考類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1af94-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="1af94-142">如需如何依傳值和依傳址方式來傳遞參考類型的詳細資訊，請參閱[傳遞參考類型參數](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1af94-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="1af94-143">參考傳回值</span><span class="sxs-lookup"><span data-stu-id="1af94-143">Reference return values</span></span>

<span data-ttu-id="1af94-144">參考傳回值 (或 ref 傳回值) 是方法以傳參考方式傳回給呼叫者的值。</span><span class="sxs-lookup"><span data-stu-id="1af94-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="1af94-145">也就是說，呼叫者可以修改方法所傳回的值，而且該變更會反映在包含方法的物件狀態中。</span><span class="sxs-lookup"><span data-stu-id="1af94-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="1af94-146">參考傳回值是使用 `ref` 關鍵字所定義：</span><span class="sxs-lookup"><span data-stu-id="1af94-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="1af94-147">在方法簽章中。</span><span class="sxs-lookup"><span data-stu-id="1af94-147">In the method signature.</span></span> <span data-ttu-id="1af94-148">例如，下列方法簽章指出 `GetCurrentPrice` 方法以傳參考方式傳回 <xref:System.Decimal> 值。</span><span class="sxs-lookup"><span data-stu-id="1af94-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="1af94-149">`return` 權杖與方法之 `return` 陳述式中所傳回變數之間。</span><span class="sxs-lookup"><span data-stu-id="1af94-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="1af94-150">例如: </span><span class="sxs-lookup"><span data-stu-id="1af94-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="1af94-151">為了讓呼叫者修改物件的狀態，參考傳回值必須儲存至明確定義為 [ref 區域變數](#ref-locals)的變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="1af94-152">所呼叫的方法也可能將傳回值宣告為 `ref readonly`，以透過傳址方式將值傳回，並且強制使呼叫程式碼無法修改傳回值。</span><span class="sxs-lookup"><span data-stu-id="1af94-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="1af94-153">呼叫的方法可以將值儲存在區域 [ref readonly](#ref-readonly-locals) 變數，以避免複製傳回值。</span><span class="sxs-lookup"><span data-stu-id="1af94-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="1af94-154">如需範例，請參閱 [ref 傳回值和 ref 區域變數範例](#a-ref-returns-and-ref-locals-example)。</span><span class="sxs-lookup"><span data-stu-id="1af94-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="1af94-155">ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="1af94-155">Ref locals</span></span>

<span data-ttu-id="1af94-156">ref 區域變數用來參考使用 `return ref` 所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="1af94-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="1af94-157">ref 區域變數無法初始化至非 ref 傳回值。</span><span class="sxs-lookup"><span data-stu-id="1af94-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="1af94-158">換句話說，初始化的右側必須是參考。</span><span class="sxs-lookup"><span data-stu-id="1af94-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="1af94-159">任何對 ref 區域變數值進行的修改，都會反映在其方法以傳參考方式傳回值之物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="1af94-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="1af94-160">定義 ref 區域變數的方式是在變數宣告前面使用 `ref` 關鍵字，並且緊接在以傳參考方式傳回值的方法呼叫前面。</span><span class="sxs-lookup"><span data-stu-id="1af94-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="1af94-161">例如，下列陳述式定義名為 `GetEstimatedValue` 之方法所傳回的 ref 區域變數值：</span><span class="sxs-lookup"><span data-stu-id="1af94-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="1af94-162">您可透過相同方式以參考存取值。</span><span class="sxs-lookup"><span data-stu-id="1af94-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="1af94-163">在某些情況下，以參考存取值會避免潛在過度浪費資源的複製作業，進而增加效能。</span><span class="sxs-lookup"><span data-stu-id="1af94-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="1af94-164">例如，下列陳述式示範了如何定義用於參考值的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="1af94-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="1af94-165">請注意，在這兩個範例中，`ref` 關鍵字必須用在兩個位置，否則編譯器會產生錯誤 CS8172「無法使用值將傳址變數初始化」。</span><span class="sxs-lookup"><span data-stu-id="1af94-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="1af94-166">從 C# 7.3 開始，`foreach` 陳述式的反覆運算變數可以是 ref 區域變數或 ref readonly 區域變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="1af94-167">如需詳細資訊，請參閱 [foreach 陳述式](foreach-in.md)一文。</span><span class="sxs-lookup"><span data-stu-id="1af94-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="1af94-168">ref readonly 區域變數</span><span class="sxs-lookup"><span data-stu-id="1af94-168">Ref readonly locals</span></span>

<span data-ttu-id="1af94-169">ref readonly 區域變數是用來參考傳回值 (由特徵標記中有 `ref readonly` 且使用 `return ref` 的方法或屬性傳回)。</span><span class="sxs-lookup"><span data-stu-id="1af94-169">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="1af94-170">`ref readonly` 區域變數結合了 `ref` 區域變數的屬性和 `readonly` 變數：它是受指派之儲存體的別名，且無法修改。</span><span class="sxs-lookup"><span data-stu-id="1af94-170">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="1af94-171">ref 傳回值和 ref 區域變數範例</span><span class="sxs-lookup"><span data-stu-id="1af94-171">A ref returns and ref locals example</span></span>

<span data-ttu-id="1af94-172">下面範例會定義具有 `Title` 和 `Author` 這兩個 <xref:System.String> 欄位的 `Book` 類別。</span><span class="sxs-lookup"><span data-stu-id="1af94-172">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="1af94-173">它也會定義 `BookCollection` 類別，以包含 `Book` 物件的私用陣列。</span><span class="sxs-lookup"><span data-stu-id="1af94-173">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="1af94-174">以傳參考方式傳回個別書籍物件，方法是呼叫其 `GetBookByTitle` 方法。</span><span class="sxs-lookup"><span data-stu-id="1af94-174">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="1af94-175">呼叫者將 `GetBookByTitle` 方法所傳回的值儲存為 ref 區域變數時，呼叫者對傳回值進行的變更會反映在 `BookCollection` 物件中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1af94-175">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="1af94-176">ref struct 型別</span><span class="sxs-lookup"><span data-stu-id="1af94-176">Ref struct types</span></span>

<span data-ttu-id="1af94-177">將 `ref` 修飾詞新增到 `struct` 陳述式會將該類型的執行個體定義成必須堆疊配置。</span><span class="sxs-lookup"><span data-stu-id="1af94-177">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="1af94-178">換句話說，這些類型的執行個體絶對不會在堆積上建立為另一個類別的成員。</span><span class="sxs-lookup"><span data-stu-id="1af94-178">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="1af94-179">此功能的主要動機是 <xref:System.Span%601> 及相關的結構。</span><span class="sxs-lookup"><span data-stu-id="1af94-179">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="1af94-180">希望將類型 `ref struct` 保留為配置有堆疊的變數之目標，會讓編譯器強制對所有 `ref struct` 類型進行數項規則。</span><span class="sxs-lookup"><span data-stu-id="1af94-180">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="1af94-181">您無法分隔 `ref struct`。</span><span class="sxs-lookup"><span data-stu-id="1af94-181">You can't box a `ref struct`.</span></span> <span data-ttu-id="1af94-182">您不可為類型是 `object`、`dynamic` 或任何介面類型的變數，指派 `ref struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="1af94-182">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- `ref struct` <span data-ttu-id="1af94-183">類型無法實作介面。</span><span class="sxs-lookup"><span data-stu-id="1af94-183">types cannot implement interfaces.</span></span>
- <span data-ttu-id="1af94-184">您不可將 `ref struct` 宣告為類別或一般結構的成員。</span><span class="sxs-lookup"><span data-stu-id="1af94-184">You can't declare a `ref struct` as a member of a class or a normal struct.</span></span>
- <span data-ttu-id="1af94-185">您不可在非同步方法中宣告類型為 `ref struct` 的區域變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-185">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="1af94-186">但可以在傳回 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 或 `Task` 之類型別的同步方法中，宣告這些區域變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-186">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="1af94-187">您不可在迭代器中宣告 `ref struct` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-187">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="1af94-188">您不可在 Lambda 運算式或區域函式中擷取 `ref struct` 變數。</span><span class="sxs-lookup"><span data-stu-id="1af94-188">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="1af94-189">這些限制可確保您不會意外使用 `ref struct` 而將它升階成受控堆積。</span><span class="sxs-lookup"><span data-stu-id="1af94-189">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="1af94-190">您可以結合修飾詞來將結構宣告為 `readonly ref`。</span><span class="sxs-lookup"><span data-stu-id="1af94-190">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="1af94-191">`readonly ref struct` 結合了 `ref struct` 與 `readonly struct` 宣告的優點與限制。</span><span class="sxs-lookup"><span data-stu-id="1af94-191">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1af94-192">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1af94-192">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1af94-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1af94-193">See also</span></span>

- [<span data-ttu-id="1af94-194">撰寫安全、有效率的程式碼</span><span class="sxs-lookup"><span data-stu-id="1af94-194">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="1af94-195">ref 傳回值和 ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="1af94-195">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="1af94-196">條件 ref 運算式</span><span class="sxs-lookup"><span data-stu-id="1af94-196">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="1af94-197">ref 指派運算子</span><span class="sxs-lookup"><span data-stu-id="1af94-197">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="1af94-198">傳遞參數</span><span class="sxs-lookup"><span data-stu-id="1af94-198">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="1af94-199">方法參數</span><span class="sxs-lookup"><span data-stu-id="1af94-199">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="1af94-200">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1af94-200">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1af94-201">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="1af94-201">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1af94-202">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1af94-202">C# Keywords</span></span>](index.md)
