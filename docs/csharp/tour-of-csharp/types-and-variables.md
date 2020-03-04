---
title: C# 型別和變數 - C# 語言教學課程
description: 了解如何在 C# 中定義類型和宣告變數
ms.date: 02/25/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: b2a5255a243c12543a1cd59b5724b6c826306e04
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159087"
---
# <a name="types-and-variables"></a><span data-ttu-id="e3452-103">型別與變數</span><span class="sxs-lookup"><span data-stu-id="e3452-103">Types and variables</span></span>

<span data-ttu-id="e3452-104">C# 中有兩種型別：*實值型別*和*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="e3452-104">There are two kinds of types in C#: *value types* and *reference types*.</span></span> <span data-ttu-id="e3452-105">實值型別的變數直接包含其資料，而參考型別的變數則將參考儲存到其資料，後者即是物件。</span><span class="sxs-lookup"><span data-stu-id="e3452-105">Variables of value types directly contain their data whereas variables of reference types store references to their data, the latter being known as objects.</span></span> <span data-ttu-id="e3452-106">有了參考型別，兩個變數都可以參考相同的物件，因此對某個變數的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="e3452-106">With reference types, it's possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="e3452-107">使用實數值型別時，每個變數都有自己的資料複本，而且其中一個作業不可能影響另一個（`ref` 和 `out` 參數變數除外）。</span><span class="sxs-lookup"><span data-stu-id="e3452-107">With value types, the variables each have their own copy of the data, and it isn't possible for operations on one to affect the other (except for `ref` and `out` parameter variables).</span></span>

<span data-ttu-id="e3452-108">C# 的實值型別可進一步細分為*簡單型別*、*列舉型別*、*結構型別*和*可為 Null 的實值型別*。</span><span class="sxs-lookup"><span data-stu-id="e3452-108">C#’s value types are further divided into *simple types*, *enum types*, *struct types*, and *nullable value types*.</span></span> <span data-ttu-id="e3452-109">C# 的參考型別可進一步細分為*類別型別*、*介面型別*、*陣列型別*和*委派型別*。</span><span class="sxs-lookup"><span data-stu-id="e3452-109">C#’s reference types are further divided into *class types*, *interface types*, *array types*, and *delegate types*.</span></span>

<span data-ttu-id="e3452-110">下列大綱提供類型系統C#的總覽。</span><span class="sxs-lookup"><span data-stu-id="e3452-110">The following outline provides an overview of C#’s type system.</span></span>

- <span data-ttu-id="e3452-111">[值類型][ValueTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-111">[Value types][ValueTypes]</span></span>
  - <span data-ttu-id="e3452-112">[簡單型別][SimpleTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-112">[Simple types][SimpleTypes]</span></span>
    - <span data-ttu-id="e3452-113">帶正負號的整數︰`sbyte`、`short`、`int`、`long`</span><span class="sxs-lookup"><span data-stu-id="e3452-113">Signed integral: `sbyte`, `short`, `int`, `long`</span></span>
    - <span data-ttu-id="e3452-114">不帶正負號的整數︰`byte`、`ushort`、`uint`、`ulong`</span><span class="sxs-lookup"><span data-stu-id="e3452-114">Unsigned integral: `byte`, `ushort`, `uint`, `ulong`</span></span>
    - <span data-ttu-id="e3452-115">Unicode 字元：`char`</span><span class="sxs-lookup"><span data-stu-id="e3452-115">Unicode characters: `char`</span></span>
    - <span data-ttu-id="e3452-116">IEEE 二進位浮點：`float`、`double`</span><span class="sxs-lookup"><span data-stu-id="e3452-116">IEEE binary floating-point: `float`, `double`</span></span>
    - <span data-ttu-id="e3452-117">高精確度十進位浮點：`decimal`</span><span class="sxs-lookup"><span data-stu-id="e3452-117">High-precision decimal floating-point: `decimal`</span></span>
    - <span data-ttu-id="e3452-118">布林值：`bool`</span><span class="sxs-lookup"><span data-stu-id="e3452-118">Boolean: `bool`</span></span>
  - <span data-ttu-id="e3452-119">[列舉型別][EnumTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-119">[Enum types][EnumTypes]</span></span>
    - <span data-ttu-id="e3452-120">使用者定義型別，格式為 `enum E {...}`</span><span class="sxs-lookup"><span data-stu-id="e3452-120">User-defined types of the form `enum E {...}`</span></span>
  - <span data-ttu-id="e3452-121">[結構型別][StructTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-121">[Struct types][StructTypes]</span></span>
    - <span data-ttu-id="e3452-122">使用者定義型別，格式為 `struct S {...}`</span><span class="sxs-lookup"><span data-stu-id="e3452-122">User-defined types of the form `struct S {...}`</span></span>
  - <span data-ttu-id="e3452-123">[可為 Null 的實值型別][NullableTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-123">[Nullable value types][NullableTypes]</span></span>
    - <span data-ttu-id="e3452-124">含有 `null` 值的所有其他數值型別的擴充</span><span class="sxs-lookup"><span data-stu-id="e3452-124">Extensions of all other value types with a `null` value</span></span>
- <span data-ttu-id="e3452-125">[參考型別][ReferenceTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-125">[Reference types][ReferenceTypes]</span></span>
  - <span data-ttu-id="e3452-126">[類別型別][ClassTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-126">[Class types][ClassTypes]</span></span>
    - <span data-ttu-id="e3452-127">所有其他型別的基底類別︰`object`</span><span class="sxs-lookup"><span data-stu-id="e3452-127">Ultimate base class of all other types: `object`</span></span>
    - <span data-ttu-id="e3452-128">Unicode 字串：`string`</span><span class="sxs-lookup"><span data-stu-id="e3452-128">Unicode strings: `string`</span></span>
    - <span data-ttu-id="e3452-129">使用者定義型別，格式為 `class C {...}`</span><span class="sxs-lookup"><span data-stu-id="e3452-129">User-defined types of the form `class C {...}`</span></span>
  - <span data-ttu-id="e3452-130">[介面型別][InterfaceTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-130">[Interface types][InterfaceTypes]</span></span>
    - <span data-ttu-id="e3452-131">使用者定義型別，格式為 `interface I {...}`</span><span class="sxs-lookup"><span data-stu-id="e3452-131">User-defined types of the form `interface I {...}`</span></span>
  - <span data-ttu-id="e3452-132">[陣列類型][ArrayTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-132">[Array types][ArrayTypes]</span></span>
    - <span data-ttu-id="e3452-133">單一維度和多維度，例如 `int[]` 和 `int[,]`</span><span class="sxs-lookup"><span data-stu-id="e3452-133">Single- and multi-dimensional, for example, `int[]` and `int[,]`</span></span>
  - <span data-ttu-id="e3452-134">[委派型別][DelegateTypes]</span><span class="sxs-lookup"><span data-stu-id="e3452-134">[Delegate types][DelegateTypes]</span></span>
    - <span data-ttu-id="e3452-135">使用者定義型別，格式為 `delegate int D(...)`</span><span class="sxs-lookup"><span data-stu-id="e3452-135">User-defined types of the form `delegate int D(...)`</span></span>

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

<span data-ttu-id="e3452-136">如需數值型別的詳細資訊，請參閱[整數型別](../language-reference/builtin-types/integral-numeric-types.md)和[浮點數型別表](../language-reference/builtin-types/floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e3452-136">For more information about numeric types, see [Integral types](../language-reference/builtin-types/integral-numeric-types.md) and [Floating-point types table](../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>

<span data-ttu-id="e3452-137">C# 的 `bool` 型別用來代表布林值 — 此值不是 `true` 就是 `false`。</span><span class="sxs-lookup"><span data-stu-id="e3452-137">C#’s `bool` type is used to represent Boolean values—values that are either `true` or `false`.</span></span>

<span data-ttu-id="e3452-138">C# 中的字元和字串處理使用 Unicode 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="e3452-138">Character and string processing in C# uses Unicode encoding.</span></span> <span data-ttu-id="e3452-139">`char` 型別代表 UTF-16 程式碼單位，而 `string` 型別代表一系列的 UTF-16 程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="e3452-139">The `char` type represents a UTF-16 code unit, and the `string` type represents a sequence of UTF-16 code units.</span></span>

<span data-ttu-id="e3452-140">C# 程式使用*型別宣告*來建立新型別。</span><span class="sxs-lookup"><span data-stu-id="e3452-140">C# programs use *type declarations* to create new types.</span></span> <span data-ttu-id="e3452-141">型別宣告指定新型別的名稱成員。</span><span class="sxs-lookup"><span data-stu-id="e3452-141">A type declaration specifies the name and the members of the new type.</span></span> <span data-ttu-id="e3452-142">可由使用者定義的五種 C# 型別類型︰類別型別、結構型別、介面型別、列舉型別及委派型別。</span><span class="sxs-lookup"><span data-stu-id="e3452-142">Five of C#’s categories of types are user-definable: class types, struct types, interface types, enum types, and delegate types.</span></span>

<span data-ttu-id="e3452-143">`class` 型別定義資料結構，其中包含資料成員 (欄位) 和函式成員 (方法、屬性及其他)。</span><span class="sxs-lookup"><span data-stu-id="e3452-143">A `class` type defines a data structure that contains data members (fields) and function members (methods, properties, and others).</span></span> <span data-ttu-id="e3452-144">類別型別支援單一繼承和多型，這些是可供衍生類別將基底類別延伸及特製化的機制。</span><span class="sxs-lookup"><span data-stu-id="e3452-144">Class types support single inheritance and polymorphism, mechanisms whereby derived classes can extend and specialize base classes.</span></span>

<span data-ttu-id="e3452-145">`struct` 型別與類別型別相似，它代表具有資料成員和函式成員的結構。</span><span class="sxs-lookup"><span data-stu-id="e3452-145">A `struct` type is similar to a class type in that it represents a structure with data members and function members.</span></span> <span data-ttu-id="e3452-146">不過，不同于類別，結構是實數值型別，通常不需要堆積配置。</span><span class="sxs-lookup"><span data-stu-id="e3452-146">However, unlike classes, structs are value types and don't typically require heap allocation.</span></span> <span data-ttu-id="e3452-147">結構類型不支援使用者指定的繼承，而且所有結構類型都隱含地繼承自類型 `object`。</span><span class="sxs-lookup"><span data-stu-id="e3452-147">Struct types don't support user-specified inheritance, and all struct types implicitly inherit from type `object`.</span></span>

<span data-ttu-id="e3452-148">`interface` 型別將協定定義為一組具名的公用函式成員。</span><span class="sxs-lookup"><span data-stu-id="e3452-148">An `interface` type defines a contract as a named set of public function members.</span></span> <span data-ttu-id="e3452-149">實作 `class` 的 `struct` 或 `interface` 必須提供介面的函式成員的實作。</span><span class="sxs-lookup"><span data-stu-id="e3452-149">A `class` or `struct` that implements an `interface` must provide implementations of the interface’s function members.</span></span> <span data-ttu-id="e3452-150">`interface` 可以繼承自多個基底介面，`class` 或 `struct`可實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="e3452-150">An `interface` may inherit from multiple base interfaces, and a `class` or `struct` may implement multiple interfaces.</span></span>

<span data-ttu-id="e3452-151">`delegate` 型別代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="e3452-151">A `delegate` type represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="e3452-152">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="e3452-152">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="e3452-153">委派類似函式語言提供的函式型別。</span><span class="sxs-lookup"><span data-stu-id="e3452-153">Delegates are analogous to function types provided by functional languages.</span></span> <span data-ttu-id="e3452-154">它們也類似于其他語言中的函式指標概念。</span><span class="sxs-lookup"><span data-stu-id="e3452-154">They're also similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="e3452-155">不同于函式指標，委派是物件導向且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="e3452-155">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="e3452-156">`class`、`struct`、`interface`和 `delegate` 類型全都支援泛型，因此它們可以使用其他類型進行參數化。</span><span class="sxs-lookup"><span data-stu-id="e3452-156">The `class`, `struct`, `interface`, and `delegate` types all support generics, whereby they can be parameterized with other types.</span></span>

<span data-ttu-id="e3452-157">`enum` 型別是包含具名常數的不同型別。</span><span class="sxs-lookup"><span data-stu-id="e3452-157">An `enum` type is a distinct type with named constants.</span></span> <span data-ttu-id="e3452-158">每個 `enum` 型別都具有一個基礎型別，其必須是八種整數型別之一。</span><span class="sxs-lookup"><span data-stu-id="e3452-158">Every `enum` type has an underlying type, which must be one of the eight integral types.</span></span> <span data-ttu-id="e3452-159">`enum` 型別的值組與基礎型別的值組相同。</span><span class="sxs-lookup"><span data-stu-id="e3452-159">The set of values of an `enum` type is the same as the set of values of the underlying type.</span></span>

<span data-ttu-id="e3452-160">C# 支援任何型別的單一維度及多維陣列。</span><span class="sxs-lookup"><span data-stu-id="e3452-160">C# supports single- and multi-dimensional arrays of any type.</span></span> <span data-ttu-id="e3452-161">不同于以上所列的類型，陣列類型不需要先宣告，就可以使用它們。</span><span class="sxs-lookup"><span data-stu-id="e3452-161">Unlike the types listed above, array types don't have to be declared before they can be used.</span></span> <span data-ttu-id="e3452-162">而陣列型別的建構方法，是在型別名稱之後加上方括弧。</span><span class="sxs-lookup"><span data-stu-id="e3452-162">Instead, array types are constructed by following a type name with square brackets.</span></span> <span data-ttu-id="e3452-163">例如，`int[]` 是 `int` 的單一維度陣列、`int[,]` 是 `int` 的雙維陣列，而 `int[][]` 是 `int` 的單一維度陣列的單一維度陣列。</span><span class="sxs-lookup"><span data-stu-id="e3452-163">For example, `int[]` is a single-dimensional array of `int`, `int[,]` is a two-dimensional array of `int`, and `int[][]` is a single-dimensional array of single-dimensional array of `int`.</span></span>

<span data-ttu-id="e3452-164">可為 null 的實數值型別也不需要宣告，就可以使用它們。</span><span class="sxs-lookup"><span data-stu-id="e3452-164">Nullable value types also don't have to be declared before they can be used.</span></span> <span data-ttu-id="e3452-165">針對每一個不可為 null 的實數值型別 `T`，有一個對應的可為 null 實數值型別 `T?`，可以保留額外的值 `null`。</span><span class="sxs-lookup"><span data-stu-id="e3452-165">For each non-nullable value type `T`, there is a corresponding nullable value type `T?`, which can hold an additional value, `null`.</span></span> <span data-ttu-id="e3452-166">比方說，`int?` 是可包含任一 32 位元整數或值 `null` 的型別。</span><span class="sxs-lookup"><span data-stu-id="e3452-166">For instance, `int?` is a type that can hold any 32-bit integer or the value `null`.</span></span>

<span data-ttu-id="e3452-167">C# 的型別系統已整合，任何型別值均可視為一個 `object`。</span><span class="sxs-lookup"><span data-stu-id="e3452-167">C#’s type system is unified such that a value of any type can be treated as an `object`.</span></span> <span data-ttu-id="e3452-168">C# 中的每個型別都直接或間接衍生自 `object` 類別型別，而 `object` 是所有型別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="e3452-168">Every type in C# directly or indirectly derives from the `object` class type, and `object` is the ultimate base class of all types.</span></span> <span data-ttu-id="e3452-169">參考型別的值之所以會視為物件，只是將這些值當作 `object` 型別來檢視。</span><span class="sxs-lookup"><span data-stu-id="e3452-169">Values of reference types are treated as objects simply by viewing the values as type `object`.</span></span> <span data-ttu-id="e3452-170">數值型別的值之所以會視為物件，只是透過執行 *boxing* 和 *unboxing* 作業。</span><span class="sxs-lookup"><span data-stu-id="e3452-170">Values of value types are treated as objects by performing *boxing* and *unboxing operations*.</span></span> <span data-ttu-id="e3452-171">在下列範例中，`int` 值會轉換成 `object`，並再次轉換回 `int`。</span><span class="sxs-lookup"><span data-stu-id="e3452-171">In the following example, an `int` value is converted to `object` and back again to `int`.</span></span>

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

<span data-ttu-id="e3452-172">當實值型別的值轉換成 `object` 類型時，會配置一個 `object` 執行個體 (亦稱為「Box」) 以包含值，而值會複製到該方塊。</span><span class="sxs-lookup"><span data-stu-id="e3452-172">When a value of a value type is converted to type `object`, an `object` instance, also called a "box", is allocated to hold the value, and the value is copied into that box.</span></span> <span data-ttu-id="e3452-173">相反地，當 `object` 參考轉換為實值型別時，會檢查參考的 `object` 是否為數值型別正確的方塊，如果檢查成功，則會將方塊中的複製出來。</span><span class="sxs-lookup"><span data-stu-id="e3452-173">Conversely, when an `object` reference is cast to a value type, a check is made that the referenced `object` is a box of the correct value type, and, if the check succeeds, the value in the box is copied out.</span></span>

<span data-ttu-id="e3452-174">C# 的整合類型系統實際上表示實值型別可以「依需求」變成物件。</span><span class="sxs-lookup"><span data-stu-id="e3452-174">C#’s unified type system effectively means that value types can become objects "on demand."</span></span> <span data-ttu-id="e3452-175">因為整合，使用 `object` 型別的一般用途程式庫就能搭配參考型別和實值型別使用。</span><span class="sxs-lookup"><span data-stu-id="e3452-175">Because of the unification, general-purpose libraries that use type `object` can be used with both reference types and value types.</span></span>

<span data-ttu-id="e3452-176">C# 中有數種*變數*，包括欄位、陣列元素、區域變數和參數。</span><span class="sxs-lookup"><span data-stu-id="e3452-176">There are several kinds of *variables* in C#, including fields, array elements, local variables, and parameters.</span></span> <span data-ttu-id="e3452-177">變數表示儲存位置，每個變數都有一種型別，其決定哪些值可以儲存在變數中，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e3452-177">Variables represent storage locations, and every variable has a type that determines what values can be stored in the variable, as shown below.</span></span>

- <span data-ttu-id="e3452-178">不可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="e3452-178">Non-nullable value type</span></span>
  - <span data-ttu-id="e3452-179">該型別的值</span><span class="sxs-lookup"><span data-stu-id="e3452-179">A value of that exact type</span></span>
- <span data-ttu-id="e3452-180">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="e3452-180">Nullable value type</span></span>
  - <span data-ttu-id="e3452-181">`null` 值或該型別的值</span><span class="sxs-lookup"><span data-stu-id="e3452-181">A `null` value or a value of that exact type</span></span>
- <span data-ttu-id="e3452-182">物件 (object)</span><span class="sxs-lookup"><span data-stu-id="e3452-182">object</span></span>
  - <span data-ttu-id="e3452-183">`null` 參考、任一參考型別之物件的參考，或是任一實值型別的 Boxed 值的參考</span><span class="sxs-lookup"><span data-stu-id="e3452-183">A `null` reference, a reference to an object of any reference type, or a reference to a boxed value of any value type</span></span>
- <span data-ttu-id="e3452-184">類別型別</span><span class="sxs-lookup"><span data-stu-id="e3452-184">Class type</span></span>
  - <span data-ttu-id="e3452-185">`null` 參考、該類別型別之執行個體的參考，或衍生自該類別型別之類別執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="e3452-185">A `null` reference, a reference to an instance of that class type, or a reference to an instance of a class derived from that class type</span></span>
- <span data-ttu-id="e3452-186">介面類型</span><span class="sxs-lookup"><span data-stu-id="e3452-186">Interface type</span></span>
  - <span data-ttu-id="e3452-187">`null` 參考、實作該介面型別之類別型別的執行個體的參考，或實作該介面型別之實值型別的 Boxed 值的參考</span><span class="sxs-lookup"><span data-stu-id="e3452-187">A `null` reference, a reference to an instance of a class type that implements that interface type, or a reference to a boxed value of a value type that implements that interface type</span></span>
- <span data-ttu-id="e3452-188">陣列型別</span><span class="sxs-lookup"><span data-stu-id="e3452-188">Array type</span></span>
  - <span data-ttu-id="e3452-189">`null` 參考、該陣列型別之執行個體的參考，或相容的陣列型別之執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="e3452-189">A `null` reference, a reference to an instance of that array type, or a reference to an instance of a compatible array type</span></span>
- <span data-ttu-id="e3452-190">委派類型</span><span class="sxs-lookup"><span data-stu-id="e3452-190">Delegate type</span></span>
  - <span data-ttu-id="e3452-191">`null` 參考或相容的委派類型之執行個體的參考</span><span class="sxs-lookup"><span data-stu-id="e3452-191">A `null` reference or a reference to an instance of a compatible delegate type</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="e3452-192">[上一頁](program-structure.md)
> [下一頁](expressions.md)</span><span class="sxs-lookup"><span data-stu-id="e3452-192">[Previous](program-structure.md)
[Next](expressions.md)</span></span>
