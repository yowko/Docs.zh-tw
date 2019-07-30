---
title: Unmanaged 型別 - C# 參考
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512068"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="54bd4-102">Unmanaged 型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="54bd4-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="54bd4-103">**unmanaged 型別**是任何不屬於參考型別或建構型別 (包含至少一個型別引數的型別) 的型別，並且在巢狀結構的任何層級中都不包含參考型別或建構型別欄位。</span><span class="sxs-lookup"><span data-stu-id="54bd4-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="54bd4-104">換句話說，unmanaged 型別是以下其中一個型別：</span><span class="sxs-lookup"><span data-stu-id="54bd4-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="54bd4-105">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`</span><span class="sxs-lookup"><span data-stu-id="54bd4-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="54bd4-106">任何 [enum](../keywords/enum.md) 型別</span><span class="sxs-lookup"><span data-stu-id="54bd4-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="54bd4-107">任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別</span><span class="sxs-lookup"><span data-stu-id="54bd4-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="54bd4-108">任何使用者定義，並非建構型別且只包含 unmanaged 型別欄位的 [struct](../keywords/struct.md) 型別</span><span class="sxs-lookup"><span data-stu-id="54bd4-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="54bd4-109">從 C# 7.3 開始，您可以使用 [`unmanaged` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定型別參數是非指標 unmanaged 型別。</span><span class="sxs-lookup"><span data-stu-id="54bd4-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="54bd4-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="54bd4-110">C# language specification</span></span>

<span data-ttu-id="54bd4-111">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="54bd4-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54bd4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54bd4-112">See also</span></span>

- [<span data-ttu-id="54bd4-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="54bd4-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="54bd4-114">指標型別</span><span class="sxs-lookup"><span data-stu-id="54bd4-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="54bd4-115">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="54bd4-115">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="54bd4-116">sizeof 運算子</span><span class="sxs-lookup"><span data-stu-id="54bd4-116">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="54bd4-117">stackalloc 運算子</span><span class="sxs-lookup"><span data-stu-id="54bd4-117">stackalloc operator</span></span>](../operators/stackalloc.md)
