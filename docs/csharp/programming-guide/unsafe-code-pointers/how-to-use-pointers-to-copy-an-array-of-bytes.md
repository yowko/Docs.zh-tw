---
title: '如何使用指標來複製位元組陣列-c # 程式設計手冊'
description: 瞭解如何使用指標來複製位元組陣列。 請參閱程式碼範例和其他可用的資源。
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381784"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="7bed4-104">如何使用指標來複製位元組陣列（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="7bed4-104">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="7bed4-105">下列範例會使用指標，以將位元組從某個陣列複製到另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="7bed4-105">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="7bed4-106">這個範例會使用 [unsafe](../../language-reference/keywords/unsafe.md) 關鍵字，讓您可以使用 `Copy` 方法中的指標。</span><span class="sxs-lookup"><span data-stu-id="7bed4-106">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="7bed4-107">[fixed](../../language-reference/keywords/fixed-statement.md) 陳述式用來宣告來源和目的陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="7bed4-107">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="7bed4-108">`fixed` 陳述式會將來源和目的陣列的位置「釘選」\*\* 到記憶體中，讓記憶體回收不會移動它們。</span><span class="sxs-lookup"><span data-stu-id="7bed4-108">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="7bed4-109">`fixed` 區塊完成時，會取消釘選陣列的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="7bed4-109">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="7bed4-110">因為這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，所以必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項進行編譯。</span><span class="sxs-lookup"><span data-stu-id="7bed4-110">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="7bed4-111">這個範例會使用索引 (而不是第二個非受控指標) 來存取這兩個陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="7bed4-111">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="7bed4-112">`pSource` 和 `pTarget` 指標的宣告會釘選到陣列。</span><span class="sxs-lookup"><span data-stu-id="7bed4-112">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="7bed4-113">這項功能從 C# 7.3 開始可供使用。</span><span class="sxs-lookup"><span data-stu-id="7bed4-113">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="7bed4-114">範例</span><span class="sxs-lookup"><span data-stu-id="7bed4-114">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="7bed4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bed4-115">See also</span></span>

- [<span data-ttu-id="7bed4-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7bed4-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7bed4-117">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="7bed4-117">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="7bed4-118">-unsafe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="7bed4-118">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="7bed4-119">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="7bed4-119">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
