---
title: 預設值表 - C# 參考
ms.custom: seodec18
description: 了解 C# 實值型別的預設值是什麼。
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: dfab5107d4a0ad14c3ffbfc6a5f3c4317b44d17c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424226"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="04a5f-103">預設值表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="04a5f-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="04a5f-104">下列表格顯示[實值型別](value-types.md)的預設值。</span><span class="sxs-lookup"><span data-stu-id="04a5f-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="04a5f-105">值類型</span><span class="sxs-lookup"><span data-stu-id="04a5f-105">Value type</span></span>|<span data-ttu-id="04a5f-106">預設值</span><span class="sxs-lookup"><span data-stu-id="04a5f-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="04a5f-107">bool</span><span class="sxs-lookup"><span data-stu-id="04a5f-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="04a5f-108">byte</span><span class="sxs-lookup"><span data-stu-id="04a5f-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-109">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-109">0</span></span>|
|[<span data-ttu-id="04a5f-110">char</span><span class="sxs-lookup"><span data-stu-id="04a5f-110">char</span></span>](char.md)|<span data-ttu-id="04a5f-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="04a5f-111">'\0'</span></span>|
|[<span data-ttu-id="04a5f-112">decimal</span><span class="sxs-lookup"><span data-stu-id="04a5f-112">decimal</span></span>](decimal.md)|<span data-ttu-id="04a5f-113">0M</span><span class="sxs-lookup"><span data-stu-id="04a5f-113">0M</span></span>|
|[<span data-ttu-id="04a5f-114">double</span><span class="sxs-lookup"><span data-stu-id="04a5f-114">double</span></span>](double.md)|<span data-ttu-id="04a5f-115">0.0D</span><span class="sxs-lookup"><span data-stu-id="04a5f-115">0.0D</span></span>|
|[<span data-ttu-id="04a5f-116">enum</span><span class="sxs-lookup"><span data-stu-id="04a5f-116">enum</span></span>](enum.md)|<span data-ttu-id="04a5f-117">這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。</span><span class="sxs-lookup"><span data-stu-id="04a5f-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="04a5f-118">float</span><span class="sxs-lookup"><span data-stu-id="04a5f-118">float</span></span>](float.md)|<span data-ttu-id="04a5f-119">0.0F</span><span class="sxs-lookup"><span data-stu-id="04a5f-119">0.0F</span></span>|
|[<span data-ttu-id="04a5f-120">int</span><span class="sxs-lookup"><span data-stu-id="04a5f-120">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-121">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-121">0</span></span>|
|[<span data-ttu-id="04a5f-122">long</span><span class="sxs-lookup"><span data-stu-id="04a5f-122">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-123">0L</span><span class="sxs-lookup"><span data-stu-id="04a5f-123">0L</span></span>|
|[<span data-ttu-id="04a5f-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="04a5f-124">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-125">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-125">0</span></span>|
|[<span data-ttu-id="04a5f-126">short</span><span class="sxs-lookup"><span data-stu-id="04a5f-126">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-127">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-127">0</span></span>|
|[<span data-ttu-id="04a5f-128">struct</span><span class="sxs-lookup"><span data-stu-id="04a5f-128">struct</span></span>](struct.md)|<span data-ttu-id="04a5f-129">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="04a5f-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="04a5f-130">uint</span><span class="sxs-lookup"><span data-stu-id="04a5f-130">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-131">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-131">0</span></span>|
|[<span data-ttu-id="04a5f-132">ulong</span><span class="sxs-lookup"><span data-stu-id="04a5f-132">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-133">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-133">0</span></span>|
|[<span data-ttu-id="04a5f-134">ushort</span><span class="sxs-lookup"><span data-stu-id="04a5f-134">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="04a5f-135">0</span><span class="sxs-lookup"><span data-stu-id="04a5f-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="04a5f-136">備註</span><span class="sxs-lookup"><span data-stu-id="04a5f-136">Remarks</span></span>

<span data-ttu-id="04a5f-137">您無法在 C# 中使用未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="04a5f-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="04a5f-138">您可以使用該型別的預設值初始化變數。</span><span class="sxs-lookup"><span data-stu-id="04a5f-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="04a5f-139">您也可以使用型別的預設值來指定方法中[選擇性引數](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments)的預設值。</span><span class="sxs-lookup"><span data-stu-id="04a5f-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="04a5f-140">使用[預設值運算式](../../programming-guide/statements-expressions-operators/default-value-expressions.md)以產生型別的預設值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="04a5f-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="04a5f-141">從 C# 7.1 開始，您可以使用 [`default` 常值](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference)　來以型別的預設值初始化變數：</span><span class="sxs-lookup"><span data-stu-id="04a5f-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="04a5f-142">您也可以使用無參數建構函式或隱含無參數建構函式來產生實值型別的預設值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="04a5f-142">You also can use the parameterless constructor or the implicit parameterless constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="04a5f-143">如需建構函式的詳細資訊，請參閱[建構函式](../../programming-guide/classes-and-structs/constructors.md)一文。</span><span class="sxs-lookup"><span data-stu-id="04a5f-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="04a5f-144">任何[參考型別](reference-types.md)的預設值皆為 `null`。</span><span class="sxs-lookup"><span data-stu-id="04a5f-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="04a5f-145">[可為 Null 的型別](../../programming-guide/nullable-types/index.md)的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性為 `false`，且其 <xref:System.Nullable%601.Value%2A> 屬性為未定義的執行個體。</span><span class="sxs-lookup"><span data-stu-id="04a5f-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="04a5f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04a5f-146">See also</span></span>

- [<span data-ttu-id="04a5f-147">C# 參考</span><span class="sxs-lookup"><span data-stu-id="04a5f-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="04a5f-148">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="04a5f-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="04a5f-149">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="04a5f-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="04a5f-150">實值型別</span><span class="sxs-lookup"><span data-stu-id="04a5f-150">Value types</span></span>](value-types.md)
- [<span data-ttu-id="04a5f-151">實值型別表</span><span class="sxs-lookup"><span data-stu-id="04a5f-151">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="04a5f-152">內建型別表</span><span class="sxs-lookup"><span data-stu-id="04a5f-152">Built-in types table</span></span>](built-in-types-table.md)
