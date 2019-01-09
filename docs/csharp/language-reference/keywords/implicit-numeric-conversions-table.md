---
title: 隱含數值轉換表 - C# 參考
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: ab6506e619c675ddd68237c4ddca870e9e14098f
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058460"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="6b5cd-102">隱含數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6b5cd-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="6b5cd-103">下表顯示 .NET 數字類型間預先定義的隱含數值轉換。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="6b5cd-104">從</span><span class="sxs-lookup"><span data-stu-id="6b5cd-104">From</span></span>|<span data-ttu-id="6b5cd-105">以</span><span class="sxs-lookup"><span data-stu-id="6b5cd-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="6b5cd-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="6b5cd-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="6b5cd-107">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-108">byte</span><span class="sxs-lookup"><span data-stu-id="6b5cd-108">byte</span></span>](byte.md)|<span data-ttu-id="6b5cd-109">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-110">char</span><span class="sxs-lookup"><span data-stu-id="6b5cd-110">char</span></span>](char.md)|<span data-ttu-id="6b5cd-111">`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-112">short</span><span class="sxs-lookup"><span data-stu-id="6b5cd-112">short</span></span>](short.md)|<span data-ttu-id="6b5cd-113">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-114">ushort</span><span class="sxs-lookup"><span data-stu-id="6b5cd-114">ushort</span></span>](ushort.md)|<span data-ttu-id="6b5cd-115">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-116">int</span><span class="sxs-lookup"><span data-stu-id="6b5cd-116">int</span></span>](int.md)|<span data-ttu-id="6b5cd-117">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-118">uint</span><span class="sxs-lookup"><span data-stu-id="6b5cd-118">uint</span></span>](uint.md)|<span data-ttu-id="6b5cd-119">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-120">long</span><span class="sxs-lookup"><span data-stu-id="6b5cd-120">long</span></span>](long.md)|<span data-ttu-id="6b5cd-121">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-122">ulong</span><span class="sxs-lookup"><span data-stu-id="6b5cd-122">ulong</span></span>](ulong.md)|<span data-ttu-id="6b5cd-123">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="6b5cd-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="6b5cd-124">float</span><span class="sxs-lookup"><span data-stu-id="6b5cd-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="6b5cd-125">備註</span><span class="sxs-lookup"><span data-stu-id="6b5cd-125">Remarks</span></span>  

- <span data-ttu-id="6b5cd-126">任何[整數型別](integral-types-table.md)都會隱含轉換為任何[浮點類型](floating-point-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="6b5cd-127">從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="6b5cd-128">`char`、`byte` 及 `sbyte` 類型沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-128">There are no implicit conversions to the `char`, `byte` and `sbyte` types.</span></span>  

- <span data-ttu-id="6b5cd-129">沒有來自 `char`、`double` 及 `decimal` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-129">There are no implicit conversions from the `char`, `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="6b5cd-130">`decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="6b5cd-131">類型 `int` 常數運算式的值 (例如整數常值所代表的值) 可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，前提是其在目的地類型的範圍內：</span><span class="sxs-lookup"><span data-stu-id="6b5cd-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="6b5cd-132">如需隱含轉換的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[隱含轉換](~/_csharplang/spec/conversions.md#implicit-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="6b5cd-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6b5cd-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b5cd-133">See also</span></span>

- [<span data-ttu-id="6b5cd-134">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6b5cd-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b5cd-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6b5cd-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6b5cd-136">整數型別表</span><span class="sxs-lookup"><span data-stu-id="6b5cd-136">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="6b5cd-137">浮點數類型表</span><span class="sxs-lookup"><span data-stu-id="6b5cd-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="6b5cd-138">內建型別表</span><span class="sxs-lookup"><span data-stu-id="6b5cd-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="6b5cd-139">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="6b5cd-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="6b5cd-140">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="6b5cd-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
