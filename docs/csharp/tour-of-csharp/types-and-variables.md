---
title: C# 型別和變數 - C# 語言教學課程
description: 了解如何在 C# 中定義類型和宣告變數
ms.date: 04/24/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 6a3bd3dc802f0d080fd96036067f709e62faf426
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141000"
---
# <a name="types-and-variables"></a><span data-ttu-id="3978a-103">型別與變數</span><span class="sxs-lookup"><span data-stu-id="3978a-103">Types and variables</span></span>

<span data-ttu-id="3978a-104">C# 中有兩種型別：*實值型別*和*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="3978a-104">There are two kinds of types in C#: *value types* and *reference types*.</span></span> <span data-ttu-id="3978a-105">實值型別的變數直接包含其資料，而參考型別的變數則將參考儲存到其資料，後者即是物件。</span><span class="sxs-lookup"><span data-stu-id="3978a-105">Variables of value types directly contain their data whereas variables of reference types store references to their data, the latter being known as objects.</span></span> <span data-ttu-id="3978a-106">有了參考型別，兩個變數都可以參考相同的物件，因此對某個變數的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="3978a-106">With reference types, it's possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="3978a-107">使用實數值型別時，每個變數都有自己的資料複本，而且其中一個作業不可能影響另一個（ `ref`和`out`參數變數除外）。</span><span class="sxs-lookup"><span data-stu-id="3978a-107">With value types, the variables each have their own copy of the data, and it isn't possible for operations on one to affect the other (except for `ref` and `out` parameter variables).</span></span>

<span data-ttu-id="3978a-108">C # 的實值型別會進一步分成*簡單*型別、*列舉*型別、*結構*型別和*可為 null*的實值型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-108">C#'s value types are further divided into *simple types*, *enum types*, *struct types*, and *nullable value types*.</span></span> <span data-ttu-id="3978a-109">C # 的參考型別會進一步分割成*類別類型*、*介面類別型*、*陣列類型*和*委派類型*。</span><span class="sxs-lookup"><span data-stu-id="3978a-109">C#'s reference types are further divided into *class types*, *interface types*, *array types*, and *delegate types*.</span></span>

<span data-ttu-id="3978a-110">下列大綱提供 c # 型別系統的總覽。</span><span class="sxs-lookup"><span data-stu-id="3978a-110">The following outline provides an overview of C#'s type system.</span></span>

- <span data-ttu-id="3978a-111">[值類型][ValueTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-111">[Value types][ValueTypes]</span></span>
  - <span data-ttu-id="3978a-112">[簡單型別][SimpleTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-112">[Simple types][SimpleTypes]</span></span>
    - <span data-ttu-id="3978a-113">帶正負號的整數︰`sbyte`、`short`、`int`、`long`</span><span class="sxs-lookup"><span data-stu-id="3978a-113">Signed integral: `sbyte`, `short`, `int`, `long`</span></span>
    - <span data-ttu-id="3978a-114">不帶正負號的整數︰`byte`、`ushort`、`uint`、`ulong`</span><span class="sxs-lookup"><span data-stu-id="3978a-114">Unsigned integral: `byte`, `ushort`, `uint`, `ulong`</span></span>
    - <span data-ttu-id="3978a-115">Unicode 字元：`char`</span><span class="sxs-lookup"><span data-stu-id="3978a-115">Unicode characters: `char`</span></span>
    - <span data-ttu-id="3978a-116">IEEE 二進位浮點：`float`、`double`</span><span class="sxs-lookup"><span data-stu-id="3978a-116">IEEE binary floating-point: `float`, `double`</span></span>
    - <span data-ttu-id="3978a-117">高精確度十進位浮點：`decimal`</span><span class="sxs-lookup"><span data-stu-id="3978a-117">High-precision decimal floating-point: `decimal`</span></span>
    - <span data-ttu-id="3978a-118">布林值：`bool`</span><span class="sxs-lookup"><span data-stu-id="3978a-118">Boolean: `bool`</span></span>
  - <span data-ttu-id="3978a-119">[列舉類型][EnumTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-119">[Enum types][EnumTypes]</span></span>
    - <span data-ttu-id="3978a-120">使用者定義型別，格式為 `enum E {...}`</span><span class="sxs-lookup"><span data-stu-id="3978a-120">User-defined types of the form `enum E {...}`</span></span>
  - <span data-ttu-id="3978a-121">[結構型別][StructTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-121">[Struct types][StructTypes]</span></span>
    - <span data-ttu-id="3978a-122">使用者定義型別，格式為 `struct S {...}`</span><span class="sxs-lookup"><span data-stu-id="3978a-122">User-defined types of the form `struct S {...}`</span></span>
  - <span data-ttu-id="3978a-123">[可為 null 的實數值型別][NullableTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-123">[Nullable value types][NullableTypes]</span></span>
    - <span data-ttu-id="3978a-124">含有 `null` 值的所有其他數值型別的擴充</span><span class="sxs-lookup"><span data-stu-id="3978a-124">Extensions of all other value types with a `null` value</span></span>
  - <span data-ttu-id="3978a-125">[元組數值型別][TupleTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-125">[Tuple value types][TupleTypes]</span></span>
    - <span data-ttu-id="3978a-126">使用者定義型別，格式為 `(T1, T2, ...)`</span><span class="sxs-lookup"><span data-stu-id="3978a-126">User-defined types of the form `(T1, T2, ...)`</span></span>
- <span data-ttu-id="3978a-127">[參考型別][ReferenceTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-127">[Reference types][ReferenceTypes]</span></span>
  - <span data-ttu-id="3978a-128">[類別類型][ClassTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-128">[Class types][ClassTypes]</span></span>
    - <span data-ttu-id="3978a-129">所有其他型別的基底類別︰`object`</span><span class="sxs-lookup"><span data-stu-id="3978a-129">Ultimate base class of all other types: `object`</span></span>
    - <span data-ttu-id="3978a-130">Unicode 字串：`string`</span><span class="sxs-lookup"><span data-stu-id="3978a-130">Unicode strings: `string`</span></span>
    - <span data-ttu-id="3978a-131">使用者定義型別，格式為 `class C {...}`</span><span class="sxs-lookup"><span data-stu-id="3978a-131">User-defined types of the form `class C {...}`</span></span>
  - <span data-ttu-id="3978a-132">[介面型別][InterfaceTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-132">[Interface types][InterfaceTypes]</span></span>
    - <span data-ttu-id="3978a-133">使用者定義型別，格式為 `interface I {...}`</span><span class="sxs-lookup"><span data-stu-id="3978a-133">User-defined types of the form `interface I {...}`</span></span>
  - <span data-ttu-id="3978a-134">[陣列類型][ArrayTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-134">[Array types][ArrayTypes]</span></span>
    - <span data-ttu-id="3978a-135">單一維度和多維度，例如 `int[]` 和 `int[,]`</span><span class="sxs-lookup"><span data-stu-id="3978a-135">Single- and multi-dimensional, for example, `int[]` and `int[,]`</span></span>
  - <span data-ttu-id="3978a-136">[委派型別][DelegateTypes]</span><span class="sxs-lookup"><span data-stu-id="3978a-136">[Delegate types][DelegateTypes]</span></span>
    - <span data-ttu-id="3978a-137">使用者定義型別，格式為 `delegate int D(...)`</span><span class="sxs-lookup"><span data-stu-id="3978a-137">User-defined types of the form `delegate int D(...)`</span></span>

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[TupleTypes]: ../tuples.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

<span data-ttu-id="3978a-138">如需數值型別的詳細資訊，請參閱[整數型別](../language-reference/builtin-types/integral-numeric-types.md)和[浮點數型別表](../language-reference/builtin-types/floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3978a-138">For more information about numeric types, see [Integral types](../language-reference/builtin-types/integral-numeric-types.md) and [Floating-point types table](../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>

<span data-ttu-id="3978a-139">C # `bool`的型別用來代表布林值，也就是`true`或`false`的值。</span><span class="sxs-lookup"><span data-stu-id="3978a-139">C#'s `bool` type is used to represent Boolean values—values that are either `true` or `false`.</span></span>

<span data-ttu-id="3978a-140">C# 中的字元和字串處理使用 Unicode 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="3978a-140">Character and string processing in C# uses Unicode encoding.</span></span> <span data-ttu-id="3978a-141">`char` 型別代表 UTF-16 程式碼單位，而 `string` 型別代表一系列的 UTF-16 程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="3978a-141">The `char` type represents a UTF-16 code unit, and the `string` type represents a sequence of UTF-16 code units.</span></span>

<span data-ttu-id="3978a-142">C# 程式使用*型別宣告*來建立新型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-142">C# programs use *type declarations* to create new types.</span></span> <span data-ttu-id="3978a-143">型別宣告指定新型別的名稱成員。</span><span class="sxs-lookup"><span data-stu-id="3978a-143">A type declaration specifies the name and the members of the new type.</span></span> <span data-ttu-id="3978a-144">C # 的型別類別有五種是使用者可定義的：類別類型、結構類型、介面類別型、列舉類型和委派類型。</span><span class="sxs-lookup"><span data-stu-id="3978a-144">Five of C#'s categories of types are user-definable: class types, struct types, interface types, enum types, and delegate types.</span></span>

<span data-ttu-id="3978a-145">`class` 型別定義資料結構，其中包含資料成員 (欄位) 和函式成員 (方法、屬性及其他)。</span><span class="sxs-lookup"><span data-stu-id="3978a-145">A `class` type defines a data structure that contains data members (fields) and function members (methods, properties, and others).</span></span> <span data-ttu-id="3978a-146">類別型別支援單一繼承和多型，這些是可供衍生類別將基底類別延伸及特製化的機制。</span><span class="sxs-lookup"><span data-stu-id="3978a-146">Class types support single inheritance and polymorphism, mechanisms whereby derived classes can extend and specialize base classes.</span></span>

<span data-ttu-id="3978a-147">`struct` 型別與類別型別相似，它代表具有資料成員和函式成員的結構。</span><span class="sxs-lookup"><span data-stu-id="3978a-147">A `struct` type is similar to a class type in that it represents a structure with data members and function members.</span></span> <span data-ttu-id="3978a-148">不過，不同于類別，結構是實數值型別，通常不需要堆積配置。</span><span class="sxs-lookup"><span data-stu-id="3978a-148">However, unlike classes, structs are value types and don't typically require heap allocation.</span></span> <span data-ttu-id="3978a-149">結構類型不支援使用者指定的繼承，而且所有結構類型都隱含地繼承`object`自類型。</span><span class="sxs-lookup"><span data-stu-id="3978a-149">Struct types don't support user-specified inheritance, and all struct types implicitly inherit from type `object`.</span></span>

<span data-ttu-id="3978a-150">`interface` 型別將協定定義為一組具名的公用函式成員。</span><span class="sxs-lookup"><span data-stu-id="3978a-150">An `interface` type defines a contract as a named set of public function members.</span></span> <span data-ttu-id="3978a-151">執行`class`的`struct`或`interface`必須提供介面的函式成員的實作為。</span><span class="sxs-lookup"><span data-stu-id="3978a-151">A `class` or `struct` that implements an `interface` must provide implementations of the interface's function members.</span></span> <span data-ttu-id="3978a-152">`interface` 可以繼承自多個基底介面，`class` 或 `struct`可實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="3978a-152">An `interface` may inherit from multiple base interfaces, and a `class` or `struct` may implement multiple interfaces.</span></span>

<span data-ttu-id="3978a-153">`delegate` 型別代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-153">A `delegate` type represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="3978a-154">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="3978a-154">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="3978a-155">委派類似函式語言提供的函式型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-155">Delegates are analogous to function types provided by functional languages.</span></span> <span data-ttu-id="3978a-156">它們也類似于其他語言中的函式指標概念。</span><span class="sxs-lookup"><span data-stu-id="3978a-156">They're also similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="3978a-157">不同于函式指標，委派是物件導向且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="3978a-157">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="3978a-158">`class`、 `struct`、 `interface`和`delegate`類型全都支援泛型，因此可以使用其他類型來參數化。</span><span class="sxs-lookup"><span data-stu-id="3978a-158">The `class`, `struct`, `interface`, and `delegate` types all support generics, whereby they can be parameterized with other types.</span></span>

<span data-ttu-id="3978a-159">`enum` 型別是包含具名常數的不同型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-159">An `enum` type is a distinct type with named constants.</span></span> <span data-ttu-id="3978a-160">每個 `enum` 型別都具有一個基礎型別，其必須是八種整數型別之一。</span><span class="sxs-lookup"><span data-stu-id="3978a-160">Every `enum` type has an underlying type, which must be one of the eight integral types.</span></span> <span data-ttu-id="3978a-161">`enum` 型別的值組與基礎型別的值組相同。</span><span class="sxs-lookup"><span data-stu-id="3978a-161">The set of values of an `enum` type is the same as the set of values of the underlying type.</span></span>

<span data-ttu-id="3978a-162">C# 支援任何型別的單一維度及多維陣列。</span><span class="sxs-lookup"><span data-stu-id="3978a-162">C# supports single- and multi-dimensional arrays of any type.</span></span> <span data-ttu-id="3978a-163">不同于以上所列的類型，陣列類型不需要先宣告，就可以使用它們。</span><span class="sxs-lookup"><span data-stu-id="3978a-163">Unlike the types listed above, array types don't have to be declared before they can be used.</span></span> <span data-ttu-id="3978a-164">而陣列型別的建構方法，是在型別名稱之後加上方括弧。</span><span class="sxs-lookup"><span data-stu-id="3978a-164">Instead, array types are constructed by following a type name with square brackets.</span></span> <span data-ttu-id="3978a-165">例如，`int[]` 是 `int` 的單一維度陣列、`int[,]` 是 `int` 的雙維陣列，而 `int[][]` 是 `int` 的單一維度陣列的單一維度陣列。</span><span class="sxs-lookup"><span data-stu-id="3978a-165">For example, `int[]` is a single-dimensional array of `int`, `int[,]` is a two-dimensional array of `int`, and `int[][]` is a single-dimensional array of single-dimensional array of `int`.</span></span>

<span data-ttu-id="3978a-166">可為 null 的實數值型別也不需要宣告，就可以使用它們。</span><span class="sxs-lookup"><span data-stu-id="3978a-166">Nullable value types also don't have to be declared before they can be used.</span></span> <span data-ttu-id="3978a-167">針對每一個不可為 null 的`T`實數值型別，有一個對應的`T?`可為 null 實數值型別，可以`null`保留額外的值。</span><span class="sxs-lookup"><span data-stu-id="3978a-167">For each non-nullable value type `T`, there is a corresponding nullable value type `T?`, which can hold an additional value, `null`.</span></span> <span data-ttu-id="3978a-168">比方說，`int?` 是可包含任一 32 位元整數或值 `null` 的型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-168">For instance, `int?` is a type that can hold any 32-bit integer or the value `null`.</span></span>

<span data-ttu-id="3978a-169">C # 的類型系統是統一的，因此可以將任何類型的值視為`object`。</span><span class="sxs-lookup"><span data-stu-id="3978a-169">C#'s type system is unified such that a value of any type can be treated as an `object`.</span></span> <span data-ttu-id="3978a-170">C# 中的每個型別都直接或間接衍生自 `object` 類別型別，而 `object` 是所有型別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="3978a-170">Every type in C# directly or indirectly derives from the `object` class type, and `object` is the ultimate base class of all types.</span></span> <span data-ttu-id="3978a-171">參考型別的值之所以會視為物件，只是將這些值當作 `object` 型別來檢視。</span><span class="sxs-lookup"><span data-stu-id="3978a-171">Values of reference types are treated as objects simply by viewing the values as type `object`.</span></span> <span data-ttu-id="3978a-172">數值型別的值之所以會視為物件，只是透過執行 *boxing* 和 *unboxing* 作業。</span><span class="sxs-lookup"><span data-stu-id="3978a-172">Values of value types are treated as objects by performing *boxing* and *unboxing operations*.</span></span> <span data-ttu-id="3978a-173">在下列範例中，`int` 值會轉換成 `object`，並再次轉換回 `int`。</span><span class="sxs-lookup"><span data-stu-id="3978a-173">In the following example, an `int` value is converted to `object` and back again to `int`.</span></span>

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

<span data-ttu-id="3978a-174">當實數值型別的值指派給`object`參考時，會配置 "box" 來保存值。</span><span class="sxs-lookup"><span data-stu-id="3978a-174">When a value of a value type is assigned to an `object` reference, a "box" is allocated to hold the value.</span></span> <span data-ttu-id="3978a-175">該方塊是參考型別的實例，而值會複製到該方塊中。</span><span class="sxs-lookup"><span data-stu-id="3978a-175">That box is an instance of a reference type, and the value is copied into that box.</span></span> <span data-ttu-id="3978a-176">相反地，當`object`參考轉換成實值型別時，就會檢查參考的`object`是否為正確值型別的方塊。</span><span class="sxs-lookup"><span data-stu-id="3978a-176">Conversely, when an `object` reference is cast to a value type, a check is made that the referenced `object` is a box of the correct value type.</span></span> <span data-ttu-id="3978a-177">如果檢查成功，則會將方塊中的值複製到實數值型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-177">If the check succeeds, the value in the box is copied to the value type.</span></span>

<span data-ttu-id="3978a-178">C # 的統一型別系統實際上表示實值型別`object`會被視為「視需要」參考。</span><span class="sxs-lookup"><span data-stu-id="3978a-178">C#'s unified type system effectively means that value types are treated as `object` references "on demand."</span></span> <span data-ttu-id="3978a-179">由於使用類型`object`的統一、一般用途程式庫可以與衍生自`object`的所有類型搭配使用，包括參考型別和實數值型別。</span><span class="sxs-lookup"><span data-stu-id="3978a-179">Because of the unification, general-purpose libraries that use type `object` can be used with all types that derive from `object`, including both reference types and value types.</span></span>

<span data-ttu-id="3978a-180">C# 中有數種*變數*，包括欄位、陣列元素、區域變數和參數。</span><span class="sxs-lookup"><span data-stu-id="3978a-180">There are several kinds of *variables* in C#, including fields, array elements, local variables, and parameters.</span></span> <span data-ttu-id="3978a-181">變數表示儲存位置，每個變數都有一種型別，其決定哪些值可以儲存在變數中，如下所示。</span><span class="sxs-lookup"><span data-stu-id="3978a-181">Variables represent storage locations, and every variable has a type that determines what values can be stored in the variable, as shown below.</span></span>

- <span data-ttu-id="3978a-182">不可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="3978a-182">Non-nullable value type</span></span>
  - <span data-ttu-id="3978a-183">該型別的值</span><span class="sxs-lookup"><span data-stu-id="3978a-183">A value of that exact type</span></span>
- <span data-ttu-id="3978a-184">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="3978a-184">Nullable value type</span></span>
  - <span data-ttu-id="3978a-185">`null` 值或該型別的值</span><span class="sxs-lookup"><span data-stu-id="3978a-185">A `null` value or a value of that exact type</span></span>
- <span data-ttu-id="3978a-186">物件</span><span class="sxs-lookup"><span data-stu-id="3978a-186">object</span></span>
  - <span data-ttu-id="3978a-187">`null` 參考、任一參考型別之物件的參考，或是任一實值型別的 Boxed 值的參考</span><span class="sxs-lookup"><span data-stu-id="3978a-187">A `null` reference, a reference to an object of any reference type, or a reference to a boxed value of any value type</span></span>
- <span data-ttu-id="3978a-188">類別型別</span><span class="sxs-lookup"><span data-stu-id="3978a-188">Class type</span></span>
  - <span data-ttu-id="3978a-189">`null` 參考、該類別型別之執行個體的參考，或衍生自該類別型別之類別執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="3978a-189">A `null` reference, a reference to an instance of that class type, or a reference to an instance of a class derived from that class type</span></span>
- <span data-ttu-id="3978a-190">介面類型</span><span class="sxs-lookup"><span data-stu-id="3978a-190">Interface type</span></span>
  - <span data-ttu-id="3978a-191">`null` 參考、實作該介面型別之類別型別的執行個體的參考，或實作該介面型別之實值型別的 Boxed 值的參考</span><span class="sxs-lookup"><span data-stu-id="3978a-191">A `null` reference, a reference to an instance of a class type that implements that interface type, or a reference to a boxed value of a value type that implements that interface type</span></span>
- <span data-ttu-id="3978a-192">陣列型別</span><span class="sxs-lookup"><span data-stu-id="3978a-192">Array type</span></span>
  - <span data-ttu-id="3978a-193">`null` 參考、該陣列型別之執行個體的參考，或相容的陣列型別之執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="3978a-193">A `null` reference, a reference to an instance of that array type, or a reference to an instance of a compatible array type</span></span>
- <span data-ttu-id="3978a-194">委派類型</span><span class="sxs-lookup"><span data-stu-id="3978a-194">Delegate type</span></span>
  - <span data-ttu-id="3978a-195">`null` 參考或相容的委派類型之執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="3978a-195">A `null` reference or a reference to an instance of a compatible delegate type</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="3978a-196">[上一頁](program-structure.md)
> [下一頁](expressions.md)</span><span class="sxs-lookup"><span data-stu-id="3978a-196">[Previous](program-structure.md)
[Next](expressions.md)</span></span>
