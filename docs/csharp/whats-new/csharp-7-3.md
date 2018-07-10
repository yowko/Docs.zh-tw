---
title: C# 7.3 的新功能
description: C# 7.3 新功能的概觀
ms.date: 05/16/2018
ms.openlocfilehash: 135351fa06a498e4aa90cb4d9372880b8119de0f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106771"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="7ffe1-103">C# 7.3 的新功能</span><span class="sxs-lookup"><span data-stu-id="7ffe1-103">What's new in C# 7.3</span></span>

<span data-ttu-id="7ffe1-104">C# 7.3 版有兩個主要的佈景主題。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="7ffe1-105">其中一個佈景主題提供了使安全的程式碼具有與不安全的程式碼一樣高效能的功能。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="7ffe1-106">第二個佈景主題提供現有功能的累加增強功能。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="7ffe1-107">此外，此版本中加入了新的編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="7ffe1-108">下列新功能針對安全的程式碼支援較佳效能的佈景主題：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="7ffe1-109">您可以在不釘選的情況下存取固定的欄位。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="7ffe1-110">您可以重新指派 `ref` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="7ffe1-111">您可以在 `stackalloc` 陣列上使用初始設定式。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="7ffe1-112">您可以搭配支援模式的任何型別使用 `fixed` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="7ffe1-113">您可以使用其他的泛型限制式。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="7ffe1-114">已在現有功能中提供下列增強功能：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="7ffe1-115">您可以使用 Tuple 型別測試 `==` 和 `!=`。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="7ffe1-116">您可以在更多位置使用運算式變數。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="7ffe1-117">您可以將屬性附加至自動實作屬性的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="7ffe1-118">已改善當引數依 `in` 不同時的方法解析。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="7ffe1-119">多載解析現在會有較少模稜兩可的情況。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="7ffe1-120">新的編譯器選項：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-120">The new compiler options are:</span></span>

- <span data-ttu-id="7ffe1-121">`-publicsign`，用來啟用組件的開放原始碼軟體 (OSS) 簽署。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="7ffe1-122">`-pathmap`，用來提供來源目錄的對應。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="7ffe1-123">這篇文章的其餘部分提供詳細資料和連結，讓您深入了解每個增強功能。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-performant-safe-code"></a><span data-ttu-id="7ffe1-124">啟用更多高效能的安全的程式碼</span><span class="sxs-lookup"><span data-stu-id="7ffe1-124">Enabling more performant safe code</span></span>

<span data-ttu-id="7ffe1-125">您應該能夠安全地撰寫與不安全的程式碼一樣高效能的 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="7ffe1-126">安全的程式碼可避免一些錯誤類別，例如緩衝區溢位、偏離的指標和其他記憶體存取錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="7ffe1-127">這些新功能擴充了可驗證安全的程式碼的功能。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="7ffe1-128">儘可能使用安全的建構來撰寫更多的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="7ffe1-129">這些功能都讓這變得更容易。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="7ffe1-130">索引 `fixed` 欄位不需要釘選</span><span class="sxs-lookup"><span data-stu-id="7ffe1-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="7ffe1-131">請考量此建構：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="7ffe1-132">在舊版的 C# 中，您需要釘選變數，才能存取屬於 `myFixedField` 的其中一個整數。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="7ffe1-133">現在，下列程式碼會在安全的內容中編譯：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-133">Now, the following code compiles in a safe context:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="7ffe1-134">變數 `p` 會存取 `myFixedField` 中的一個元素。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="7ffe1-135">您不需要宣告個別的 `int*` 變數。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="7ffe1-136">請注意，您仍然需要 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="7ffe1-137">在舊版的 C# 中，您需要宣告第二個固定指標：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="7ffe1-138">如需詳細資訊，請參閱有關 [`fixed` 陳述式](../language-reference/keywords/fixed-statement.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-138">Fore more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="7ffe1-139">`ref` 區域變數可能會重新指派</span><span class="sxs-lookup"><span data-stu-id="7ffe1-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="7ffe1-140">現在，`ref` 區域變數可能會在初始化之後被重新指派，以參照不同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="7ffe1-141">下列程式碼現在會編譯：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="7ffe1-142">如需詳細資訊，請參閱有關 [`ref` 傳回和 `ref` 區域變數](../programming-guide/classes-and-structs/ref-returns.md)的文章，以及有關 [`foreach`](../language-reference/keywords/foreach-in.md) 的文章。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="7ffe1-143">`stackalloc` 陣列支援初始設定式</span><span class="sxs-lookup"><span data-stu-id="7ffe1-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="7ffe1-144">您可以在初始化陣列時，指定陣列中元素的值：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="7ffe1-145">現在，相同的語法可以套用至使用 `stackalloc` 宣告的陣列：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="7ffe1-146">如需詳細資訊，請參閱語言參考中的 [`stackalloc` 陳述式](../language-reference/keywords/stackalloc.md)一文。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="7ffe1-147">更多型別支援 `fixed` 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ffe1-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="7ffe1-148">`fixed` 陳述式支援一組有限的型別。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="7ffe1-149">從 C# 7.3 開始，包含傳回 `ref T` 或 `ref readonly T` 之 `GetPinnableReference()` 方法的任何型別都可能是 `fixed`。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="7ffe1-150">新增此功能表示 `fixed` 可以與 <xref:System.Span%601?displayProperty=nameWithType> 和相關型別一起使用。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="7ffe1-151">如需詳細資訊，請參閱語言參考中的 [`fixed` 陳述式](../language-reference/keywords/fixed-statement.md)一文。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="7ffe1-152">增強泛型限制式</span><span class="sxs-lookup"><span data-stu-id="7ffe1-152">Enhanced generic constraints</span></span>

<span data-ttu-id="7ffe1-153">您現在可以指定型別 <xref:System.Enum?displayProperty=nameWithType> 或 <xref:System.Delegate?displayProperty=nameWithType> 作為型別參數的基底類別限制式。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="7ffe1-154">您也可以使用新的 `unmanaged` 限制式指定型別參數必須是**非受控型別**。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="7ffe1-155">**非受控型別**是非參考型別的型別，而且未包含任何巢狀層級的參考型別。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="7ffe1-156">如需詳細資訊，請參閱有關 [`where` 泛型限制式](../language-reference/keywords/where-generic-type-constraint.md)和[型別參數的限制式](../programming-guide/generics/constraints-on-type-parameters.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="7ffe1-157">讓現有的功能變得更好</span><span class="sxs-lookup"><span data-stu-id="7ffe1-157">Make existing features better</span></span>

<span data-ttu-id="7ffe1-158">第二個佈景主題提供了語言功能的改進。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-158">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="7ffe1-159">撰寫 C# 時，這些功能可以提高生產力。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-159">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="7ffe1-160">Tuple 支援 `==` 和 `!=`</span><span class="sxs-lookup"><span data-stu-id="7ffe1-160">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="7ffe1-161">C# Tuple 型別現在支援 `==` 和 `!=`。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-161">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="7ffe1-162">如需詳細資訊，請參閱 [Tuple](../tuples.md) 文章中涵蓋[相等](../tuples.md#equality-and-tuples)的一節。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-162">Fore more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="7ffe1-163">將屬性附加至自動實作屬性的支援欄位</span><span class="sxs-lookup"><span data-stu-id="7ffe1-163">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="7ffe1-164">現在支援此語法：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-164">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="7ffe1-165">屬性 `SomeThingAboutFieldAttribute` 套用至編譯器針對 `SomeProperty` 產生的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-165">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="7ffe1-166">如需詳細資訊，請參閱 C# 程式設計指南中的[屬性](../programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-166">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="7ffe1-167">`in` 方法多載解析 tiebreaker</span><span class="sxs-lookup"><span data-stu-id="7ffe1-167">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="7ffe1-168">當加入 `in` 引數修飾詞時，這兩種方法會造成模稜兩可：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-168">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="7ffe1-169">現在，by 值 (上述範例中的第一個) 多載會優於 by 唯讀參考版本。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-169">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="7ffe1-170">若要呼叫具有唯讀參考引數的版本，您呼叫方法時必須包含 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-170">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="7ffe1-171">這已實作為錯誤 (Bug) 修正。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-171">This was implemented as a bug fix.</span></span> <span data-ttu-id="7ffe1-172">即使將語言版本設定為 "7.2"，這也不再模棱兩可。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-172">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="7ffe1-173">如需詳細資訊，請參閱有關 [`in` 參數修飾詞](../language-reference/keywords/in-parameter-modifier.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-173">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="7ffe1-174">在初始設定式中擴充運算式變數</span><span class="sxs-lookup"><span data-stu-id="7ffe1-174">Extend expression variables in initializers</span></span>

<span data-ttu-id="7ffe1-175">加入 C# 7.0 中以允許 `out` 變數宣告的語法已經擴充，以包含欄位初始設定式、屬性初始設定式、建構函式初始設定式和查詢子句。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-175">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="7ffe1-176">它讓您能執行如下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-176">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="7ffe1-177">改進的多載候選項目</span><span class="sxs-lookup"><span data-stu-id="7ffe1-177">Improved overload candidates</span></span>

<span data-ttu-id="7ffe1-178">在每個版本中，多載解析規則都會更新，以解決模稜兩可的方法引動過程具有「明確」選項的情況。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-178">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="7ffe1-179">此版本新增三個新的規則，以協助編譯器挑選明確的選項：</span><span class="sxs-lookup"><span data-stu-id="7ffe1-179">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="7ffe1-180">當方法群組同時包含執行個體和靜態成員時，如果在沒有執行個體接收者或內容的情況下叫用方法，編譯器會捨棄執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-180">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="7ffe1-181">如果使用執行個體接收者叫用方法，編譯器就會捨棄靜態成員。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-181">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="7ffe1-182">沒有接收者時，編譯器只會在靜態內容中包含靜態成員，否則將同時包含靜態成員和執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-182">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="7ffe1-183">當無法確定接收者是執行個體或型別時，編譯器會包含兩者。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-183">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="7ffe1-184">無法使用隱含 `this` 執行個體接收者的靜態內容，包括未定義 `this` 的成員主體 (例如靜態成員)，以及不能使用 `this` 的位置 (例如欄位初始設定式和建構函式初始設定式)。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-184">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="7ffe1-185">當方法群組包含某些型別引數不滿足其限制式的泛型方法時，這些成員將會從候選集合中移除。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-185">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="7ffe1-186">針對方法群組轉換，其傳回型別與委派的傳回型別不符合的候選方法，將會從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-186">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="7ffe1-187">您只會注意到此變更，因為若確定何種方法較佳，就會發現模稜兩可的方法多載會有較少的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-187">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="7ffe1-188">新的編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7ffe1-188">New compiler options</span></span>

<span data-ttu-id="7ffe1-189">新的編譯器選項支援 C# 程式的新組建和 DevOps 案例。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-189">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="7ffe1-190">公用或開放原始碼簽署</span><span class="sxs-lookup"><span data-stu-id="7ffe1-190">Public or Open Source signing</span></span>

<span data-ttu-id="7ffe1-191">`-publicsign` 編譯器選項會指示編譯器使用公開金鑰簽署組件。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-191">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="7ffe1-192">該組件標示為已簽署，但簽章取自公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-192">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="7ffe1-193">此選項可讓您使用公開金鑰，從開放原始碼專案建置簽署的組件。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-193">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="7ffe1-194">如需詳細資訊，請參閱 [-publicsign 編譯器選項](../language-reference/compiler-options/publicsign-compiler-option.md)一文。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-194">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="7ffe1-195">pathmap</span><span class="sxs-lookup"><span data-stu-id="7ffe1-195">pathmap</span></span>

<span data-ttu-id="7ffe1-196">`-pathmap` 編譯器選項會指示編譯器使用對應的來源路徑取代建置環境的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-196">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="7ffe1-197">`-pathmap` 選項控制編譯器寫入 PDB 檔案或 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-197">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="7ffe1-198">如需詳細資訊，請參閱 [-pathmap 編譯器選項](../language-reference/compiler-options/pathmap-compiler-option.md)一文。</span><span class="sxs-lookup"><span data-stu-id="7ffe1-198">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
