---
title: 位元運算子 (F#)
description: '深入了解 F # 程式設計語言中可用的位元運算子。'
ms.date: 07/20/2018
ms.openlocfilehash: ed76fcf5f9c569a2f288cf260e99dc29fd65ef3b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "48581504"
---
# <a name="bitwise-operators"></a><span data-ttu-id="79fcd-103">位元運算子</span><span class="sxs-lookup"><span data-stu-id="79fcd-103">Bitwise Operators</span></span>

<span data-ttu-id="79fcd-104">本主題說明 F # 語言中可用的位元運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-104">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="79fcd-105">位元運算子的摘要</span><span class="sxs-lookup"><span data-stu-id="79fcd-105">Summary of Bitwise Operators</span></span>

<span data-ttu-id="79fcd-106">下表描述支援 F # 語言中的 unboxed 整數類資料類型的位元運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-106">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="79fcd-107">運算子</span><span class="sxs-lookup"><span data-stu-id="79fcd-107">Operator</span></span>|<span data-ttu-id="79fcd-108">注意</span><span class="sxs-lookup"><span data-stu-id="79fcd-108">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="79fcd-109">位元 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-109">Bitwise AND operator.</span></span> <span data-ttu-id="79fcd-110">如果且只有在兩個來源運算元的對應位元為 1，結果中會有值為 1。</span><span class="sxs-lookup"><span data-stu-id="79fcd-110">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="79fcd-111">位元的 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-111">Bitwise OR operator.</span></span> <span data-ttu-id="79fcd-112">在結果中的位元具有值 1，如果有任一個來源中的對應位元的運算元都是 1。</span><span class="sxs-lookup"><span data-stu-id="79fcd-112">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="79fcd-113">位元互斥 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-113">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="79fcd-114">在結果中的位元具有值 1，如果且只有在來源運算元的位元具有不相等的值。</span><span class="sxs-lookup"><span data-stu-id="79fcd-114">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="79fcd-115">位元否定運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-115">Bitwise negation operator.</span></span> <span data-ttu-id="79fcd-116">這是一元運算子，而且產生的結果，在其中所有的 0 位元，在來源運算元會轉換成 1 的位元和所有的 1 位元轉換成 0 位元。</span><span class="sxs-lookup"><span data-stu-id="79fcd-116">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="79fcd-117">位元左移運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-117">Bitwise left-shift operator.</span></span> <span data-ttu-id="79fcd-118">結果會是第一個運算元與位元左移第二個運算元的位元數目。</span><span class="sxs-lookup"><span data-stu-id="79fcd-118">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="79fcd-119">移出的最大顯著性的位置的位元不會旋轉的最小顯著性的位置。</span><span class="sxs-lookup"><span data-stu-id="79fcd-119">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="79fcd-120">最小顯著性的位元是以零填補。</span><span class="sxs-lookup"><span data-stu-id="79fcd-120">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="79fcd-121">第二個引數的型別是`int32`。</span><span class="sxs-lookup"><span data-stu-id="79fcd-121">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="79fcd-122">位元右移位運算子。</span><span class="sxs-lookup"><span data-stu-id="79fcd-122">Bitwise right-shift operator.</span></span> <span data-ttu-id="79fcd-123">結果會是第一個運算元與位元向右移位由第二個運算元的位元數目。</span><span class="sxs-lookup"><span data-stu-id="79fcd-123">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="79fcd-124">移出的最小顯著性的位置的位元不會旋轉的最大顯著性的位置。</span><span class="sxs-lookup"><span data-stu-id="79fcd-124">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="79fcd-125">不帶正負號的類型，最小顯著性的位元是以零填補。</span><span class="sxs-lookup"><span data-stu-id="79fcd-125">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="79fcd-126">帶正負號的型別具有負數值，最小顯著性的位元會填補的。</span><span class="sxs-lookup"><span data-stu-id="79fcd-126">For signed types with negative values, the most significant bits are padded with ones.</span></span> <span data-ttu-id="79fcd-127">第二個引數的型別是`int32`。</span><span class="sxs-lookup"><span data-stu-id="79fcd-127">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="79fcd-128">與位元運算子，可以使用下列類型： `byte`， `sbyte`， `int16`， `uint16`， `int32 (int)`， `uint32`， `int64`， `uint64`， `nativeint`，以及`unativeint`。</span><span class="sxs-lookup"><span data-stu-id="79fcd-128">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="79fcd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79fcd-129">See also</span></span>

- [<span data-ttu-id="79fcd-130">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="79fcd-130">Symbol and Operator Reference</span></span>](index.md)
- [<span data-ttu-id="79fcd-131">算術運算子</span><span class="sxs-lookup"><span data-stu-id="79fcd-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="79fcd-132">布林運算子</span><span class="sxs-lookup"><span data-stu-id="79fcd-132">Boolean Operators</span></span>](boolean-operators.md)
