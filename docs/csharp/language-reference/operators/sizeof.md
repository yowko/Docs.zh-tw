---
title: sizeof 運算子 - C# 參考
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 8e4518718d0975f8b4a65870f15d8c52d692c2f5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625731"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="07478-102">sizeof 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="07478-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="07478-103">`sizeof` 運算子會返回指定型別變數所佔用的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="07478-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="07478-104">`sizeof` 運算子的引數必須是[非受控型別](../builtin-types/unmanaged-types.md)的名稱，或是[限制](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)為非受控型別的型別參數。</span><span class="sxs-lookup"><span data-stu-id="07478-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="07478-105">`sizeof` 運算子需要 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="07478-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="07478-106">但是，下表顯示的運算式會在編譯時評估至對應的常數值，因此不需要 unsafe 內容：</span><span class="sxs-lookup"><span data-stu-id="07478-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="07478-107">運算是</span><span class="sxs-lookup"><span data-stu-id="07478-107">Expression</span></span>|<span data-ttu-id="07478-108">常數值</span><span class="sxs-lookup"><span data-stu-id="07478-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="07478-109">1</span><span class="sxs-lookup"><span data-stu-id="07478-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="07478-110">1</span><span class="sxs-lookup"><span data-stu-id="07478-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="07478-111">2</span><span class="sxs-lookup"><span data-stu-id="07478-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="07478-112">2</span><span class="sxs-lookup"><span data-stu-id="07478-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="07478-113">4</span><span class="sxs-lookup"><span data-stu-id="07478-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="07478-114">4</span><span class="sxs-lookup"><span data-stu-id="07478-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="07478-115">8</span><span class="sxs-lookup"><span data-stu-id="07478-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="07478-116">8</span><span class="sxs-lookup"><span data-stu-id="07478-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="07478-117">2</span><span class="sxs-lookup"><span data-stu-id="07478-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="07478-118">4</span><span class="sxs-lookup"><span data-stu-id="07478-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="07478-119">8</span><span class="sxs-lookup"><span data-stu-id="07478-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="07478-120">16</span><span class="sxs-lookup"><span data-stu-id="07478-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="07478-121">1</span><span class="sxs-lookup"><span data-stu-id="07478-121">1</span></span>|

<span data-ttu-id="07478-122">您也不需要在 `sizeof` 運算子的運算元是 [enum](../builtin-types/enum.md) 型別時使用 unsafe 內容。</span><span class="sxs-lookup"><span data-stu-id="07478-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="07478-123">下列範例示範 `sizeof` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="07478-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="07478-124">`sizeof` 運算子會傳回通用語言執行平台在受控記憶體中原先將配置的位元組數。</span><span class="sxs-lookup"><span data-stu-id="07478-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="07478-125">針對 [struct](../builtin-types/struct.md)型別，該值包含任何填補，如先前範例所示範。</span><span class="sxs-lookup"><span data-stu-id="07478-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="07478-126">`sizeof` 運算子的結果可能會與 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法的結果不同，因為後者會傳回型別在 *unmanaged* 記憶體中的大小。</span><span class="sxs-lookup"><span data-stu-id="07478-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="07478-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="07478-127">C# language specification</span></span>

<span data-ttu-id="07478-128">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator)中的 [sizeof 運算子](~/_csharplang/spec/introduction.md)區段。</span><span class="sxs-lookup"><span data-stu-id="07478-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07478-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07478-129">See also</span></span>

- [<span data-ttu-id="07478-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="07478-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="07478-131">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="07478-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="07478-132">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="07478-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="07478-133">指標型別</span><span class="sxs-lookup"><span data-stu-id="07478-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="07478-134">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="07478-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="07478-135">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="07478-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
