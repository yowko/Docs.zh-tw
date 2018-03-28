---
title: ref 傳回值和 ref 區域變數 (C# 手冊)
description: 了解如何定義和使用 ref 傳回值和 ref 區域變數值
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c37c6dd61ae02813bcc467982f3b175da9136e4a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="7651b-103">ref 傳回值和 ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="7651b-103">Ref returns and ref locals</span></span>

<span data-ttu-id="7651b-104">從 C# 7 開始，C# 支援參考傳回值 (ref 傳回值)。</span><span class="sxs-lookup"><span data-stu-id="7651b-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="7651b-105">參考傳回值允許方法將變數參考 (而非值) 傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="7651b-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="7651b-106">呼叫者接著可以選擇將傳回的變數視為以傳值方式或以傳址方式傳回。</span><span class="sxs-lookup"><span data-stu-id="7651b-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="7651b-107">呼叫者可建立本身為參考傳回值的新變數，稱為 ref 區域變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="7651b-108">何謂參考傳回值？</span><span class="sxs-lookup"><span data-stu-id="7651b-108">What is a reference return value?</span></span>

<span data-ttu-id="7651b-109">大部分的開發人員都熟悉「以傳址方式」將引數傳遞給已呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="7651b-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="7651b-110">已呼叫方法的引數清單包含以傳址方式傳遞的變數，而且呼叫者會觀察到已呼叫方法對其值進行的任何變更。</span><span class="sxs-lookup"><span data-stu-id="7651b-110">A called method's argument list includes a variable passed by reference, and any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="7651b-111">「參考傳回值」表示方法傳回「參考」(或別名) 至某些變數，這些變數的範圍包括方法，且其存留期必須超過方法的傳回時間。</span><span class="sxs-lookup"><span data-stu-id="7651b-111">A *reference return value* means that a method returns a *reference* (or an alias) to some variable whose scope includes the method and whose lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="7651b-112">呼叫者對方法的傳回值所進行的修改，是針對方法傳回的變數進行。</span><span class="sxs-lookup"><span data-stu-id="7651b-112">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="7651b-113">宣告方法傳回「參考傳回值」，表示方法會將別名傳回給變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-113">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="7651b-114">此設計通常用於呼叫的程式碼應可透過別名來存取該變數 (包括進行修改) 時。</span><span class="sxs-lookup"><span data-stu-id="7651b-114">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="7651b-115">這樣一來，以傳址方式傳回的方法就不能有傳回型別 `void`。</span><span class="sxs-lookup"><span data-stu-id="7651b-115">It follows that methods returning by reference cannot have the return type `void`.</span></span>

<span data-ttu-id="7651b-116">方法可傳回為參考傳回值的運算式有一些限制。</span><span class="sxs-lookup"><span data-stu-id="7651b-116">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="7651b-117">它們包括：</span><span class="sxs-lookup"><span data-stu-id="7651b-117">These include:</span></span>

- <span data-ttu-id="7651b-118">傳回值必須有超過方法執行期間的存留期。</span><span class="sxs-lookup"><span data-stu-id="7651b-118">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="7651b-119">換句話說，它不能是將它傳回之方法中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-119">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="7651b-120">它可以是類別的執行個體或靜態欄位，也可以是傳遞給方法的引數。</span><span class="sxs-lookup"><span data-stu-id="7651b-120">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="7651b-121">嘗試傳回區域變數會產生編譯器錯誤 CS8168「無法以傳址方式傳回本機 'obj'，因為其非參考本機」。</span><span class="sxs-lookup"><span data-stu-id="7651b-121">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="7651b-122">傳回值不能是常值 `null`。</span><span class="sxs-lookup"><span data-stu-id="7651b-122">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="7651b-123">嘗試傳回 `null` 會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。</span><span class="sxs-lookup"><span data-stu-id="7651b-123">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="7651b-124">使用 ref 傳回值的方法，可以將別名傳回給目前值為 Null (未具現化) 的變數，或是[可為 Null 的型別](../nullable-types/index.md)的實值型別。</span><span class="sxs-lookup"><span data-stu-id="7651b-124">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="7651b-125">傳回值不能是常數、列舉成員、屬性的以傳值方式傳回值，或是 `class` 或 `struct` 的方法。</span><span class="sxs-lookup"><span data-stu-id="7651b-125">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="7651b-126">嘗試傳回這些會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。</span><span class="sxs-lookup"><span data-stu-id="7651b-126">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="7651b-127">此外，因為非同步方法可能會在完成執行之前傳回，但仍未知其傳回值，所以非同步方法並不允許參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="7651b-127">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="7651b-128">定義 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="7651b-128">Defining a ref return value</span></span>

<span data-ttu-id="7651b-129">將 [ref](../../language-reference/keywords/ref.md) 關鍵字新增至方法簽章的傳回型別，即可定義 ref 傳回值。</span><span class="sxs-lookup"><span data-stu-id="7651b-129">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="7651b-130">例如，下列簽章指出 `GetContactInformation` 屬性會將 `Person` 物件的參考傳回給呼叫者：</span><span class="sxs-lookup"><span data-stu-id="7651b-130">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="7651b-131">此外，方法主體中每個 [return](../../language-reference/keywords/return.md) 陳述式所傳回的物件名稱前面必須加上 [ref](../../language-reference/keywords/ref.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7651b-131">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="7651b-132">例如，下列 `return` 陳述式會傳回對名為 `p` 之 `Person` 物件的參考：</span><span class="sxs-lookup"><span data-stu-id="7651b-132">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="7651b-133">使用 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="7651b-133">Consuming a ref return value</span></span>

<span data-ttu-id="7651b-134">ref 傳回值是在已呼叫方法的範圍中，另一個變數的別名。</span><span class="sxs-lookup"><span data-stu-id="7651b-134">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="7651b-135">您可以將任何使用 ref 傳回值的用法，解譯為使用別名所代表的變數：</span><span class="sxs-lookup"><span data-stu-id="7651b-135">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="7651b-136">當您指派其值時，是將值指派給別名的變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-136">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="7651b-137">當您讀取其值時，是讀取別名的變數值。</span><span class="sxs-lookup"><span data-stu-id="7651b-137">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="7651b-138">如果您以「傳址」方式傳回它，就是將別名傳回至同一個變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-138">If you return it *by reference* you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="7651b-139">如果您以「傳址」方式將它傳遞到另一個方法，就是將參考傳遞至別名的變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-139">If you pass it to another method *by reference* you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="7651b-140">當您建立 [ref 區域變數](#ref-local)別名時，就是對相同變數建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="7651b-140">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="7651b-141">ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="7651b-141">Ref locals</span></span>

<span data-ttu-id="7651b-142">假設 `GetContactInformation` 方法是宣告為 ref 傳回值：</span><span class="sxs-lookup"><span data-stu-id="7651b-142">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="7651b-143">傳值方式指派會讀取變數值，並將它指派給新的變數：</span><span class="sxs-lookup"><span data-stu-id="7651b-143">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="7651b-144">上述的指派將 `p` 宣告為區域變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-144">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="7651b-145">其初始值的複製來源，是讀取 `GetContactInformation` 所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="7651b-145">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="7651b-146">對 `p` 的任何後續指派將不會變更 `GetContactInformation` 傳回的變數值。</span><span class="sxs-lookup"><span data-stu-id="7651b-146">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="7651b-147">變數 `p` 不再是所傳回之變數的別名。</span><span class="sxs-lookup"><span data-stu-id="7651b-147">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="7651b-148">您宣告「ref 區域變數」以將別名複製到原始的值。</span><span class="sxs-lookup"><span data-stu-id="7651b-148">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="7651b-149">在下列指派中，`p` 是 `GetContactInformation` 所傳回之變數的別名。</span><span class="sxs-lookup"><span data-stu-id="7651b-149">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="7651b-150">後續 `p` 的使用方式與使用 `GetContactInformation` 傳回的變數相同，因為 `p` 是該變數的別名。</span><span class="sxs-lookup"><span data-stu-id="7651b-150">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="7651b-151">變更 `p` 也會變更 `GetContactInformation` 傳回的變數。</span><span class="sxs-lookup"><span data-stu-id="7651b-151">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="7651b-152">請注意，`ref` 關鍵字是用於區域變數宣告的前面「和」方法呼叫的前面。</span><span class="sxs-lookup"><span data-stu-id="7651b-152">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="7651b-153">您可透過相同方式以參考存取值。</span><span class="sxs-lookup"><span data-stu-id="7651b-153">You can access a value by reference in the same way.</span></span> <span data-ttu-id="7651b-154">在某些情況下，以參考存取值會避免潛在過度浪費資源的複製作業，進而增加效能。</span><span class="sxs-lookup"><span data-stu-id="7651b-154">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="7651b-155">例如，下列陳述式示範了如何定義用於參考值的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="7651b-155">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="7651b-156">請注意，區域變數宣告與第二個範例前的值都會使用 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7651b-156">Note that the `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="7651b-157">無法在這兩個範例內的變數宣告和指派中同時包含 `ref` 關鍵字，會導致編譯器錯誤 CS8172「無法使用值將傳址變數初始化」。</span><span class="sxs-lookup"><span data-stu-id="7651b-157">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="7651b-158">ref 傳回值和 ref 區域變數：範例</span><span class="sxs-lookup"><span data-stu-id="7651b-158">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="7651b-159">下列範例定義 `NumberStore` 類別，以儲存整數值的陣列。</span><span class="sxs-lookup"><span data-stu-id="7651b-159">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="7651b-160">`FindNumber` 方法會以傳址方式傳回第一個數字，而此數字大於或等於傳遞為引數的數字。</span><span class="sxs-lookup"><span data-stu-id="7651b-160">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="7651b-161">如果數字未大於或等於引數，則方法會在索引 0 傳回數字。</span><span class="sxs-lookup"><span data-stu-id="7651b-161">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="7651b-162">下列範例會呼叫 `NumberStore.FindNumber` 方法來擷取大於或等於 16 的第一個值。</span><span class="sxs-lookup"><span data-stu-id="7651b-162">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="7651b-163">呼叫者接著會將方法所傳回的值加倍。</span><span class="sxs-lookup"><span data-stu-id="7651b-163">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="7651b-164">如範例輸出所示，這項變更會反映在 `NumberStore` 執行個體的陣列元素值中。</span><span class="sxs-lookup"><span data-stu-id="7651b-164">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="7651b-165">如果不支援參考傳回值，則通常是透過傳回陣列元素和其值的索引來執行這類作業。</span><span class="sxs-lookup"><span data-stu-id="7651b-165">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="7651b-166">呼叫者接著可以使用這個索引，來修改不同方法呼叫中的值。</span><span class="sxs-lookup"><span data-stu-id="7651b-166">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="7651b-167">不過，呼叫者也可以修改要存取的索引，也可能修改其他陣列值。</span><span class="sxs-lookup"><span data-stu-id="7651b-167">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="7651b-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7651b-168">See also</span></span>

[<span data-ttu-id="7651b-169">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="7651b-169">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="7651b-170">具備實值型別的參考語意</span><span class="sxs-lookup"><span data-stu-id="7651b-170">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
