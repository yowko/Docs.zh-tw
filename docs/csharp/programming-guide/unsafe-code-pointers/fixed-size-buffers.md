---
title: 固定大小緩衝區 (C# 程式設計手冊)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 310c5eed5507f75239efc78b6132fbc91211d29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339588"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="95ea9-102">固定大小緩衝區 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="95ea9-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="95ea9-103">在 C# 中，您可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 陳述式，在資料結構中建立具有固定大小陣列的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="95ea9-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="95ea9-104">當您撰寫的方法會與其他語言或平台的資料來源互通時，固定大小緩衝區就很有用。</span><span class="sxs-lookup"><span data-stu-id="95ea9-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="95ea9-105">固定陣列可接受一般結構成員所允許的任何屬性或修飾詞。</span><span class="sxs-lookup"><span data-stu-id="95ea9-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="95ea9-106">唯一的限制是陣列類型必須為 `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="95ea9-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="95ea9-107">備註</span><span class="sxs-lookup"><span data-stu-id="95ea9-107">Remarks</span></span>

<span data-ttu-id="95ea9-108">在安全的程式碼中，包含陣列的 C# 結構不包含陣列項目。</span><span class="sxs-lookup"><span data-stu-id="95ea9-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="95ea9-109">相反地，該結構會包含元素的參考。</span><span class="sxs-lookup"><span data-stu-id="95ea9-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="95ea9-110">您可以將固定大小的陣列嵌入用於[不安全](../../language-reference/keywords/unsafe.md)程式碼區塊的 [struct](../../language-reference/keywords/struct.md)。</span><span class="sxs-lookup"><span data-stu-id="95ea9-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="95ea9-111">下列 `struct` 的大小為 8 個位元組。</span><span class="sxs-lookup"><span data-stu-id="95ea9-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="95ea9-112">`pathName` 陣列是參考：</span><span class="sxs-lookup"><span data-stu-id="95ea9-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="95ea9-113">`struct` 可以在不安全的程式碼中包含內嵌陣列。</span><span class="sxs-lookup"><span data-stu-id="95ea9-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="95ea9-114">在下列範例中，`fixedBuffer` 陣列具有固定大小。</span><span class="sxs-lookup"><span data-stu-id="95ea9-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="95ea9-115">您可以使用 `fixed` 陳述式來建立第一個項目的指標。</span><span class="sxs-lookup"><span data-stu-id="95ea9-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="95ea9-116">透過這個指標即可存取陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="95ea9-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="95ea9-117">`fixed` 陳述式會將 `fixedBuffer` 執行個體欄位釘選到記憶體中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="95ea9-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="95ea9-118">128 個元素的 `char` 陣列大小為 256 個位元組。</span><span class="sxs-lookup"><span data-stu-id="95ea9-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="95ea9-119">不論編碼為何，在固定大小的 [char](../../language-reference/keywords/char.md) 緩衝區中，每個字元一律會有兩個位元組。</span><span class="sxs-lookup"><span data-stu-id="95ea9-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="95ea9-120">即使 char 緩衝區使用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構也一樣。</span><span class="sxs-lookup"><span data-stu-id="95ea9-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="95ea9-121">如需詳細資訊，請參閱<xref:System.Runtime.InteropServices.CharSet>。</span><span class="sxs-lookup"><span data-stu-id="95ea9-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="95ea9-122">上述範例將示範如何存取 `fixed` 欄位而無需進行釘選，這是從 C# 7.3 開始可供使用的功能。</span><span class="sxs-lookup"><span data-stu-id="95ea9-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3..</span></span>

<span data-ttu-id="95ea9-123">另一個常見的固定大小陣列是 [bool](../../language-reference/keywords/bool.md) 陣列。</span><span class="sxs-lookup"><span data-stu-id="95ea9-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="95ea9-124">`bool` 陣列中的元素大小一律為一個位元組。</span><span class="sxs-lookup"><span data-stu-id="95ea9-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="95ea9-125">`bool` 陣列不適用於建立位元陣列或緩衝區。</span><span class="sxs-lookup"><span data-stu-id="95ea9-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="95ea9-126">除了使用 [stackalloc](../../language-reference/keywords/stackalloc.md) 所建立的記憶體以外，C# 編譯器和 Common Language Runtime (CLR) 不會執行任何安全性緩衝區溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="95ea9-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="95ea9-127">請與所有不安全的程式碼一樣小心使用。</span><span class="sxs-lookup"><span data-stu-id="95ea9-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="95ea9-128">不安全的緩衝區與一般陣列的差異如下：</span><span class="sxs-lookup"><span data-stu-id="95ea9-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="95ea9-129">您只能在不安全的內容中使用不安全的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="95ea9-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="95ea9-130">不安全的緩衝區一律是向量或一維陣列。</span><span class="sxs-lookup"><span data-stu-id="95ea9-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="95ea9-131">陣列的宣告應包含計數，例如 `char id[8]`。</span><span class="sxs-lookup"><span data-stu-id="95ea9-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="95ea9-132">您不能使用 `char id[]`。</span><span class="sxs-lookup"><span data-stu-id="95ea9-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="95ea9-133">不安全的緩衝區只能是不安全內容中結構的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="95ea9-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="95ea9-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="95ea9-134">See Also</span></span>

[<span data-ttu-id="95ea9-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="95ea9-135">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="95ea9-136">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="95ea9-136">Unsafe Code and Pointers</span></span>](index.md)  
[<span data-ttu-id="95ea9-137">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="95ea9-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
[<span data-ttu-id="95ea9-138">互通性</span><span class="sxs-lookup"><span data-stu-id="95ea9-138">Interoperability</span></span>](../interop/index.md)
