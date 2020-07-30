---
title: 固定大小緩衝區 - C# 程式設計指南
description: 瞭解固定大小的緩衝區。 固定大小緩衝區是用來撰寫與其他語言的資料來源互通的方法。
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 1d4f5068121cdc98976954f2d99f4ac020c3b2a8
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381238"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="33cf8-104">固定大小緩衝區 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="33cf8-104">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="33cf8-105">在 C# 中，您可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 陳述式，在資料結構中建立具有固定大小陣列的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="33cf8-105">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="33cf8-106">當您撰寫的方法會與其他語言或平台的資料來源互通時，固定大小緩衝區就很有用。</span><span class="sxs-lookup"><span data-stu-id="33cf8-106">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="33cf8-107">固定陣列可接受一般結構成員所允許的任何屬性或修飾詞。</span><span class="sxs-lookup"><span data-stu-id="33cf8-107">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="33cf8-108">唯一的限制是陣列類型必須為 `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="33cf8-108">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="33cf8-109">備註</span><span class="sxs-lookup"><span data-stu-id="33cf8-109">Remarks</span></span>

<span data-ttu-id="33cf8-110">在安全的程式碼中，包含陣列的 C# 結構不包含陣列項目。</span><span class="sxs-lookup"><span data-stu-id="33cf8-110">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="33cf8-111">相反地，該結構會包含元素的參考。</span><span class="sxs-lookup"><span data-stu-id="33cf8-111">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="33cf8-112">您可以將固定大小的陣列嵌入用於[不安全](../../language-reference/keywords/unsafe.md)程式碼區塊的 [struct](../../language-reference/builtin-types/struct.md)。</span><span class="sxs-lookup"><span data-stu-id="33cf8-112">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="33cf8-113">下列的大小 `struct` 不會取決於陣列中的元素數目，因為 `pathName` 是參考：</span><span class="sxs-lookup"><span data-stu-id="33cf8-113">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

<span data-ttu-id="33cf8-114">`struct` 可以在不安全的程式碼中包含內嵌陣列。</span><span class="sxs-lookup"><span data-stu-id="33cf8-114">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="33cf8-115">在下列範例中，`fixedBuffer` 陣列具有固定大小。</span><span class="sxs-lookup"><span data-stu-id="33cf8-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="33cf8-116">您可以使用 `fixed` 陳述式來建立第一個項目的指標。</span><span class="sxs-lookup"><span data-stu-id="33cf8-116">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="33cf8-117">透過這個指標即可存取陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="33cf8-117">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="33cf8-118">`fixed` 陳述式會將 `fixedBuffer` 執行個體欄位釘選到記憶體中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="33cf8-118">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

<span data-ttu-id="33cf8-119">128 個元素的 `char` 陣列大小為 256 個位元組。</span><span class="sxs-lookup"><span data-stu-id="33cf8-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="33cf8-120">不論編碼為何，在固定大小的 [char](../../language-reference/builtin-types/char.md) 緩衝區中，每個字元一律會有兩個位元組。</span><span class="sxs-lookup"><span data-stu-id="33cf8-120">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="33cf8-121">即使 char 緩衝區使用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構也一樣。</span><span class="sxs-lookup"><span data-stu-id="33cf8-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="33cf8-122">如需詳細資訊，請參閱 <xref:System.Runtime.InteropServices.CharSet>。</span><span class="sxs-lookup"><span data-stu-id="33cf8-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="33cf8-123">上述範例示範如何存取 `fixed` 欄位而無需進行釘選，這是從 C# 7.3 開始可供使用的功能。</span><span class="sxs-lookup"><span data-stu-id="33cf8-123">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="33cf8-124">另一個常見的固定大小陣列是 [bool](../../language-reference/builtin-types/bool.md) 陣列。</span><span class="sxs-lookup"><span data-stu-id="33cf8-124">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="33cf8-125">`bool` 陣列中的元素大小一律為一個位元組。</span><span class="sxs-lookup"><span data-stu-id="33cf8-125">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="33cf8-126">`bool` 陣列不適用於建立位元陣列或緩衝區。</span><span class="sxs-lookup"><span data-stu-id="33cf8-126">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="33cf8-127">固定大小的緩衝區會使用來編譯 <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> ，這會指示 common language runtime （CLR）類型包含可能溢位的非受控陣列。</span><span class="sxs-lookup"><span data-stu-id="33cf8-127">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="33cf8-128">這類似于使用[stackalloc](../../language-reference/operators/stackalloc.md)所建立的記憶體，它會自動啟用 CLR 中的緩衝區溢位偵測功能。</span><span class="sxs-lookup"><span data-stu-id="33cf8-128">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="33cf8-129">上一個範例顯示如何在中存在固定大小的緩衝區 `unsafe struct` 。</span><span class="sxs-lookup"><span data-stu-id="33cf8-129">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="33cf8-130">編譯器產生的 c # 的屬性如下所示 `Buffer` ：</span><span class="sxs-lookup"><span data-stu-id="33cf8-130">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="33cf8-131">固定大小緩衝區與一般陣列有下列不同之處：</span><span class="sxs-lookup"><span data-stu-id="33cf8-131">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="33cf8-132">僅可用於[不安全](../../language-reference/keywords/unsafe.md)的內容中。</span><span class="sxs-lookup"><span data-stu-id="33cf8-132">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="33cf8-133">只能是結構的實例欄位。</span><span class="sxs-lookup"><span data-stu-id="33cf8-133">May only be instance fields of structs.</span></span>
- <span data-ttu-id="33cf8-134">它們一律是向量或一維陣列。</span><span class="sxs-lookup"><span data-stu-id="33cf8-134">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="33cf8-135">宣告應包含長度，例如 `fixed char id[8]` 。</span><span class="sxs-lookup"><span data-stu-id="33cf8-135">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="33cf8-136">您不能使用 `fixed char id[]`。</span><span class="sxs-lookup"><span data-stu-id="33cf8-136">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="33cf8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33cf8-137">See also</span></span>

- [<span data-ttu-id="33cf8-138">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="33cf8-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="33cf8-139">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="33cf8-139">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="33cf8-140">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="33cf8-140">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="33cf8-141">互通性</span><span class="sxs-lookup"><span data-stu-id="33cf8-141">Interoperability</span></span>](../interop/index.md)
