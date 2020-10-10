---
description: ref 關鍵字 - C# 參考
title: ref 關鍵字 - C# 參考
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: d2855738c723ba6d2437257793f18349b18629dc
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877583"
---
# <a name="ref-c-reference"></a><span data-ttu-id="9f963-103">ref (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9f963-103">ref (C# Reference)</span></span>

<span data-ttu-id="9f963-104">`ref` 關鍵字指出以傳址方式傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="9f963-104">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="9f963-105">它用於三個不同的內容：</span><span class="sxs-lookup"><span data-stu-id="9f963-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="9f963-106">在方法簽章和方法呼叫中，以傳址方式將引數傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="9f963-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="9f963-107">如需詳細資訊，請參閱[以傳址方式傳遞引數](#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="9f963-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="9f963-108">在方法簽章中，以傳參考方式將值傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="9f963-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="9f963-109">如需詳細資訊，請參閱[參考傳回值](#reference-return-values)。</span><span class="sxs-lookup"><span data-stu-id="9f963-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="9f963-110">在成員主體中，指出參考傳回值儲存在本機作為呼叫者想要修改的參考，或是一般而言，以參考存取另一個值的區域變數。</span><span class="sxs-lookup"><span data-stu-id="9f963-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="9f963-111">如需詳細資訊，請參閱 [ref 區域變數](#ref-locals)。</span><span class="sxs-lookup"><span data-stu-id="9f963-111">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="9f963-112">在 `struct` 宣告中來宣告 `ref struct` 或 `readonly ref struct`。</span><span class="sxs-lookup"><span data-stu-id="9f963-112">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="9f963-113">如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `ref` 結構](../builtin-types/struct.md#ref-struct)一節。</span><span class="sxs-lookup"><span data-stu-id="9f963-113">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="9f963-114">以傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="9f963-114">Passing an argument by reference</span></span>

<span data-ttu-id="9f963-115">用於方法的參數清單時，`ref` 關鍵字指出以傳參考方式傳遞引數，而不是以傳值方式。</span><span class="sxs-lookup"><span data-stu-id="9f963-115">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="9f963-116">`ref` 關鍵字會使形式參數成為引數的別名，其必須為變數。</span><span class="sxs-lookup"><span data-stu-id="9f963-116">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="9f963-117">換句話說，參數上的任何作業都會在引數上進行。</span><span class="sxs-lookup"><span data-stu-id="9f963-117">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="9f963-118">例如，如果呼叫端傳遞區域變數運算式或陣列元素存取運算式，而且被呼叫的方法取代 ref 參數所參考的物件，則呼叫端的區域變數或陣列元素現在會在方法傳回時參考新的物件。</span><span class="sxs-lookup"><span data-stu-id="9f963-118">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="9f963-119">請勿將參考傳遞的概念與參考類型的概念相混淆。</span><span class="sxs-lookup"><span data-stu-id="9f963-119">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="9f963-120">兩個概念並不相同。</span><span class="sxs-lookup"><span data-stu-id="9f963-120">The two concepts are not the same.</span></span> <span data-ttu-id="9f963-121">方法參數可以由 `ref` 修改，而不論其是否為實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="9f963-121">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="9f963-122">當實值類型由參考傳遞時，沒有 boxing。</span><span class="sxs-lookup"><span data-stu-id="9f963-122">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="9f963-123">若要使用 `ref` 參數，方法定義和呼叫方法都必須明確使用 `ref` 關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9f963-123">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="9f963-124">傳遞至 `ref` 或 `in` 參數的引數，必須在傳遞之前先初始化。</span><span class="sxs-lookup"><span data-stu-id="9f963-124">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="9f963-125">這與 [out](out-parameter-modifier.md) 參數不同，其引數不需要在傳遞之前先明確初始化。</span><span class="sxs-lookup"><span data-stu-id="9f963-125">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="9f963-126">類別的成員的簽章，不能只有在 `ref`、`in` 或 `out` 部分不同。</span><span class="sxs-lookup"><span data-stu-id="9f963-126">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="9f963-127">如果類型的兩個成員之間，唯一的區別在於其中一個有 `ref` 參數，而另一個有 `out` 或 `in` 參數，則會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f963-127">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="9f963-128">例如，下列程式碼不會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="9f963-128">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="9f963-129">但如果一種方法有 `ref`、`in` 或 `out` 參數，而另一種方法有實值參數，則可以對方法進行多載，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="9f963-129">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="9f963-130">其他需要簽章比對的情況 (像是隱藏或覆寫)，`in`、`ref` 及 `out` 是簽章的一部分，但彼此不相符。</span><span class="sxs-lookup"><span data-stu-id="9f963-130">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="9f963-131">屬性不是變數。</span><span class="sxs-lookup"><span data-stu-id="9f963-131">Properties are not variables.</span></span> <span data-ttu-id="9f963-132">它們都是方法，且不能傳遞給 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="9f963-132">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="9f963-133">您不可為下列幾種方法使用 `ref`、`in` 和 `out` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="9f963-133">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="9f963-134">使用 [async](async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="9f963-134">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="9f963-135">迭代器方法，其包括 [yield return](yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9f963-135">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="9f963-136">此外， [擴充方法](../../programming-guide/classes-and-structs/extension-methods.md) 具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="9f963-136">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="9f963-137">`out`關鍵字不能用在擴充方法的第一個引數上。</span><span class="sxs-lookup"><span data-stu-id="9f963-137">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="9f963-138">`ref`當引數不是結構，或是不受限於不是結構的泛型型別時，無法在擴充方法的第一個引數上使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9f963-138">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="9f963-139">`in`除非第一個引數是結構，否則無法使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9f963-139">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="9f963-140">`in`關鍵字不能用於任何泛型型別，即使當條件約束為結構時也一樣。</span><span class="sxs-lookup"><span data-stu-id="9f963-140">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="9f963-141">以傳址方式傳遞引數：範例</span><span class="sxs-lookup"><span data-stu-id="9f963-141">Passing an argument by reference: An example</span></span>

<span data-ttu-id="9f963-142">先前的範例會以傳參考方式傳遞實值型別。</span><span class="sxs-lookup"><span data-stu-id="9f963-142">The previous examples pass value types by reference.</span></span> <span data-ttu-id="9f963-143">您也可以使用 `ref` 關鍵字，以傳參考方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="9f963-143">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="9f963-144">以傳址方式傳遞參考型別，可讓已呼叫方法取代參考參數在呼叫者中所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="9f963-144">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="9f963-145">物件的儲存位置會以參考參數值的方式，傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="9f963-145">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="9f963-146">如果您變更參數儲存位置中的值 (指向新的物件)，則也會變更呼叫端所參考的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="9f963-146">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="9f963-147">下列範例會以 `ref` 參數，傳遞參考類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f963-147">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="9f963-148">如需如何依傳值和依傳址方式來傳遞參考類型的詳細資訊，請參閱[傳遞參考類型參數](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9f963-148">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="9f963-149">參考傳回值</span><span class="sxs-lookup"><span data-stu-id="9f963-149">Reference return values</span></span>

<span data-ttu-id="9f963-150">參考傳回值 (或 ref 傳回值) 是方法以傳參考方式傳回給呼叫者的值。</span><span class="sxs-lookup"><span data-stu-id="9f963-150">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="9f963-151">也就是說，呼叫者可以修改方法所傳回的值，而且該變更會反映在呼叫方法中物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="9f963-151">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="9f963-152">參考傳回值是使用 `ref` 關鍵字所定義：</span><span class="sxs-lookup"><span data-stu-id="9f963-152">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="9f963-153">在方法簽章中。</span><span class="sxs-lookup"><span data-stu-id="9f963-153">In the method signature.</span></span> <span data-ttu-id="9f963-154">例如，下列方法簽章指出 `GetCurrentPrice` 方法以傳參考方式傳回 <xref:System.Decimal> 值。</span><span class="sxs-lookup"><span data-stu-id="9f963-154">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="9f963-155">`return` 權杖與方法之 `return` 陳述式中所傳回變數之間。</span><span class="sxs-lookup"><span data-stu-id="9f963-155">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="9f963-156">例如：</span><span class="sxs-lookup"><span data-stu-id="9f963-156">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="9f963-157">為了讓呼叫者修改物件的狀態，參考傳回值必須儲存至明確定義為 [ref 區域變數](#ref-locals)的變數。</span><span class="sxs-lookup"><span data-stu-id="9f963-157">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="9f963-158">以下是更完整的 ref 傳回範例，同時顯示方法簽章和方法主體。</span><span class="sxs-lookup"><span data-stu-id="9f963-158">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="9f963-159">所呼叫的方法也可能將傳回值宣告為 `ref readonly`，以透過傳址方式將值傳回，並且強制使呼叫程式碼無法修改傳回值。</span><span class="sxs-lookup"><span data-stu-id="9f963-159">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="9f963-160">呼叫方法可以將值儲存在本機 [ref readonly](#ref-readonly-locals) 變數中，以避免複製傳回的值。</span><span class="sxs-lookup"><span data-stu-id="9f963-160">The calling method can avoid copying the returned value by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="9f963-161">如需範例，請參閱 [ref 傳回值和 ref 區域變數範例](#a-ref-returns-and-ref-locals-example)。</span><span class="sxs-lookup"><span data-stu-id="9f963-161">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="9f963-162">ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="9f963-162">Ref locals</span></span>

<span data-ttu-id="9f963-163">ref 區域變數用來參考使用 `return ref` 所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="9f963-163">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="9f963-164">ref 區域變數無法初始化至非 ref 傳回值。</span><span class="sxs-lookup"><span data-stu-id="9f963-164">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="9f963-165">換句話說，初始化的右手邊必須是參考。</span><span class="sxs-lookup"><span data-stu-id="9f963-165">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="9f963-166">任何對 ref 區域變數值進行的修改，都會反映在其方法以傳址方式傳回值之物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="9f963-166">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="9f963-167">定義 ref 區域變數的方式是在變數宣告前面使用 `ref` 關鍵字，並且緊接在以傳參考方式傳回值的方法呼叫前面。</span><span class="sxs-lookup"><span data-stu-id="9f963-167">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="9f963-168">例如，下列陳述式定義名為 `GetEstimatedValue` 之方法所傳回的 ref 區域變數值：</span><span class="sxs-lookup"><span data-stu-id="9f963-168">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="9f963-169">您可透過相同方式以參考存取值。</span><span class="sxs-lookup"><span data-stu-id="9f963-169">You can access a value by reference in the same way.</span></span> <span data-ttu-id="9f963-170">在某些情況下，以參考存取值會避免潛在過度浪費資源的複製作業，進而增加效能。</span><span class="sxs-lookup"><span data-stu-id="9f963-170">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="9f963-171">例如，下列陳述式示範了如何定義用於參考值的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="9f963-171">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="9f963-172">在這兩個範例中 `ref` ，關鍵字都必須用於這兩個位置，否則編譯器會產生錯誤 CS8172 「無法使用值將傳址變數初始化」。</span><span class="sxs-lookup"><span data-stu-id="9f963-172">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="9f963-173">從 C# 7.3 開始，`foreach` 陳述式的反覆運算變數可以是 ref 區域變數或 ref readonly 區域變數。</span><span class="sxs-lookup"><span data-stu-id="9f963-173">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="9f963-174">如需詳細資訊，請參閱 [foreach 陳述式](foreach-in.md)一文。</span><span class="sxs-lookup"><span data-stu-id="9f963-174">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="9f963-175">此外，從 c # 7.3 開始，您可以使用 [ref 指派運算子](../operators/assignment-operator.md#ref-assignment-operator)重新指派 ref 區域變數或 ref readonly 區域變數。</span><span class="sxs-lookup"><span data-stu-id="9f963-175">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="9f963-176">ref readonly 區域變數</span><span class="sxs-lookup"><span data-stu-id="9f963-176">Ref readonly locals</span></span>

<span data-ttu-id="9f963-177">ref readonly 區域變數是用來參考傳回值 (由特徵標記中有 `ref readonly` 且使用 `return ref` 的方法或屬性傳回)。</span><span class="sxs-lookup"><span data-stu-id="9f963-177">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="9f963-178">`ref readonly` 區域變數結合了 `ref` 區域變數的屬性和 `readonly` 變數：它是受指派之儲存體的別名，且無法修改。</span><span class="sxs-lookup"><span data-stu-id="9f963-178">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="9f963-179">ref 傳回值和 ref 區域變數範例</span><span class="sxs-lookup"><span data-stu-id="9f963-179">A ref returns and ref locals example</span></span>

<span data-ttu-id="9f963-180">下面範例會定義具有 `Title` 和 `Author` 這兩個 <xref:System.String> 欄位的 `Book` 類別。</span><span class="sxs-lookup"><span data-stu-id="9f963-180">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="9f963-181">它也會定義 `BookCollection` 類別，以包含 `Book` 物件的私用陣列。</span><span class="sxs-lookup"><span data-stu-id="9f963-181">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="9f963-182">以傳址方式傳回個別書籍物件，方法是呼叫其 `GetBookByTitle` 方法。</span><span class="sxs-lookup"><span data-stu-id="9f963-182">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="9f963-183">呼叫者將 `GetBookByTitle` 方法所傳回的值儲存為 ref 區域變數時，呼叫者對傳回值進行的變更會反映在 `BookCollection` 物件中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9f963-183">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="9f963-184">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9f963-184">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f963-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f963-185">See also</span></span>

- [<span data-ttu-id="9f963-186">撰寫安全有效率的程式碼</span><span class="sxs-lookup"><span data-stu-id="9f963-186">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="9f963-187">ref 傳回值和 ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="9f963-187">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="9f963-188">條件 ref 運算式</span><span class="sxs-lookup"><span data-stu-id="9f963-188">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="9f963-189">傳遞參數</span><span class="sxs-lookup"><span data-stu-id="9f963-189">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="9f963-190">方法參數</span><span class="sxs-lookup"><span data-stu-id="9f963-190">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="9f963-191">C # 參考</span><span class="sxs-lookup"><span data-stu-id="9f963-191">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9f963-192">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9f963-192">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9f963-193">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9f963-193">C# Keywords</span></span>](index.md)
