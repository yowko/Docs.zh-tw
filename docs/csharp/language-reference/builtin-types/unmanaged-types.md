---
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 81eef59ceb20bcae6c749dd59578ce35da253826
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204478"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="4ec05-102">Unmanaged 型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4ec05-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="4ec05-103">A type is an **unmanaged type** if it's any of the following types:</span><span class="sxs-lookup"><span data-stu-id="4ec05-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="4ec05-104">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`</span><span class="sxs-lookup"><span data-stu-id="4ec05-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="4ec05-105">任何 [enum](../keywords/enum.md) 型別</span><span class="sxs-lookup"><span data-stu-id="4ec05-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="4ec05-106">任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別</span><span class="sxs-lookup"><span data-stu-id="4ec05-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="4ec05-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span><span class="sxs-lookup"><span data-stu-id="4ec05-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="4ec05-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span><span class="sxs-lookup"><span data-stu-id="4ec05-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="4ec05-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="4ec05-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="4ec05-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span><span class="sxs-lookup"><span data-stu-id="4ec05-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="4ec05-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span><span class="sxs-lookup"><span data-stu-id="4ec05-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="4ec05-112">The example of not an unmanaged type is `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="4ec05-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="4ec05-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span><span class="sxs-lookup"><span data-stu-id="4ec05-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="4ec05-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span><span class="sxs-lookup"><span data-stu-id="4ec05-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="4ec05-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4ec05-115">C# language specification</span></span>

<span data-ttu-id="4ec05-116">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="4ec05-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ec05-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ec05-117">See also</span></span>

- [<span data-ttu-id="4ec05-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4ec05-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4ec05-119">指標型別</span><span class="sxs-lookup"><span data-stu-id="4ec05-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4ec05-120">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="4ec05-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="4ec05-121">sizeof 運算子</span><span class="sxs-lookup"><span data-stu-id="4ec05-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="4ec05-122">stackalloc 運算子</span><span class="sxs-lookup"><span data-stu-id="4ec05-122">stackalloc operator</span></span>](../operators/stackalloc.md)
