---
title: 基本類型
description: '探索 F # 語言中使用的基本基本類型。'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557694"
---
# <a name="basic-types"></a><span data-ttu-id="921bf-103">基本類型</span><span class="sxs-lookup"><span data-stu-id="921bf-103">Basic types</span></span>

<span data-ttu-id="921bf-104">本主題列出在 F # 語言中定義的基本類型。</span><span class="sxs-lookup"><span data-stu-id="921bf-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="921bf-105">這些類型在 F # 中是最基本的，形成幾乎每一個 F # 程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="921bf-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="921bf-106">它們是 .NET 基本型別的超集合。</span><span class="sxs-lookup"><span data-stu-id="921bf-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="921bf-107">類型</span><span class="sxs-lookup"><span data-stu-id="921bf-107">Type</span></span>|<span data-ttu-id="921bf-108">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="921bf-108">.NET type</span></span>|<span data-ttu-id="921bf-109">描述</span><span class="sxs-lookup"><span data-stu-id="921bf-109">Description</span></span>|<span data-ttu-id="921bf-110">範例</span><span class="sxs-lookup"><span data-stu-id="921bf-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="921bf-111">可能的值是 `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="921bf-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="921bf-112">從0到255的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="921bf-113">介於-128 到127之間的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="921bf-114">介於-32768 到32767之間的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="921bf-115">從0到65535的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="921bf-116">介於-2147483648 到2147483647之間的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="921bf-117">從0到4294967295的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="921bf-118">從-9223372036854775808 到9223372036854775807的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="921bf-119">0到18446744073709551615之間的值。</span><span class="sxs-lookup"><span data-stu-id="921bf-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="921bf-120">作為帶正負號整數的原生指標。</span><span class="sxs-lookup"><span data-stu-id="921bf-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="921bf-121">原生指標，作為不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="921bf-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="921bf-122">浮點數資料類型至少有28個有效位數。</span><span class="sxs-lookup"><span data-stu-id="921bf-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="921bf-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="921bf-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="921bf-124">64位浮點數類型。</span><span class="sxs-lookup"><span data-stu-id="921bf-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="921bf-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="921bf-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="921bf-126">32位浮點數類型。</span><span class="sxs-lookup"><span data-stu-id="921bf-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="921bf-127">Unicode 字元值。</span><span class="sxs-lookup"><span data-stu-id="921bf-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="921bf-128">Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="921bf-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="921bf-129">不適用</span><span class="sxs-lookup"><span data-stu-id="921bf-129">not applicable</span></span>|<span data-ttu-id="921bf-130">指出沒有實際值。</span><span class="sxs-lookup"><span data-stu-id="921bf-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="921bf-131">型別只有一個正式值，即表示 `()` 。</span><span class="sxs-lookup"><span data-stu-id="921bf-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="921bf-132">單位值（ `()` ）通常用來做為需要值的預留位置，但沒有可用的實際值或意義。</span><span class="sxs-lookup"><span data-stu-id="921bf-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="921bf-133">您可以使用 [Bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) 型別，對64位整數類型的整數執行太大的計算。</span><span class="sxs-lookup"><span data-stu-id="921bf-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) type.</span></span> <span data-ttu-id="921bf-134">`bigint` 不會被視為基本類型;這是的縮寫 `System.Numerics.BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="921bf-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="921bf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="921bf-135">See also</span></span>

- [<span data-ttu-id="921bf-136">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="921bf-136">F# Language Reference</span></span>](index.md)
