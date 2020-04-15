---
title: 內建型態 - C# 參考
description: 瞭解 C# 內建值和參考類型
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bf8823c6674b1ff3f0028a50df8ce8d0f803cfc1
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389486"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="7df75-103">內建型態 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7df75-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="7df75-104">下表列出 C# 內建[值](value-types.md)類型:</span><span class="sxs-lookup"><span data-stu-id="7df75-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="7df75-105">C# 類型關鍵字</span><span class="sxs-lookup"><span data-stu-id="7df75-105">C# type keyword</span></span>|<span data-ttu-id="7df75-106">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="7df75-106">.NET type</span></span>|
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

<span data-ttu-id="7df75-107">下表列出 C# 內置[參考](../keywords/reference-types.md)型態:</span><span class="sxs-lookup"><span data-stu-id="7df75-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="7df75-108">C# 類型關鍵字</span><span class="sxs-lookup"><span data-stu-id="7df75-108">C# type keyword</span></span>|<span data-ttu-id="7df75-109">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="7df75-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="7df75-110">在前面表中,左列中的每個 C# 類型關鍵字是相應 .NET 類型的別名。</span><span class="sxs-lookup"><span data-stu-id="7df75-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="7df75-111">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="7df75-111">They are interchangeable.</span></span> <span data-ttu-id="7df75-112">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="7df75-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="7df75-113">關鍵字[`void`](void.md)表示缺少類型。</span><span class="sxs-lookup"><span data-stu-id="7df75-113">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="7df75-114">使用它作為不返回值的方法的返回類型。</span><span class="sxs-lookup"><span data-stu-id="7df75-114">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="7df75-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df75-115">See also</span></span>

- [<span data-ttu-id="7df75-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7df75-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7df75-117">C# 類型的預設值</span><span class="sxs-lookup"><span data-stu-id="7df75-117">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="7df75-118">`dynamic`關鍵字</span><span class="sxs-lookup"><span data-stu-id="7df75-118">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
