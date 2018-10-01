---
title: 內建類型資料表 (C# 參考)
description: 內建 C# 類型的關鍵字
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fd9ba878d77bdb219542db55bb38023c60c7bec4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507308"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="1a6cd-103">內建類型資料表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1a6cd-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="1a6cd-104">下表顯示內建 C# 型別的關鍵字，這些是 <xref:System> 命名空間中預先定義型別的別名。</span><span class="sxs-lookup"><span data-stu-id="1a6cd-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="1a6cd-105">C# 類型</span><span class="sxs-lookup"><span data-stu-id="1a6cd-105">C# type</span></span>|<span data-ttu-id="1a6cd-106">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="1a6cd-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="1a6cd-107">bool</span><span class="sxs-lookup"><span data-stu-id="1a6cd-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-108">byte</span><span class="sxs-lookup"><span data-stu-id="1a6cd-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="1a6cd-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-110">char</span><span class="sxs-lookup"><span data-stu-id="1a6cd-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-111">decimal</span><span class="sxs-lookup"><span data-stu-id="1a6cd-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-112">double</span><span class="sxs-lookup"><span data-stu-id="1a6cd-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-113">float</span><span class="sxs-lookup"><span data-stu-id="1a6cd-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-114">int</span><span class="sxs-lookup"><span data-stu-id="1a6cd-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-115">uint</span><span class="sxs-lookup"><span data-stu-id="1a6cd-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-116">long</span><span class="sxs-lookup"><span data-stu-id="1a6cd-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-117">ulong</span><span class="sxs-lookup"><span data-stu-id="1a6cd-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-118">object</span><span class="sxs-lookup"><span data-stu-id="1a6cd-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-119">short</span><span class="sxs-lookup"><span data-stu-id="1a6cd-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-120">ushort</span><span class="sxs-lookup"><span data-stu-id="1a6cd-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="1a6cd-121">string</span><span class="sxs-lookup"><span data-stu-id="1a6cd-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="1a6cd-122">備註</span><span class="sxs-lookup"><span data-stu-id="1a6cd-122">Remarks</span></span>

<span data-ttu-id="1a6cd-123">表中除了 `object` 和 `string` 以外的所有型別，都視為簡單型別。</span><span class="sxs-lookup"><span data-stu-id="1a6cd-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="1a6cd-124">C# 型別關鍵字和它們的別名都可互換。</span><span class="sxs-lookup"><span data-stu-id="1a6cd-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="1a6cd-125">例如，您可以使用下列任一個宣告來宣告整數變數：</span><span class="sxs-lookup"><span data-stu-id="1a6cd-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="1a6cd-126">使用 [typeof](typeof.md) 運算子，取得表示指定類型的 <xref:System.Type?displayProperty=nameWithType> 執行個體：</span><span class="sxs-lookup"><span data-stu-id="1a6cd-126">Use the [typeof](typeof.md) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="1a6cd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a6cd-127">See also</span></span>

- [<span data-ttu-id="1a6cd-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1a6cd-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="1a6cd-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1a6cd-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1a6cd-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1a6cd-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1a6cd-131">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="1a6cd-131">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="1a6cd-132">實值型別</span><span class="sxs-lookup"><span data-stu-id="1a6cd-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="1a6cd-133">參考型別</span><span class="sxs-lookup"><span data-stu-id="1a6cd-133">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="1a6cd-134">預設值表</span><span class="sxs-lookup"><span data-stu-id="1a6cd-134">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="1a6cd-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="1a6cd-135">dynamic</span></span>](dynamic.md)
