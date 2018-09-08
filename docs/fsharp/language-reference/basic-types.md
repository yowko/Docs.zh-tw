---
title: '基本類型 （F #）'
description: '探索基本 F # 語言中使用的基本類型。'
ms.date: 07/09/2018
ms.openlocfilehash: 8f948d066323527b09b1d3f9f4167b95b1c875cf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202202"
---
# <a name="basic-types"></a><span data-ttu-id="44688-103">基本類型</span><span class="sxs-lookup"><span data-stu-id="44688-103">Basic types</span></span>

<span data-ttu-id="44688-104">本主題列出 F # 語言中所定義的基本型別。</span><span class="sxs-lookup"><span data-stu-id="44688-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="44688-105">這些類型是最基本 F #，形成幾乎每個 F # 程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="44688-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="44688-106">也就是.NET 基本類型的超集。</span><span class="sxs-lookup"><span data-stu-id="44688-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="44688-107">類型</span><span class="sxs-lookup"><span data-stu-id="44688-107">Type</span></span>|<span data-ttu-id="44688-108">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="44688-108">.NET type</span></span>|<span data-ttu-id="44688-109">描述</span><span class="sxs-lookup"><span data-stu-id="44688-109">Description</span></span>|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="44688-110">可能的值為 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="44688-110">Possible values are `true` and `false`.</span></span>|
|`byte`|<xref:System.Byte>|<span data-ttu-id="44688-111">介於 0 到 255 的值。</span><span class="sxs-lookup"><span data-stu-id="44688-111">Values from 0 to 255.</span></span>|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="44688-112">介於-128 到 127 的值。</span><span class="sxs-lookup"><span data-stu-id="44688-112">Values from -128 to 127.</span></span>|
|`int16`|<xref:System.Int16>|<span data-ttu-id="44688-113">範圍為-32768 到 32767 之間的值。</span><span class="sxs-lookup"><span data-stu-id="44688-113">Values from -32768 to 32767.</span></span>|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="44688-114">介於 0 到 65535 的值。</span><span class="sxs-lookup"><span data-stu-id="44688-114">Values from 0 to 65535.</span></span>|
|`int`|<xref:System.Int32>|<span data-ttu-id="44688-115">從-2,147,483,648 到 2,147,483,647 的值。</span><span class="sxs-lookup"><span data-stu-id="44688-115">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|<xref:System.UInt32>|<span data-ttu-id="44688-116">介於 0 到 4,294,967,295 的值。</span><span class="sxs-lookup"><span data-stu-id="44688-116">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|<xref:System.Int64>|<span data-ttu-id="44688-117">值-9223372036854775808 到 9,223,372,036,854,775,807。</span><span class="sxs-lookup"><span data-stu-id="44688-117">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="44688-118">介於 0 到 18446744073709551615 的值。</span><span class="sxs-lookup"><span data-stu-id="44688-118">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="44688-119">為帶正負號的整數變數的原生指標。</span><span class="sxs-lookup"><span data-stu-id="44688-119">A native pointer as a signed integer.</span></span>|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="44688-120">原生指標做為不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="44688-120">A native pointer as an unsigned integer.</span></span>|
|`char`|<xref:System.Char>|<span data-ttu-id="44688-121">Unicode 字元值。</span><span class="sxs-lookup"><span data-stu-id="44688-121">Unicode character values.</span></span>|
|`string`|<xref:System.String>|<span data-ttu-id="44688-122">Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="44688-122">Unicode text.</span></span>|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="44688-123">浮點資料型別具有至少 28 位有效位數。</span><span class="sxs-lookup"><span data-stu-id="44688-123">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="44688-124">不適用</span><span class="sxs-lookup"><span data-stu-id="44688-124">not applicable</span></span>|<span data-ttu-id="44688-125">表示沒有實際的值。</span><span class="sxs-lookup"><span data-stu-id="44688-125">Indicates the absence of an actual value.</span></span> <span data-ttu-id="44688-126">類型具有一個型式的值，表示`()`。</span><span class="sxs-lookup"><span data-stu-id="44688-126">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="44688-127">單位值， `()`，通常做為預留位置，其中需要值時，但沒有真正的值使用，或有意義。</span><span class="sxs-lookup"><span data-stu-id="44688-127">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|<xref:System.Void>|<span data-ttu-id="44688-128">表示沒有類型或值。</span><span class="sxs-lookup"><span data-stu-id="44688-128">Indicates no type or value.</span></span>|
|<span data-ttu-id="44688-129">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="44688-129">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="44688-130">32 位元浮點數類型。</span><span class="sxs-lookup"><span data-stu-id="44688-130">A 32-bit floating point type.</span></span>|
|<span data-ttu-id="44688-131">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="44688-131">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="44688-132">64 位元浮點數類型。</span><span class="sxs-lookup"><span data-stu-id="44688-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="44688-133">您也可以使用 64 位元整數類型執行計算整數太大[bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型別。</span><span class="sxs-lookup"><span data-stu-id="44688-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="44688-134">`bigint` 不是基本的類型;它是縮寫`System.Numerics.BigInteger`。</span><span class="sxs-lookup"><span data-stu-id="44688-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="44688-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44688-135">See also</span></span>

- [<span data-ttu-id="44688-136">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="44688-136">F# Language Reference</span></span>](index.md)
