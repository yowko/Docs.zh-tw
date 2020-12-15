---
title: 具名和選擇性引數 - C# 程式設計手冊
description: 'C # 中的具名引數會依名稱指定引數，而不是使用位置。 可以省略選擇性引數。'
ms.date: 09/25/2020
ms.custom: contperf-fy21q1
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: bb79d956124a610bac0de6825c1f42655789e98d
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513103"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="4604a-104">具名和選擇性引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4604a-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="4604a-105">C# 4 引進具名和選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="4604a-106">*具名引數* 可讓您指定參數的引數，方法是將引數與其名稱比對，而不是在參數清單中的位置。</span><span class="sxs-lookup"><span data-stu-id="4604a-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="4604a-107">「選擇性引數」可讓您省略某些參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="4604a-108">這兩種技巧都可以搭配方法、索引子、建構函式和委派使用。</span><span class="sxs-lookup"><span data-stu-id="4604a-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="4604a-109">當您使用具名和選擇性引數時，會依照引數清單中的引數顯示順序來評估引數，不是依照參數清單的順序。</span><span class="sxs-lookup"><span data-stu-id="4604a-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="4604a-110">具名引數和選擇性參數可讓您為選取的參數提供引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="4604a-111">這項功能可大幅簡化對 COM 介面的呼叫，例如 Microsoft Office Automation Api。</span><span class="sxs-lookup"><span data-stu-id="4604a-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="4604a-112">具名引數</span><span class="sxs-lookup"><span data-stu-id="4604a-112">Named Arguments</span></span>

<span data-ttu-id="4604a-113">具名引數讓您無法比對所呼叫方法的參數清單中的參數順序。</span><span class="sxs-lookup"><span data-stu-id="4604a-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="4604a-114">參數名稱可以指定每個引數的參數。</span><span class="sxs-lookup"><span data-stu-id="4604a-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="4604a-115">例如，將訂單詳細資料列印 (例如，賣方名稱、訂單編號 & 產品名稱) 的函式，可以藉由依函式定義的順序來傳送引數（依位置）來呼叫。</span><span class="sxs-lookup"><span data-stu-id="4604a-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="4604a-116">如果您不記得參數的順序，但知道它們的名稱，您可以依任何順序傳送引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="4604a-117">具名引數也藉由識別每個引數所代表的意義，改善程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="4604a-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="4604a-118">在下列範例方法中， `sellerName` 不能是 null 或空白字元。</span><span class="sxs-lookup"><span data-stu-id="4604a-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="4604a-119">因為 `sellerName` 和 `productName` 都是字串類型，所以可以使用具名引數來區分兩者，並減少讀取程式碼的任何人的混淆，而不是依位置傳送引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="4604a-120">在下列情況下，具名引數在與位置引數搭配使用時有效：</span><span class="sxs-lookup"><span data-stu-id="4604a-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="4604a-121">它們的後面沒有任何位置引數，或</span><span class="sxs-lookup"><span data-stu-id="4604a-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="4604a-122">_從 C# 7.2 開始_，它們會用於正確的位置。</span><span class="sxs-lookup"><span data-stu-id="4604a-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="4604a-123">在下列範例中，`orderNum` 參數位於正確位置，但未明確命名。</span><span class="sxs-lookup"><span data-stu-id="4604a-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="4604a-124">遵循任何非順序具名引數的位置引數無效。</span><span class="sxs-lookup"><span data-stu-id="4604a-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="4604a-125">範例</span><span class="sxs-lookup"><span data-stu-id="4604a-125">Example</span></span>

<span data-ttu-id="4604a-126">下列程式碼會實作本節的範例，以及一些其他範例。</span><span class="sxs-lookup"><span data-stu-id="4604a-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="4604a-127">選擇性引數</span><span class="sxs-lookup"><span data-stu-id="4604a-127">Optional Arguments</span></span>

<span data-ttu-id="4604a-128">方法、函式、索引子或委派的定義可以指定其參數為必要或選擇性。</span><span class="sxs-lookup"><span data-stu-id="4604a-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="4604a-129">任何呼叫都必須提供所有必要參數的引數，但可以省略選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="4604a-130">每個選擇性參數都有預設值，為其定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="4604a-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="4604a-131">如不傳送該參數的任何引數，則使用預設值。</span><span class="sxs-lookup"><span data-stu-id="4604a-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="4604a-132">預設值必須是下列其中一個運算式類型︰</span><span class="sxs-lookup"><span data-stu-id="4604a-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="4604a-133">常數運算式；</span><span class="sxs-lookup"><span data-stu-id="4604a-133">a constant expression;</span></span>  
- <span data-ttu-id="4604a-134">`new ValType()` 形式的運算式，其中 `ValType` 是實值型別，例如 [enum](../../language-reference/builtin-types/enum.md) 或 [struct](../../language-reference/builtin-types/struct.md)；</span><span class="sxs-lookup"><span data-stu-id="4604a-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="4604a-135">[default(ValType)](../../language-reference/operators/default.md) 形式的運算式，其中 `ValType` 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="4604a-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="4604a-136">選擇性參數是定義在參數清單的結尾，在任何必要參數之後。</span><span class="sxs-lookup"><span data-stu-id="4604a-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="4604a-137">如果呼叫端為任何一個連續的選擇性參數提供引數，它就必須提供所有前面選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="4604a-138">不支援引數清單中以逗號分隔的間距。</span><span class="sxs-lookup"><span data-stu-id="4604a-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="4604a-139">例如，在下列程式碼中，執行個體方法 `ExampleMethod` 使用一個必要參數及兩個選擇性參數來定義。</span><span class="sxs-lookup"><span data-stu-id="4604a-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="4604a-140">以下呼叫 `ExampleMethod` 子句會造成編譯器錯誤，因為提供了第三個參數的引數，但未提供第二個參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="4604a-141">不過，如果您知道第三個參數的名稱，您可以使用具名引數來完成工作。</span><span class="sxs-lookup"><span data-stu-id="4604a-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="4604a-142">IntelliSense 使用括弧表示選擇性參數，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="4604a-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![顯示 ExampleMethod 方法之 IntelliSense 快速諮詢的螢幕擷取畫面。](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="4604a-144">您也可以使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 類別來宣告選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4604a-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="4604a-145">`OptionalAttribute` 參數不需要預設值。</span><span class="sxs-lookup"><span data-stu-id="4604a-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="4604a-146">範例</span><span class="sxs-lookup"><span data-stu-id="4604a-146">Example</span></span>

<span data-ttu-id="4604a-147">在下例中，`ExampleClass` 的建構函式有一個參數，而它是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4604a-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="4604a-148">`ExampleMethod` 執行個體方法有一個必要參數 `required` 和兩個選擇性參數 `optionalstr` 及 `optionalint`。</span><span class="sxs-lookup"><span data-stu-id="4604a-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="4604a-149">`Main` 中的程式碼會示範叫用建構函式和方法的不同方式。</span><span class="sxs-lookup"><span data-stu-id="4604a-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="4604a-150">上述程式碼顯示未正確套用選擇性參數的一些範例。</span><span class="sxs-lookup"><span data-stu-id="4604a-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="4604a-151">第一個說明必須為第一個參數提供引數，這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="4604a-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="4604a-152">COM 介面</span><span class="sxs-lookup"><span data-stu-id="4604a-152">COM Interfaces</span></span>

<span data-ttu-id="4604a-153">指名的和選擇性引數，以及動態物件的支援，可大幅改善與 COM Api 的互通性，例如 Office Automation Api。</span><span class="sxs-lookup"><span data-stu-id="4604a-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="4604a-154">例如，Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> 介面的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> 方法有七個參數，都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4604a-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="4604a-155">下圖會顯示這些參數：</span><span class="sxs-lookup"><span data-stu-id="4604a-155">These parameters are shown in the following illustration:</span></span>

![顯示 AutoFormat 方法之 IntelliSense 快速諮詢的螢幕擷取畫面。](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="4604a-157">在 C# 3.0 和舊版中，每個參數都需要引數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="4604a-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="4604a-158">不過，您可以使用 C# 4.0 引入的具名和選擇性引數，大幅簡化對 `AutoFormat` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4604a-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="4604a-159">如果您不想要變更參數的預設值，則具名引數和選擇性引數可讓您省略選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="4604a-160">在下列的呼叫中，只指定七個參數其中之一的值。</span><span class="sxs-lookup"><span data-stu-id="4604a-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="4604a-161">如需詳細資訊和範例，請參閱 [如何在 office 程式設計中使用指名的和選擇性引數](./how-to-use-named-and-optional-arguments-in-office-programming.md) ，以及 [如何使用 c # 功能存取 office interop 物件](../interop/how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="4604a-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="4604a-162">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="4604a-162">Overload Resolution</span></span>

<span data-ttu-id="4604a-163">使用具名和選擇性引數會以下列方式影響多載解析︰</span><span class="sxs-lookup"><span data-stu-id="4604a-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="4604a-164">如果每個參數都是選擇性或為依名稱或位置對應要呼叫之陳述式的單一引數，且該引數可以轉換成參數的型別，則方法、索引子或建構函式就是執行的候選項目。</span><span class="sxs-lookup"><span data-stu-id="4604a-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="4604a-165">如果找到多個候選項目，則慣用轉換的多載解析規則會套用至明確指定的引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="4604a-166">會忽略選擇性參數的省略引數。</span><span class="sxs-lookup"><span data-stu-id="4604a-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="4604a-167">如果有兩個候選項目被判定為同樣的情況，喜好設定會移至沒有選擇性參數的候選項目，而在呼叫中省略這些參數。</span><span class="sxs-lookup"><span data-stu-id="4604a-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="4604a-168">多載解析通常偏好擁有較少參數的候選項目。</span><span class="sxs-lookup"><span data-stu-id="4604a-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="4604a-169">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4604a-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
