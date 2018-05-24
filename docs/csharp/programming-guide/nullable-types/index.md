---
title: 可為 Null 的類型 (C# 程式設計手冊)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: fcff492f420a60a41b373bf9042ed0c2d66d0446
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="acf86-102">可為 Null 的類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="acf86-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="acf86-103">可為 Null 的型別是 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="acf86-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="acf86-104">可為 Null 的型別可以代表其基礎值型別的正確值範圍，再加上額外的 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="acf86-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="acf86-105">例如，您可以將範圍從 -2147483648 到 2147483647 的任何值指派給 `Nullable<Int32>` (發音為「Nullable of Int32」)，或為它指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="acf86-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="acf86-106">您可以為 `Nullable<bool>` 指派下列值：[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 或 [null](../../../csharp/language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="acf86-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="acf86-107">當您正在處理包含可能不會指派值之元素的資料庫和其他資料型別時，將 `null` 指派為數字或布林值型別的功能特別有用。</span><span class="sxs-lookup"><span data-stu-id="acf86-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="acf86-108">例如，資料庫中的布林值欄位可以儲存 `true` 或 `false` 的值，而它也可能是未定義的。</span><span class="sxs-lookup"><span data-stu-id="acf86-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
<span data-ttu-id="acf86-109">如需詳細資訊，請參閱[使用可為 Null 的型別](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span><span class="sxs-lookup"><span data-stu-id="acf86-109">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="acf86-110">可為 Null 的型別概觀</span><span class="sxs-lookup"><span data-stu-id="acf86-110">Nullable Types Overview</span></span>  
 <span data-ttu-id="acf86-111">可為 Null 的型別特色如下：</span><span class="sxs-lookup"><span data-stu-id="acf86-111">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="acf86-112">可為 Null 的型別代表可指派 `null` 值的實值型別變數。</span><span class="sxs-lookup"><span data-stu-id="acf86-112">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="acf86-113">您無法根據參考型別建立可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="acf86-113">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="acf86-114">(參考型別已經支援 `null` 值)。</span><span class="sxs-lookup"><span data-stu-id="acf86-114">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="acf86-115">語法 `T?` 是 <xref:System.Nullable%601> 的縮寫，其中 `T` 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="acf86-115">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="acf86-116">這兩種格式是可互換的。</span><span class="sxs-lookup"><span data-stu-id="acf86-116">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="acf86-117">將值指派給可為 Null 的型別，就像您針對一般實值型別所做的一樣，例如 `int? x = 10;` 或 `double? d = 4.108`。</span><span class="sxs-lookup"><span data-stu-id="acf86-117">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="acf86-118">您也可以為可為 Null 的型別指派值 `null`: `int? x = null.`</span><span class="sxs-lookup"><span data-stu-id="acf86-118">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="acf86-119">使用 <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> 方法來傳回指派的值，或者，如果值為 `null`，則傳回基礎類型的預設值，例如 `int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="acf86-119">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="acf86-120">使用 <xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 唯讀屬性，以測試是否有 Null 並擷取值，如下列範例所示：`if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="acf86-120">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="acf86-121">如果變數包含值，`HasValue` 屬性就會傳回 `true`，或者，如果它是 `null`，則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="acf86-121">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="acf86-122">如果指派了其中一個，則 `Value` 屬性會傳回值。</span><span class="sxs-lookup"><span data-stu-id="acf86-122">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="acf86-123">否則會擲回 <xref:System.InvalidOperationException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="acf86-123">Otherwise, a <xref:System.InvalidOperationException?displayProperty=nameWithType> is thrown.</span></span>  
  
    -   <span data-ttu-id="acf86-124">`HasValue` 的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="acf86-124">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="acf86-125">`Value` 屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="acf86-125">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="acf86-126">您也可以使用 `==` 和 `!=` 運算子搭配可為 Null 的型別，如下列範例所示︰`if (x != null) y = x;`</span><span class="sxs-lookup"><span data-stu-id="acf86-126">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="acf86-127">使用 `??` 運算子來指派預設值，在將目前值為 `null` 之可為 Null 的型別指派給非可為 Null 的型別時，將會套用此預設值，例如 `int? x = null; int y = x ?? -1;`</span><span class="sxs-lookup"><span data-stu-id="acf86-127">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="acf86-128">不允許巢狀可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="acf86-128">Nested nullable types are not allowed.</span></span> <span data-ttu-id="acf86-129">系統將不會編譯下列這一行：`Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="acf86-129">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="acf86-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="acf86-130">Related Sections</span></span>  
 <span data-ttu-id="acf86-131">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="acf86-131">For more information:</span></span>  
  
-   [<span data-ttu-id="acf86-132">使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="acf86-132">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="acf86-133">對可為 Null 的型別進行 boxing</span><span class="sxs-lookup"><span data-stu-id="acf86-133">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="acf86-134">??運算子</span><span class="sxs-lookup"><span data-stu-id="acf86-134">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="acf86-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="acf86-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="acf86-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="acf86-136">See Also</span></span>  
 <xref:System.Nullable>  
 [<span data-ttu-id="acf86-137">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="acf86-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="acf86-138">C#</span><span class="sxs-lookup"><span data-stu-id="acf86-138">C#</span></span>](../../../csharp/index.md)  
 [<span data-ttu-id="acf86-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="acf86-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="acf86-140">「增益」(Lift) 的真正意義是什麼？(英文)</span><span class="sxs-lookup"><span data-stu-id="acf86-140">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
