---
title: 預設值表 (C# 參考)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
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
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="e885e-102">預設值表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e885e-102">Default values table (C# Reference)</span></span>

<span data-ttu-id="e885e-103">下表顯示預設建構函式所傳回之實值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="e885e-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="e885e-104">預設建構函式是透過 `new` 運算子來叫用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e885e-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="e885e-105">上面的陳述式與下面的陳述式效果相同：</span><span class="sxs-lookup"><span data-stu-id="e885e-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="e885e-106">請記住，C# 中不允許使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="e885e-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="e885e-107">值類型</span><span class="sxs-lookup"><span data-stu-id="e885e-107">Value type</span></span>|<span data-ttu-id="e885e-108">預設值</span><span class="sxs-lookup"><span data-stu-id="e885e-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="e885e-109">bool</span><span class="sxs-lookup"><span data-stu-id="e885e-109">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="e885e-110">byte</span><span class="sxs-lookup"><span data-stu-id="e885e-110">byte</span></span>](byte.md)|<span data-ttu-id="e885e-111">0</span><span class="sxs-lookup"><span data-stu-id="e885e-111">0</span></span>|
|[<span data-ttu-id="e885e-112">char</span><span class="sxs-lookup"><span data-stu-id="e885e-112">char</span></span>](char.md)|<span data-ttu-id="e885e-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="e885e-113">'\0'</span></span>|
|[<span data-ttu-id="e885e-114">decimal</span><span class="sxs-lookup"><span data-stu-id="e885e-114">decimal</span></span>](decimal.md)|<span data-ttu-id="e885e-115">0M</span><span class="sxs-lookup"><span data-stu-id="e885e-115">0M</span></span>|
|[<span data-ttu-id="e885e-116">double</span><span class="sxs-lookup"><span data-stu-id="e885e-116">double</span></span>](double.md)|<span data-ttu-id="e885e-117">0.0D</span><span class="sxs-lookup"><span data-stu-id="e885e-117">0.0D</span></span>|
|[<span data-ttu-id="e885e-118">enum</span><span class="sxs-lookup"><span data-stu-id="e885e-118">enum</span></span>](enum.md)|<span data-ttu-id="e885e-119">這個值是由運算式 (E)0 所產生，其中 E 是列舉識別項。</span><span class="sxs-lookup"><span data-stu-id="e885e-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="e885e-120">float</span><span class="sxs-lookup"><span data-stu-id="e885e-120">float</span></span>](float.md)|<span data-ttu-id="e885e-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="e885e-121">0.0F</span></span>|
|[<span data-ttu-id="e885e-122">int</span><span class="sxs-lookup"><span data-stu-id="e885e-122">int</span></span>](int.md)|<span data-ttu-id="e885e-123">0</span><span class="sxs-lookup"><span data-stu-id="e885e-123">0</span></span>|
|[<span data-ttu-id="e885e-124">long</span><span class="sxs-lookup"><span data-stu-id="e885e-124">long</span></span>](long.md)|<span data-ttu-id="e885e-125">0L</span><span class="sxs-lookup"><span data-stu-id="e885e-125">0L</span></span>|
|[<span data-ttu-id="e885e-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="e885e-126">sbyte</span></span>](sbyte.md)|<span data-ttu-id="e885e-127">0</span><span class="sxs-lookup"><span data-stu-id="e885e-127">0</span></span>|
|[<span data-ttu-id="e885e-128">short</span><span class="sxs-lookup"><span data-stu-id="e885e-128">short</span></span>](short.md)|<span data-ttu-id="e885e-129">0</span><span class="sxs-lookup"><span data-stu-id="e885e-129">0</span></span>|
|[<span data-ttu-id="e885e-130">struct</span><span class="sxs-lookup"><span data-stu-id="e885e-130">struct</span></span>](struct.md)|<span data-ttu-id="e885e-131">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="e885e-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="e885e-132">uint</span><span class="sxs-lookup"><span data-stu-id="e885e-132">uint</span></span>](uint.md)|<span data-ttu-id="e885e-133">0</span><span class="sxs-lookup"><span data-stu-id="e885e-133">0</span></span>|
|[<span data-ttu-id="e885e-134">ulong</span><span class="sxs-lookup"><span data-stu-id="e885e-134">ulong</span></span>](ulong.md)|<span data-ttu-id="e885e-135">0</span><span class="sxs-lookup"><span data-stu-id="e885e-135">0</span></span>|
|[<span data-ttu-id="e885e-136">ushort</span><span class="sxs-lookup"><span data-stu-id="e885e-136">ushort</span></span>](ushort.md)|<span data-ttu-id="e885e-137">0</span><span class="sxs-lookup"><span data-stu-id="e885e-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="e885e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e885e-138">See also</span></span>
 [<span data-ttu-id="e885e-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e885e-139">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="e885e-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e885e-140">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="e885e-141">實值型別表</span><span class="sxs-lookup"><span data-stu-id="e885e-141">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="e885e-142">實值型別</span><span class="sxs-lookup"><span data-stu-id="e885e-142">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="e885e-143">內建型別表</span><span class="sxs-lookup"><span data-stu-id="e885e-143">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="e885e-144">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="e885e-144">Reference Tables for Types</span></span>](reference-tables-for-types.md)
