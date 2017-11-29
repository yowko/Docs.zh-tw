---
title: "位元運算子 (F#)"
description: "深入了解 F # 程式語言中可用的位元運算子。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a><span data-ttu-id="47d61-104">位元運算子</span><span class="sxs-lookup"><span data-stu-id="47d61-104">Bitwise Operators</span></span>

<span data-ttu-id="47d61-105">本主題說明在 F # 語言中可用的位元運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-105">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="47d61-106">位元運算子的摘要</span><span class="sxs-lookup"><span data-stu-id="47d61-106">Summary of Bitwise Operators</span></span>
<span data-ttu-id="47d61-107">下表描述支援 F # 語言中的 unboxed 整數類資料類型的位元運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-107">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="47d61-108">運算子</span><span class="sxs-lookup"><span data-stu-id="47d61-108">Operator</span></span>|<span data-ttu-id="47d61-109">注意</span><span class="sxs-lookup"><span data-stu-id="47d61-109">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="47d61-110">位元 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-110">Bitwise AND operator.</span></span> <span data-ttu-id="47d61-111">如果且只有在兩個來源運算元的對應位元為 1，結果中的位元會有 1 的值。</span><span class="sxs-lookup"><span data-stu-id="47d61-111">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="47d61-112">位元 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-112">Bitwise OR operator.</span></span> <span data-ttu-id="47d61-113">在結果中的位元具有值 1，如果在來源中的對應位元的運算元都是 1。</span><span class="sxs-lookup"><span data-stu-id="47d61-113">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="47d61-114">位元互斥 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-114">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="47d61-115">如果且只有來源運算元的位元有相等的值，結果中的位元會有 1 的值。</span><span class="sxs-lookup"><span data-stu-id="47d61-115">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="47d61-116">位元否定運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-116">Bitwise negation operator.</span></span> <span data-ttu-id="47d61-117">這是一元運算子，而且產生的結果，在其中所有來源運算元中的 0 位元都轉換成 1 個位元，而所有的 1 位元會都轉換成 0 位元。</span><span class="sxs-lookup"><span data-stu-id="47d61-117">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="47d61-118">位元左移位運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-118">Bitwise left-shift operator.</span></span> <span data-ttu-id="47d61-119">結果會是第一個運算元的位元移位左邊的第二個運算元的位元數。</span><span class="sxs-lookup"><span data-stu-id="47d61-119">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="47d61-120">位元移出的最重要的位置不會旋轉至最不重要的位置。</span><span class="sxs-lookup"><span data-stu-id="47d61-120">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="47d61-121">最小顯著性位元填補零。</span><span class="sxs-lookup"><span data-stu-id="47d61-121">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="47d61-122">第二個引數的型別是`int32`。</span><span class="sxs-lookup"><span data-stu-id="47d61-122">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="47d61-123">位元右移位運算子。</span><span class="sxs-lookup"><span data-stu-id="47d61-123">Bitwise right-shift operator.</span></span> <span data-ttu-id="47d61-124">結果會是第一個運算元與第二個運算元的位元數向右移位的位元。</span><span class="sxs-lookup"><span data-stu-id="47d61-124">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="47d61-125">位元移出的最小顯著性位置不會旋轉至最重要的位置。</span><span class="sxs-lookup"><span data-stu-id="47d61-125">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="47d61-126">不帶正負號的類型，最大顯著性位元填補零。</span><span class="sxs-lookup"><span data-stu-id="47d61-126">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="47d61-127">帶正負號的類型，最大顯著性位元和填補。</span><span class="sxs-lookup"><span data-stu-id="47d61-127">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="47d61-128">第二個引數的型別是`int32`。</span><span class="sxs-lookup"><span data-stu-id="47d61-128">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="47d61-129">下列型別可與位元運算子： `byte`， `sbyte`， `int16`， `uint16`， `int32 (int)`， `uint32`， `int64`， `uint64`， `nativeint`，和`unativeint`。</span><span class="sxs-lookup"><span data-stu-id="47d61-129">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="47d61-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47d61-130">See Also</span></span>
[<span data-ttu-id="47d61-131">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="47d61-131">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="47d61-132">算術運算子</span><span class="sxs-lookup"><span data-stu-id="47d61-132">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="47d61-133">布林運算子</span><span class="sxs-lookup"><span data-stu-id="47d61-133">Boolean Operators</span></span>](boolean-operators.md)

