---
title: 預設值表 (C# 參考)
description: 了解 C# 實值型別的預設值是什麼。
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 184a9f42ddd3654a81aef0b7ce35e404de2d4bb9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43737979"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="5efb2-103">預設值表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5efb2-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="5efb2-104">下列表格顯示[實值型別](value-types.md)的預設值。</span><span class="sxs-lookup"><span data-stu-id="5efb2-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="5efb2-105">值類型</span><span class="sxs-lookup"><span data-stu-id="5efb2-105">Value type</span></span>|<span data-ttu-id="5efb2-106">預設值</span><span class="sxs-lookup"><span data-stu-id="5efb2-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="5efb2-107">bool</span><span class="sxs-lookup"><span data-stu-id="5efb2-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="5efb2-108">byte</span><span class="sxs-lookup"><span data-stu-id="5efb2-108">byte</span></span>](byte.md)|<span data-ttu-id="5efb2-109">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-109">0</span></span>|
|[<span data-ttu-id="5efb2-110">char</span><span class="sxs-lookup"><span data-stu-id="5efb2-110">char</span></span>](char.md)|<span data-ttu-id="5efb2-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="5efb2-111">'\0'</span></span>|
|[<span data-ttu-id="5efb2-112">decimal</span><span class="sxs-lookup"><span data-stu-id="5efb2-112">decimal</span></span>](decimal.md)|<span data-ttu-id="5efb2-113">0M</span><span class="sxs-lookup"><span data-stu-id="5efb2-113">0M</span></span>|
|[<span data-ttu-id="5efb2-114">double</span><span class="sxs-lookup"><span data-stu-id="5efb2-114">double</span></span>](double.md)|<span data-ttu-id="5efb2-115">0.0D</span><span class="sxs-lookup"><span data-stu-id="5efb2-115">0.0D</span></span>|
|[<span data-ttu-id="5efb2-116">enum</span><span class="sxs-lookup"><span data-stu-id="5efb2-116">enum</span></span>](enum.md)|<span data-ttu-id="5efb2-117">這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。</span><span class="sxs-lookup"><span data-stu-id="5efb2-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="5efb2-118">float</span><span class="sxs-lookup"><span data-stu-id="5efb2-118">float</span></span>](float.md)|<span data-ttu-id="5efb2-119">0.0F</span><span class="sxs-lookup"><span data-stu-id="5efb2-119">0.0F</span></span>|
|[<span data-ttu-id="5efb2-120">int</span><span class="sxs-lookup"><span data-stu-id="5efb2-120">int</span></span>](int.md)|<span data-ttu-id="5efb2-121">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-121">0</span></span>|
|[<span data-ttu-id="5efb2-122">long</span><span class="sxs-lookup"><span data-stu-id="5efb2-122">long</span></span>](long.md)|<span data-ttu-id="5efb2-123">0L</span><span class="sxs-lookup"><span data-stu-id="5efb2-123">0L</span></span>|
|[<span data-ttu-id="5efb2-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="5efb2-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="5efb2-125">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-125">0</span></span>|
|[<span data-ttu-id="5efb2-126">short</span><span class="sxs-lookup"><span data-stu-id="5efb2-126">short</span></span>](short.md)|<span data-ttu-id="5efb2-127">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-127">0</span></span>|
|[<span data-ttu-id="5efb2-128">struct</span><span class="sxs-lookup"><span data-stu-id="5efb2-128">struct</span></span>](struct.md)|<span data-ttu-id="5efb2-129">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="5efb2-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="5efb2-130">uint</span><span class="sxs-lookup"><span data-stu-id="5efb2-130">uint</span></span>](uint.md)|<span data-ttu-id="5efb2-131">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-131">0</span></span>|
|[<span data-ttu-id="5efb2-132">ulong</span><span class="sxs-lookup"><span data-stu-id="5efb2-132">ulong</span></span>](ulong.md)|<span data-ttu-id="5efb2-133">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-133">0</span></span>|
|[<span data-ttu-id="5efb2-134">ushort</span><span class="sxs-lookup"><span data-stu-id="5efb2-134">ushort</span></span>](ushort.md)|<span data-ttu-id="5efb2-135">0</span><span class="sxs-lookup"><span data-stu-id="5efb2-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="5efb2-136">備註</span><span class="sxs-lookup"><span data-stu-id="5efb2-136">Remarks</span></span>

<span data-ttu-id="5efb2-137">您無法在 C# 中使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="5efb2-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="5efb2-138">您可以使用該型別的預設值初始化變數。</span><span class="sxs-lookup"><span data-stu-id="5efb2-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="5efb2-139">您也可以使用型別的預設值來指定方法中[選擇性引數](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments)的預設值。</span><span class="sxs-lookup"><span data-stu-id="5efb2-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="5efb2-140">使用[預設值運算式](../../programming-guide/statements-expressions-operators/default-value-expressions.md)以產生型別的預設值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5efb2-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="5efb2-141">從 C# 7.1 開始，您可以使用 [`default` 常值](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference)　來以型別的預設值初始化變數：</span><span class="sxs-lookup"><span data-stu-id="5efb2-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="5efb2-142">您也可以使用預設建構函式或隱含預設建構函式產生實值型別的預設值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5efb2-142">You also can use the default constructor or the implicit default constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="5efb2-143">如需建構函式的詳細資訊，請參閱[建構函式](../../programming-guide/classes-and-structs/constructors.md)一文。</span><span class="sxs-lookup"><span data-stu-id="5efb2-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="5efb2-144">任何[參考型別](reference-types.md)的預設值皆為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5efb2-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="5efb2-145">[可為 Null 的型別](../../programming-guide/nullable-types/index.md)的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性為 `false`，且其 <xref:System.Nullable%601.Value%2A> 屬性為未定義的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5efb2-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="5efb2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5efb2-146">See also</span></span>

- [<span data-ttu-id="5efb2-147">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5efb2-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5efb2-148">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5efb2-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5efb2-149">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5efb2-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5efb2-150">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="5efb2-150">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="5efb2-151">實值型別</span><span class="sxs-lookup"><span data-stu-id="5efb2-151">Value types</span></span>](value-types.md)
- [<span data-ttu-id="5efb2-152">實值型別表</span><span class="sxs-lookup"><span data-stu-id="5efb2-152">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="5efb2-153">內建型別表</span><span class="sxs-lookup"><span data-stu-id="5efb2-153">Built-in types table</span></span>](built-in-types-table.md)
