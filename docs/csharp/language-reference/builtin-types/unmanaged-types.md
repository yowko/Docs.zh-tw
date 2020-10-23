---
description: 瞭解 C 中的非受控類型#
title: Unmanaged 型別 - C# 參考
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 4374872af13c94e1a1af6b9f2c431f076c6f7dff
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471795"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="eba34-103">Unmanaged 型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="eba34-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="eba34-104">如果類型為下列任何一種類型，則類型為 **非受控型** 別：</span><span class="sxs-lookup"><span data-stu-id="eba34-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="eba34-105">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 或 `bool`</span><span class="sxs-lookup"><span data-stu-id="eba34-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="eba34-106">任何 [enum](enum.md) 型別</span><span class="sxs-lookup"><span data-stu-id="eba34-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="eba34-107">任何[指標](../../programming-guide/unsafe-code-pointers/pointer-types.md)型別</span><span class="sxs-lookup"><span data-stu-id="eba34-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="eba34-108">只有包含一個型別引數的型別 (類型的任何使用者定義 [結構](struct.md) 類型，其中只包含非受控類型的欄位，而在 c # 7.3 和更早版本中，則不是結構化類型) </span><span class="sxs-lookup"><span data-stu-id="eba34-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="eba34-109">從 c # 7.3 開始，您可以使用[ `unmanaged` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)指定型別參數為非指標、不可為 null 的非 null 非受控型別。</span><span class="sxs-lookup"><span data-stu-id="eba34-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="eba34-110">從 c # 8.0 開始，包含非受控型別之欄位 *的結構化結構類型* 也不受管理，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="eba34-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="eba34-111">泛型結構可能是非受控和非受控結構類型的來源。</span><span class="sxs-lookup"><span data-stu-id="eba34-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="eba34-112">上述範例會定義泛型結構 `Coords<T>` ，並提供非受控結構類型的範例。</span><span class="sxs-lookup"><span data-stu-id="eba34-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="eba34-113">非受控類型的範例為 `Coords<object>` 。</span><span class="sxs-lookup"><span data-stu-id="eba34-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="eba34-114">它不是未受管理的，因為它具有 `object` 不受管理的類型欄位。</span><span class="sxs-lookup"><span data-stu-id="eba34-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="eba34-115">如果您想要讓 *所有* 的結構化型別都是非受控型別，請 `unmanaged` 在泛型結構的定義中使用條件約束：</span><span class="sxs-lookup"><span data-stu-id="eba34-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="eba34-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="eba34-116">C# language specification</span></span>

<span data-ttu-id="eba34-117">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指標型別](~/_csharplang/spec/unsafe-code.md#pointer-types)。</span><span class="sxs-lookup"><span data-stu-id="eba34-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eba34-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba34-118">See also</span></span>

- [<span data-ttu-id="eba34-119">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="eba34-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="eba34-120">指標類型</span><span class="sxs-lookup"><span data-stu-id="eba34-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="eba34-121">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="eba34-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="eba34-122">sizeof 運算子</span><span class="sxs-lookup"><span data-stu-id="eba34-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="eba34-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="eba34-123">stackalloc</span></span>](../operators/stackalloc.md)
