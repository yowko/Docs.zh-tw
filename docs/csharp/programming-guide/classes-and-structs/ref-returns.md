---
title: ref 傳回值和 ref 區域變數 (C# 手冊)
description: 了解如何定義和使用 ref 傳回值和 ref 區域變數值
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: fcac162f63438b6cbe54908383467d4b0f227c39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081827"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="e8bca-103">ref 傳回值和 ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="e8bca-103">Ref returns and ref locals</span></span>

<span data-ttu-id="e8bca-104">從 C# 7.0 開始，C# 支援參考傳回值 (ref 傳回值)。</span><span class="sxs-lookup"><span data-stu-id="e8bca-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="e8bca-105">參考傳回值允許方法將變數參考 (而非值) 傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e8bca-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="e8bca-106">呼叫者接著可以選擇將傳回的變數視為以傳值方式或以傳址方式傳回。</span><span class="sxs-lookup"><span data-stu-id="e8bca-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="e8bca-107">呼叫者可建立本身為參考傳回值的新變數，稱為 ref 區域變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="e8bca-108">何謂參考傳回值？</span><span class="sxs-lookup"><span data-stu-id="e8bca-108">What is a reference return value?</span></span>

<span data-ttu-id="e8bca-109">大部分的開發人員都熟悉「以傳址方式」將引數傳遞給已呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e8bca-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="e8bca-110">所呼叫方法的引數清單包含以傳址方式傳遞的變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="e8bca-111">呼叫者會觀察到所呼叫方法對其值進行的任何變更。</span><span class="sxs-lookup"><span data-stu-id="e8bca-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="e8bca-112">「參考傳回值」表示方法會將「參考」 (或別名) 傳回給某個變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="e8bca-113">該變數的範圍必須包含方法。</span><span class="sxs-lookup"><span data-stu-id="e8bca-113">That variable's scope must include the method.</span></span> <span data-ttu-id="e8bca-114">該變數的存留期必須延伸到傳回方法。</span><span class="sxs-lookup"><span data-stu-id="e8bca-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="e8bca-115">呼叫者對方法的傳回值所進行的修改，是針對方法傳回的變數進行。</span><span class="sxs-lookup"><span data-stu-id="e8bca-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="e8bca-116">宣告方法傳回「參考傳回值」，表示方法會將別名傳回給變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="e8bca-117">此設計通常用於呼叫的程式碼應可透過別名來存取該變數 (包括進行修改) 時。</span><span class="sxs-lookup"><span data-stu-id="e8bca-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="e8bca-118">這樣一來，以傳址方式傳回的方法就不能有傳回型別 `void`。</span><span class="sxs-lookup"><span data-stu-id="e8bca-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="e8bca-119">方法可傳回為參考傳回值的運算式有一些限制。</span><span class="sxs-lookup"><span data-stu-id="e8bca-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="e8bca-120">限制包含：</span><span class="sxs-lookup"><span data-stu-id="e8bca-120">Restrictions include:</span></span>

- <span data-ttu-id="e8bca-121">傳回值必須有超過方法執行期間的存留期。</span><span class="sxs-lookup"><span data-stu-id="e8bca-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="e8bca-122">換句話說，它不能是將它傳回之方法中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="e8bca-123">它可以是類別的執行個體或靜態欄位，也可以是傳遞給方法的引數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="e8bca-124">嘗試傳回區域變數會產生編譯器錯誤 CS8168「無法以傳址方式傳回本機 'obj'，因為其非參考本機」。</span><span class="sxs-lookup"><span data-stu-id="e8bca-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="e8bca-125">傳回值不能是常值 `null`。</span><span class="sxs-lookup"><span data-stu-id="e8bca-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="e8bca-126">傳回 `null` 會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。</span><span class="sxs-lookup"><span data-stu-id="e8bca-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="e8bca-127">使用 ref 傳回值的方法，可以將別名傳回給目前值為 Null (未具現化) 的變數，或是[可為 Null 的型別](../nullable-types/index.md)的實值型別。</span><span class="sxs-lookup"><span data-stu-id="e8bca-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="e8bca-128">傳回值不能是常數、列舉成員、屬性的以傳值方式傳回值，或是 `class` 或 `struct` 的方法。</span><span class="sxs-lookup"><span data-stu-id="e8bca-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="e8bca-129">違反此規則會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。</span><span class="sxs-lookup"><span data-stu-id="e8bca-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="e8bca-130">此外，非同步方法上不允許參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="e8bca-131">在非同步方法完成執行之前，可能會傳回非同步方法，但其傳回值仍然為未知。</span><span class="sxs-lookup"><span data-stu-id="e8bca-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="e8bca-132">定義 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="e8bca-132">Defining a ref return value</span></span>

<span data-ttu-id="e8bca-133">傳回*參考傳回值*的方法必須滿足下列兩個條件：</span><span class="sxs-lookup"><span data-stu-id="e8bca-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="e8bca-134">方法簽章在傳回型別前包含 [ref](../../language-reference/keywords/ref.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e8bca-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="e8bca-135">方法主體中的每個 [return](../../language-reference/keywords/return.md) 陳述式在所傳回執行個體前包含 [ref](../../language-reference/keywords/ref.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e8bca-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="e8bca-136">下列範例顯示滿足那些條件並傳回參考給名為 `p` 之 `Person` 物件的方法：</span><span class="sxs-lookup"><span data-stu-id="e8bca-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="e8bca-137">使用 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="e8bca-137">Consuming a ref return value</span></span>

<span data-ttu-id="e8bca-138">ref 傳回值是在已呼叫方法的範圍中，另一個變數的別名。</span><span class="sxs-lookup"><span data-stu-id="e8bca-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="e8bca-139">您可以將任何使用 ref 傳回值的用法，解譯為使用別名所代表的變數：</span><span class="sxs-lookup"><span data-stu-id="e8bca-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="e8bca-140">當您指派其值時，是將值指派給別名的變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="e8bca-141">當您讀取其值時，是讀取別名的變數值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="e8bca-142">如果您以「傳址」方式傳回它，就是將別名傳回至同一個變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="e8bca-143">如果您以「傳址」方式將它傳遞到另一個方法，就是將參考傳遞至別名的變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="e8bca-144">當您建立 [ref 區域變數](#ref-locals)別名時，就是對相同變數建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="e8bca-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="e8bca-145">ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="e8bca-145">Ref locals</span></span>

<span data-ttu-id="e8bca-146">假設 `GetContactInformation` 方法是宣告為 ref 傳回值：</span><span class="sxs-lookup"><span data-stu-id="e8bca-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="e8bca-147">傳值方式指派會讀取變數值，並將它指派給新的變數：</span><span class="sxs-lookup"><span data-stu-id="e8bca-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="e8bca-148">上述的指派將 `p` 宣告為區域變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="e8bca-149">其初始值的複製來源，是讀取 `GetContactInformation` 所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="e8bca-150">對 `p` 的任何後續指派將不會變更 `GetContactInformation` 傳回的變數值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="e8bca-151">變數 `p` 不再是所傳回之變數的別名。</span><span class="sxs-lookup"><span data-stu-id="e8bca-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="e8bca-152">您宣告「ref 區域變數」以將別名複製到原始的值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="e8bca-153">在下列指派中，`p` 是 `GetContactInformation` 所傳回之變數的別名。</span><span class="sxs-lookup"><span data-stu-id="e8bca-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="e8bca-154">後續 `p` 的使用方式與使用 `GetContactInformation` 傳回的變數相同，因為 `p` 是該變數的別名。</span><span class="sxs-lookup"><span data-stu-id="e8bca-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="e8bca-155">變更 `p` 也會變更 `GetContactInformation` 傳回的變數。</span><span class="sxs-lookup"><span data-stu-id="e8bca-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="e8bca-156">`ref` 關鍵字是用於區域變數宣告的前面「和」方法呼叫的前面。</span><span class="sxs-lookup"><span data-stu-id="e8bca-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="e8bca-157">您可透過相同方式以參考存取值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="e8bca-158">在某些情況下，以參考存取值會避免潛在過度浪費資源的複製作業，進而增加效能。</span><span class="sxs-lookup"><span data-stu-id="e8bca-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="e8bca-159">例如，下列陳述式示範了如何定義用於參考值的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="e8bca-160">區域變數宣告的前面「和」第二個範例中值的前面都會使用 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e8bca-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="e8bca-161">無法在這兩個範例內的變數宣告和指派中同時包含 `ref` 關鍵字，會導致編譯器錯誤 CS8172「無法使用值將傳址變數初始化」。</span><span class="sxs-lookup"><span data-stu-id="e8bca-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="e8bca-162">在 C# 7.3 之前，無法重新指派 ref 區域變數，以在初始化之後參照不同的儲存體。</span><span class="sxs-lookup"><span data-stu-id="e8bca-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="e8bca-163">已移除該限制。</span><span class="sxs-lookup"><span data-stu-id="e8bca-163">That restriction has been removed.</span></span> <span data-ttu-id="e8bca-164">下列範例示範重新指派：</span><span class="sxs-lookup"><span data-stu-id="e8bca-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="e8bca-165">ref 區域變數在宣告後仍然必須予以初始化。</span><span class="sxs-lookup"><span data-stu-id="e8bca-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="e8bca-166">ref 傳回值和 ref 區域變數：範例</span><span class="sxs-lookup"><span data-stu-id="e8bca-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="e8bca-167">下列範例定義 `NumberStore` 類別，以儲存整數值的陣列。</span><span class="sxs-lookup"><span data-stu-id="e8bca-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="e8bca-168">`FindNumber` 方法會以傳址方式傳回第一個數字，而此數字大於或等於傳遞為引數的數字。</span><span class="sxs-lookup"><span data-stu-id="e8bca-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="e8bca-169">如果數字未大於或等於引數，則方法會在索引 0 傳回數字。</span><span class="sxs-lookup"><span data-stu-id="e8bca-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="e8bca-170">下列範例會呼叫 `NumberStore.FindNumber` 方法來擷取大於或等於 16 的第一個值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="e8bca-171">呼叫者接著會將方法所傳回的值加倍。</span><span class="sxs-lookup"><span data-stu-id="e8bca-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="e8bca-172">範例輸出顯示 `NumberStore` 執行個體之陣列項目值中所反映的變更。</span><span class="sxs-lookup"><span data-stu-id="e8bca-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="e8bca-173">如果不支援參考傳回值，則是透過傳回陣列項目和其值的索引來執行這類作業。</span><span class="sxs-lookup"><span data-stu-id="e8bca-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="e8bca-174">呼叫者接著可以使用這個索引，來修改不同方法呼叫中的值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="e8bca-175">不過，呼叫者也可以修改要存取的索引，也可能修改其他陣列值。</span><span class="sxs-lookup"><span data-stu-id="e8bca-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="e8bca-176">下列範例示範在 C# 7.3 之後如何重寫 `FindNumber` 方法以使用 ref 本機重新指派：</span><span class="sxs-lookup"><span data-stu-id="e8bca-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="e8bca-177">如果搜尋數目較接近陣列結尾，則這個第二個版本對較長的序列更具效率。</span><span class="sxs-lookup"><span data-stu-id="e8bca-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8bca-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8bca-178">See also</span></span>

- [<span data-ttu-id="e8bca-179">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e8bca-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="e8bca-180">撰寫安全、有效率的程式碼</span><span class="sxs-lookup"><span data-stu-id="e8bca-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
