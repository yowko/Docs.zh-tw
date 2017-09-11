---
title: "固定大小緩衝區 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e1a3dcf953cb56fc3436fdd5e7ecb60478a12922
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="966c2-102">固定大小緩衝區 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="966c2-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="966c2-103">在 C# 中，您可以使用 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式，在資料結構中建立具有固定大小陣列的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="966c2-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="966c2-104">當您使用現有的程式碼時，例如以其他語言撰寫的程式碼、既有的 Dll 或 COM 專案，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="966c2-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="966c2-105">固定陣列可接受一般結構成員所允許的任何屬性或修飾詞。</span><span class="sxs-lookup"><span data-stu-id="966c2-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="966c2-106">唯一的限制是陣列類型必須為 `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="966c2-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="966c2-107">備註</span><span class="sxs-lookup"><span data-stu-id="966c2-107">Remarks</span></span>  
 <span data-ttu-id="966c2-108">在舊版 C# 中，因為包含陣列的 C# 結構並未包含陣列元素，所以很難宣告 C++ 樣式的固定大小結構。</span><span class="sxs-lookup"><span data-stu-id="966c2-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="966c2-109">相反地，該結構會包含元素的參考。</span><span class="sxs-lookup"><span data-stu-id="966c2-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="966c2-110">C# 2.0 新增一項功能，可將固定大小的陣列嵌入用於[不安全](../../../csharp/language-reference/keywords/unsafe.md)的程式碼區塊中的[結構](../../../csharp/language-reference/keywords/struct.md)。</span><span class="sxs-lookup"><span data-stu-id="966c2-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="966c2-111">例如，在 C# 2.0 之前，下列 `struct` 的大小會是 8 個位元組。</span><span class="sxs-lookup"><span data-stu-id="966c2-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="966c2-112">`pathName` 陣列是堆積配置陣列的參考：</span><span class="sxs-lookup"><span data-stu-id="966c2-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 <span data-ttu-id="966c2-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="966c2-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span></span>  
  
 <span data-ttu-id="966c2-114">從 C# 2.0 開始，`struct` 可以包含內嵌陣列。</span><span class="sxs-lookup"><span data-stu-id="966c2-114">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="966c2-115">在下列範例中，`fixedBuffer` 陣列具有固定大小。</span><span class="sxs-lookup"><span data-stu-id="966c2-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="966c2-116">若要存取陣列的元素，您可以使用 `fixed` 陳述式來建立第一個元素的指標。</span><span class="sxs-lookup"><span data-stu-id="966c2-116">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="966c2-117">`fixed` 陳述式會將 `fixedBuffer` 的執行個體固定在記憶體中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="966c2-117">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 <span data-ttu-id="966c2-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="966c2-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span></span>  
  
 <span data-ttu-id="966c2-119">128 個元素的 `char` 陣列大小為 256 個位元組。</span><span class="sxs-lookup"><span data-stu-id="966c2-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="966c2-120">不論編碼為何，在固定大小的 [char](../../../csharp/language-reference/keywords/char.md) 緩衝區中，每個字元一律會有兩個位元組。</span><span class="sxs-lookup"><span data-stu-id="966c2-120">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="966c2-121">即使 char 緩衝區使用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構也一樣。</span><span class="sxs-lookup"><span data-stu-id="966c2-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="966c2-122">如需詳細資訊，請參閱<xref:System.Runtime.InteropServices.CharSet>。</span><span class="sxs-lookup"><span data-stu-id="966c2-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="966c2-123">另一個常見的固定大小陣列是 [bool](../../../csharp/language-reference/keywords/bool.md) 陣列。</span><span class="sxs-lookup"><span data-stu-id="966c2-123">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="966c2-124">`bool` 陣列中的元素大小一律為一個位元組。</span><span class="sxs-lookup"><span data-stu-id="966c2-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="966c2-125">`bool` 陣列不適用於建立位元陣列或緩衝區。</span><span class="sxs-lookup"><span data-stu-id="966c2-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="966c2-126">除了使用 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) 所建立的記憶體以外，C# 編譯器和 Common Language Runtime (CLR) 不會執行任何安全性緩衝區溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="966c2-126">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="966c2-127">請與所有不安全的程式碼一樣小心使用。</span><span class="sxs-lookup"><span data-stu-id="966c2-127">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="966c2-128">不安全的緩衝區與一般陣列的差異如下：</span><span class="sxs-lookup"><span data-stu-id="966c2-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="966c2-129">您只能在不安全的內容中使用不安全的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="966c2-129">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="966c2-130">不安全的緩衝區一律是向量或一維陣列。</span><span class="sxs-lookup"><span data-stu-id="966c2-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="966c2-131">陣列的宣告應包含計數，例如 `char id[8]`。</span><span class="sxs-lookup"><span data-stu-id="966c2-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="966c2-132">您不能改用 `char id[]`。</span><span class="sxs-lookup"><span data-stu-id="966c2-132">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="966c2-133">不安全的緩衝區只能是不安全內容中結構的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="966c2-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966c2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="966c2-134">See Also</span></span>  
 <span data-ttu-id="966c2-135">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="966c2-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="966c2-136">[不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="966c2-136">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="966c2-137">[fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="966c2-137">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="966c2-138">互通性</span><span class="sxs-lookup"><span data-stu-id="966c2-138">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)

