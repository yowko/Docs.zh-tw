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
ms.openlocfilehash: 9c3efe1dbea355e8bc00ef44e08efcc9d0e0bdca
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424171"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="034c4-102">隱含數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="034c4-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="034c4-103">下表顯示 .NET 數字類型間預先定義的隱含數值轉換。</span><span class="sxs-lookup"><span data-stu-id="034c4-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="034c4-104">從</span><span class="sxs-lookup"><span data-stu-id="034c4-104">From</span></span>|<span data-ttu-id="034c4-105">以</span><span class="sxs-lookup"><span data-stu-id="034c4-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="034c4-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="034c4-106">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-107">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-108">byte</span><span class="sxs-lookup"><span data-stu-id="034c4-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-109">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-110">char</span><span class="sxs-lookup"><span data-stu-id="034c4-110">char</span></span>](char.md)|<span data-ttu-id="034c4-111">`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-112">short</span><span class="sxs-lookup"><span data-stu-id="034c4-112">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-113">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-114">ushort</span><span class="sxs-lookup"><span data-stu-id="034c4-114">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-115">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="034c4-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-116">int</span><span class="sxs-lookup"><span data-stu-id="034c4-116">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-117">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-118">uint</span><span class="sxs-lookup"><span data-stu-id="034c4-118">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-119">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-120">long</span><span class="sxs-lookup"><span data-stu-id="034c4-120">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-121">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-122">ulong</span><span class="sxs-lookup"><span data-stu-id="034c4-122">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="034c4-123">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="034c4-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="034c4-124">float</span><span class="sxs-lookup"><span data-stu-id="034c4-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="034c4-125">備註</span><span class="sxs-lookup"><span data-stu-id="034c4-125">Remarks</span></span>  

- <span data-ttu-id="034c4-126">任何[整數型別](../builtin-types/integral-numeric-types.md)都會隱含轉換為任何[浮點類型](floating-point-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="034c4-126">Any [integral type](../builtin-types/integral-numeric-types.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="034c4-127">從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="034c4-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="034c4-128">`char`、`byte` 與 `sbyte` 類型沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="034c4-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="034c4-129">沒有來自 `double` 與 `decimal` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="034c4-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="034c4-130">`decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="034c4-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="034c4-131">類型 `int` 常數運算式的值 (例如整數常值所代表的值) 可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，前提是其在目的地類型的範圍內：</span><span class="sxs-lookup"><span data-stu-id="034c4-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="034c4-132">如需隱含轉換的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[隱含轉換](~/_csharplang/spec/conversions.md#implicit-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="034c4-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="034c4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="034c4-133">See also</span></span>

- [<span data-ttu-id="034c4-134">C# 參考</span><span class="sxs-lookup"><span data-stu-id="034c4-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="034c4-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="034c4-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="034c4-136">整數型別</span><span class="sxs-lookup"><span data-stu-id="034c4-136">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="034c4-137">浮點數類型表</span><span class="sxs-lookup"><span data-stu-id="034c4-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="034c4-138">內建型別表</span><span class="sxs-lookup"><span data-stu-id="034c4-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="034c4-139">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="034c4-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="034c4-140">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="034c4-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
