---
title: "使用動態類型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
caps.latest.revision: 30
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 36e10ef6a63aae2e901be50b9286370caec50e6a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-type-dynamic-c-programming-guide"></a><span data-ttu-id="811da-102">使用動態類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="811da-102">Using Type dynamic (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="811da-103"> 引進一種新類型 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="811da-103"> introduces a new type, `dynamic`.</span></span> <span data-ttu-id="811da-104">此類型是靜態類型，但 `dynamic` 類型的物件會略過靜態類型檢查。</span><span class="sxs-lookup"><span data-stu-id="811da-104">The type is a static type, but an object of type `dynamic` bypasses static type checking.</span></span> <span data-ttu-id="811da-105">在大多數情況下，其運作會像是具有 `object` 類型。</span><span class="sxs-lookup"><span data-stu-id="811da-105">In most cases, it functions like it has type `object`.</span></span> <span data-ttu-id="811da-106">在編譯時期，會假設類型為 `dynamic` 的項目能夠支援所有作業。</span><span class="sxs-lookup"><span data-stu-id="811da-106">At compile time, an element that is typed as `dynamic` is assumed to support any operation.</span></span> <span data-ttu-id="811da-107">因此，您無須考慮物件是從 COM API、動態語言 (例如 IronPython)、HTML 文件物件模型 (DOM)、反映或是程式其他地方取得其值。</span><span class="sxs-lookup"><span data-stu-id="811da-107">Therefore, you do not have to be concerned about whether the object gets its value from a COM API, from a dynamic language such as IronPython, from the HTML Document Object Model (DOM), from reflection, or from somewhere else in the program.</span></span> <span data-ttu-id="811da-108">不過，如果程式碼無效，則會在執行階段攔截到錯誤。</span><span class="sxs-lookup"><span data-stu-id="811da-108">However, if the code is not valid, errors are caught at run time.</span></span>  
  
 <span data-ttu-id="811da-109">例如，如果下列程式碼中的執行個體方法 `exampleMethod1` 只有一個參數，則編譯器會將 `ec.exampleMethod1(10, 4)` 方法的第一個呼叫視為無效，因為它包含兩個引數。</span><span class="sxs-lookup"><span data-stu-id="811da-109">For example, if instance method `exampleMethod1` in the following code has only one parameter, the compiler recognizes that the first call to the method, `ec.exampleMethod1(10, 4)`, is not valid because it contains two arguments.</span></span> <span data-ttu-id="811da-110">呼叫會造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="811da-110">The call causes a compiler error.</span></span> <span data-ttu-id="811da-111">編譯器不會檢查 `dynamic_ec.exampleMethod1(10, 4)` 方法的第二個呼叫，因為 `dynamic_ec` 的類型為 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="811da-111">The second call to the method, `dynamic_ec.exampleMethod1(10, 4)`, is not checked by the compiler because the type of `dynamic_ec` is `dynamic`.</span></span> <span data-ttu-id="811da-112">因此，不會報告編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="811da-112">Therefore, no compiler error is reported.</span></span> <span data-ttu-id="811da-113">不過，這項錯誤並不是永遠不會被發現。</span><span class="sxs-lookup"><span data-stu-id="811da-113">However, the error does not escape notice indefinitely.</span></span> <span data-ttu-id="811da-114">它會在執行階段被攔截，並造成執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="811da-114">It is caught at run time and causes a run-time exception.</span></span>  
  
 <span data-ttu-id="811da-115">[!code-cs[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-115">[!code-cs[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]</span></span>  
  
 <span data-ttu-id="811da-116">[!code-cs[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-116">[!code-cs[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]</span></span>  
  
 <span data-ttu-id="811da-117">上述範例中的編譯器角色，就是將每個陳述式應該對類型為 `dynamic` 的物件或運算式所進行之動作的相關資訊封裝在一起。</span><span class="sxs-lookup"><span data-stu-id="811da-117">The role of the compiler in these examples is to package together information about what each statement is proposing to do to the object or expression that is typed as `dynamic`.</span></span> <span data-ttu-id="811da-118">在執行階段，會檢查這些預存資訊，如果有任何陳述式無效，便會造成執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="811da-118">At run time, the stored information is examined, and any statement that is not valid causes a run-time exception.</span></span>  
  
 <span data-ttu-id="811da-119">大多數動態作業的結果本身就是 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="811da-119">The result of most dynamic operations is itself `dynamic`.</span></span> <span data-ttu-id="811da-120">例如，如果您在下列範例中將滑鼠指標停在 `testSum` 的使用用途上，IntelliSense 會顯示 **(區域變數) dynamic testSum** 類型。</span><span class="sxs-lookup"><span data-stu-id="811da-120">For example, if you rest the mouse pointer over the use of `testSum` in the following example, IntelliSense displays the type **(local variable) dynamic testSum**.</span></span>  
  
 <span data-ttu-id="811da-121">[!code-cs[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-121">[!code-cs[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]</span></span>  
  
 <span data-ttu-id="811da-122">結果不是 `dynamic` 的作業包括從 `dynamic` 轉換成另一種類型，以及包含 `dynamic` 類型引數的建構函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="811da-122">Operations in which the result is not `dynamic` include conversions from `dynamic` to another type, and constructor calls that include arguments of type `dynamic`.</span></span> <span data-ttu-id="811da-123">例如，下列宣告中 `testInstance` 的類型是 `ExampleClass`，而不是 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="811da-123">For example, the type of `testInstance` in the following declaration is `ExampleClass`, not `dynamic`.</span></span>  
  
 <span data-ttu-id="811da-124">[!code-cs[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-124">[!code-cs[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]</span></span>  
  
 <span data-ttu-id="811da-125">下一節＜轉換＞會顯示轉換範例。</span><span class="sxs-lookup"><span data-stu-id="811da-125">Conversion examples are shown in the following section, "Conversions."</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="811da-126">轉換</span><span class="sxs-lookup"><span data-stu-id="811da-126">Conversions</span></span>  
 <span data-ttu-id="811da-127">動態物件和其他類型間的轉換很簡單。</span><span class="sxs-lookup"><span data-stu-id="811da-127">Conversions between dynamic objects and other types are easy.</span></span> <span data-ttu-id="811da-128">因此，開發人員可以在動態和非動態行為之間進行切換。</span><span class="sxs-lookup"><span data-stu-id="811da-128">This enables the developer to switch between dynamic and non-dynamic behavior.</span></span>  
  
 <span data-ttu-id="811da-129">所有物件都能隱含轉換成動態類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="811da-129">Any object can be converted to dynamic type implicitly, as shown in the following examples.</span></span>  
  
 <span data-ttu-id="811da-130">[!code-cs[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-130">[!code-cs[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]</span></span>  
  
 <span data-ttu-id="811da-131">相反地，隱含轉換可以動態套用至 `dynamic` 類型的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="811da-131">Conversely, an implicit conversion can be dynamically applied to any expression of type `dynamic`.</span></span>  
  
 <span data-ttu-id="811da-132">[!code-cs[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-132">[!code-cs[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]</span></span>  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a><span data-ttu-id="811da-133">dynamic 類型引數的多載解析</span><span class="sxs-lookup"><span data-stu-id="811da-133">Overload Resolution with Arguments of Type dynamic</span></span>  
 <span data-ttu-id="811da-134">如果方法呼叫中有一或多個引數的類型為 `dynamic`，或如果方法呼叫的接收端類型為 `dynamic`，則會在執行階段 (而不是編譯時期) 發生多載解析。</span><span class="sxs-lookup"><span data-stu-id="811da-134">Overload resolution occurs at run time instead of at compile time if one or more of the arguments in a method call have the type `dynamic`, or if the receiver of the method call is of type `dynamic`.</span></span> <span data-ttu-id="811da-135">在下列範例中，如果唯一可存取的 `exampleMethod2` 方法已定義為接受字串引數，則將 `d1` 作為引數傳送不會造成編譯器錯誤，但會造成執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="811da-135">In the following example, if the only accessible `exampleMethod2` method is defined to take a string argument, sending `d1` as the argument does not cause a compiler error, but it does cause a run-time exception.</span></span> <span data-ttu-id="811da-136">多載解析會在執行階段失敗，因為 `d1` 的執行階段類型為 `int`，而 `exampleMethod2` 需要字串。</span><span class="sxs-lookup"><span data-stu-id="811da-136">Overload resolution fails at run time because the run-time type of `d1` is `int`, and `exampleMethod2` requires a string.</span></span>  
  
 <span data-ttu-id="811da-137">[!code-cs[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-137">[!code-cs[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]</span></span>  
  
## <a name="dynamic-language-runtime"></a><span data-ttu-id="811da-138">Dynamic Language Runtime</span><span class="sxs-lookup"><span data-stu-id="811da-138">Dynamic Language Runtime</span></span>  
 <span data-ttu-id="811da-139">Dynamic Language Runtime (DLR) 是 [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)] 中的新 API。</span><span class="sxs-lookup"><span data-stu-id="811da-139">The dynamic language runtime (DLR) is a new API in [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="811da-140">它提供的基礎結構支援 C# 中的 `dynamic` 類型，也支援實作 IronPython 和 IronRuby 之類的動態程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="811da-140">It provides the infrastructure that supports the `dynamic` type in C#, and also the implementation of dynamic programming languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="811da-141">如需 DLR 的詳細資訊，請參閱 [Dynamic Language Runtime 概觀](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="811da-141">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
## <a name="com-interop"></a><span data-ttu-id="811da-142">COM Interop</span><span class="sxs-lookup"><span data-stu-id="811da-142">COM Interop</span></span>  
 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="811da-143"> 包含幾項功能，可改善與 COM API (例如 Office Automation API) 相互操作的體驗。</span><span class="sxs-lookup"><span data-stu-id="811da-143"> includes several features that improve the experience of interoperating with COM APIs such as the Office Automation APIs.</span></span> <span data-ttu-id="811da-144">這些改進包括使用 `dynamic` 類型，以及使用[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="811da-144">Among the improvements are the use of the `dynamic` type, and of [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>  
  
 <span data-ttu-id="811da-145">許多 COM 方法允許針對引數類型和傳回型別進行變化，方法是將類型指定為 `object`。</span><span class="sxs-lookup"><span data-stu-id="811da-145">Many COM methods allow for variation in argument types and return type by designating the types as `object`.</span></span> <span data-ttu-id="811da-146">這需要對值進行明確轉型，才能與 C# 中的強型別變數配合使用。</span><span class="sxs-lookup"><span data-stu-id="811da-146">This has necessitated explicit casting of the values to coordinate with strongly typed variables in C#.</span></span> <span data-ttu-id="811da-147">如果您使用 [/link (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 選項進行編譯，則引進 `dynamic` 類型可讓您將 COM 簽章中出現的 `object` 項目視為具有 `dynamic` 類型，藉此避免大部分的轉型。</span><span class="sxs-lookup"><span data-stu-id="811da-147">If you compile by using the [/link (C# Compiler Options)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) option, the introduction of the `dynamic` type enables you to treat the occurrences of `object` in COM signatures as if they were of type `dynamic`, and thereby to avoid much of the casting.</span></span> <span data-ttu-id="811da-148">例如，下列陳述式將比較使用 `dynamic` 類型和不使用 `dynamic` 類型存取 Microsoft Office Excel 試算表中儲存格的方式。</span><span class="sxs-lookup"><span data-stu-id="811da-148">For example, the following statements contrast how you access a cell in a Microsoft Office Excel spreadsheet with the `dynamic` type and without the `dynamic` type.</span></span>  
  
 <span data-ttu-id="811da-149">[!code-cs[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-149">[!code-cs[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]</span></span>  
  
 <span data-ttu-id="811da-150">[!code-cs[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="811da-150">[!code-cs[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="811da-151">相關主題</span><span class="sxs-lookup"><span data-stu-id="811da-151">Related Topics</span></span>  
  
|<span data-ttu-id="811da-152">標題</span><span class="sxs-lookup"><span data-stu-id="811da-152">Title</span></span>|<span data-ttu-id="811da-153">描述</span><span class="sxs-lookup"><span data-stu-id="811da-153">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="811da-154">dynamic</span><span class="sxs-lookup"><span data-stu-id="811da-154">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)|<span data-ttu-id="811da-155">說明如何使用 `dynamic` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="811da-155">Describes the usage of the `dynamic` keyword.</span></span>|  
|[<span data-ttu-id="811da-156">Dynamic Language Runtime 概觀</span><span class="sxs-lookup"><span data-stu-id="811da-156">Dynamic Language Runtime Overview</span></span>](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|<span data-ttu-id="811da-157">提供 DLR 概觀，DLR 是在 Common Language Runtime (CLR) 中新增一組動態語言服務的執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="811da-157">Provides an overview of the DLR, which is a runtime environment that adds a set of services for dynamic languages to the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="811da-158">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="811da-158">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|<span data-ttu-id="811da-159">針對建立自訂動態物件及建立存取 `IronPython` 程式庫的專案，提供逐步指示。</span><span class="sxs-lookup"><span data-stu-id="811da-159">Provides step-by-step instructions for creating a custom dynamic object and for creating a project that accesses an `IronPython` library.</span></span>|  
|[<span data-ttu-id="811da-160">如何：使用 Visual C# 功能存取 Office Interop 物件</span><span class="sxs-lookup"><span data-stu-id="811da-160">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|<span data-ttu-id="811da-161">示範如何建立使用具名和選擇性引數、`dynamic` 類型，以及其他可簡化 Office API 物件存取之增強功能的專案。</span><span class="sxs-lookup"><span data-stu-id="811da-161">Demonstrates how to create a project that uses named and optional arguments, the `dynamic` type, and other enhancements that simplify access to Office API objects.</span></span>|

