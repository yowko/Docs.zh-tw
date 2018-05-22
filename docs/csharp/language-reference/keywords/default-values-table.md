---
title: 預設值表 (C# 參考)
description: 了解預設建構函式所傳回之實值型別的預設值。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="de4c8-103">預設值表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="de4c8-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="de4c8-104">下表顯示預設建構函式所傳回之實值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="de4c8-104">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="de4c8-105">預設建構函式是透過 `new` 運算子來叫用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="de4c8-105">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="de4c8-106">上面的陳述式與下面的陳述式效果相同：</span><span class="sxs-lookup"><span data-stu-id="de4c8-106">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="de4c8-107">請記住，C# 中不允許使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="de4c8-107">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="de4c8-108">值類型</span><span class="sxs-lookup"><span data-stu-id="de4c8-108">Value type</span></span>|<span data-ttu-id="de4c8-109">預設值</span><span class="sxs-lookup"><span data-stu-id="de4c8-109">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="de4c8-110">bool</span><span class="sxs-lookup"><span data-stu-id="de4c8-110">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="de4c8-111">byte</span><span class="sxs-lookup"><span data-stu-id="de4c8-111">byte</span></span>](byte.md)|<span data-ttu-id="de4c8-112">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-112">0</span></span>|
|[<span data-ttu-id="de4c8-113">char</span><span class="sxs-lookup"><span data-stu-id="de4c8-113">char</span></span>](char.md)|<span data-ttu-id="de4c8-114">'\0'</span><span class="sxs-lookup"><span data-stu-id="de4c8-114">'\0'</span></span>|
|[<span data-ttu-id="de4c8-115">decimal</span><span class="sxs-lookup"><span data-stu-id="de4c8-115">decimal</span></span>](decimal.md)|<span data-ttu-id="de4c8-116">0M</span><span class="sxs-lookup"><span data-stu-id="de4c8-116">0M</span></span>|
|[<span data-ttu-id="de4c8-117">double</span><span class="sxs-lookup"><span data-stu-id="de4c8-117">double</span></span>](double.md)|<span data-ttu-id="de4c8-118">0.0D</span><span class="sxs-lookup"><span data-stu-id="de4c8-118">0.0D</span></span>|
|[<span data-ttu-id="de4c8-119">enum</span><span class="sxs-lookup"><span data-stu-id="de4c8-119">enum</span></span>](enum.md)|<span data-ttu-id="de4c8-120">這個值是由運算式 (E)0 所產生，其中 E 是列舉識別項。</span><span class="sxs-lookup"><span data-stu-id="de4c8-120">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="de4c8-121">float</span><span class="sxs-lookup"><span data-stu-id="de4c8-121">float</span></span>](float.md)|<span data-ttu-id="de4c8-122">0.0F</span><span class="sxs-lookup"><span data-stu-id="de4c8-122">0.0F</span></span>|
|[<span data-ttu-id="de4c8-123">int</span><span class="sxs-lookup"><span data-stu-id="de4c8-123">int</span></span>](int.md)|<span data-ttu-id="de4c8-124">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-124">0</span></span>|
|[<span data-ttu-id="de4c8-125">long</span><span class="sxs-lookup"><span data-stu-id="de4c8-125">long</span></span>](long.md)|<span data-ttu-id="de4c8-126">0L</span><span class="sxs-lookup"><span data-stu-id="de4c8-126">0L</span></span>|
|[<span data-ttu-id="de4c8-127">sbyte</span><span class="sxs-lookup"><span data-stu-id="de4c8-127">sbyte</span></span>](sbyte.md)|<span data-ttu-id="de4c8-128">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-128">0</span></span>|
|[<span data-ttu-id="de4c8-129">short</span><span class="sxs-lookup"><span data-stu-id="de4c8-129">short</span></span>](short.md)|<span data-ttu-id="de4c8-130">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-130">0</span></span>|
|[<span data-ttu-id="de4c8-131">struct</span><span class="sxs-lookup"><span data-stu-id="de4c8-131">struct</span></span>](struct.md)|<span data-ttu-id="de4c8-132">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="de4c8-132">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="de4c8-133">uint</span><span class="sxs-lookup"><span data-stu-id="de4c8-133">uint</span></span>](uint.md)|<span data-ttu-id="de4c8-134">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-134">0</span></span>|
|[<span data-ttu-id="de4c8-135">ulong</span><span class="sxs-lookup"><span data-stu-id="de4c8-135">ulong</span></span>](ulong.md)|<span data-ttu-id="de4c8-136">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-136">0</span></span>|
|[<span data-ttu-id="de4c8-137">ushort</span><span class="sxs-lookup"><span data-stu-id="de4c8-137">ushort</span></span>](ushort.md)|<span data-ttu-id="de4c8-138">0</span><span class="sxs-lookup"><span data-stu-id="de4c8-138">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="de4c8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de4c8-139">See also</span></span>
 [<span data-ttu-id="de4c8-140">C# 參考</span><span class="sxs-lookup"><span data-stu-id="de4c8-140">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="de4c8-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="de4c8-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="de4c8-142">實值型別表</span><span class="sxs-lookup"><span data-stu-id="de4c8-142">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="de4c8-143">實值型別</span><span class="sxs-lookup"><span data-stu-id="de4c8-143">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="de4c8-144">內建型別表</span><span class="sxs-lookup"><span data-stu-id="de4c8-144">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="de4c8-145">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="de4c8-145">Reference Tables for Types</span></span>](reference-tables-for-types.md)
