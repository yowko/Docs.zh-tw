---
title: 'Unsafe 程式碼和指標 - C# 程式設計手冊'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - 'security [C#], type safety'
  - 'C# language, unsafe code'
  - 'type safety [C#]'
  - 'unsafe keyword [C#]'
  - 'unsafe code [C#]'
  - 'C# language, pointers'
  - 'pointers [C#], about pointers'
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="1ad66-102">Unsafe 程式碼和指標 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1ad66-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="1ad66-103">為了維護型別安全和安全性，C# 預設不支援指標算術。</span><span class="sxs-lookup"><span data-stu-id="1ad66-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="1ad66-104">不過，藉由使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，即可定義能在其中使用指標的不安全內容。</span><span class="sxs-lookup"><span data-stu-id="1ad66-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="1ad66-105">如需指標的詳細資訊，請參閱[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1ad66-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ad66-106">在 Common Language Runtime (CLR) 中，不安全的程式碼是指無法驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ad66-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="1ad66-107">C# 中不安全的程式碼不一定具有危險性，這不過是其安全性無法由 CLR 驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ad66-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="1ad66-108">因此，CLR 只會執行完全受信任之組件中不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ad66-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="1ad66-109">如果您使用不安全的程式碼，則有責任確保程式碼不會帶來安全性風險或造成指標錯誤。</span><span class="sxs-lookup"><span data-stu-id="1ad66-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="1ad66-110">不安全的程式碼概觀</span><span class="sxs-lookup"><span data-stu-id="1ad66-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="1ad66-111">不安全的程式碼具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1ad66-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="1ad66-112">方法、類型和程式碼區塊可以定義為不安全。</span><span class="sxs-lookup"><span data-stu-id="1ad66-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="1ad66-113">在某些情況下，不安全的程式碼可能會藉由移除陣列界限檢查，來提升應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="1ad66-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="1ad66-114">當您呼叫需要指標的原生函式時，需要不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ad66-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="1ad66-115">使用不安全的程式碼會帶來安全性和穩定性風險。</span><span class="sxs-lookup"><span data-stu-id="1ad66-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="1ad66-116">為了讓 C# 編譯不安全的程式碼，必須以 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 來編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ad66-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ad66-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="1ad66-117">Related Sections</span></span>  
 <span data-ttu-id="1ad66-118">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="1ad66-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1ad66-119">指標型別</span><span class="sxs-lookup"><span data-stu-id="1ad66-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="1ad66-120">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="1ad66-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="1ad66-121">如何：使用指標複製位元組陣列</span><span class="sxs-lookup"><span data-stu-id="1ad66-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="1ad66-122">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="1ad66-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1ad66-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1ad66-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ad66-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad66-124">See also</span></span>

- [<span data-ttu-id="1ad66-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1ad66-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
