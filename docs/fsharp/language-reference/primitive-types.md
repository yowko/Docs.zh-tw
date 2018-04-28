---
title: 基本類型 (F#)
description: '探索用於 F # 語言的基本基本類型。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7832151ee211f56547ecad98fc31f1454cb18870
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="primitive-types"></a><span data-ttu-id="08002-103">基本類型</span><span class="sxs-lookup"><span data-stu-id="08002-103">Primitive Types</span></span>

<span data-ttu-id="08002-104">本主題列出用於 F # 語言的基本基本類型。</span><span class="sxs-lookup"><span data-stu-id="08002-104">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="08002-105">它也會提供對應的 .NET 類型以及每個類型的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="08002-105">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="08002-106">基本類型的摘要</span><span class="sxs-lookup"><span data-stu-id="08002-106">Summary of Primitive Types</span></span>
<span data-ttu-id="08002-107">下表摘要說明基本的 F # 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="08002-107">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="08002-108">類型</span><span class="sxs-lookup"><span data-stu-id="08002-108">Type</span></span>|<span data-ttu-id="08002-109">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="08002-109">.NET type</span></span>|<span data-ttu-id="08002-110">描述</span><span class="sxs-lookup"><span data-stu-id="08002-110">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="08002-111">可能的值為 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="08002-111">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="08002-112">從 0 到 255 之間的值。</span><span class="sxs-lookup"><span data-stu-id="08002-112">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="08002-113">從-128 到 127 的值。</span><span class="sxs-lookup"><span data-stu-id="08002-113">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="08002-114">從-32768 到 32767 之間的值。</span><span class="sxs-lookup"><span data-stu-id="08002-114">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="08002-115">介於 0 到 65535 的值。</span><span class="sxs-lookup"><span data-stu-id="08002-115">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="08002-116">從-2,147,483,648 到 2,147,483,647 的值。</span><span class="sxs-lookup"><span data-stu-id="08002-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="08002-117">介於 0 到 4,294,967,295 的值。</span><span class="sxs-lookup"><span data-stu-id="08002-117">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="08002-118">值-9223372036854775808 到 9,223,372,036,854,775,807。</span><span class="sxs-lookup"><span data-stu-id="08002-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="08002-119">介於 0 到 18446744073709551615 的值。</span><span class="sxs-lookup"><span data-stu-id="08002-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="08002-120">原生指標為帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="08002-120">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="08002-121">原生指標的不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="08002-121">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="08002-122">Unicode 字元值。</span><span class="sxs-lookup"><span data-stu-id="08002-122">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="08002-123">Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="08002-123">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="08002-124">浮點資料類型具有至少 28 位有效位數。</span><span class="sxs-lookup"><span data-stu-id="08002-124">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="08002-125">不適用</span><span class="sxs-lookup"><span data-stu-id="08002-125">not applicable</span></span>|<span data-ttu-id="08002-126">指出實際的值不存在。</span><span class="sxs-lookup"><span data-stu-id="08002-126">Indicates the absence of an actual value.</span></span> <span data-ttu-id="08002-127">類型具有一個型式的值，表示`()`。</span><span class="sxs-lookup"><span data-stu-id="08002-127">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="08002-128">單位值， `()`，通常是做為預留位置，其中需要值時，但沒有真正的價值可用或有意義。</span><span class="sxs-lookup"><span data-stu-id="08002-128">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="08002-129">表示沒有類型或值。</span><span class="sxs-lookup"><span data-stu-id="08002-129">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="08002-130">32 位元浮點類型。</span><span class="sxs-lookup"><span data-stu-id="08002-130">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="08002-131">64 位元浮點類型。</span><span class="sxs-lookup"><span data-stu-id="08002-131">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="08002-132">您也可以使用 64 位元整數類型的執行與整數太大的計算[bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型別。</span><span class="sxs-lookup"><span data-stu-id="08002-132">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="08002-133">`bigint` 不是基本型別。它是的縮寫`System.Numerics.BigInteger`。</span><span class="sxs-lookup"><span data-stu-id="08002-133">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="08002-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08002-134">See Also</span></span>
[<span data-ttu-id="08002-135">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="08002-135">F# Language Reference</span></span>](index.md)
