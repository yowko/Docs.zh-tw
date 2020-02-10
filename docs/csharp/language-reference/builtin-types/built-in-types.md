---
title: 內建類型- C#參考
description: 瞭解C#內建的值和參考型別
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 4f748373350ed0596a5f1d595c273243ae3227c3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095306"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="411e6-103">內建類型（C#參考）</span><span class="sxs-lookup"><span data-stu-id="411e6-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="411e6-104">下表列出內C#建的實[值](value-types.md)類型：</span><span class="sxs-lookup"><span data-stu-id="411e6-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="411e6-105">C#type 關鍵字</span><span class="sxs-lookup"><span data-stu-id="411e6-105">C# type keyword</span></span>|<span data-ttu-id="411e6-106">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="411e6-106">.NET type</span></span>|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="411e6-107">下表列出內建C#的[引用](../keywords/reference-types.md)類型：</span><span class="sxs-lookup"><span data-stu-id="411e6-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="411e6-108">C#type 關鍵字</span><span class="sxs-lookup"><span data-stu-id="411e6-108">C# type keyword</span></span>|<span data-ttu-id="411e6-109">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="411e6-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="411e6-110">在上表中，左欄C#中的每個類型關鍵字都是對應 .net 類型的別名。</span><span class="sxs-lookup"><span data-stu-id="411e6-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="411e6-111">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="411e6-111">They are interchangeable.</span></span> <span data-ttu-id="411e6-112">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="411e6-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

## <a name="see-also"></a><span data-ttu-id="411e6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="411e6-113">See also</span></span>

- [<span data-ttu-id="411e6-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="411e6-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="411e6-115">類型的C#預設值</span><span class="sxs-lookup"><span data-stu-id="411e6-115">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="411e6-116">`dynamic` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="411e6-116">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
