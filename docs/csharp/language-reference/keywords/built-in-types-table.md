---
title: "內建類型資料表 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="b6519-102">內建類型資料表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b6519-102">Built-In Types Table (C# Reference)</span></span>
<span data-ttu-id="b6519-103">下表顯示內建 C# 型別的關鍵字，這些是 <xref:System> 命名空間中預先定義型別的別名。</span><span class="sxs-lookup"><span data-stu-id="b6519-103">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="b6519-104">C# 類型</span><span class="sxs-lookup"><span data-stu-id="b6519-104">C# Type</span></span>|<span data-ttu-id="b6519-105">.NET Framework 型別</span><span class="sxs-lookup"><span data-stu-id="b6519-105">.NET Framework Type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="b6519-106">bool</span><span class="sxs-lookup"><span data-stu-id="b6519-106">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[<span data-ttu-id="b6519-107">byte</span><span class="sxs-lookup"><span data-stu-id="b6519-107">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[<span data-ttu-id="b6519-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="b6519-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[<span data-ttu-id="b6519-109">char</span><span class="sxs-lookup"><span data-stu-id="b6519-109">char</span></span>](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[<span data-ttu-id="b6519-110">decimal</span><span class="sxs-lookup"><span data-stu-id="b6519-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[<span data-ttu-id="b6519-111">double</span><span class="sxs-lookup"><span data-stu-id="b6519-111">double</span></span>](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[<span data-ttu-id="b6519-112">float</span><span class="sxs-lookup"><span data-stu-id="b6519-112">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[<span data-ttu-id="b6519-113">int</span><span class="sxs-lookup"><span data-stu-id="b6519-113">int</span></span>](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[<span data-ttu-id="b6519-114">uint</span><span class="sxs-lookup"><span data-stu-id="b6519-114">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[<span data-ttu-id="b6519-115">long</span><span class="sxs-lookup"><span data-stu-id="b6519-115">long</span></span>](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[<span data-ttu-id="b6519-116">ulong</span><span class="sxs-lookup"><span data-stu-id="b6519-116">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[<span data-ttu-id="b6519-117">object</span><span class="sxs-lookup"><span data-stu-id="b6519-117">object</span></span>](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[<span data-ttu-id="b6519-118">short</span><span class="sxs-lookup"><span data-stu-id="b6519-118">short</span></span>](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[<span data-ttu-id="b6519-119">ushort</span><span class="sxs-lookup"><span data-stu-id="b6519-119">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[<span data-ttu-id="b6519-120">string</span><span class="sxs-lookup"><span data-stu-id="b6519-120">string</span></span>](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a><span data-ttu-id="b6519-121">備註</span><span class="sxs-lookup"><span data-stu-id="b6519-121">Remarks</span></span>  
 <span data-ttu-id="b6519-122">表中除了 `object` 和 `string` 以外的所有型別，都視為簡單型別。</span><span class="sxs-lookup"><span data-stu-id="b6519-122">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
 <span data-ttu-id="b6519-123">C# 型別關鍵字和它們的別名都可互換。</span><span class="sxs-lookup"><span data-stu-id="b6519-123">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="b6519-124">例如，您可以使用下列任一個宣告來宣告整數變數：</span><span class="sxs-lookup"><span data-stu-id="b6519-124">For example, you can declare an integer variable by using either of the following declarations:</span></span>  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 <span data-ttu-id="b6519-125">若要顯示任何 C# 型別的實際型別，請使用 `GetType()` 系統方法。</span><span class="sxs-lookup"><span data-stu-id="b6519-125">To display the actual type for any C# type, use the system method `GetType()`.</span></span> <span data-ttu-id="b6519-126">例如，下列陳述式顯示代表 `myVariable` 型別的系統別名：</span><span class="sxs-lookup"><span data-stu-id="b6519-126">For example, the following statement displays the system alias that represents the type of `myVariable`:</span></span>  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 <span data-ttu-id="b6519-127">您也可以使用 [typeof](../../../csharp/language-reference/keywords/typeof.md) 運算子。</span><span class="sxs-lookup"><span data-stu-id="b6519-127">You can also use the [typeof](../../../csharp/language-reference/keywords/typeof.md) operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6519-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6519-128">See Also</span></span>  
 [<span data-ttu-id="b6519-129">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b6519-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b6519-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b6519-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b6519-131">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b6519-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b6519-132">實值型別</span><span class="sxs-lookup"><span data-stu-id="b6519-132">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="b6519-133">預設值表</span><span class="sxs-lookup"><span data-stu-id="b6519-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="b6519-134">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="b6519-134">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [<span data-ttu-id="b6519-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="b6519-135">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="b6519-136">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="b6519-136">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
