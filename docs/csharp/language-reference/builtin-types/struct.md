---
title: 結構類型- C#參考
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 523269ffc9de9b750330fcefd15a9026d6dc59b8
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239777"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="9241f-102">結構類型（C#參考）</span><span class="sxs-lookup"><span data-stu-id="9241f-102">Structure types (C# reference)</span></span>

<span data-ttu-id="9241f-103">*結構型*別（或*結構型*別）是可以封裝資料和相關功能的實[值型](value-types.md)別。</span><span class="sxs-lookup"><span data-stu-id="9241f-103">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="9241f-104">您可以使用 `struct` 關鍵字來定義結構類型：</span><span class="sxs-lookup"><span data-stu-id="9241f-104">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](~/samples/snippets/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

<span data-ttu-id="9241f-105">結構類型具有*值的語義*。</span><span class="sxs-lookup"><span data-stu-id="9241f-105">Structure types have *value semantics*.</span></span> <span data-ttu-id="9241f-106">也就是說，結構類型的變數會包含類型的實例。</span><span class="sxs-lookup"><span data-stu-id="9241f-106">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="9241f-107">根據預設，變數值會在指派時複製、將引數傳遞至方法，並傳回方法結果。</span><span class="sxs-lookup"><span data-stu-id="9241f-107">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="9241f-108">在結構類型變數的情況下，會複製類型的實例。</span><span class="sxs-lookup"><span data-stu-id="9241f-108">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="9241f-109">如需詳細資訊，請參閱實[數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9241f-109">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="9241f-110">一般來說，您會使用結構類型來設計以資料為中心的小型類型，以提供些許或無行為。</span><span class="sxs-lookup"><span data-stu-id="9241f-110">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="9241f-111">例如，.NET 會使用結構類型來代表數位（[整數](integral-numeric-types.md)和[實數](floating-point-numeric-types.md)）、[布林值](bool.md)、 [Unicode 字元](char.md)和[時間實例](xref:System.DateTime)。</span><span class="sxs-lookup"><span data-stu-id="9241f-111">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="9241f-112">如果您將焦點放在類型的行為，請考慮定義[類別](../keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="9241f-112">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="9241f-113">類別類型具有*參考語義*。</span><span class="sxs-lookup"><span data-stu-id="9241f-113">Class types have *reference semantics*.</span></span> <span data-ttu-id="9241f-114">也就是說，類別類型的變數包含類型實例的參考，而不是實例本身。</span><span class="sxs-lookup"><span data-stu-id="9241f-114">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="9241f-115">結構類型設計的限制</span><span class="sxs-lookup"><span data-stu-id="9241f-115">Limitations with the design of a structure type</span></span>

<span data-ttu-id="9241f-116">當您設計結構類型時，您具有與[類別](../keywords/class.md)類型相同的功能，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="9241f-116">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="9241f-117">您不能宣告無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="9241f-117">You cannot declare a parameterless constructor.</span></span> <span data-ttu-id="9241f-118">每個結構類型已經提供隱含的無參數的函式，以產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="9241f-118">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="9241f-119">您無法在其宣告中初始化實例欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="9241f-119">You cannot initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="9241f-120">不過，您可以在其宣告中初始化[靜態](../keywords/static.md)或[常數](../keywords/const.md)欄位或靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="9241f-120">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="9241f-121">結構類型的「構造函式」必須初始化該類型的所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="9241f-121">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="9241f-122">結構類型無法繼承自其他類別或結構類型，而且不能是類別的基底。</span><span class="sxs-lookup"><span data-stu-id="9241f-122">A structure type cannot inherit from other class or structure type and it cannot be the base of a class.</span></span> <span data-ttu-id="9241f-123">不過，結構類型可以執行[介面](../keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="9241f-123">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="9241f-124">您不[能在結構類型中宣告](../../programming-guide/classes-and-structs/destructors.md)完成項。</span><span class="sxs-lookup"><span data-stu-id="9241f-124">You cannot declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="9241f-125">結構類型的具現化</span><span class="sxs-lookup"><span data-stu-id="9241f-125">Instantiation of a structure type</span></span>

<span data-ttu-id="9241f-126">在C#中，您必須先初始化已宣告的變數，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="9241f-126">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="9241f-127">因為結構類型變數無法 `null` （除非它是[可為 null 的實數值型別](nullable-value-types.md)的變數），所以您必須具現化對應類型的實例。</span><span class="sxs-lookup"><span data-stu-id="9241f-127">Because a structure-type variable cannot be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="9241f-128">有幾種方式可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="9241f-128">There are several ways to do that.</span></span>

<span data-ttu-id="9241f-129">通常，您可以使用[`new`](../operators/new-operator.md)運算子來呼叫適當的處理常式，以具現化結構類型。</span><span class="sxs-lookup"><span data-stu-id="9241f-129">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="9241f-130">每個結構類型都至少有一個函式。</span><span class="sxs-lookup"><span data-stu-id="9241f-130">Every structure type has at least one constructor.</span></span> <span data-ttu-id="9241f-131">這是隱含的無參數的函式，它會產生類型的[預設值](default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="9241f-131">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="9241f-132">您也可以使用[預設](../operators/default.md)的運算子或常值來產生類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="9241f-132">You can also use the [default](../operators/default.md) operator or literal to produce the default value of a type.</span></span>

<span data-ttu-id="9241f-133">如果結構類型的所有實例欄位都可存取，您也可以在不使用 `new` 運算子的情況下將它具現化。</span><span class="sxs-lookup"><span data-stu-id="9241f-133">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="9241f-134">在此情況下，您必須在第一次使用實例之前，先初始化所有實例欄位。</span><span class="sxs-lookup"><span data-stu-id="9241f-134">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="9241f-135">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="9241f-135">The following example shows how to do that:</span></span>

[!code-csharp[without new](~/samples/snippets/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

<span data-ttu-id="9241f-136">在內[建實數值型別](value-types.md#built-in-value-types)的情況下，請使用對應的常值來指定類型的值。</span><span class="sxs-lookup"><span data-stu-id="9241f-136">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="9241f-137">以傳址方式傳遞結構型別變數</span><span class="sxs-lookup"><span data-stu-id="9241f-137">Passing structure-type variables by reference</span></span>

<span data-ttu-id="9241f-138">當您將結構型別變數當做引數傳遞至方法，或從方法傳回結構型別值時，會複製結構型別的整個實例。</span><span class="sxs-lookup"><span data-stu-id="9241f-138">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="9241f-139">這可能會影響您的程式碼在涉及大型結構類型的高效能案例中的效能。</span><span class="sxs-lookup"><span data-stu-id="9241f-139">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="9241f-140">您可以透過傳址方式傳遞結構型別變數，以避免值複製。</span><span class="sxs-lookup"><span data-stu-id="9241f-140">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="9241f-141">您可以使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、 [`out`](../keywords/out-parameter-modifier.md)或[`in`](../keywords/in-parameter-modifier.md)方法參數修飾詞，來指出引數必須以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="9241f-141">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="9241f-142">使用[ref](../../programming-guide/classes-and-structs/ref-returns.md) return 傳回以傳址方式傳回的方法結果。</span><span class="sxs-lookup"><span data-stu-id="9241f-142">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="9241f-143">如需詳細資訊，請參閱[撰寫安全C#且有效率](../../write-safe-efficient-code.md)的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9241f-143">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="9241f-144">轉換</span><span class="sxs-lookup"><span data-stu-id="9241f-144">Conversions</span></span>

<span data-ttu-id="9241f-145">針對任何結構類型，會在 <xref:System.ValueType?displayProperty=nameWithType> 和 <xref:System.Object?displayProperty=nameWithType> 類型之間存在進行的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="9241f-145">For any structure type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="9241f-146">結構型別和它所執行的任何介面之間也有一個裝箱和取消裝箱轉換。</span><span class="sxs-lookup"><span data-stu-id="9241f-146">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9241f-147">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9241f-147">C# language specification</span></span>

<span data-ttu-id="9241f-148">如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[結構](~/_csharplang/spec/structs.md)一節。</span><span class="sxs-lookup"><span data-stu-id="9241f-148">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9241f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9241f-149">See also</span></span>

- [<span data-ttu-id="9241f-150">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9241f-150">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9241f-151">設計方針-在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="9241f-151">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="9241f-152">設計方針-結構設計</span><span class="sxs-lookup"><span data-stu-id="9241f-152">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="9241f-153">類別和結構</span><span class="sxs-lookup"><span data-stu-id="9241f-153">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
