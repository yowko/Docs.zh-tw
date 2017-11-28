---
title: "C# 型別和變數 - C# 語言教學課程"
description: "了解如何在 C# 中定義類型和宣告變數"
keywords: ".NET, csharp, 型別, 參考型別, 實值型別"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 1f1031384520b9ed37246361da8bbc1b42addb0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="types-and-variables"></a><span data-ttu-id="83735-104">型別與變數</span><span class="sxs-lookup"><span data-stu-id="83735-104">Types and variables</span></span>

<span data-ttu-id="83735-105">C# 中有兩種型別：*實值型別*和*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="83735-105">There are two kinds of types in C#: *value types* and *reference types*.</span></span> <span data-ttu-id="83735-106">實值型別的變數直接包含其資料，而參考型別的變數則將參考儲存到其資料，後者即是物件。</span><span class="sxs-lookup"><span data-stu-id="83735-106">Variables of value types directly contain their data whereas variables of reference types store references to their data, the latter being known as objects.</span></span> <span data-ttu-id="83735-107">使用參考型別時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="83735-107">With reference types, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="83735-108">使用實值型別時，變數各有自己的資料複本，因此在某一個變數上進行的作業不可能會影響其他變數 (但 `ref` 和 `out` 參數變數除外)。</span><span class="sxs-lookup"><span data-stu-id="83735-108">With value types, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other (except in the case of `ref` and `out` parameter variables).</span></span>

<span data-ttu-id="83735-109">C# 的實值型別可進一步細分為*簡單型別*、*列舉型別*、*結構型別*和*可為 Null 的實值型別*。</span><span class="sxs-lookup"><span data-stu-id="83735-109">C#’s value types are further divided into *simple types*, *enum types*, *struct types*, and *nullable value types*.</span></span> <span data-ttu-id="83735-110">C# 的參考型別可進一步細分為*類別型別*、*介面型別*、*陣列型別*和*委派型別*。</span><span class="sxs-lookup"><span data-stu-id="83735-110">C#’s reference types are further divided into *class types*, *interface types*, *array types*, and *delegate types*.</span></span>

<span data-ttu-id="83735-111">以下提供 C# 的型別系統概觀。</span><span class="sxs-lookup"><span data-stu-id="83735-111">The following provides an overview of C#’s type system.</span></span>

* <span data-ttu-id="83735-112">值類型</span><span class="sxs-lookup"><span data-stu-id="83735-112">Value types</span></span>
    - <span data-ttu-id="83735-113">簡單型別</span><span class="sxs-lookup"><span data-stu-id="83735-113">Simple Types</span></span>
        * <span data-ttu-id="83735-114">帶正負號的整數︰`sbyte`、`short`、`int`、`long`</span><span class="sxs-lookup"><span data-stu-id="83735-114">Signed integral: `sbyte`, `short`, `int`, `long`</span></span>
        * <span data-ttu-id="83735-115">不帶正負號的整數︰`byte`、`ushort`、`uint`、`ulong`</span><span class="sxs-lookup"><span data-stu-id="83735-115">Unsigned integral: `byte`, `ushort`, `uint`, `ulong`</span></span>
        * <span data-ttu-id="83735-116">Unicode 字元：`char`</span><span class="sxs-lookup"><span data-stu-id="83735-116">Unicode characters: `char`</span></span>
        * <span data-ttu-id="83735-117">IEEE 浮點數：`float`、`double`</span><span class="sxs-lookup"><span data-stu-id="83735-117">IEEE floating point: `float`, `double`</span></span>
        * <span data-ttu-id="83735-118">高精確度十進位︰`decimal`</span><span class="sxs-lookup"><span data-stu-id="83735-118">High-precision decimal: `decimal`</span></span>
        * <span data-ttu-id="83735-119">布林值：`bool`</span><span class="sxs-lookup"><span data-stu-id="83735-119">Boolean: `bool`</span></span>
    - <span data-ttu-id="83735-120">列舉型別</span><span class="sxs-lookup"><span data-stu-id="83735-120">Enum types</span></span>
        * <span data-ttu-id="83735-121">使用者定義型別，格式為 `enum E {...}`</span><span class="sxs-lookup"><span data-stu-id="83735-121">User-defined types of the form `enum E {...}`</span></span>
    - <span data-ttu-id="83735-122">結構型別</span><span class="sxs-lookup"><span data-stu-id="83735-122">Struct types</span></span>
        * <span data-ttu-id="83735-123">使用者定義型別，格式為 `struct S {...}`</span><span class="sxs-lookup"><span data-stu-id="83735-123">User-defined types of the form `struct S {...}`</span></span>
    - <span data-ttu-id="83735-124">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="83735-124">Nullable value types</span></span>
        * <span data-ttu-id="83735-125">含有 `null` 值的所有其他數值型別的擴充</span><span class="sxs-lookup"><span data-stu-id="83735-125">Extensions of all other value types with a `null` value</span></span>
* <span data-ttu-id="83735-126">參考型別</span><span class="sxs-lookup"><span data-stu-id="83735-126">Reference types</span></span>
    - <span data-ttu-id="83735-127">類別型別</span><span class="sxs-lookup"><span data-stu-id="83735-127">Class types</span></span>
        * <span data-ttu-id="83735-128">所有其他型別的基底類別︰`object`</span><span class="sxs-lookup"><span data-stu-id="83735-128">Ultimate base class of all other types: `object`</span></span>
        * <span data-ttu-id="83735-129">Unicode 字串：`string`</span><span class="sxs-lookup"><span data-stu-id="83735-129">Unicode strings: `string`</span></span>
        * <span data-ttu-id="83735-130">使用者定義型別，格式為 `class C {...}`</span><span class="sxs-lookup"><span data-stu-id="83735-130">User-defined types of the form `class C {...}`</span></span>
    - <span data-ttu-id="83735-131">介面型別</span><span class="sxs-lookup"><span data-stu-id="83735-131">Interface types</span></span>
        * <span data-ttu-id="83735-132">使用者定義型別，格式為 `interface I {...}`</span><span class="sxs-lookup"><span data-stu-id="83735-132">User-defined types of the form `interface I {...}`</span></span>
    - <span data-ttu-id="83735-133">陣列型別</span><span class="sxs-lookup"><span data-stu-id="83735-133">Array types</span></span>
        * <span data-ttu-id="83735-134">單一維度和多維度，例如 `int[]` 和 `int[,]`</span><span class="sxs-lookup"><span data-stu-id="83735-134">Single- and multi-dimensional, for example, `int[]` and `int[,]`</span></span>
    - <span data-ttu-id="83735-135">委派型別</span><span class="sxs-lookup"><span data-stu-id="83735-135">Delegate types</span></span>
        * <span data-ttu-id="83735-136">使用者定義型別，格式為 `delegate int D(...)`</span><span class="sxs-lookup"><span data-stu-id="83735-136">User-defined types of the form `delegate int D(...)`</span></span>

<span data-ttu-id="83735-137">八種整數型別支援 8 位元、16 位元、32 位元和 64 位元的值 (帶正負號或不帶正負號)。</span><span class="sxs-lookup"><span data-stu-id="83735-137">The eight integral types provide support for 8-bit, 16-bit, 32-bit, and 64-bit values in signed or unsigned form.</span></span>

<span data-ttu-id="83735-138">兩個浮點數型別 `float` 和`double` 分別使用 32 位元單精確度和 64 位元雙精確度 IEC-60559 格式表示。</span><span class="sxs-lookup"><span data-stu-id="83735-138">The two floating-point types, `float` and `double`, are represented using the 32-bit single-precision and 64-bit double-precision IEC-60559 formats, respectively.</span></span>

<span data-ttu-id="83735-139">`decimal` 型別是 128 位元的資料型別，適合財務和貨幣計算。</span><span class="sxs-lookup"><span data-stu-id="83735-139">The `decimal` type is a 128-bit data type suitable for financial and monetary calculations.</span></span>

<span data-ttu-id="83735-140">C# 的 `bool` 型別用來代表布林值 — 不是 `true` 或 `false` 的值。</span><span class="sxs-lookup"><span data-stu-id="83735-140">C#’s `bool` type is used to represent Boolean values—values that are either `true` or `false`.</span></span>

<span data-ttu-id="83735-141">C# 中的字元和字串處理使用 Unicode 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83735-141">Character and string processing in C# uses Unicode encoding.</span></span> <span data-ttu-id="83735-142">`char` 型別代表 UTF-16 程式碼單位，而 `string` 型別代表一系列的 UTF-16 程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="83735-142">The `char` type represents a UTF-16 code unit, and the `string` type represents a sequence of UTF-16 code units.</span></span>

<span data-ttu-id="83735-143">以下摘要說明 C# 的數值型別。</span><span class="sxs-lookup"><span data-stu-id="83735-143">This summarizes C#’s numeric types.</span></span>

* <span data-ttu-id="83735-144">帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="83735-144">Signed Integral</span></span>
    - <span data-ttu-id="83735-145">`sbyte`：8 位元，-128 到 127 之間</span><span class="sxs-lookup"><span data-stu-id="83735-145">`sbyte`:  8 bits, range from -128 - 127</span></span>
    - <span data-ttu-id="83735-146">`short`：16 位元，-32,768 到 32,767 之間</span><span class="sxs-lookup"><span data-stu-id="83735-146">`short`: 16 bits, range from -32,768 - 32,767</span></span>
    - <span data-ttu-id="83735-147">`int`：32 位元，-2,147,483,648 到 2,147,483,647 之間</span><span class="sxs-lookup"><span data-stu-id="83735-147">`int`  : 32 bits, range from -2,147,483,648 - 2,147,483,647</span></span>
    - <span data-ttu-id="83735-148">`long`：64 位元，––9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 之間</span><span class="sxs-lookup"><span data-stu-id="83735-148">`long` : 64 bits, range from –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>
* <span data-ttu-id="83735-149">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="83735-149">Unsigned integral</span></span>
    - <span data-ttu-id="83735-150">`byte`：8 位元，0 到 255 之間</span><span class="sxs-lookup"><span data-stu-id="83735-150">`byte`   :  8 bits, range from 0 - 255</span></span>
    - <span data-ttu-id="83735-151">`ushort`：16 位元，0 到 65,535 之間</span><span class="sxs-lookup"><span data-stu-id="83735-151">`ushort` : 16 bits, range from 0 - 65,535</span></span>
    - <span data-ttu-id="83735-152">`uint`：32 位元，0 到 4,294,967,295 之間</span><span class="sxs-lookup"><span data-stu-id="83735-152">`uint`   : 32 bits, range from 0 - 4,294,967,295</span></span>
    - <span data-ttu-id="83735-153">`ulong`：64 位元，0 到 18,446,744,073,709,551,615 之間</span><span class="sxs-lookup"><span data-stu-id="83735-153">`ulong`  : 64 bits, range from 0 - 18,446,744,073,709,551,615</span></span>
* <span data-ttu-id="83735-154">浮點</span><span class="sxs-lookup"><span data-stu-id="83735-154">Floating point</span></span>
    - <span data-ttu-id="83735-155">`float`：32 位元，1.5 × 10<sup>-45</sup> 到 3.4 × 10<sup>38</sup> 之間，7 位數精確度</span><span class="sxs-lookup"><span data-stu-id="83735-155">`float`  : 32 bits, range from 1.5 × 10<sup>−45</sup> - 3.4 × 10<sup>38</sup>,    7-digit precision</span></span>
    - <span data-ttu-id="83735-156">`double`：64 位元，5.0 × 10<sup>−324</sup> 到 1.7 × 10<sup>308</sup> 之間，15 位數精確度</span><span class="sxs-lookup"><span data-stu-id="83735-156">`double` : 64 bits, range from 5.0 × 10<sup>−324</sup> - 1.7 × 10<sup>308</sup>, 15-digit precision</span></span>
* <span data-ttu-id="83735-157">Decimal</span><span class="sxs-lookup"><span data-stu-id="83735-157">Decimal</span></span>
    - <span data-ttu-id="83735-158">`decimal`：128 位元，至少在 –7.9 × 10<sup>−28</sup> 到 7.9 × 10<sup>28</sup> 之間，至少 28 位數精確度</span><span class="sxs-lookup"><span data-stu-id="83735-158">`decimal` : 128 bits, range is at least –7.9 × 10<sup>−28</sup> -  7.9 × 10<sup>28</sup>, with at least 28-digit precision</span></span>
    
<span data-ttu-id="83735-159">C# 程式使用*型別宣告*來建立新型別。</span><span class="sxs-lookup"><span data-stu-id="83735-159">C# programs use *type declarations* to create new types.</span></span> <span data-ttu-id="83735-160">型別宣告指定新型別的名稱成員。</span><span class="sxs-lookup"><span data-stu-id="83735-160">A type declaration specifies the name and the members of the new type.</span></span> <span data-ttu-id="83735-161">可由使用者定義的五種 C# 型別類型︰類別型別、結構型別、介面型別、列舉型別及委派型別。</span><span class="sxs-lookup"><span data-stu-id="83735-161">Five of C#’s categories of types are user-definable: class types, struct types, interface types, enum types, and delegate types.</span></span>

<span data-ttu-id="83735-162">`class` 型別定義資料結構，其中包含資料成員 (欄位) 和函式成員 (方法、屬性及其他)。</span><span class="sxs-lookup"><span data-stu-id="83735-162">A `class` type defines a data structure that contains data members (fields) and function members (methods, properties, and others).</span></span> <span data-ttu-id="83735-163">類別型別支援單一繼承和多型，這些是可供衍生類別將基底類別延伸及特製化的機制。</span><span class="sxs-lookup"><span data-stu-id="83735-163">Class types support single inheritance and polymorphism, mechanisms whereby derived classes can extend and specialize base classes.</span></span>

<span data-ttu-id="83735-164">`struct` 型別與類別型別相似，它代表具有資料成員和函式成員的結構。</span><span class="sxs-lookup"><span data-stu-id="83735-164">A `struct` type is similar to a class type in that it represents a structure with data members and function members.</span></span> <span data-ttu-id="83735-165">不過，不同於類別，結構是實值型別，而且通常不需要堆積配置。</span><span class="sxs-lookup"><span data-stu-id="83735-165">However, unlike classes, structs are value types and do not typically require heap allocation.</span></span> <span data-ttu-id="83735-166">結構型別不支援使用者指定的繼承，且所有結構型別都隱含地繼承自 `object` 型別。</span><span class="sxs-lookup"><span data-stu-id="83735-166">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type `object`.</span></span>

<span data-ttu-id="83735-167">`interface` 型別將協定定義為一組具名的公用函式成員。</span><span class="sxs-lookup"><span data-stu-id="83735-167">An `interface` type defines a contract as a named set of public function members.</span></span> <span data-ttu-id="83735-168">實作 `interface` 的 `class` 或 `struct` 必須提供介面的函式成員的實作。</span><span class="sxs-lookup"><span data-stu-id="83735-168">A `class` or `struct` that implements an `interface` must provide implementations of the interface’s function members.</span></span> <span data-ttu-id="83735-169">`interface` 可以繼承自多個基底介面，`class` 或 `struct`可實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="83735-169">An `interface` may inherit from multiple base interfaces, and a `class` or `struct` may implement multiple interfaces.</span></span>

<span data-ttu-id="83735-170">`delegate` 型別代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="83735-170">A `delegate` type represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="83735-171">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="83735-171">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="83735-172">委派類似函式語言提供的函式型別。</span><span class="sxs-lookup"><span data-stu-id="83735-172">Delegates are analogous to function types provided by functional languages.</span></span> <span data-ttu-id="83735-173">它們也類似其他程式設計語言中的函式指標，但與函式指標的不同之處是，委派是物件導向且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="83735-173">They are also similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="83735-174">`class`、`struct`、`interface` 和 `delegate` 類型全都支援泛型，因此它們可以使用其他類型來參數化。</span><span class="sxs-lookup"><span data-stu-id="83735-174">The `class`, `struct`, `interface` and `delegate` types all support generics, whereby they can be parameterized with other types.</span></span>

<span data-ttu-id="83735-175">`enum` 型別是包含具名常數的不同型別。</span><span class="sxs-lookup"><span data-stu-id="83735-175">An `enum` type is a distinct type with named constants.</span></span> <span data-ttu-id="83735-176">每個 `enum` 型別都具有一個基礎型別，其必須是八種整數型別之一。</span><span class="sxs-lookup"><span data-stu-id="83735-176">Every `enum` type has an underlying type, which must be one of the eight integral types.</span></span> <span data-ttu-id="83735-177">`enum` 型別的值組與基礎型別的值組相同。</span><span class="sxs-lookup"><span data-stu-id="83735-177">The set of values of an `enum` type is the same as the set of values of the underlying type.</span></span>

<span data-ttu-id="83735-178">C# 支援任何型別的單一維度及多維陣列。</span><span class="sxs-lookup"><span data-stu-id="83735-178">C# supports single- and multi-dimensional arrays of any type.</span></span> <span data-ttu-id="83735-179">不同於上述型別，陣列型別不需宣告即可使用。</span><span class="sxs-lookup"><span data-stu-id="83735-179">Unlike the types listed above, array types do not have to be declared before they can be used.</span></span> <span data-ttu-id="83735-180">而陣列型別的建構方法，是在型別名稱之後加上方括弧。</span><span class="sxs-lookup"><span data-stu-id="83735-180">Instead, array types are constructed by following a type name with square brackets.</span></span> <span data-ttu-id="83735-181">例如，`int[]` 是 `int` 的單一維度陣列、`int[,]` 是 `int` 的雙維陣列，而 `int[][]` 是 `int` 的單一維度陣列的單一維度陣列。</span><span class="sxs-lookup"><span data-stu-id="83735-181">For example, `int[]` is a single-dimensional array of `int`, `int[,]` is a two-dimensional array of `int`, and `int[][]` is a single-dimensional array of single-dimensional array of `int`.</span></span>

<span data-ttu-id="83735-182">可為 Null 的實值型別不需宣告即可使用。</span><span class="sxs-lookup"><span data-stu-id="83735-182">Nullable value types also do not have to be declared before they can be used.</span></span> <span data-ttu-id="83735-183">針對每個不可為 Null 的實值型別 `T`，會有一個對應的可為 Null 實值型別 `T?`，其中可包含一個額外值 `null`。</span><span class="sxs-lookup"><span data-stu-id="83735-183">For each non-nullable value type `T` there is a corresponding nullable value type `T?`, which can hold an additional value, `null`.</span></span> <span data-ttu-id="83735-184">比方說，`int?` 是可包含任一 32 位元整數或值 `null` 的型別。</span><span class="sxs-lookup"><span data-stu-id="83735-184">For instance, `int?` is a type that can hold any 32-bit integer or the value `null`.</span></span>

<span data-ttu-id="83735-185">C# 的型別系統已整合，任何型別值均可視為一個 `object`。</span><span class="sxs-lookup"><span data-stu-id="83735-185">C#’s type system is unified such that a value of any type can be treated as an `object`.</span></span> <span data-ttu-id="83735-186">C# 中的每個型別都直接或間接衍生自 `object` 類別型別，而 `object` 是所有型別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="83735-186">Every type in C# directly or indirectly derives from the `object` class type, and `object` is the ultimate base class of all types.</span></span> <span data-ttu-id="83735-187">參考型別的值之所以會視為物件，只是將這些值當作 `object` 型別來檢視。</span><span class="sxs-lookup"><span data-stu-id="83735-187">Values of reference types are treated as objects simply by viewing the values as type `object`.</span></span> <span data-ttu-id="83735-188">數值型別的值之所以會視為物件，只是透過執行 *boxing* 和 *unboxing* 作業。</span><span class="sxs-lookup"><span data-stu-id="83735-188">Values of value types are treated as objects by performing *boxing* and *unboxing operations*.</span></span> <span data-ttu-id="83735-189">在下列範例中，`int` 值會轉換成 `object`，並再次轉換回 `int`。</span><span class="sxs-lookup"><span data-stu-id="83735-189">In the following example, an `int` value is converted to `object` and back again to `int`.</span></span>

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

<span data-ttu-id="83735-190">當實值型別的值轉換成 `object` 類型時，會配置一個 `object` 執行個體 (亦稱為「Box」) 以包含值，而值會複製到該方塊。</span><span class="sxs-lookup"><span data-stu-id="83735-190">When a value of a value type is converted to type `object`, an `object` instance, also called a "box", is allocated to hold the value, and the value is copied into that box.</span></span> <span data-ttu-id="83735-191">相反地，當 `object` 參考轉換為實值型別時，會檢查參考的 `object` 是否為數值型別正確的方塊，如果檢查成功，則會將方塊中的複製出來。</span><span class="sxs-lookup"><span data-stu-id="83735-191">Conversely, when an `object` reference is cast to a value type, a check is made that the referenced `object` is a box of the correct value type, and, if the check succeeds, the value in the box is copied out.</span></span>

<span data-ttu-id="83735-192">C# 的整合類型系統實際上表示實值型別可以「依需求」變成物件。</span><span class="sxs-lookup"><span data-stu-id="83735-192">C#’s unified type system effectively means that value types can become objects "on demand."</span></span> <span data-ttu-id="83735-193">因為整合，使用 `object` 型別的一般用途程式庫就能搭配參考型別和實值型別使用。</span><span class="sxs-lookup"><span data-stu-id="83735-193">Because of the unification, general-purpose libraries that use type `object` can be used with both reference types and value types.</span></span>

<span data-ttu-id="83735-194">C# 中有數種*變數*，包括欄位、陣列元素、區域變數和參數。</span><span class="sxs-lookup"><span data-stu-id="83735-194">There are several kinds of *variables* in C#, including fields, array elements, local variables, and parameters.</span></span> <span data-ttu-id="83735-195">變數表示儲存位置，每個變數都有一種型別，其決定哪些值可以儲存在變數中，如下所示。</span><span class="sxs-lookup"><span data-stu-id="83735-195">Variables represent storage locations, and every variable has a type that determines what values can be stored in the variable, as shown below.</span></span>

* <span data-ttu-id="83735-196">不可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="83735-196">Non-nullable value type</span></span>
    - <span data-ttu-id="83735-197">該型別的值</span><span class="sxs-lookup"><span data-stu-id="83735-197">A value of that exact type</span></span>
* <span data-ttu-id="83735-198">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="83735-198">Nullable value type</span></span>
    - <span data-ttu-id="83735-199">`null` 值或該型別的值</span><span class="sxs-lookup"><span data-stu-id="83735-199">A `null` value or a value of that exact type</span></span>
* <span data-ttu-id="83735-200">object</span><span class="sxs-lookup"><span data-stu-id="83735-200">object</span></span>
    - <span data-ttu-id="83735-201">`null` 參考、任一參考型別之物件的參考，或是任一實值型別的 Boxed 值的參考</span><span class="sxs-lookup"><span data-stu-id="83735-201">A `null` reference, a reference to an object of any reference type, or a reference to a boxed value of any value type</span></span>
* <span data-ttu-id="83735-202">類別型別</span><span class="sxs-lookup"><span data-stu-id="83735-202">Class type</span></span>
    - <span data-ttu-id="83735-203">`null` 參考、該類別型別之執行個體的參考，或衍生自該類別型別之類別執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="83735-203">A `null` reference, a reference to an instance of that class type, or a reference to an instance of a class derived from that class type</span></span>
* <span data-ttu-id="83735-204">介面類型</span><span class="sxs-lookup"><span data-stu-id="83735-204">Interface type</span></span>
    - <span data-ttu-id="83735-205">`null` 參考、實作該介面型別之類別型別的執行個體的參考，或實作該介面型別之實值型別的 Boxed 值的參考</span><span class="sxs-lookup"><span data-stu-id="83735-205">A `null` reference, a reference to an instance of a class type that implements that interface type, or a reference to a boxed value of a value type that implements that interface type</span></span>
* <span data-ttu-id="83735-206">陣列型別</span><span class="sxs-lookup"><span data-stu-id="83735-206">Array type</span></span>
    - <span data-ttu-id="83735-207">`null` 參考、該陣列型別之執行個體的參考，或相容的陣列型別之執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="83735-207">A `null` reference, a reference to an instance of that array type, or a reference to an instance of a compatible array type</span></span>
* <span data-ttu-id="83735-208">委派類型</span><span class="sxs-lookup"><span data-stu-id="83735-208">Delegate type</span></span>
    - <span data-ttu-id="83735-209">`null` 參考或相容的委派類型之執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="83735-209">A `null` reference or a reference to an instance of a compatible delegate type</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="83735-210">[上一頁](program-structure.md)
[下一頁](expressions.md)</span><span class="sxs-lookup"><span data-stu-id="83735-210">[Previous](program-structure.md)
[Next](expressions.md)</span></span>
