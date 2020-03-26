---
title: C# 類型的預設值 - C# 引用
description: 瞭解 C# 類型的預設值，如布林、字元、int、浮點、雙精度值等。
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507252"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="0576f-103">C# 類型的預設值（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="0576f-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="0576f-104">下列表格顯示 C# 型別的預設值：</span><span class="sxs-lookup"><span data-stu-id="0576f-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="0576f-105">類型</span><span class="sxs-lookup"><span data-stu-id="0576f-105">Type</span></span>|<span data-ttu-id="0576f-106">預設值</span><span class="sxs-lookup"><span data-stu-id="0576f-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="0576f-107">任何參考類型</span><span class="sxs-lookup"><span data-stu-id="0576f-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="0576f-108">任何[內建整數數值型別](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="0576f-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="0576f-109">0 (零)</span><span class="sxs-lookup"><span data-stu-id="0576f-109">0 (zero)</span></span>|
|<span data-ttu-id="0576f-110">任何[內建浮點數值型別](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="0576f-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="0576f-111">0 (零)</span><span class="sxs-lookup"><span data-stu-id="0576f-111">0 (zero)</span></span>|
|[<span data-ttu-id="0576f-112">Bool</span><span class="sxs-lookup"><span data-stu-id="0576f-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="0576f-113">字元</span><span class="sxs-lookup"><span data-stu-id="0576f-113">char</span></span>](char.md)|<span data-ttu-id="0576f-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="0576f-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="0576f-115">枚舉</span><span class="sxs-lookup"><span data-stu-id="0576f-115">enum</span></span>](enum.md)|<span data-ttu-id="0576f-116">這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。</span><span class="sxs-lookup"><span data-stu-id="0576f-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="0576f-117">struct</span><span class="sxs-lookup"><span data-stu-id="0576f-117">struct</span></span>](struct.md)|<span data-ttu-id="0576f-118">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="0576f-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="0576f-119">任何[可為 Null 的值型別](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="0576f-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="0576f-120"><xref:System.Nullable%601.HasValue%2A> 屬性是 `false` 且未定義 <xref:System.Nullable%601.Value%2A> 屬性的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0576f-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="0576f-121">該預設值也稱為空數值型別的*空*值。</span><span class="sxs-lookup"><span data-stu-id="0576f-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="0576f-122">使用[`default`運算子](../operators/default.md#default-operator)組建類型的預設值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="0576f-122">Use the [`default` operator](../operators/default.md#default-operator) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="0576f-123">從 C# 7.1 開始，可以使用[`default`文本](../operators/default.md#default-literal)初始化具有其類型的預設值的變數：</span><span class="sxs-lookup"><span data-stu-id="0576f-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="0576f-124">針對值型別，隱含無參數建構函式也會產生型別的預設值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0576f-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="0576f-125">在運行時，如果<xref:System.Type?displayProperty=nameWithType>實例表示數值型別，則可以使用<xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType>方法調用無參數建構函式以獲取類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="0576f-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0576f-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0576f-126">C# language specification</span></span>

<span data-ttu-id="0576f-127">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="0576f-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0576f-128">預設值</span><span class="sxs-lookup"><span data-stu-id="0576f-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="0576f-129">預設建構函式</span><span class="sxs-lookup"><span data-stu-id="0576f-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="0576f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0576f-130">See also</span></span>

- [<span data-ttu-id="0576f-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0576f-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0576f-132">建構函式</span><span class="sxs-lookup"><span data-stu-id="0576f-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
