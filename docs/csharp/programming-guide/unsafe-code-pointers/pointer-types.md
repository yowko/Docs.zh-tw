---
title: 指標類型 - C# 程式設計手冊
description: 瞭解指標類型。 查看不同指標的範例、程式碼範例，並查看其他可用的資源。
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 9c62a31f9a4a090fe56fb10ac45fe2f93f1b036e
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382031"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="33995-104">指標類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="33995-104">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="33995-105">在 unsafe 內容中，類型有可能是指標類型、實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="33995-105">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="33995-106">指標類型宣告會使用下列其中一種格式：</span><span class="sxs-lookup"><span data-stu-id="33995-106">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="33995-107">在指標型別中的 `*` 之前指定的型別稱為**參考型別**。</span><span class="sxs-lookup"><span data-stu-id="33995-107">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="33995-108">只有 [unmanaged 型別](../../language-reference/builtin-types/unmanaged-types.md)才可以是參考型別。</span><span class="sxs-lookup"><span data-stu-id="33995-108">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="33995-109">指標型別不會從 [object](../../language-reference/builtin-types/reference-types.md) 繼承，而且指標型別與 `object` 之間無法進行轉換。</span><span class="sxs-lookup"><span data-stu-id="33995-109">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="33995-110">此外，boxing 和 unboxing 不支援指標。</span><span class="sxs-lookup"><span data-stu-id="33995-110">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="33995-111">不過，不同的指標類型之間以及指標類型與整數類資料類型之間可以進行轉換。</span><span class="sxs-lookup"><span data-stu-id="33995-111">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="33995-112">當您在相同的宣告中宣告多個指標時，星號 (\*) 只會與基礎類型一起出現，而不會做為每個指標名稱的前置詞使用。</span><span class="sxs-lookup"><span data-stu-id="33995-112">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="33995-113">例如：</span><span class="sxs-lookup"><span data-stu-id="33995-113">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="33995-114">指標無法指向參考或包含參考的 [struct](../../language-reference/builtin-types/struct.md)，因為即使指標指向物件參考，依然可以對物件參考進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="33995-114">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="33995-115">記憶體回收行程不會持續追蹤是否有任何指標類型指向物件。</span><span class="sxs-lookup"><span data-stu-id="33995-115">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="33995-116">`myType*` 類型的指標變數值是 `myType` 類型變數的位址。</span><span class="sxs-lookup"><span data-stu-id="33995-116">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="33995-117">以下是指標類型宣告的範例：</span><span class="sxs-lookup"><span data-stu-id="33995-117">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="33995-118">範例</span><span class="sxs-lookup"><span data-stu-id="33995-118">Example</span></span>|<span data-ttu-id="33995-119">描述</span><span class="sxs-lookup"><span data-stu-id="33995-119">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="33995-120">`p` 為整數的指標。</span><span class="sxs-lookup"><span data-stu-id="33995-120">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="33995-121">`p` 為整數指標的指標。</span><span class="sxs-lookup"><span data-stu-id="33995-121">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="33995-122">`p` 為整數的一維陣列指標。</span><span class="sxs-lookup"><span data-stu-id="33995-122">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="33995-123">`p` 為字元的指標。</span><span class="sxs-lookup"><span data-stu-id="33995-123">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="33995-124">`p` 為未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="33995-124">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="33995-125">您可以使用指標間接運算子 \* 存取指標變數所指向位置的內容。</span><span class="sxs-lookup"><span data-stu-id="33995-125">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="33995-126">例如，請參考下列宣告：</span><span class="sxs-lookup"><span data-stu-id="33995-126">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="33995-127">這個運算式 `*myVariable` 表示位於 `int` 所包含之位址的 `myVariable` 變數。</span><span class="sxs-lookup"><span data-stu-id="33995-127">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="33995-128">[fixed 陳述式](../../language-reference/keywords/fixed-statement.md)和[指標轉換](./pointer-conversions.md)主題中有數個指標範例。</span><span class="sxs-lookup"><span data-stu-id="33995-128">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="33995-129">下列範例使用 `unsafe` 關鍵字和 `fixed` 陳述式，並示範如何讓內部指標遞增。</span><span class="sxs-lookup"><span data-stu-id="33995-129">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="33995-130">您可以將這個程式碼貼入主控台應用程式的 Main 函式中來執行它 </span><span class="sxs-lookup"><span data-stu-id="33995-130">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="33995-131">這些範例必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項集合來編譯。</span><span class="sxs-lookup"><span data-stu-id="33995-131">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](snippets/FixedKeywordExamples.cs#5)]

<span data-ttu-id="33995-132">您無法將間接運算子套用至 `void*` 類型的指標。</span><span class="sxs-lookup"><span data-stu-id="33995-132">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="33995-133">不過，您可以使用轉型，將 Void 指標轉換成任何其他指標類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="33995-133">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="33995-134">指標可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="33995-134">A pointer can be `null`.</span></span> <span data-ttu-id="33995-135">將間接運算子套用至 null 指標會產生實作定義的行為。</span><span class="sxs-lookup"><span data-stu-id="33995-135">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="33995-136">在方法之間傳遞指標時，可能會導致未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="33995-136">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="33995-137">請考慮使用透過 `in`、`out` 或 `ref` 參數或是以函式結果的方式，將指標傳至區域變數的方法。</span><span class="sxs-lookup"><span data-stu-id="33995-137">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="33995-138">如果已在固定區塊中設定指標，則該指標指向的變數就可能不再是固定的。</span><span class="sxs-lookup"><span data-stu-id="33995-138">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="33995-139">下表所列出的運算子和陳述式可以用於 unsafe 內容中的指標：</span><span class="sxs-lookup"><span data-stu-id="33995-139">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="33995-140">運算子/陳述式</span><span class="sxs-lookup"><span data-stu-id="33995-140">Operator/Statement</span></span>|<span data-ttu-id="33995-141">用途</span><span class="sxs-lookup"><span data-stu-id="33995-141">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="33995-142">執行指標間接取值。</span><span class="sxs-lookup"><span data-stu-id="33995-142">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="33995-143">透過指標存取結構的成員。</span><span class="sxs-lookup"><span data-stu-id="33995-143">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="33995-144">索引指標。</span><span class="sxs-lookup"><span data-stu-id="33995-144">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="33995-145">取得變數位址。</span><span class="sxs-lookup"><span data-stu-id="33995-145">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="33995-146">`++` 和 `--`</span><span class="sxs-lookup"><span data-stu-id="33995-146">`++` and `--`</span></span>|<span data-ttu-id="33995-147">遞增和遞減指標。</span><span class="sxs-lookup"><span data-stu-id="33995-147">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="33995-148">`+` 和 `-`</span><span class="sxs-lookup"><span data-stu-id="33995-148">`+` and `-`</span></span>|<span data-ttu-id="33995-149">執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="33995-149">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="33995-150">`==`、`!=`、`<`、`>`、`<=` 和 `>=`</span><span class="sxs-lookup"><span data-stu-id="33995-150">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="33995-151">比較指標。</span><span class="sxs-lookup"><span data-stu-id="33995-151">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="33995-152">在堆疊上配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="33995-152">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="33995-153">`fixed`句</span><span class="sxs-lookup"><span data-stu-id="33995-153">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="33995-154">暫時固定變數以便找到其位址。</span><span class="sxs-lookup"><span data-stu-id="33995-154">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="33995-155">如需指標相關運算子的詳細資訊，請參閱[指標相關運算子](../../language-reference/operators/pointer-related-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="33995-155">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="33995-156">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="33995-156">C# language specification</span></span>

<span data-ttu-id="33995-157">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="33995-157">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33995-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33995-158">See also</span></span>

- [<span data-ttu-id="33995-159">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="33995-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="33995-160">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="33995-160">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="33995-161">指標轉換</span><span class="sxs-lookup"><span data-stu-id="33995-161">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="33995-162">參考型別</span><span class="sxs-lookup"><span data-stu-id="33995-162">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="33995-163">值類型</span><span class="sxs-lookup"><span data-stu-id="33995-163">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="33995-164">不安全</span><span class="sxs-lookup"><span data-stu-id="33995-164">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
