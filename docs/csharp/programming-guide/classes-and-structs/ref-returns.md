---
title: "ref 傳回值和 ref 區域變數 (C# 手冊)"
description: "了解如何定義和使用 ref 傳回值和 ref 區域變數值"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="1ac05-103">ref 傳回值和 ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="1ac05-103">Ref returns and ref locals</span></span>

<span data-ttu-id="1ac05-104">從 C# 7 開始，C# 支援參考傳回值 (ref 傳回值)。</span><span class="sxs-lookup"><span data-stu-id="1ac05-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="1ac05-105">參考傳回值允許方法將物件參考而非值傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="1ac05-105">A reference return value allows a method to return a reference to an object, rather than a value, back to a caller.</span></span> <span data-ttu-id="1ac05-106">呼叫者接著可以選擇將傳回的物件視為已傳回，就像已以傳值方式或以傳址方式傳回它一樣。</span><span class="sxs-lookup"><span data-stu-id="1ac05-106">The caller can then choose to treat the returned object returned as if it were returned by value or by reference.</span></span> <span data-ttu-id="1ac05-107">呼叫者處理為參考而非值，並以傳址方式傳回的值，即 ref 區域變數。</span><span class="sxs-lookup"><span data-stu-id="1ac05-107">A value returned by reference that the caller handles as a reference rather than a value is a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="1ac05-108">何謂參考傳回值？</span><span class="sxs-lookup"><span data-stu-id="1ac05-108">What is a reference return value?</span></span>

<span data-ttu-id="1ac05-109">大部分的開發人員都熟悉「以傳址方式」將引數傳遞給已呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1ac05-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="1ac05-110">已呼叫方法的引數清單包含以傳址方式傳遞的值，而且已呼叫方法對其值進行的任何變更都會傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="1ac05-110">A called method's argument list includes a value passed by reference, and any changes made to its value by the called method are returned to the caller.</span></span> <span data-ttu-id="1ac05-111">「參考傳回值」則相反：</span><span class="sxs-lookup"><span data-stu-id="1ac05-111">A *reference return value* is the opposite:</span></span>

- <span data-ttu-id="1ac05-112">已呼叫方法的傳回值 (而非傳遞給它的引數) 是參考。</span><span class="sxs-lookup"><span data-stu-id="1ac05-112">The called method's return value, rather than an argument passed to it, is a reference.</span></span>

- <span data-ttu-id="1ac05-113">呼叫者 (而非已呼叫方法) 可以修改方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-113">The caller, rather than the called method, can modify the value returned by the method.</span></span>

- <span data-ttu-id="1ac05-114">方法的呼叫者傳回值修改會反映在呼叫其方法之物件的狀態中，而不是反映在呼叫者之物件狀態中的引數修改。</span><span class="sxs-lookup"><span data-stu-id="1ac05-114">Instead of modifications to the argument that are reflected in state of the object on the caller, modifications to the method's return value by the caller are reflected in the state of the object whose method was called.</span></span>

<span data-ttu-id="1ac05-115">參考傳回值可以產生更精簡的程式碼，以及允許物件只公開個別資料項目，例如呼叫者感興趣的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="1ac05-115">Reference return values can produce more compact code, as well as allow an object to expose only the individual data items, such as an array element, that are of interest to the caller.</span></span> <span data-ttu-id="1ac05-116">這可降低呼叫者不小心修改物件狀態的可能性。</span><span class="sxs-lookup"><span data-stu-id="1ac05-116">This reduces the likelihood that the caller will inadvertently modify the object's state.</span></span>

<span data-ttu-id="1ac05-117">方法可傳回為參考傳回值的值有一些限制。</span><span class="sxs-lookup"><span data-stu-id="1ac05-117">There are some restrictions on the value that a method can return as a reference return value.</span></span> <span data-ttu-id="1ac05-118">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="1ac05-118">These include:</span></span>

- <span data-ttu-id="1ac05-119">傳回值不能是 `void`。</span><span class="sxs-lookup"><span data-stu-id="1ac05-119">The return value cannot be `void`.</span></span> <span data-ttu-id="1ac05-120">嘗試定義具有 `void` 參考傳回值的方法會產生編譯器錯誤 CS1547「在此內容中不可使用關鍵字 'void'」。</span><span class="sxs-lookup"><span data-stu-id="1ac05-120">Attempting to define a method with a `void` reference return value generates compiler error CS1547, "Keyword 'void' cannot be used in this context."</span></span>
 
- <span data-ttu-id="1ac05-121">傳回值不能是傳回它之方法中的區域變數；它的範圍必須位在傳回它的方法外部。</span><span class="sxs-lookup"><span data-stu-id="1ac05-121">The return value cannot be a local variable in the method that returns it; it must have a scope that is outside the method that returns it.</span></span> <span data-ttu-id="1ac05-122">它可以是類別的執行個體或靜態欄位，也可以是傳遞給方法的引數。</span><span class="sxs-lookup"><span data-stu-id="1ac05-122">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="1ac05-123">嘗試傳回區域變數會產生編譯器錯誤 CS8168「無法以傳址方式傳回本機 'obj'，因為其非參考本機」。</span><span class="sxs-lookup"><span data-stu-id="1ac05-123">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="1ac05-124">傳回值不能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="1ac05-124">The return value cannot be a `null`.</span></span> <span data-ttu-id="1ac05-125">嘗試傳回 `null` 會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。</span><span class="sxs-lookup"><span data-stu-id="1ac05-125">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="1ac05-126">如果具有 ref 傳回值的方法需要傳回 Null 值，您可以傳回參考型別的 Null (未具現化) 值或實值型別的[可為 Null 的類型](../nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac05-126">If a method with a ref return needs to return a null value, you can either return a null (uninstantiated) value for a reference type or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="1ac05-127">傳回值不能是常數、列舉成員，或是 `class` 或 `struct` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ac05-127">The return value cannot be a constant, an enumeration member, or a property of a `class` or `struct`.</span></span> <span data-ttu-id="1ac05-128">嘗試傳回這些會產生編譯器錯誤 CS8156「無法在此內容中使用運算式，因為其可能不會以傳址方式傳回」。</span><span class="sxs-lookup"><span data-stu-id="1ac05-128">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="1ac05-129">此外，因為非同步方法可能會在完成執行之前傳回，但仍未知其傳回值，所以非同步方法並不允許參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-129">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="1ac05-130">定義 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="1ac05-130">Defining a ref return value</span></span>

<span data-ttu-id="1ac05-131">將 [ref](../../language-reference/keywords/ref.md) 關鍵字新增至方法簽章的傳回型別，即可定義 ref 傳回值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-131">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="1ac05-132">例如，下列簽章指出 `GetContactInformation` 屬性會將 `Person` 物件的參考傳回給呼叫者：</span><span class="sxs-lookup"><span data-stu-id="1ac05-132">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="1ac05-133">此外，方法主體中每個 [return](../../language-reference/keywords/return.md) 陳述式所傳回的物件名稱前面必須加上 [ref](../../language-reference/keywords/ref.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1ac05-133">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="1ac05-134">例如，下列 `return` 陳述式會以傳址方式傳回名為 `p` 的 `Person` 物件：</span><span class="sxs-lookup"><span data-stu-id="1ac05-134">For example, the following `return` statement returns a `Person` object named `p` by reference:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="1ac05-135">使用 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="1ac05-135">Consuming a ref return value</span></span>

<span data-ttu-id="1ac05-136">呼叫者可以使用兩種方式之一來處理 ref 傳回值：</span><span class="sxs-lookup"><span data-stu-id="1ac05-136">A caller can handle a ref return value in either of two ways:</span></span>

- <span data-ttu-id="1ac05-137">作為從方法以傳值方式傳回的一般值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-137">As an ordinary value returned by value from a method.</span></span> <span data-ttu-id="1ac05-138">呼叫者可以選擇忽略傳回值是參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-138">The caller can choose to ignore that the return value is a reference return value.</span></span> <span data-ttu-id="1ac05-139">在此情況下，對方法呼叫所傳回的值進行的任何變更都不會反映在已呼叫類型的狀態中。</span><span class="sxs-lookup"><span data-stu-id="1ac05-139">In this case, any changes made to the value returned by the method call are not reflected in the state of the called type.</span></span> <span data-ttu-id="1ac05-140">如果傳回值是實值型別，則對方法呼叫所傳回的值進行的任何變更都不會反映在已呼叫類型的狀態中。</span><span class="sxs-lookup"><span data-stu-id="1ac05-140">If the returned value is a value type, any changes made to the value returned by the method call are not reflected in the state of the called type.</span></span>

- <span data-ttu-id="1ac05-141">作為參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-141">As a reference return value.</span></span> <span data-ttu-id="1ac05-142">呼叫者必須定義將參考傳回值指派為 [ref 區域變數](#ref-local)的變數，而且針對方法呼叫所傳回之值的任何變更都會反映在已呼叫類型的狀態中。</span><span class="sxs-lookup"><span data-stu-id="1ac05-142">The caller must define the variable to which the reference return value is assigned as a [ref local](#ref-local), and any changes to the value returned by the method call are reflected in the state of the called type.</span></span> 

## <a name="ref-locals"></a><span data-ttu-id="1ac05-143">ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="1ac05-143">Ref locals</span></span>

<span data-ttu-id="1ac05-144">若要將參考傳回值處理為參考，呼叫者必須使用 `ref` 關鍵字將值宣告為 *ref 區域變數*。</span><span class="sxs-lookup"><span data-stu-id="1ac05-144">To handle the reference return value as a reference, the caller must declare the value to be a *ref local* by using the `ref` keyword.</span></span> <span data-ttu-id="1ac05-145">例如，如果 `Person.GetContactInfomation` 方法所傳回的值是要用作參考，而非值，則方法呼叫會顯示為：</span><span class="sxs-lookup"><span data-stu-id="1ac05-145">For example, if the value returned by the `Person.GetContactInfomation` method is to be consumed as a reference rather than a value, the method call appears as:</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="1ac05-146">請注意，`ref` 關鍵字是用於區域變數宣告的前面「和」方法呼叫的前面。</span><span class="sxs-lookup"><span data-stu-id="1ac05-146">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> <span data-ttu-id="1ac05-147">無法在變數宣告和指派中同時包含 `ref` 關鍵字，會導致編譯器錯誤 CS8172「無法使用值將傳址變數初始化」。</span><span class="sxs-lookup"><span data-stu-id="1ac05-147">Failure to include both `ref` keywords in the variable declaration and assignment results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
<span data-ttu-id="1ac05-148">對方法所傳回 `Person` 物件的後續變更會反映在 `contacts` 物件中。</span><span class="sxs-lookup"><span data-stu-id="1ac05-148">Subsequent changes to the `Person` object returned by the method are reflected in the `contacts` object.</span></span>

<span data-ttu-id="1ac05-149">如果未使用 `ref` 關鍵字將 `p` 定義為 ref 區域變數，則呼叫者對 `p` 進行的任何變更都不會反映在 `contacts` 物件中。</span><span class="sxs-lookup"><span data-stu-id="1ac05-149">If `p` is not defined as a ref local by using the `ref` keyword, any changes made to `p` by the caller are not reflected in the `contacts` object.</span></span>
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="1ac05-150">ref 傳回值和 ref 區域變數：範例</span><span class="sxs-lookup"><span data-stu-id="1ac05-150">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="1ac05-151">下列範例定義 `NumberStore` 類別，以儲存整數值的陣列。</span><span class="sxs-lookup"><span data-stu-id="1ac05-151">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="1ac05-152">`FindNumber` 方法會以傳址方式傳回第一個數字，而此數字大於或等於傳遞為引數的數字。</span><span class="sxs-lookup"><span data-stu-id="1ac05-152">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="1ac05-153">如果數字未大於或等於引數，則方法會在索引 0 傳回數字。</span><span class="sxs-lookup"><span data-stu-id="1ac05-153">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="1ac05-154">下列範例會呼叫 `NumberStore.FindNumber` 方法來擷取大於或等於 16 的第一個值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-154">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="1ac05-155">呼叫者接著會將方法所傳回的值加倍。</span><span class="sxs-lookup"><span data-stu-id="1ac05-155">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="1ac05-156">如範例輸出所示，這項變更會反映在 `NumberStore` 執行個體的陣列元素值中。</span><span class="sxs-lookup"><span data-stu-id="1ac05-156">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="1ac05-157">如果不支援參考傳回值，則通常是透過傳回陣列元素和其值的索引來執行這類作業。</span><span class="sxs-lookup"><span data-stu-id="1ac05-157">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="1ac05-158">呼叫者接著可以使用這個索引，來修改不同方法呼叫中的值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-158">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="1ac05-159">不過，呼叫者也可以修改要存取的索引，也可能修改其他陣列值。</span><span class="sxs-lookup"><span data-stu-id="1ac05-159">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="1ac05-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac05-160">See also</span></span>

[<span data-ttu-id="1ac05-161">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1ac05-161">ref keyword</span></span>](../../language-reference/keywords/ref.md)
