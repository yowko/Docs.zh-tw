---
title: 不安全的程式碼與指標 - C# 程式設計手冊
Description: "瞭解 unsafe 程式碼和指標。 C # 不支援指標，但是您可以定義不安全的內容，其中的指標可與 ' unsafe ' 關鍵字搭配使用。"
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381771"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="f063a-104">不安全的程式碼和指標 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f063a-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="f063a-105">為了維護型別安全和安全性，C# 預設不支援指標算術。</span><span class="sxs-lookup"><span data-stu-id="f063a-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="f063a-106">不過，藉由使用 [unsafe](../../language-reference/keywords/unsafe.md) 關鍵字，即可定義能在其中使用指標的不安全內容。</span><span class="sxs-lookup"><span data-stu-id="f063a-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="f063a-107">如需指標的詳細資訊，請參閱[指標類型](pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f063a-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f063a-108">在 Common Language Runtime (CLR) 中，不安全的程式碼是指無法驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f063a-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="f063a-109">C# 中不安全的程式碼不一定具有危險性，這不過是其安全性無法由 CLR 驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f063a-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="f063a-110">因此，CLR 只會執行完全受信任之組件中不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f063a-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="f063a-111">如果您使用不安全的程式碼，則有責任確保程式碼不會帶來安全性風險或造成指標錯誤。</span><span class="sxs-lookup"><span data-stu-id="f063a-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="f063a-112">不安全的程式碼概觀</span><span class="sxs-lookup"><span data-stu-id="f063a-112">Unsafe code overview</span></span>

<span data-ttu-id="f063a-113">不安全的程式碼具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f063a-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="f063a-114">方法、類型和程式碼區塊可以定義為不安全。</span><span class="sxs-lookup"><span data-stu-id="f063a-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="f063a-115">在某些情況下，不安全的程式碼可能會藉由移除陣列界限檢查，來提升應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="f063a-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="f063a-116">當您呼叫需要指標的原生函式時，需要不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f063a-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="f063a-117">使用不安全的程式碼會帶來安全性和穩定性風險。</span><span class="sxs-lookup"><span data-stu-id="f063a-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="f063a-118">包含不安全之區塊的程式碼必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項編譯。</span><span class="sxs-lookup"><span data-stu-id="f063a-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="f063a-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="f063a-119">Related sections</span></span>

<span data-ttu-id="f063a-120">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="f063a-120">For more information, see:</span></span>

- [<span data-ttu-id="f063a-121">指標類型</span><span class="sxs-lookup"><span data-stu-id="f063a-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="f063a-122">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="f063a-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="f063a-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f063a-123">C# language specification</span></span>

<span data-ttu-id="f063a-124">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)中的[不安全的程式碼](~/_csharplang/spec/unsafe-code.md)主題。</span><span class="sxs-lookup"><span data-stu-id="f063a-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f063a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f063a-125">See also</span></span>

- [<span data-ttu-id="f063a-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f063a-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f063a-127">不安全</span><span class="sxs-lookup"><span data-stu-id="f063a-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
