---
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846456"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="0530b-102">Unmanaged 型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0530b-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="0530b-103">類型是**非託管類型**（如果是以下任何類型）：</span><span class="sxs-lookup"><span data-stu-id="0530b-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="0530b-104">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`</span><span class="sxs-lookup"><span data-stu-id="0530b-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="0530b-105">任何 [enum](enum.md) 型別</span><span class="sxs-lookup"><span data-stu-id="0530b-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="0530b-106">任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別</span><span class="sxs-lookup"><span data-stu-id="0530b-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="0530b-107">任何使用者定義的[結構](struct.md)類型，僅包含非託管類型的欄位，並且在 C# 7.3 和更早版本中，不是構造類型（至少包含一個類型參數的類型）</span><span class="sxs-lookup"><span data-stu-id="0530b-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="0530b-108">從 C# 7.3 開始，可以使用[`unmanaged`約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定類型參數是非指標、不可空的不可託管類型。</span><span class="sxs-lookup"><span data-stu-id="0530b-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="0530b-109">從 C# 8.0 開始，僅包含非託管類型的欄位的*構造*結構類型也是非託管的，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="0530b-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="0530b-110">泛型結構可能是非託管類型和非非託管構造類型的源。</span><span class="sxs-lookup"><span data-stu-id="0530b-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="0530b-111">前面的示例定義了泛型結構，`Coords<T>`並介紹了非託管構造類型的示例。</span><span class="sxs-lookup"><span data-stu-id="0530b-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="0530b-112">非託管類型的示例為`Coords<object>`。</span><span class="sxs-lookup"><span data-stu-id="0530b-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="0530b-113">它不是非託管的，因為它具有`object`類型的欄位，該欄位不是非託管的。</span><span class="sxs-lookup"><span data-stu-id="0530b-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="0530b-114">如果希望*所有*構造類型都是非託管類型，請使用泛型結構`unmanaged`定義中的約束：</span><span class="sxs-lookup"><span data-stu-id="0530b-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="0530b-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0530b-115">C# language specification</span></span>

<span data-ttu-id="0530b-116">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="0530b-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0530b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0530b-117">See also</span></span>

- [<span data-ttu-id="0530b-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0530b-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0530b-119">指標類型</span><span class="sxs-lookup"><span data-stu-id="0530b-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0530b-120">記憶體和跨距相關類型</span><span class="sxs-lookup"><span data-stu-id="0530b-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="0530b-121">sizeof 運算子</span><span class="sxs-lookup"><span data-stu-id="0530b-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="0530b-122">stackalloc 運算子</span><span class="sxs-lookup"><span data-stu-id="0530b-122">stackalloc operator</span></span>](../operators/stackalloc.md)
