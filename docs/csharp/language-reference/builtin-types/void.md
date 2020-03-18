---
title: 空 - C# 參考
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: c6c1c28e3d7a53a1dcadcf50d8d7f42c8c8aeee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846204"
---
# <a name="void-c-reference"></a><span data-ttu-id="03a08-102">空（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="03a08-102">void (C# reference)</span></span>

<span data-ttu-id="03a08-103">使用`void`作為[方法](../../programming-guide/classes-and-structs/methods.md)（或[局部函數](../../programming-guide/classes-and-structs/local-functions.md)）的返回類型來指定該方法不傳回值。</span><span class="sxs-lookup"><span data-stu-id="03a08-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

<span data-ttu-id="03a08-104">您還可以使用`void`作為參考型別來聲明指向未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="03a08-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="03a08-105">如需詳細資訊，請參閱[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="03a08-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="03a08-106">不能用作`void`變數的類型。</span><span class="sxs-lookup"><span data-stu-id="03a08-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="03a08-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03a08-107">See also</span></span>

- [<span data-ttu-id="03a08-108">C# 參考</span><span class="sxs-lookup"><span data-stu-id="03a08-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
