---
title: unsafe 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 79cb246c4094f02d1319d28fcc94d0d3d5bd9cb5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128423"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="225a6-102">unsafe (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="225a6-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="225a6-103">`unsafe` 關鍵字表示任何與指標有關的作業都需要的不安全內容。</span><span class="sxs-lookup"><span data-stu-id="225a6-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="225a6-104">如需詳細資訊，請參閱[不安全的程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="225a6-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="225a6-105">您可以在類型或成員的宣告中使用 `unsafe` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="225a6-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="225a6-106">類型或成員的整個文字範圍因此視為不安全內容。</span><span class="sxs-lookup"><span data-stu-id="225a6-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="225a6-107">例如，下列是使用 `unsafe` 修飾詞所宣告的方法︰</span><span class="sxs-lookup"><span data-stu-id="225a6-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="225a6-108">不安全內容的範圍是從參數清單延伸到方法結尾，因此也可以在參數清單中使用指標︰</span><span class="sxs-lookup"><span data-stu-id="225a6-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="225a6-109">您也可以使用不安全區塊，以在這個區塊內使用不安全程式碼。</span><span class="sxs-lookup"><span data-stu-id="225a6-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="225a6-110">例如：</span><span class="sxs-lookup"><span data-stu-id="225a6-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="225a6-111">若要編譯不安全的程式碼，您必須指定 [/unsafe](../compiler-options/unsafe-compiler-option.md) 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="225a6-111">To compile unsafe code, you must specify the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="225a6-112">Common Language Runtime 不會驗證不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="225a6-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="225a6-113">範例</span><span class="sxs-lookup"><span data-stu-id="225a6-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="225a6-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="225a6-114">C# language specification</span></span>

<span data-ttu-id="225a6-115">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)中的 [Unsafe 程式碼](~/_csharplang/spec/unsafe-code.md)。</span><span class="sxs-lookup"><span data-stu-id="225a6-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="225a6-116">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="225a6-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="225a6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="225a6-117">See also</span></span>

- [<span data-ttu-id="225a6-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="225a6-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="225a6-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="225a6-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="225a6-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="225a6-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="225a6-121">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="225a6-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="225a6-122">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="225a6-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="225a6-123">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="225a6-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)