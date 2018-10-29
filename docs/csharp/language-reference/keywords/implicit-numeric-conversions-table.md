---
title: 隱含數值轉換表 (C# 參考)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: c3c0153a0ae3e07839822c8bb978b1a09277bd53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188699"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="1d0b3-102">隱含數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1d0b3-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="1d0b3-103">下表顯示 .NET 數字類型間預先定義的隱含數值轉換。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="1d0b3-104">從</span><span class="sxs-lookup"><span data-stu-id="1d0b3-104">From</span></span>|<span data-ttu-id="1d0b3-105">以</span><span class="sxs-lookup"><span data-stu-id="1d0b3-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="1d0b3-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="1d0b3-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="1d0b3-107">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-108">byte</span><span class="sxs-lookup"><span data-stu-id="1d0b3-108">byte</span></span>](byte.md)|<span data-ttu-id="1d0b3-109">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-110">short</span><span class="sxs-lookup"><span data-stu-id="1d0b3-110">short</span></span>](short.md)|<span data-ttu-id="1d0b3-111">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-112">ushort</span><span class="sxs-lookup"><span data-stu-id="1d0b3-112">ushort</span></span>](ushort.md)|<span data-ttu-id="1d0b3-113">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-114">int</span><span class="sxs-lookup"><span data-stu-id="1d0b3-114">int</span></span>](int.md)|<span data-ttu-id="1d0b3-115">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-116">uint</span><span class="sxs-lookup"><span data-stu-id="1d0b3-116">uint</span></span>](uint.md)|<span data-ttu-id="1d0b3-117">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-118">long</span><span class="sxs-lookup"><span data-stu-id="1d0b3-118">long</span></span>](long.md)|<span data-ttu-id="1d0b3-119">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-120">char</span><span class="sxs-lookup"><span data-stu-id="1d0b3-120">char</span></span>](char.md)|<span data-ttu-id="1d0b3-121">`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="1d0b3-122">float</span><span class="sxs-lookup"><span data-stu-id="1d0b3-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="1d0b3-123">ulong</span><span class="sxs-lookup"><span data-stu-id="1d0b3-123">ulong</span></span>](ulong.md)|<span data-ttu-id="1d0b3-124">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="1d0b3-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d0b3-125">備註</span><span class="sxs-lookup"><span data-stu-id="1d0b3-125">Remarks</span></span>  

- <span data-ttu-id="1d0b3-126">任何[整數型別](integral-types-table.md)都會隱含轉換為任何[浮點類型](floating-point-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="1d0b3-127">從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="1d0b3-128">`char` 類型沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="1d0b3-129">`float` 和 `double` 類型以及 `decimal` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="1d0b3-130">類型 `int` 常數運算式的值 (例如整數常值所代表的值) 可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，前提是其在目的地類型的範圍內：</span><span class="sxs-lookup"><span data-stu-id="1d0b3-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="1d0b3-131">如需隱含轉換的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[隱含轉換](~/_csharplang/spec/conversions.md#implicit-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="1d0b3-131">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1d0b3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d0b3-132">See also</span></span>

- [<span data-ttu-id="1d0b3-133">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1d0b3-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d0b3-134">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1d0b3-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d0b3-135">整數型別表</span><span class="sxs-lookup"><span data-stu-id="1d0b3-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="1d0b3-136">浮點數類型表</span><span class="sxs-lookup"><span data-stu-id="1d0b3-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="1d0b3-137">內建型別表</span><span class="sxs-lookup"><span data-stu-id="1d0b3-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="1d0b3-138">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="1d0b3-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="1d0b3-139">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="1d0b3-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
