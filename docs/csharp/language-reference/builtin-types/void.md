---
title: 'void-c # 參考'
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: faf1cea4d02ba042cd9fee1cfa6d18168c49dd61
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854980"
---
# <a name="void-c-reference"></a><span data-ttu-id="885ca-102">void (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="885ca-102">void (C# reference)</span></span>

<span data-ttu-id="885ca-103">您可以使用 `void` 做為[方法](../../programming-guide/classes-and-structs/methods.md)的傳回型別 (或[區域](../../programming-guide/classes-and-structs/local-functions.md)函式) 來指定方法不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="885ca-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

<span data-ttu-id="885ca-104">您也可以使用 `void` 做為參考型別，宣告未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="885ca-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="885ca-105">如需詳細資訊，請參閱[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="885ca-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="885ca-106">您不能使用 `void` 做為變數的類型。</span><span class="sxs-lookup"><span data-stu-id="885ca-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="885ca-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="885ca-107">See also</span></span>

- [<span data-ttu-id="885ca-108">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="885ca-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
