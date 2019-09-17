---
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374107"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="6ddf7-102">Unmanaged 型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6ddf7-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="6ddf7-103">如果類型為下列任何類型，則其為**非受控類型**：</span><span class="sxs-lookup"><span data-stu-id="6ddf7-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="6ddf7-104">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`</span><span class="sxs-lookup"><span data-stu-id="6ddf7-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="6ddf7-105">任何 [enum](../keywords/enum.md) 型別</span><span class="sxs-lookup"><span data-stu-id="6ddf7-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="6ddf7-106">任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別</span><span class="sxs-lookup"><span data-stu-id="6ddf7-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="6ddf7-107">只有包含非受控類型欄位和（在7.3 和更早版本中C# ）的任何使用者定義[結構](../keywords/struct.md)類型不是結構化類型（至少包含一個類型引數的類型）</span><span class="sxs-lookup"><span data-stu-id="6ddf7-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="6ddf7-108">從 C# 7.3 開始，您可以使用 [`unmanaged` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定型別參數是非指標 unmanaged 型別。</span><span class="sxs-lookup"><span data-stu-id="6ddf7-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

<span data-ttu-id="6ddf7-109">從C# 8.0 開始，僅包含非受控類型欄位*的結構化結構類型*也是未受管理的，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6ddf7-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="6ddf7-110">泛型結構可能是非受控和非受控結構類型的來源。</span><span class="sxs-lookup"><span data-stu-id="6ddf7-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="6ddf7-111">上述範例會定義泛型結構`Coords<T>` ，並提供非受控結構類型的範例。</span><span class="sxs-lookup"><span data-stu-id="6ddf7-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="6ddf7-112">非受控類型的範例是`Coords<object>`。</span><span class="sxs-lookup"><span data-stu-id="6ddf7-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="6ddf7-113">它不是未受管理的，因為它具有`object`類型的欄位，這不是未受管理。</span><span class="sxs-lookup"><span data-stu-id="6ddf7-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="6ddf7-114">如果您想要*所有*結構化類型都是非受控類型`unmanaged` ，請在泛型結構的定義中使用條件約束：</span><span class="sxs-lookup"><span data-stu-id="6ddf7-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="6ddf7-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6ddf7-115">C# language specification</span></span>

<span data-ttu-id="6ddf7-116">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="6ddf7-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ddf7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ddf7-117">See also</span></span>

- [<span data-ttu-id="6ddf7-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6ddf7-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6ddf7-119">指標型別</span><span class="sxs-lookup"><span data-stu-id="6ddf7-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="6ddf7-120">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="6ddf7-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="6ddf7-121">sizeof 運算子</span><span class="sxs-lookup"><span data-stu-id="6ddf7-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="6ddf7-122">stackalloc 運算子</span><span class="sxs-lookup"><span data-stu-id="6ddf7-122">stackalloc operator</span></span>](../operators/stackalloc.md)
