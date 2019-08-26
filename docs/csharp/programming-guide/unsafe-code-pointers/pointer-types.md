---
title: 指標類型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 4d0801cd81e00c84be278b44730058798b0acfa9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588200"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="5d0f0-102">指標類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5d0f0-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="5d0f0-103">在 unsafe 內容中，類型有可能是指標類型、實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="5d0f0-104">指標類型宣告會使用下列其中一種格式：</span><span class="sxs-lookup"><span data-stu-id="5d0f0-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="5d0f0-105">在指標型別中的 `*` 之前指定的型別稱為**參考型別**。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="5d0f0-106">只有 [unmanaged 型別](../../language-reference/builtin-types/unmanaged-types.md)才可以是參考型別。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="5d0f0-107">指標型別不會從 [object](../../language-reference/keywords/object.md) 繼承，而且指標型別與 `object` 之間無法進行轉換。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-107">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="5d0f0-108">此外，boxing 和 unboxing 不支援指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="5d0f0-109">不過，不同的指標類型之間以及指標類型與整數類資料類型之間可以進行轉換。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="5d0f0-110">當您在相同的宣告中宣告多個指標時，星號 (\*) 只會與基礎類型一起出現，而不會做為每個指標名稱的前置詞使用。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="5d0f0-111">例如：</span><span class="sxs-lookup"><span data-stu-id="5d0f0-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="5d0f0-112">指標無法指向參考或包含參考的 [struct](../../language-reference/keywords/struct.md)，因為即使指標指向物件參考，依然可以對物件參考進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-112">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="5d0f0-113">記憶體回收行程不會持續追蹤是否有任何指標類型指向物件。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="5d0f0-114">`myType*` 類型的指標變數值是 `myType` 類型變數的位址。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="5d0f0-115">以下是指標類型宣告的範例：</span><span class="sxs-lookup"><span data-stu-id="5d0f0-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="5d0f0-116">範例</span><span class="sxs-lookup"><span data-stu-id="5d0f0-116">Example</span></span>|<span data-ttu-id="5d0f0-117">說明</span><span class="sxs-lookup"><span data-stu-id="5d0f0-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="5d0f0-118">`p` 為整數的指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="5d0f0-119">`p` 為整數指標的指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="5d0f0-120">`p` 為整數的一維陣列指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="5d0f0-121">`p` 為字元的指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="5d0f0-122">`p` 為未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="5d0f0-123">您可以使用指標間接運算子 \* 存取指標變數所指向位置的內容。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="5d0f0-124">例如，請參考下列宣告：</span><span class="sxs-lookup"><span data-stu-id="5d0f0-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="5d0f0-125">這個運算式 `*myVariable` 表示位於 `int` 所包含之位址的 `myVariable` 變數。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="5d0f0-126">[fixed 陳述式](../../language-reference/keywords/fixed-statement.md)和[指標轉換](./pointer-conversions.md)主題中有數個指標範例。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="5d0f0-127">下列範例使用 `unsafe` 關鍵字和 `fixed` 陳述式，並示範如何讓內部指標遞增。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="5d0f0-128">您可以將這個程式碼貼入主控台應用程式的 Main 函式中來執行它</span><span class="sxs-lookup"><span data-stu-id="5d0f0-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="5d0f0-129">這些範例必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項集合來編譯。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="5d0f0-130">您無法將間接運算子套用至 `void*` 類型的指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="5d0f0-131">不過，您可以使用轉型，將 Void 指標轉換成任何其他指標類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="5d0f0-132">指標可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-132">A pointer can be `null`.</span></span> <span data-ttu-id="5d0f0-133">將間接運算子套用至 null 指標會產生實作定義的行為。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="5d0f0-134">在方法之間傳遞指標時，可能會導致未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="5d0f0-135">請考慮使用透過 `in`、`out` 或 `ref` 參數或是以函式結果的方式，將指標傳至區域變數的方法。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="5d0f0-136">如果已在固定區塊中設定指標，則該指標指向的變數就可能不再是固定的。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="5d0f0-137">下表所列出的運算子和陳述式可以用於 unsafe 內容中的指標：</span><span class="sxs-lookup"><span data-stu-id="5d0f0-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="5d0f0-138">運算子/陳述式</span><span class="sxs-lookup"><span data-stu-id="5d0f0-138">Operator/Statement</span></span>|<span data-ttu-id="5d0f0-139">使用</span><span class="sxs-lookup"><span data-stu-id="5d0f0-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="5d0f0-140">執行指標間接取值。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="5d0f0-141">透過指標存取結構的成員。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="5d0f0-142">索引指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="5d0f0-143">取得變數位址。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="5d0f0-144">`++` 和 `--`</span><span class="sxs-lookup"><span data-stu-id="5d0f0-144">`++` and `--`</span></span>|<span data-ttu-id="5d0f0-145">遞增和遞減指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="5d0f0-146">`+` 和 `-`</span><span class="sxs-lookup"><span data-stu-id="5d0f0-146">`+` and `-`</span></span>|<span data-ttu-id="5d0f0-147">執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="5d0f0-148">`==`、`!=`、`<`、`>`、`<=` 和 `>=`</span><span class="sxs-lookup"><span data-stu-id="5d0f0-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="5d0f0-149">比較指標。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-149">Compares pointers.</span></span>|
|[<span data-ttu-id="5d0f0-150">`stackalloc` 運算子</span><span class="sxs-lookup"><span data-stu-id="5d0f0-150">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="5d0f0-151">在堆疊上配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-151">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="5d0f0-152">`fixed` 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d0f0-152">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="5d0f0-153">暫時固定變數以便找到其位址。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-153">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="5d0f0-154">如需指標相關運算子的詳細資訊，請參閱[指標相關運算子](../../language-reference/operators/pointer-related-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-154">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5d0f0-155">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5d0f0-155">C# language specification</span></span>

<span data-ttu-id="5d0f0-156">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="5d0f0-156">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d0f0-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d0f0-157">See also</span></span>

- [<span data-ttu-id="5d0f0-158">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5d0f0-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5d0f0-159">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="5d0f0-159">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="5d0f0-160">指標轉換</span><span class="sxs-lookup"><span data-stu-id="5d0f0-160">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="5d0f0-161">型別</span><span class="sxs-lookup"><span data-stu-id="5d0f0-161">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="5d0f0-162">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="5d0f0-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
