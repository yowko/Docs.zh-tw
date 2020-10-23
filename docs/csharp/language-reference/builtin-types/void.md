---
description: 深入瞭解 C 中的 void 關鍵字#
title: 'void-c # 參考'
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: fb22fffadeff4db9fcd8e1c8753d44455186aa5a
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471633"
---
# <a name="void-c-reference"></a><span data-ttu-id="88c6e-103">void (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="88c6e-103">void (C# reference)</span></span>

<span data-ttu-id="88c6e-104">您可以使用 `void` 做為 [方法](../../programming-guide/classes-and-structs/methods.md) 的傳回類型 (或 [區域函數](../../programming-guide/classes-and-structs/local-functions.md)) 來指定方法不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="88c6e-104">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/shared/VoidType.cs#VoidExample)]

<span data-ttu-id="88c6e-105">您也可以使用 `void` 做為參考型別來宣告未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="88c6e-105">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="88c6e-106">如需詳細資訊，請參閱[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="88c6e-106">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="88c6e-107">您無法使用 `void` 做為變數的類型。</span><span class="sxs-lookup"><span data-stu-id="88c6e-107">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="88c6e-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88c6e-108">See also</span></span>

- [<span data-ttu-id="88c6e-109">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="88c6e-109">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
