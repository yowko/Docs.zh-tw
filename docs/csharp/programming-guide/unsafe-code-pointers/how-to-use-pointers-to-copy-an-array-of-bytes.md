---
title: 如何使用指標複製位元組陣列 - C# 程式設計指南
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698452"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="82059-102">如何使用指標複製位元組陣列（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="82059-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="82059-103">下列範例會使用指標，以將位元組從某個陣列複製到另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="82059-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="82059-104">這個範例會使用 [unsafe](../../language-reference/keywords/unsafe.md) 關鍵字，讓您可以使用 `Copy` 方法中的指標。</span><span class="sxs-lookup"><span data-stu-id="82059-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="82059-105">[fixed](../../language-reference/keywords/fixed-statement.md) 陳述式用來宣告來源和目的陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="82059-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="82059-106">`fixed` 陳述式會將來源和目的陣列的位置「釘選」\*\* 到記憶體中，讓記憶體回收不會移動它們。</span><span class="sxs-lookup"><span data-stu-id="82059-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="82059-107">`fixed` 區塊完成時，會取消釘選陣列的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="82059-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="82059-108">因為這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，所以必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項進行編譯。</span><span class="sxs-lookup"><span data-stu-id="82059-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="82059-109">這個範例會使用索引 (而不是第二個非受控指標) 來存取這兩個陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="82059-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="82059-110">`pSource` 和 `pTarget` 指標的宣告會釘選到陣列。</span><span class="sxs-lookup"><span data-stu-id="82059-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="82059-111">這項功能從 C# 7.3 開始可供使用。</span><span class="sxs-lookup"><span data-stu-id="82059-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="82059-112">範例</span><span class="sxs-lookup"><span data-stu-id="82059-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="82059-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82059-113">See also</span></span>

- [<span data-ttu-id="82059-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="82059-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="82059-115">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="82059-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="82059-116">-unsafe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="82059-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="82059-117">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="82059-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
