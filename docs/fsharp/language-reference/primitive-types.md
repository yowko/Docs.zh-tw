---
title: "基本類型 (F#)"
description: "探索用於 F # 語言的基本基本類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a><span data-ttu-id="3301f-104">基本類型</span><span class="sxs-lookup"><span data-stu-id="3301f-104">Primitive Types</span></span>

<span data-ttu-id="3301f-105">本主題列出用於 F # 語言的基本基本類型。</span><span class="sxs-lookup"><span data-stu-id="3301f-105">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="3301f-106">它也會提供對應的 .NET 類型以及每個類型的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="3301f-106">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="3301f-107">基本類型的摘要</span><span class="sxs-lookup"><span data-stu-id="3301f-107">Summary of Primitive Types</span></span>
<span data-ttu-id="3301f-108">下表摘要說明基本的 F # 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="3301f-108">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="3301f-109">類型</span><span class="sxs-lookup"><span data-stu-id="3301f-109">Type</span></span>|<span data-ttu-id="3301f-110">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="3301f-110">.NET type</span></span>|<span data-ttu-id="3301f-111">說明</span><span class="sxs-lookup"><span data-stu-id="3301f-111">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="3301f-112">可能的值為 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="3301f-112">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="3301f-113">從 0 到 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-113">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="3301f-114">從-128 到 127 的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-114">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="3301f-115">從-32768 到 32767 之間的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-115">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="3301f-116">介於 0 到 65535 的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-116">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="3301f-117">從-2,147,483,648 到 2,147,483,647 的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-117">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="3301f-118">介於 0 到 4,294,967,295 的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-118">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="3301f-119">值-9223372036854775808 到 9,223,372,036,854,775,807。</span><span class="sxs-lookup"><span data-stu-id="3301f-119">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="3301f-120">介於 0 到 18446744073709551615 的值。</span><span class="sxs-lookup"><span data-stu-id="3301f-120">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="3301f-121">原生指標為帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="3301f-121">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="3301f-122">原生指標的不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="3301f-122">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="3301f-123">Unicode 字元值。</span><span class="sxs-lookup"><span data-stu-id="3301f-123">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="3301f-124">Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="3301f-124">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="3301f-125">浮點資料類型具有至少 28 位有效位數。</span><span class="sxs-lookup"><span data-stu-id="3301f-125">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="3301f-126">不適用</span><span class="sxs-lookup"><span data-stu-id="3301f-126">not applicable</span></span>|<span data-ttu-id="3301f-127">指出實際的值不存在。</span><span class="sxs-lookup"><span data-stu-id="3301f-127">Indicates the absence of an actual value.</span></span> <span data-ttu-id="3301f-128">類型具有一個型式的值，表示`()`。</span><span class="sxs-lookup"><span data-stu-id="3301f-128">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="3301f-129">單位值， `()`，通常是做為預留位置，其中需要值時，但沒有真正的價值可用或有意義。</span><span class="sxs-lookup"><span data-stu-id="3301f-129">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="3301f-130">表示沒有類型或值。</span><span class="sxs-lookup"><span data-stu-id="3301f-130">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="3301f-131">32 位元浮點類型。</span><span class="sxs-lookup"><span data-stu-id="3301f-131">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="3301f-132">64 位元浮點類型。</span><span class="sxs-lookup"><span data-stu-id="3301f-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="3301f-133">您也可以使用 64 位元整數類型的執行與整數太大的計算[bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型別。</span><span class="sxs-lookup"><span data-stu-id="3301f-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="3301f-134">`bigint`不是基本型別。它是的縮寫`System.Numerics.BigInteger`。</span><span class="sxs-lookup"><span data-stu-id="3301f-134">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3301f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3301f-135">See Also</span></span>
[<span data-ttu-id="3301f-136">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="3301f-136">F# Language Reference</span></span>](index.md)
