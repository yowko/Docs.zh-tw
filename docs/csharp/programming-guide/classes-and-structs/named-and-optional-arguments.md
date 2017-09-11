---
title: "具名和選擇性引數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: a7f05e3e0b19bf6457989f8db2b46741cf6b28c1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/29/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="4cf97-102">具名和選擇性引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4cf97-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="4cf97-103"> 介紹具名和選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="4cf97-104">「具名引數」可讓您使用參數的名稱而非使用參數清單中的參數位置來關聯引數，指定特定參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="4cf97-105">「選擇性引數」可讓您省略某些參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="4cf97-106">這兩種技巧都可以搭配方法、索引子、建構函式和委派使用。</span><span class="sxs-lookup"><span data-stu-id="4cf97-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="4cf97-107">當您使用具名和選擇性引數時，會依照引數清單中的引數顯示順序來評估引數，不是依照參數清單的順序。</span><span class="sxs-lookup"><span data-stu-id="4cf97-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="4cf97-108">具名和選擇性參數一起使用時，可讓您只為選擇性參數清單中的幾個參數提供引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="4cf97-109">這項功能大幅有助呼叫 COM 介面，例如 Microsoft Office Automation API。</span><span class="sxs-lookup"><span data-stu-id="4cf97-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="4cf97-110">具名引數</span><span class="sxs-lookup"><span data-stu-id="4cf97-110">Named Arguments</span></span>  
 <span data-ttu-id="4cf97-111">具名引數讓您不需要記住或查詢呼叫方法參數清單中的參數順序。</span><span class="sxs-lookup"><span data-stu-id="4cf97-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="4cf97-112">參數名稱可以指定每個引數的參數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="4cf97-113">例如，依函式定義的順序來傳送位置的體重和身高引數，可以標準方式呼叫計算身體質量指數 (BMI) 的函式。</span><span class="sxs-lookup"><span data-stu-id="4cf97-113">For example, a function that calculates body mass index (BMI) can be called in the standard way by sending arguments for weight and height by position, in the order defined by the function.</span></span>  
  
 `CalculateBMI(123, 64);`  
  
 <span data-ttu-id="4cf97-114">如果您不記得參數的順序，但知道它們的名稱，您可以依照任何順序傳送引數：體重先或身高先。</span><span class="sxs-lookup"><span data-stu-id="4cf97-114">If you do not remember the order of the parameters but you do know their names, you can send the arguments in either order, weight first or height first.</span></span>  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 <span data-ttu-id="4cf97-115">具名引數也藉由識別每個引數所代表的意義，改善程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="4cf97-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span>  
  
 <span data-ttu-id="4cf97-116">具名引數可以接在位置引數後面，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4cf97-116">A named argument can follow positional arguments, as shown here.</span></span>  
  
 `CalculateBMI(123, height: 64);`  
  
 <span data-ttu-id="4cf97-117">但位置引數不能接在具名引數後面。</span><span class="sxs-lookup"><span data-stu-id="4cf97-117">However, a positional argument cannot follow a named argument.</span></span> <span data-ttu-id="4cf97-118">下列陳述式會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cf97-118">The following statement causes a compiler error.</span></span>  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a><span data-ttu-id="4cf97-119">範例</span><span class="sxs-lookup"><span data-stu-id="4cf97-119">Example</span></span>  
 <span data-ttu-id="4cf97-120">下列程式碼會實作本節的範例。</span><span class="sxs-lookup"><span data-stu-id="4cf97-120">The following code implements the examples from this section.</span></span>  
  
 <span data-ttu-id="4cf97-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4cf97-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span></span>  
  
## <a name="optional-arguments"></a><span data-ttu-id="4cf97-122">選擇性引數</span><span class="sxs-lookup"><span data-stu-id="4cf97-122">Optional Arguments</span></span>  
 <span data-ttu-id="4cf97-123">方法、建構函式、索引子或委派的定義可以指定其參數為必要項目或選擇項目。</span><span class="sxs-lookup"><span data-stu-id="4cf97-123">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="4cf97-124">任何呼叫都必須提供所有必要參數的引數，但可以省略選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-124">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="4cf97-125">每個選擇性參數都有預設值，為其定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="4cf97-125">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="4cf97-126">如不傳送該參數的任何引數，則使用預設值。</span><span class="sxs-lookup"><span data-stu-id="4cf97-126">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="4cf97-127">預設值必須是下列其中一個運算式類型︰</span><span class="sxs-lookup"><span data-stu-id="4cf97-127">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="4cf97-128">常數運算式；</span><span class="sxs-lookup"><span data-stu-id="4cf97-128">a constant expression;</span></span>  
  
-   <span data-ttu-id="4cf97-129">`new ValType()` 形式的運算式，其中 `ValType` 是實值型別，例如 [enum](../../../csharp/language-reference/keywords/enum.md) 或 [struct](../../../csharp/programming-guide/classes-and-structs/structs.md)；</span><span class="sxs-lookup"><span data-stu-id="4cf97-129">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="4cf97-130">[default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) 形式的運算式，其中 `ValType` 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="4cf97-130">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="4cf97-131">選擇性參數是定義在參數清單的結尾，在任何必要參數之後。</span><span class="sxs-lookup"><span data-stu-id="4cf97-131">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="4cf97-132">如果呼叫端為任何一個連續的選擇性參數提供引數，它就必須提供所有前面選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-132">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="4cf97-133">不支援引數清單使用逗點分隔間距。</span><span class="sxs-lookup"><span data-stu-id="4cf97-133">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="4cf97-134">例如，在下列程式碼中，執行個體方法 `ExampleMethod` 使用一個必要參數及兩個選擇性參數來定義。</span><span class="sxs-lookup"><span data-stu-id="4cf97-134">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 <span data-ttu-id="4cf97-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4cf97-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="4cf97-136">以下呼叫 `ExampleMethod` 子句會造成編譯器錯誤，因為提供了第三個參數的引數，但未提供第二個參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-136">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="4cf97-137">不過，如果您知道第三個參數的名稱，您可以使用具名引數來完成工作。</span><span class="sxs-lookup"><span data-stu-id="4cf97-137">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="4cf97-138">IntelliSense 使用括弧表示選擇性參數，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="4cf97-138">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="4cf97-139">![IntelliSense 對於 ExampleMethod 方法的快速諮詢。](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="4cf97-139">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="4cf97-140">ExampleMethod 的選擇性參數</span><span class="sxs-lookup"><span data-stu-id="4cf97-140">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cf97-141">您也可以使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 類別來宣告選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-141">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="4cf97-142">`OptionalAttribute` 參數不需要預設值。</span><span class="sxs-lookup"><span data-stu-id="4cf97-142">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cf97-143">範例</span><span class="sxs-lookup"><span data-stu-id="4cf97-143">Example</span></span>  
 <span data-ttu-id="4cf97-144">在下例中，`ExampleClass` 的建構函式有一個參數，而它是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4cf97-144">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="4cf97-145">`ExampleMethod` 執行個體方法有一個必要參數 `required` 和兩個選擇性參數 `optionalstr` 及 `optionalint`。</span><span class="sxs-lookup"><span data-stu-id="4cf97-145">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="4cf97-146">`Main` 中的程式碼會示範叫用建構函式和方法的不同方式。</span><span class="sxs-lookup"><span data-stu-id="4cf97-146">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 <span data-ttu-id="4cf97-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4cf97-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span></span>  
  
## <a name="com-interfaces"></a><span data-ttu-id="4cf97-148">COM 介面</span><span class="sxs-lookup"><span data-stu-id="4cf97-148">COM Interfaces</span></span>  
 <span data-ttu-id="4cf97-149">具名和選擇性引數以及對動態物件和其他增強功能的支援，大幅改善與 COM API 的互通性，例如 Office Automation API。</span><span class="sxs-lookup"><span data-stu-id="4cf97-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="4cf97-150">例如，Microsoft Office Excel [Range Interface](http://go.microsoft.com/fwlink/?LinkId=148196) (範圍介面) 的 [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) 方法有七個參數，它們都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-150">For example, the [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) method in the Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="4cf97-151">下圖會顯示這些參數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-151">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="4cf97-152">![IntelliSense 對於 AutoFormat 方法的快速諮詢。](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="4cf97-152">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="4cf97-153">AutoFormat 參數</span><span class="sxs-lookup"><span data-stu-id="4cf97-153">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="4cf97-154">在 C# 3.0 和舊版中，每個參數都需要引數，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="4cf97-154">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 <span data-ttu-id="4cf97-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="4cf97-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span></span>  
  
 <span data-ttu-id="4cf97-156">不過，您可以使用 C# 4.0 引入的具名和選擇性引數，大幅簡化對 `AutoFormat` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4cf97-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="4cf97-157">如果您不想變更參數的預設值，具名和選擇性引數可讓您省略選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="4cf97-158">在下列的呼叫中，只指定七個參數其中之一的值。</span><span class="sxs-lookup"><span data-stu-id="4cf97-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 <span data-ttu-id="4cf97-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="4cf97-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="4cf97-160">如需詳細資訊和範例，請參閱[如何︰在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)和[如何︰使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="4cf97-160">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="4cf97-161">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="4cf97-161">Overload Resolution</span></span>  
 <span data-ttu-id="4cf97-162">使用具名和選擇性引數會以下列方式影響多載解析︰</span><span class="sxs-lookup"><span data-stu-id="4cf97-162">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="4cf97-163">如果每個參數都是選擇性或為依名稱或位置對應要呼叫之陳述式的單一引數，且該引數可以轉換成參數的型別，則方法、索引子或建構函式就是執行的候選項目。</span><span class="sxs-lookup"><span data-stu-id="4cf97-163">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="4cf97-164">如果找到多個候選項目，則慣用轉換的多載解析規則會套用至明確指定的引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-164">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="4cf97-165">會忽略選擇性參數的省略引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-165">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="4cf97-166">如果兩個候選項目的評斷結果一樣好，則偏向沒有選擇性參數的候選項目，其會在呼叫中省略引數。</span><span class="sxs-lookup"><span data-stu-id="4cf97-166">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="4cf97-167">這是多載解析一般偏好參數較少之候選項目的結果。</span><span class="sxs-lookup"><span data-stu-id="4cf97-167">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4cf97-168">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4cf97-168">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4cf97-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cf97-169">See Also</span></span>  
 <span data-ttu-id="4cf97-170">[如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="4cf97-170">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="4cf97-171">[使用動態型別](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="4cf97-171">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="4cf97-172">[使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span><span class="sxs-lookup"><span data-stu-id="4cf97-172">[Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span></span>  
 [<span data-ttu-id="4cf97-173">使用索引子</span><span class="sxs-lookup"><span data-stu-id="4cf97-173">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)

