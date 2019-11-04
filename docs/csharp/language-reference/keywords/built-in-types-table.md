---
title: 內建類型資料表 - C# 參考
ms.custom: seodec18
description: 內建 C# 類型的關鍵字
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 22bdfa197e3ce9c119203c74eeb0eb8217022a68
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422912"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="78510-103">內建類型資料表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="78510-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="78510-104">下表顯示內C#建類型的關鍵字，這些是 <xref:System> 命名空間中預先定義類型的別名：</span><span class="sxs-lookup"><span data-stu-id="78510-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace:</span></span>

|<span data-ttu-id="78510-105">C# 類型</span><span class="sxs-lookup"><span data-stu-id="78510-105">C# type</span></span>|<span data-ttu-id="78510-106">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="78510-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="78510-107">bool</span><span class="sxs-lookup"><span data-stu-id="78510-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-108">byte</span><span class="sxs-lookup"><span data-stu-id="78510-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="78510-109">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-110">char</span><span class="sxs-lookup"><span data-stu-id="78510-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-111">decimal</span><span class="sxs-lookup"><span data-stu-id="78510-111">decimal</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-112">double</span><span class="sxs-lookup"><span data-stu-id="78510-112">double</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-113">float</span><span class="sxs-lookup"><span data-stu-id="78510-113">float</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-114">int</span><span class="sxs-lookup"><span data-stu-id="78510-114">int</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-115">uint</span><span class="sxs-lookup"><span data-stu-id="78510-115">uint</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-116">long</span><span class="sxs-lookup"><span data-stu-id="78510-116">long</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-117">ulong</span><span class="sxs-lookup"><span data-stu-id="78510-117">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-118">object</span><span class="sxs-lookup"><span data-stu-id="78510-118">object</span></span>](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-119">short</span><span class="sxs-lookup"><span data-stu-id="78510-119">short</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-120">ushort</span><span class="sxs-lookup"><span data-stu-id="78510-120">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="78510-121">string</span><span class="sxs-lookup"><span data-stu-id="78510-121">string</span></span>](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="78510-122">備註</span><span class="sxs-lookup"><span data-stu-id="78510-122">Remarks</span></span>

<span data-ttu-id="78510-123">表中除了 `object` 和 `string` 以外的所有型別，都視為簡單型別。</span><span class="sxs-lookup"><span data-stu-id="78510-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>

<span data-ttu-id="78510-124">.NET 型別與其 C# 型別關鍵字別名是可互換的。</span><span class="sxs-lookup"><span data-stu-id="78510-124">The .NET types and their C# type keyword aliases are interchangeable.</span></span> <span data-ttu-id="78510-125">例如，您可以使用下列任一個宣告來宣告整數變數：</span><span class="sxs-lookup"><span data-stu-id="78510-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="78510-126">使用 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 運算子，取得表示指定類型的 <xref:System.Type?displayProperty=nameWithType> 執行個體：</span><span class="sxs-lookup"><span data-stu-id="78510-126">Use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="78510-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="78510-127">See also</span></span>

- [<span data-ttu-id="78510-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="78510-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78510-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="78510-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78510-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="78510-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="78510-131">實值型別</span><span class="sxs-lookup"><span data-stu-id="78510-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="78510-132">參考型別</span><span class="sxs-lookup"><span data-stu-id="78510-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="78510-133">預設值表</span><span class="sxs-lookup"><span data-stu-id="78510-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="78510-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="78510-134">dynamic</span></span>](../builtin-types/reference-types.md)
