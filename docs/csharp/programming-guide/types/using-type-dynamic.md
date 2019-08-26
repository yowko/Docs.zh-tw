---
title: 使用 dynamic 類型 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 4141c64ff6dbbec60b53a41862a4273df6ef51ab
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588355"
---
# <a name="using-type-dynamic-c-programming-guide"></a><span data-ttu-id="f3e6c-102">使用 dynamic 類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f3e6c-102">Using type dynamic (C# Programming Guide)</span></span>

<span data-ttu-id="f3e6c-103">C# 4 引進一種新型別 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-103">C# 4 introduces a new type, `dynamic`.</span></span> <span data-ttu-id="f3e6c-104">此類型是靜態類型，但 `dynamic` 類型的物件會略過靜態類型檢查。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-104">The type is a static type, but an object of type `dynamic` bypasses static type checking.</span></span> <span data-ttu-id="f3e6c-105">在大多數情況下，其運作會像是具有 `object` 類型。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-105">In most cases, it functions like it has type `object`.</span></span> <span data-ttu-id="f3e6c-106">在編譯時期，會假設類型為 `dynamic` 的項目能夠支援所有作業。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-106">At compile time, an element that is typed as `dynamic` is assumed to support any operation.</span></span> <span data-ttu-id="f3e6c-107">因此，您無須考慮物件是從 COM API、動態語言 (例如 IronPython)、HTML 文件物件模型 (DOM)、反映或是程式其他地方取得其值。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-107">Therefore, you do not have to be concerned about whether the object gets its value from a COM API, from a dynamic language such as IronPython, from the HTML Document Object Model (DOM), from reflection, or from somewhere else in the program.</span></span> <span data-ttu-id="f3e6c-108">不過，如果程式碼無效，則會在執行階段攔截到錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-108">However, if the code is not valid, errors are caught at run time.</span></span>

<span data-ttu-id="f3e6c-109">例如，如果下列程式碼中的執行個體方法 `exampleMethod1` 只有一個參數，則編譯器會將 `ec.exampleMethod1(10, 4)` 方法的第一個呼叫視為無效，因為它包含兩個引數。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-109">For example, if instance method `exampleMethod1` in the following code has only one parameter, the compiler recognizes that the first call to the method, `ec.exampleMethod1(10, 4)`, is not valid because it contains two arguments.</span></span> <span data-ttu-id="f3e6c-110">呼叫會造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-110">The call causes a compiler error.</span></span> <span data-ttu-id="f3e6c-111">編譯器不會檢查 `dynamic_ec.exampleMethod1(10, 4)` 方法的第二個呼叫，因為 `dynamic_ec` 的類型為 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-111">The second call to the method, `dynamic_ec.exampleMethod1(10, 4)`, is not checked by the compiler because the type of `dynamic_ec` is `dynamic`.</span></span> <span data-ttu-id="f3e6c-112">因此，不會報告編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-112">Therefore, no compiler error is reported.</span></span> <span data-ttu-id="f3e6c-113">不過，這項錯誤並不是永遠不會被發現。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-113">However, the error does not escape notice indefinitely.</span></span> <span data-ttu-id="f3e6c-114">它會在執行階段被攔截，並造成執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-114">It is caught at run time and causes a run-time exception.</span></span>

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

<span data-ttu-id="f3e6c-115">上述範例中的編譯器角色，就是將每個陳述式應該對類型為 `dynamic` 的物件或運算式所進行之動作的相關資訊封裝在一起。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-115">The role of the compiler in these examples is to package together information about what each statement is proposing to do to the object or expression that is typed as `dynamic`.</span></span> <span data-ttu-id="f3e6c-116">在執行階段，會檢查這些預存資訊，如果有任何陳述式無效，便會造成執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-116">At run time, the stored information is examined, and any statement that is not valid causes a run-time exception.</span></span>

<span data-ttu-id="f3e6c-117">大多數動態作業的結果本身就是 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-117">The result of most dynamic operations is itself `dynamic`.</span></span> <span data-ttu-id="f3e6c-118">例如，如果您在下列範例中將滑鼠指標停在 `testSum` 的使用用途上，IntelliSense 會顯示 **(區域變數) dynamic testSum** 類型。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-118">For example, if you rest the mouse pointer over the use of `testSum` in the following example, IntelliSense displays the type **(local variable) dynamic testSum**.</span></span>

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

<span data-ttu-id="f3e6c-119">結果不是 `dynamic` 的作業包括：</span><span class="sxs-lookup"><span data-stu-id="f3e6c-119">Operations in which the result is not `dynamic` include:</span></span>

* <span data-ttu-id="f3e6c-120">從 `dynamic` 轉換成另一種類型。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-120">Conversions from `dynamic` to another type.</span></span>
* <span data-ttu-id="f3e6c-121">包含 `dynamic` 類型引數的建構函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-121">Constructor calls that include arguments of type `dynamic`.</span></span>

<span data-ttu-id="f3e6c-122">例如，下列宣告中 `testInstance` 的類型是 `ExampleClass`，而不是 `dynamic`：</span><span class="sxs-lookup"><span data-stu-id="f3e6c-122">For example, the type of `testInstance` in the following declaration is `ExampleClass`, not `dynamic`:</span></span>

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

<span data-ttu-id="f3e6c-123">下一節＜轉換＞會顯示轉換範例。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-123">Conversion examples are shown in the following section, "Conversions."</span></span>

## <a name="conversions"></a><span data-ttu-id="f3e6c-124">轉換</span><span class="sxs-lookup"><span data-stu-id="f3e6c-124">Conversions</span></span>

<span data-ttu-id="f3e6c-125">動態物件和其他類型間的轉換很簡單。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-125">Conversions between dynamic objects and other types are easy.</span></span> <span data-ttu-id="f3e6c-126">因此，開發人員可以在動態和非動態行為之間進行切換。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-126">This enables the developer to switch between dynamic and non-dynamic behavior.</span></span>

<span data-ttu-id="f3e6c-127">所有物件都能隱含轉換成動態類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-127">Any object can be converted to dynamic type implicitly, as shown in the following examples.</span></span>

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

<span data-ttu-id="f3e6c-128">相反地，隱含轉換可以動態套用至 `dynamic` 類型的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-128">Conversely, an implicit conversion can be dynamically applied to any expression of type `dynamic`.</span></span>

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a><span data-ttu-id="f3e6c-129">dynamic 類型引數的多載解析</span><span class="sxs-lookup"><span data-stu-id="f3e6c-129">Overload resolution with arguments of type dynamic</span></span>

<span data-ttu-id="f3e6c-130">如果方法呼叫中有一或多個引數的類型為 `dynamic`，或如果方法呼叫的接收端類型為 `dynamic`，則會在執行階段 (而不是編譯時期) 發生多載解析。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-130">Overload resolution occurs at run time instead of at compile time if one or more of the arguments in a method call have the type `dynamic`, or if the receiver of the method call is of type `dynamic`.</span></span> <span data-ttu-id="f3e6c-131">在下列範例中，如果唯一可存取的 `exampleMethod2` 方法已定義為接受字串引數，則將 `d1` 作為引數傳送不會造成編譯器錯誤，但會造成執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-131">In the following example, if the only accessible `exampleMethod2` method is defined to take a string argument, sending `d1` as the argument does not cause a compiler error, but it does cause a run-time exception.</span></span> <span data-ttu-id="f3e6c-132">多載解析會在執行階段失敗，因為 `d1` 的執行階段類型為 `int`，而 `exampleMethod2` 需要字串。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-132">Overload resolution fails at run time because the run-time type of `d1` is `int`, and `exampleMethod2` requires a string.</span></span>

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a><span data-ttu-id="f3e6c-133">Dynamic Language Runtime</span><span class="sxs-lookup"><span data-stu-id="f3e6c-133">Dynamic language runtime</span></span>

<span data-ttu-id="f3e6c-134">Dynamic Language Runtime (DLR) 是 .NET Framework 4 中的新 API。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-134">The dynamic language runtime (DLR) is a new API in .NET Framework 4.</span></span> <span data-ttu-id="f3e6c-135">它提供的基礎結構支援 C# 中的 `dynamic` 類型，也支援實作 IronPython 和 IronRuby 之類的動態程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-135">It provides the infrastructure that supports the `dynamic` type in C#, and also the implementation of dynamic programming languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="f3e6c-136">如需 DLR 的詳細資訊，請參閱 [Dynamic Language Runtime 概觀](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-136">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>

## <a name="com-interop"></a><span data-ttu-id="f3e6c-137">COM Interop</span><span class="sxs-lookup"><span data-stu-id="f3e6c-137">COM interop</span></span>

<span data-ttu-id="f3e6c-138">C# 4 包含幾項功能，可改善與 COM API (例如 Office Automation API) 相互操作的體驗。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-138">C# 4 includes several features that improve the experience of interoperating with COM APIs such as the Office Automation APIs.</span></span> <span data-ttu-id="f3e6c-139">這些改進包括使用 `dynamic` 類型，以及使用[具名和選擇性引數](../classes-and-structs/named-and-optional-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-139">Among the improvements are the use of the `dynamic` type, and of [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md).</span></span>

<span data-ttu-id="f3e6c-140">許多 COM 方法允許針對引數類型和傳回型別進行變化，方法是將類型指定為 `object`。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-140">Many COM methods allow for variation in argument types and return type by designating the types as `object`.</span></span> <span data-ttu-id="f3e6c-141">這需要對值進行明確轉型，才能與 C# 中的強型別變數配合使用。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-141">This has necessitated explicit casting of the values to coordinate with strongly typed variables in C#.</span></span> <span data-ttu-id="f3e6c-142">如果您使用 [/link (C# 編譯器選項)](../../language-reference/compiler-options/link-compiler-option.md) 選項進行編譯，則引進 `dynamic` 類型可讓您將 COM 簽章中出現的 `object` 項目視為具有 `dynamic` 類型，藉此避免大部分的轉型。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-142">If you compile by using the [/link (C# Compiler Options)](../../language-reference/compiler-options/link-compiler-option.md) option, the introduction of the `dynamic` type enables you to treat the occurrences of `object` in COM signatures as if they were of type `dynamic`, and thereby to avoid much of the casting.</span></span> <span data-ttu-id="f3e6c-143">例如，下列陳述式將比較使用 `dynamic` 類型和不使用 `dynamic` 類型存取 Microsoft Office Excel 試算表中儲存格的方式。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-143">For example, the following statements contrast how you access a cell in a Microsoft Office Excel spreadsheet with the `dynamic` type and without the `dynamic` type.</span></span>

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a><span data-ttu-id="f3e6c-144">相關主題</span><span class="sxs-lookup"><span data-stu-id="f3e6c-144">Related topics</span></span>

|<span data-ttu-id="f3e6c-145">標題</span><span class="sxs-lookup"><span data-stu-id="f3e6c-145">Title</span></span>|<span data-ttu-id="f3e6c-146">說明</span><span class="sxs-lookup"><span data-stu-id="f3e6c-146">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="f3e6c-147">dynamic</span><span class="sxs-lookup"><span data-stu-id="f3e6c-147">dynamic</span></span>](../../language-reference/keywords/dynamic.md)|<span data-ttu-id="f3e6c-148">說明如何使用 `dynamic` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-148">Describes the usage of the `dynamic` keyword.</span></span>|
|[<span data-ttu-id="f3e6c-149">Dynamic Language Runtime 概觀</span><span class="sxs-lookup"><span data-stu-id="f3e6c-149">Dynamic Language Runtime Overview</span></span>](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|<span data-ttu-id="f3e6c-150">提供 DLR 概觀，DLR 是在 Common Language Runtime (CLR) 中新增一組動態語言服務的執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-150">Provides an overview of the DLR, which is a runtime environment that adds a set of services for dynamic languages to the common language runtime (CLR).</span></span>|
|[<span data-ttu-id="f3e6c-151">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="f3e6c-151">Walkthrough: Creating and Using Dynamic Objects</span></span>](walkthrough-creating-and-using-dynamic-objects.md)|<span data-ttu-id="f3e6c-152">針對建立自訂動態物件及建立存取 `IronPython` 程式庫的專案，提供逐步指示。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-152">Provides step-by-step instructions for creating a custom dynamic object and for creating a project that accesses an `IronPython` library.</span></span>|
|[<span data-ttu-id="f3e6c-153">如何：使用 Visual C# 功能存取 Office Interop 物件</span><span class="sxs-lookup"><span data-stu-id="f3e6c-153">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../interop/how-to-access-office-onterop-objects.md)|<span data-ttu-id="f3e6c-154">示範如何建立使用具名和選擇性引數、`dynamic` 類型，以及其他可簡化 Office API 物件存取之增強功能的專案。</span><span class="sxs-lookup"><span data-stu-id="f3e6c-154">Demonstrates how to create a project that uses named and optional arguments, the `dynamic` type, and other enhancements that simplify access to Office API objects.</span></span>|
