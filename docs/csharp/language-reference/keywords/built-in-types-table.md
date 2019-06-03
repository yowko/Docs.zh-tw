---
title: 內建類型資料表 - C# 參考
ms.custom: seodec18
description: 內建 C# 類型的關鍵字
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bd8c52cd798496a4df3086411dfe3be6241fbff5
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422341"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="b8060-103">內建類型資料表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b8060-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="b8060-104">下表顯示內建 C# 型別的關鍵字，這些是 <xref:System> 命名空間中預先定義型別的別名。</span><span class="sxs-lookup"><span data-stu-id="b8060-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="b8060-105">C# 類型</span><span class="sxs-lookup"><span data-stu-id="b8060-105">C# type</span></span>|<span data-ttu-id="b8060-106">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="b8060-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="b8060-107">bool</span><span class="sxs-lookup"><span data-stu-id="b8060-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-108">byte</span><span class="sxs-lookup"><span data-stu-id="b8060-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="b8060-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-110">char</span><span class="sxs-lookup"><span data-stu-id="b8060-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-111">decimal</span><span class="sxs-lookup"><span data-stu-id="b8060-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-112">double</span><span class="sxs-lookup"><span data-stu-id="b8060-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-113">float</span><span class="sxs-lookup"><span data-stu-id="b8060-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-114">int</span><span class="sxs-lookup"><span data-stu-id="b8060-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-115">uint</span><span class="sxs-lookup"><span data-stu-id="b8060-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-116">long</span><span class="sxs-lookup"><span data-stu-id="b8060-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-117">ulong</span><span class="sxs-lookup"><span data-stu-id="b8060-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-118">object</span><span class="sxs-lookup"><span data-stu-id="b8060-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-119">short</span><span class="sxs-lookup"><span data-stu-id="b8060-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-120">ushort</span><span class="sxs-lookup"><span data-stu-id="b8060-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="b8060-121">string</span><span class="sxs-lookup"><span data-stu-id="b8060-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="b8060-122">備註</span><span class="sxs-lookup"><span data-stu-id="b8060-122">Remarks</span></span>

<span data-ttu-id="b8060-123">表中除了 `object` 和 `string` 以外的所有型別，都視為簡單型別。</span><span class="sxs-lookup"><span data-stu-id="b8060-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="b8060-124">C# 型別關鍵字和它們的別名都可互換。</span><span class="sxs-lookup"><span data-stu-id="b8060-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="b8060-125">例如，您可以使用下列任一個宣告來宣告整數變數：</span><span class="sxs-lookup"><span data-stu-id="b8060-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="b8060-126">使用 [typeof](typeof.md) 運算子，取得表示指定類型的 <xref:System.Type?displayProperty=nameWithType> 執行個體：</span><span class="sxs-lookup"><span data-stu-id="b8060-126">Use the [typeof](typeof.md) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="b8060-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8060-127">See also</span></span>

- [<span data-ttu-id="b8060-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b8060-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="b8060-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b8060-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b8060-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b8060-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b8060-131">實值型別</span><span class="sxs-lookup"><span data-stu-id="b8060-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="b8060-132">參考型別</span><span class="sxs-lookup"><span data-stu-id="b8060-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="b8060-133">預設值表</span><span class="sxs-lookup"><span data-stu-id="b8060-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="b8060-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="b8060-134">dynamic</span></span>](dynamic.md)
