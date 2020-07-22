---
title: 具名和選擇性引數 - C# 程式設計手冊
description: 'C # 中的具名引數會依名稱指定引數，而不是位置。 可以省略選擇性的引數。'
ms.date: 07/20/2015
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
ms.openlocfilehash: 46b9dc23644e68aea2767f2b990fe7f243a4f357
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864978"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="59b3e-104">具名和選擇性引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="59b3e-104">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="59b3e-105">C# 4 引進具名和選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="59b3e-106">「具名引數」\*\* 可讓您使用參數的名稱而非使用參數清單中的參數位置來關聯引數，指定特定參數的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-106">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="59b3e-107">「選擇性引數」\*\* 可讓您省略某些參數的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="59b3e-108">這兩種技巧都可以搭配方法、索引子、建構函式和委派使用。</span><span class="sxs-lookup"><span data-stu-id="59b3e-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="59b3e-109">當您使用具名和選擇性引數時，會依照引數清單中的引數顯示順序來評估引數，不是依照參數清單的順序。</span><span class="sxs-lookup"><span data-stu-id="59b3e-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="59b3e-110">具名和選擇性參數一起使用時，可讓您只為選擇性參數清單中的幾個參數提供引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-110">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="59b3e-111">這項功能大幅有助呼叫 COM 介面，例如 Microsoft Office Automation API。</span><span class="sxs-lookup"><span data-stu-id="59b3e-111">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="59b3e-112">具名引數</span><span class="sxs-lookup"><span data-stu-id="59b3e-112">Named Arguments</span></span>  
 <span data-ttu-id="59b3e-113">具名引數讓您不需要記住或查詢呼叫方法參數清單中的參數順序。</span><span class="sxs-lookup"><span data-stu-id="59b3e-113">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="59b3e-114">參數名稱可以指定每個引數的參數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="59b3e-115">例如，依函式定義的順序來傳送位置的引數，可透過標準方式呼叫可列印訂單詳細資料的函式 (例如，賣方名稱、訂單號碼和產品名稱)。</span><span class="sxs-lookup"><span data-stu-id="59b3e-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="59b3e-116">如果您不記得參數的順序，但知道它們的名稱，則可以依照任何順序傳送引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-116">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="59b3e-117">具名引數也藉由識別每個引數所代表的意義，改善程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="59b3e-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="59b3e-118">在下列範例方法中，`sellerName` 不可以為 Null 或空白字元。</span><span class="sxs-lookup"><span data-stu-id="59b3e-118">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="59b3e-119">因為 `sellerName` 和 `productName` 都是字串類型，所以可以使用具名引數來區分兩者，並減少讀取程式碼的任何人的混淆，而不是依位置傳送引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="59b3e-120">在下列情況下，具名引數在與位置引數搭配使用時有效：</span><span class="sxs-lookup"><span data-stu-id="59b3e-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="59b3e-121">它們的後面沒有任何位置引數，或</span><span class="sxs-lookup"><span data-stu-id="59b3e-121">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="59b3e-122">_從 C# 7.2 開始_，它們會用於正確的位置。</span><span class="sxs-lookup"><span data-stu-id="59b3e-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="59b3e-123">在下列範例中，`orderNum` 參數位於正確位置，但未明確命名。</span><span class="sxs-lookup"><span data-stu-id="59b3e-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="59b3e-124">遵循任何順序不正確的引數的位置引數無效。</span><span class="sxs-lookup"><span data-stu-id="59b3e-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="59b3e-125">範例</span><span class="sxs-lookup"><span data-stu-id="59b3e-125">Example</span></span>  
 <span data-ttu-id="59b3e-126">下列程式碼會實作本節的範例，以及一些其他範例。</span><span class="sxs-lookup"><span data-stu-id="59b3e-126">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="59b3e-127">選擇性引數</span><span class="sxs-lookup"><span data-stu-id="59b3e-127">Optional Arguments</span></span>  
 <span data-ttu-id="59b3e-128">方法、建構函式、索引子或委派的定義可以指定其參數為必要項目或選擇項目。</span><span class="sxs-lookup"><span data-stu-id="59b3e-128">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="59b3e-129">任何呼叫都必須提供所有必要參數的引數，但可以省略選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="59b3e-130">每個選擇性參數都有預設值，為其定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="59b3e-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="59b3e-131">如不傳送該參數的任何引數，則使用預設值。</span><span class="sxs-lookup"><span data-stu-id="59b3e-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="59b3e-132">預設值必須是下列其中一個運算式類型︰</span><span class="sxs-lookup"><span data-stu-id="59b3e-132">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="59b3e-133">常數運算式；</span><span class="sxs-lookup"><span data-stu-id="59b3e-133">a constant expression;</span></span>  
  
- <span data-ttu-id="59b3e-134">`new ValType()` 形式的運算式，其中 `ValType` 是實值型別，例如 [enum](../../language-reference/builtin-types/enum.md) 或 [struct](../../language-reference/builtin-types/struct.md)；</span><span class="sxs-lookup"><span data-stu-id="59b3e-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>  
  
- <span data-ttu-id="59b3e-135">[default(ValType)](../../language-reference/operators/default.md) 形式的運算式，其中 `ValType` 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="59b3e-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="59b3e-136">選擇性參數是定義在參數清單的結尾，在任何必要參數之後。</span><span class="sxs-lookup"><span data-stu-id="59b3e-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="59b3e-137">如果呼叫端為任何一個連續的選擇性參數提供引數，它就必須提供所有前面選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="59b3e-138">不支援引數清單使用逗點分隔間距。</span><span class="sxs-lookup"><span data-stu-id="59b3e-138">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="59b3e-139">例如，在下列程式碼中，執行個體方法 `ExampleMethod` 使用一個必要參數及兩個選擇性參數來定義。</span><span class="sxs-lookup"><span data-stu-id="59b3e-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="59b3e-140">以下呼叫 `ExampleMethod` 子句會造成編譯器錯誤，因為提供了第三個參數的引數，但未提供第二個參數的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="59b3e-141">不過，如果您知道第三個參數的名稱，您可以使用具名引數來完成工作。</span><span class="sxs-lookup"><span data-stu-id="59b3e-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="59b3e-142">IntelliSense 使用括弧表示選擇性參數，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="59b3e-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![顯示 ExampleMethod 方法之 IntelliSense 快速諮詢的螢幕擷取畫面。](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> <span data-ttu-id="59b3e-144">您也可以使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 類別來宣告選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="59b3e-145">`OptionalAttribute` 參數不需要預設值。</span><span class="sxs-lookup"><span data-stu-id="59b3e-145">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b3e-146">範例</span><span class="sxs-lookup"><span data-stu-id="59b3e-146">Example</span></span>  
 <span data-ttu-id="59b3e-147">在下例中，`ExampleClass` 的建構函式有一個參數，而它是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="59b3e-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="59b3e-148">`ExampleMethod` 執行個體方法有一個必要參數 `required` 和兩個選擇性參數 `optionalstr` 及 `optionalint`。</span><span class="sxs-lookup"><span data-stu-id="59b3e-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="59b3e-149">`Main` 中的程式碼會示範叫用建構函式和方法的不同方式。</span><span class="sxs-lookup"><span data-stu-id="59b3e-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="59b3e-150">COM 介面</span><span class="sxs-lookup"><span data-stu-id="59b3e-150">COM Interfaces</span></span>  
 <span data-ttu-id="59b3e-151">具名和選擇性引數以及對動態物件和其他增強功能的支援，大幅改善與 COM API 的互通性，例如 Office Automation API。</span><span class="sxs-lookup"><span data-stu-id="59b3e-151">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="59b3e-152">例如，Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> 介面的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> 方法有七個參數，都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-152">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="59b3e-153">下圖會顯示這些參數：</span><span class="sxs-lookup"><span data-stu-id="59b3e-153">These parameters are shown in the following illustration:</span></span>  
  
 ![顯示 AutoFormat 方法之 IntelliSense 快速諮詢的螢幕擷取畫面。](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="59b3e-155">在 C# 3.0 和舊版中，每個參數都需要引數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="59b3e-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="59b3e-156">不過，您可以使用 C# 4.0 引入的具名和選擇性引數，大幅簡化對 `AutoFormat` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="59b3e-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="59b3e-157">如果您不想變更參數的預設值，具名和選擇性引數可讓您省略選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="59b3e-158">在下列的呼叫中，只指定七個參數其中之一的值。</span><span class="sxs-lookup"><span data-stu-id="59b3e-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="59b3e-159">如需詳細資訊和範例，請參閱[如何在 Office 程式設計中使用命名和選擇性引數](./how-to-use-named-and-optional-arguments-in-office-programming.md)和[如何使用 c # 功能存取 Office interop 物件](../interop/how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="59b3e-159">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="59b3e-160">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="59b3e-160">Overload Resolution</span></span>  
 <span data-ttu-id="59b3e-161">使用具名和選擇性引數會以下列方式影響多載解析︰</span><span class="sxs-lookup"><span data-stu-id="59b3e-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="59b3e-162">如果每個參數都是選擇性或為依名稱或位置對應要呼叫之陳述式的單一引數，且該引數可以轉換成參數的型別，則方法、索引子或建構函式就是執行的候選項目。</span><span class="sxs-lookup"><span data-stu-id="59b3e-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="59b3e-163">如果找到多個候選項目，則慣用轉換的多載解析規則會套用至明確指定的引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="59b3e-164">會忽略選擇性參數的省略引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="59b3e-165">如果兩個候選項目的評斷結果一樣好，則偏向沒有選擇性參數的候選項目，其會在呼叫中省略引數。</span><span class="sxs-lookup"><span data-stu-id="59b3e-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="59b3e-166">這是多載解析一般偏好參數較少之候選項目的結果。</span><span class="sxs-lookup"><span data-stu-id="59b3e-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="59b3e-167">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="59b3e-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59b3e-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59b3e-168">See also</span></span>

- [<span data-ttu-id="59b3e-169">如何在 Office 程式設計中使用具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="59b3e-169">How to use named and optional arguments in Office programming</span></span>](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="59b3e-170">使用動態類型</span><span class="sxs-lookup"><span data-stu-id="59b3e-170">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="59b3e-171">使用建構函式</span><span class="sxs-lookup"><span data-stu-id="59b3e-171">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="59b3e-172">使用索引子</span><span class="sxs-lookup"><span data-stu-id="59b3e-172">Using Indexers</span></span>](../indexers/using-indexers.md)
