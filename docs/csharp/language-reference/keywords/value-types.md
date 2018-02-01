---
title: "實值型別 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a><span data-ttu-id="8bd68-102">實值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8bd68-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="8bd68-103">實值型別包含兩種主要類別：</span><span class="sxs-lookup"><span data-stu-id="8bd68-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="8bd68-104">結構</span><span class="sxs-lookup"><span data-stu-id="8bd68-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="8bd68-105">列舉</span><span class="sxs-lookup"><span data-stu-id="8bd68-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="8bd68-106">結構分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="8bd68-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="8bd68-107">數值類型</span><span class="sxs-lookup"><span data-stu-id="8bd68-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="8bd68-108">整數型別</span><span class="sxs-lookup"><span data-stu-id="8bd68-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="8bd68-109">浮點類型</span><span class="sxs-lookup"><span data-stu-id="8bd68-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [<span data-ttu-id="8bd68-110">decimal</span><span class="sxs-lookup"><span data-stu-id="8bd68-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [<span data-ttu-id="8bd68-111">bool</span><span class="sxs-lookup"><span data-stu-id="8bd68-111">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="8bd68-112">使用者定義結構。</span><span class="sxs-lookup"><span data-stu-id="8bd68-112">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="8bd68-113">實值型別的主要功能</span><span class="sxs-lookup"><span data-stu-id="8bd68-113">Main Features of Value Types</span></span>  
 <span data-ttu-id="8bd68-114">根據實值型別的變數直接包含值。</span><span class="sxs-lookup"><span data-stu-id="8bd68-114">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="8bd68-115">將一個實值型別變數指派給另一個實值型別變數會複製包含的值。</span><span class="sxs-lookup"><span data-stu-id="8bd68-115">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="8bd68-116">這與指派參考型別變數不同，後者會複製物件的參考，而不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="8bd68-116">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="8bd68-117">所有實值型別都是隱含地衍生自 <xref:System.ValueType?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8bd68-117">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8bd68-118">與參考型別不同，您無法從實值型別衍生新的類型。</span><span class="sxs-lookup"><span data-stu-id="8bd68-118">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="8bd68-119">不過，就像參考型別，結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="8bd68-119">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="8bd68-120">與參考型別不同，實值型別不能包含 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="8bd68-120">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="8bd68-121">不過，[可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)功能允許將實值型別指派給 `null`。</span><span class="sxs-lookup"><span data-stu-id="8bd68-121">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="8bd68-122">每種實值型別都具有初始化該類型預設值的隱含預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bd68-122">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="8bd68-123">如需實值型別預設值的資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="8bd68-123">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="8bd68-124">簡單類型的主要功能</span><span class="sxs-lookup"><span data-stu-id="8bd68-124">Main Features of Simple Types</span></span>  
 <span data-ttu-id="8bd68-125">所有簡單類型 (C# 語言的必要項目) 是 .NET Framework System 類型的別名。</span><span class="sxs-lookup"><span data-stu-id="8bd68-125">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="8bd68-126">例如，[int](../../../csharp/language-reference/keywords/int.md) 是 <xref:System.Int32?displayProperty=nameWithType> 的別名。</span><span class="sxs-lookup"><span data-stu-id="8bd68-126">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8bd68-127">如需完整的別名清單，請參閱[內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="8bd68-127">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="8bd68-128">在編譯時間，會評估常數運算式 (其運算元都是簡單類型常數)。</span><span class="sxs-lookup"><span data-stu-id="8bd68-128">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="8bd68-129">簡單類型可以使用常值進行初始化。</span><span class="sxs-lookup"><span data-stu-id="8bd68-129">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="8bd68-130">例如，'A' 是類型 `char` 的常值，而 2001 是類型 `int` 的常值。</span><span class="sxs-lookup"><span data-stu-id="8bd68-130">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="8bd68-131">初始化實值型別</span><span class="sxs-lookup"><span data-stu-id="8bd68-131">Initializing Value Types</span></span>  
 <span data-ttu-id="8bd68-132">必須先初始化 C# 中的區域變數，再使用它們。</span><span class="sxs-lookup"><span data-stu-id="8bd68-132">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="8bd68-133">例如，您可以宣告區域變數，而不進行初始化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8bd68-133">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```  
int myInt;  
```  
  
 <span data-ttu-id="8bd68-134">您不能先使用它，再將它初始化。</span><span class="sxs-lookup"><span data-stu-id="8bd68-134">You cannot use it before you initialize it.</span></span> <span data-ttu-id="8bd68-135">您可以使用下列陳述式來初始化執行個體：</span><span class="sxs-lookup"><span data-stu-id="8bd68-135">You can initialize it using the following statement:</span></span>  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="8bd68-136">這個陳述式相當於下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="8bd68-136">This statement is equivalent to the following statement:</span></span>  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="8bd68-137">當然，您可以有相同陳述式中的宣告和初始化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8bd68-137">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```  
int myInt = new int();  
```  
  
 <span data-ttu-id="8bd68-138">-或-</span><span class="sxs-lookup"><span data-stu-id="8bd68-138">–or–</span></span>  
  
```  
int myInt = 0;  
```  
  
 <span data-ttu-id="8bd68-139">使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子會呼叫特定類型的預設建構函式，並將預設值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="8bd68-139">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="8bd68-140">在上述範例中，預設建構函式已將 `0` 值指派給 `myInt`。</span><span class="sxs-lookup"><span data-stu-id="8bd68-140">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="8bd68-141">如需呼叫預設建構函式來指派值的詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="8bd68-141">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="8bd68-142">如果要使用使用者定義型別，請使用 [new](../../../csharp/language-reference/keywords/new.md) 來叫用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bd68-142">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="8bd68-143">例如，下列陳述式會叫用 `Point` 結構的預設建構函式：</span><span class="sxs-lookup"><span data-stu-id="8bd68-143">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="8bd68-144">在此呼叫之後，會視為已明確指派結構，也就是說，其所有成員都已初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="8bd68-144">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="8bd68-145">如需 new 運算子的詳細資訊，請參閱 [new](../../../csharp/language-reference/keywords/new.md)。</span><span class="sxs-lookup"><span data-stu-id="8bd68-145">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="8bd68-146">如需格式化數值類型輸出的資訊，請參閱[格式化數值結果表](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)。</span><span class="sxs-lookup"><span data-stu-id="8bd68-146">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd68-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bd68-147">See Also</span></span>  
 [<span data-ttu-id="8bd68-148">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8bd68-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8bd68-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8bd68-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8bd68-150">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8bd68-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8bd68-151">型別</span><span class="sxs-lookup"><span data-stu-id="8bd68-151">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="8bd68-152">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="8bd68-152">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="8bd68-153">參考型別</span><span class="sxs-lookup"><span data-stu-id="8bd68-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
