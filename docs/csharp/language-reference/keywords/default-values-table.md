---
title: "預設值表 (C# 參考)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f692ee1242af88dc6bd3938f7a00f3d11ed8ca7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="a9061-102">預設值表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a9061-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="a9061-103">下表顯示預設建構函式所傳回之實值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="a9061-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="a9061-104">預設建構函式是透過 `new` 運算子來叫用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9061-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="a9061-105">上面的陳述式與下面的陳述式效果相同：</span><span class="sxs-lookup"><span data-stu-id="a9061-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="a9061-106">請記住，C# 中不允許使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="a9061-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="a9061-107">值類型</span><span class="sxs-lookup"><span data-stu-id="a9061-107">Value type</span></span>|<span data-ttu-id="a9061-108">預設值</span><span class="sxs-lookup"><span data-stu-id="a9061-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="a9061-109">bool</span><span class="sxs-lookup"><span data-stu-id="a9061-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="a9061-110">byte</span><span class="sxs-lookup"><span data-stu-id="a9061-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="a9061-111">0</span><span class="sxs-lookup"><span data-stu-id="a9061-111">0</span></span>|
|[<span data-ttu-id="a9061-112">char</span><span class="sxs-lookup"><span data-stu-id="a9061-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="a9061-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="a9061-113">'\0'</span></span>|
|[<span data-ttu-id="a9061-114">decimal</span><span class="sxs-lookup"><span data-stu-id="a9061-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="a9061-115">0.0M</span><span class="sxs-lookup"><span data-stu-id="a9061-115">0.0M</span></span>|
|[<span data-ttu-id="a9061-116">double</span><span class="sxs-lookup"><span data-stu-id="a9061-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="a9061-117">0.0D</span><span class="sxs-lookup"><span data-stu-id="a9061-117">0.0D</span></span>|
|[<span data-ttu-id="a9061-118">enum</span><span class="sxs-lookup"><span data-stu-id="a9061-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="a9061-119">這個值是由運算式 (E)0 所產生，其中 E 是列舉識別項。</span><span class="sxs-lookup"><span data-stu-id="a9061-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="a9061-120">float</span><span class="sxs-lookup"><span data-stu-id="a9061-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="a9061-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="a9061-121">0.0F</span></span>|
|[<span data-ttu-id="a9061-122">int</span><span class="sxs-lookup"><span data-stu-id="a9061-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="a9061-123">0</span><span class="sxs-lookup"><span data-stu-id="a9061-123">0</span></span>|
|[<span data-ttu-id="a9061-124">long</span><span class="sxs-lookup"><span data-stu-id="a9061-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="a9061-125">0L</span><span class="sxs-lookup"><span data-stu-id="a9061-125">0L</span></span>|
|[<span data-ttu-id="a9061-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="a9061-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="a9061-127">0</span><span class="sxs-lookup"><span data-stu-id="a9061-127">0</span></span>|
|[<span data-ttu-id="a9061-128">short</span><span class="sxs-lookup"><span data-stu-id="a9061-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="a9061-129">0</span><span class="sxs-lookup"><span data-stu-id="a9061-129">0</span></span>|
|[<span data-ttu-id="a9061-130">struct</span><span class="sxs-lookup"><span data-stu-id="a9061-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="a9061-131">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="a9061-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="a9061-132">uint</span><span class="sxs-lookup"><span data-stu-id="a9061-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="a9061-133">0</span><span class="sxs-lookup"><span data-stu-id="a9061-133">0</span></span>|
|[<span data-ttu-id="a9061-134">ulong</span><span class="sxs-lookup"><span data-stu-id="a9061-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="a9061-135">0</span><span class="sxs-lookup"><span data-stu-id="a9061-135">0</span></span>|
|[<span data-ttu-id="a9061-136">ushort</span><span class="sxs-lookup"><span data-stu-id="a9061-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="a9061-137">0</span><span class="sxs-lookup"><span data-stu-id="a9061-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="a9061-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9061-138">See also</span></span>
 [<span data-ttu-id="a9061-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a9061-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a9061-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a9061-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a9061-141">實值型別表</span><span class="sxs-lookup"><span data-stu-id="a9061-141">Value Types Table</span></span>](../../../csharp/language-reference/keywords/value-types-table.md)  
 [<span data-ttu-id="a9061-142">實值型別</span><span class="sxs-lookup"><span data-stu-id="a9061-142">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="a9061-143">內建型別表</span><span class="sxs-lookup"><span data-stu-id="a9061-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="a9061-144">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="a9061-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
