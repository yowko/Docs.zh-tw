---
title: 指標類型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7f04cfbac72008332a429c4e0ad8bd3f4e60cc83
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880334"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="255ad-102">指標類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="255ad-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="255ad-103">在 unsafe 內容中，類型有可能是指標類型、實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="255ad-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="255ad-104">指標類型宣告會使用下列其中一種格式：</span><span class="sxs-lookup"><span data-stu-id="255ad-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="255ad-105">在指標型別中的 `*` 之前指定的型別稱為**參考型別**。</span><span class="sxs-lookup"><span data-stu-id="255ad-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="255ad-106">下列任一種型別都可能是參考型別：</span><span class="sxs-lookup"><span data-stu-id="255ad-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="255ad-107">任何整數類型：[sbyte](../../language-reference/keywords/sbyte.md)、[byte](../../language-reference/keywords/byte.md)、[short](../../language-reference/keywords/short.md)、[ushort](../../language-reference/keywords/ushort.md)、[int](../../language-reference/keywords/int.md)、[uint](../../language-reference/keywords/uint.md)、[long](../../language-reference/keywords/long.md)、[ulong](../../language-reference/keywords/ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="255ad-107">Any integral type: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span></span>
- <span data-ttu-id="255ad-108">任何浮點類型：[float](../../language-reference/keywords/float.md)、[double](../../language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="255ad-108">Any floating-point type: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span></span>
- <span data-ttu-id="255ad-109">[char](../../language-reference/keywords/char.md)。</span><span class="sxs-lookup"><span data-stu-id="255ad-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="255ad-110">[bool](../../language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="255ad-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="255ad-111">[decimal](../../language-reference/keywords/decimal.md)。</span><span class="sxs-lookup"><span data-stu-id="255ad-111">[decimal](../../language-reference/keywords/decimal.md).</span></span>
- <span data-ttu-id="255ad-112">任何 [enum](../../language-reference/keywords/enum.md) 型別。</span><span class="sxs-lookup"><span data-stu-id="255ad-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="255ad-113">任何指標類型。</span><span class="sxs-lookup"><span data-stu-id="255ad-113">Any pointer type.</span></span> <span data-ttu-id="255ad-114">這允許使用運算式，例如 `void**`。</span><span class="sxs-lookup"><span data-stu-id="255ad-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="255ad-115">任何只包含 Unmanaged 類型欄位的使用者定義結構類型。</span><span class="sxs-lookup"><span data-stu-id="255ad-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="255ad-116">指標型別不會從 [object](../../language-reference/keywords/object.md) 繼承，而且指標型別與 `object` 之間無法進行轉換。</span><span class="sxs-lookup"><span data-stu-id="255ad-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="255ad-117">此外，boxing 和 unboxing 不支援指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="255ad-118">不過，不同的指標類型之間以及指標類型與整數類資料類型之間可以進行轉換。</span><span class="sxs-lookup"><span data-stu-id="255ad-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="255ad-119">當您在相同的宣告中宣告多個指標時，星號 (\*) 只會與基礎類型一起出現，而不會做為每個指標名稱的前置詞使用。</span><span class="sxs-lookup"><span data-stu-id="255ad-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="255ad-120">例如：</span><span class="sxs-lookup"><span data-stu-id="255ad-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="255ad-121">指標無法指向參考或包含參考的 [struct](../../language-reference/keywords/struct.md)，因為即使指標指向物件參考，依然可以對物件參考進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="255ad-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="255ad-122">記憶體回收行程不會持續追蹤是否有任何指標類型指向物件。</span><span class="sxs-lookup"><span data-stu-id="255ad-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="255ad-123">`myType*` 類型的指標變數值是 `myType` 類型變數的位址。</span><span class="sxs-lookup"><span data-stu-id="255ad-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="255ad-124">以下是指標類型宣告的範例：</span><span class="sxs-lookup"><span data-stu-id="255ad-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="255ad-125">範例</span><span class="sxs-lookup"><span data-stu-id="255ad-125">Example</span></span>|<span data-ttu-id="255ad-126">說明</span><span class="sxs-lookup"><span data-stu-id="255ad-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="255ad-127">`p` 為整數的指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="255ad-128">`p` 為整數指標的指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="255ad-129">`p` 為整數的一維陣列指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="255ad-130">`p` 為字元的指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="255ad-131">`p` 為未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="255ad-132">您可以使用指標間接運算子 \* 存取指標變數所指向位置的內容。</span><span class="sxs-lookup"><span data-stu-id="255ad-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="255ad-133">例如，請參考下列宣告：</span><span class="sxs-lookup"><span data-stu-id="255ad-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="255ad-134">這個運算式 `*myVariable` 表示位於 `int` 所包含之位址的 `myVariable` 變數。</span><span class="sxs-lookup"><span data-stu-id="255ad-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="255ad-135">[fixed 陳述式](../../language-reference/keywords/fixed-statement.md)和[指標轉換](../../programming-guide/unsafe-code-pointers/pointer-conversions.md)主題中有數個指標範例。</span><span class="sxs-lookup"><span data-stu-id="255ad-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="255ad-136">下列範例使用 `unsafe` 關鍵字和 `fixed` 陳述式，並示範如何讓內部指標遞增。</span><span class="sxs-lookup"><span data-stu-id="255ad-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="255ad-137">您可以將這個程式碼貼入主控台應用程式的 Main 函式中來執行它 </span><span class="sxs-lookup"><span data-stu-id="255ad-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="255ad-138">這些範例必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項集合來編譯。</span><span class="sxs-lookup"><span data-stu-id="255ad-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="255ad-139">您無法將間接運算子套用至 `void*` 類型的指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="255ad-140">不過，您可以使用轉型，將 Void 指標轉換成任何其他指標類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="255ad-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="255ad-141">指標可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="255ad-141">A pointer can be `null`.</span></span> <span data-ttu-id="255ad-142">將間接運算子套用至 null 指標會產生實作定義的行為。</span><span class="sxs-lookup"><span data-stu-id="255ad-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="255ad-143">在方法之間傳遞指標時，可能會導致未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="255ad-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="255ad-144">請考慮使用透過 `in`、`out` 或 `ref` 參數或是以函式結果的方式，將指標傳至區域變數的方法。</span><span class="sxs-lookup"><span data-stu-id="255ad-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="255ad-145">如果已在固定區塊中設定指標，則該指標指向的變數就可能不再是固定的。</span><span class="sxs-lookup"><span data-stu-id="255ad-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="255ad-146">下表所列出的運算子和陳述式可以用於 unsafe 內容中的指標：</span><span class="sxs-lookup"><span data-stu-id="255ad-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="255ad-147">運算子/陳述式</span><span class="sxs-lookup"><span data-stu-id="255ad-147">Operator/Statement</span></span>|<span data-ttu-id="255ad-148">使用</span><span class="sxs-lookup"><span data-stu-id="255ad-148">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="255ad-149">執行指標間接取值。</span><span class="sxs-lookup"><span data-stu-id="255ad-149">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="255ad-150">透過指標存取結構的成員。</span><span class="sxs-lookup"><span data-stu-id="255ad-150">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="255ad-151">索引指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-151">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="255ad-152">取得變數位址。</span><span class="sxs-lookup"><span data-stu-id="255ad-152">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="255ad-153">`++` 和 `--`</span><span class="sxs-lookup"><span data-stu-id="255ad-153">`++` and `--`</span></span>|<span data-ttu-id="255ad-154">遞增和遞減指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-154">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="255ad-155">`+` 和 `-`</span><span class="sxs-lookup"><span data-stu-id="255ad-155">`+` and `-`</span></span>|<span data-ttu-id="255ad-156">執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="255ad-156">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="255ad-157">`==`、`!=`、`<`、`>`、`<=` 和 `>=`</span><span class="sxs-lookup"><span data-stu-id="255ad-157">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="255ad-158">比較指標。</span><span class="sxs-lookup"><span data-stu-id="255ad-158">Compares pointers.</span></span>|
|[<span data-ttu-id="255ad-159">`stackalloc` 運算子</span><span class="sxs-lookup"><span data-stu-id="255ad-159">`stackalloc` operator</span></span>](../../language-reference/keywords/stackalloc.md)|<span data-ttu-id="255ad-160">在堆疊上配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="255ad-160">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="255ad-161">`fixed` 陳述式</span><span class="sxs-lookup"><span data-stu-id="255ad-161">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="255ad-162">暫時固定變數以便找到其位址。</span><span class="sxs-lookup"><span data-stu-id="255ad-162">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="255ad-163">如需指標相關運算子的詳細資訊，請參閱[指標相關運算子](../../language-reference/operators/pointer-related-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="255ad-163">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="255ad-164">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="255ad-164">C# language specification</span></span>

<span data-ttu-id="255ad-165">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="255ad-165">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="255ad-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="255ad-166">See also</span></span>

- [<span data-ttu-id="255ad-167">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="255ad-167">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="255ad-168">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="255ad-168">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="255ad-169">指標轉換</span><span class="sxs-lookup"><span data-stu-id="255ad-169">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="255ad-170">型別</span><span class="sxs-lookup"><span data-stu-id="255ad-170">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="255ad-171">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="255ad-171">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
