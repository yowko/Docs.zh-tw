---
title: "struct (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e8a848d5543291ef335e72cb7806158827e865dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="struct-c-reference"></a><span data-ttu-id="7d749-102">struct (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7d749-102">struct (C# Reference)</span></span>
<span data-ttu-id="7d749-103">`struct` 類型是實值類型，通常可用來封裝一小組相關變數，例如矩形的座標，或詳細目錄中某個項目的特性。</span><span class="sxs-lookup"><span data-stu-id="7d749-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="7d749-104">下列範例示範簡單結構宣告：</span><span class="sxs-lookup"><span data-stu-id="7d749-104">The following example shows a simple struct declaration:</span></span>  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="7d749-105">備註</span><span class="sxs-lookup"><span data-stu-id="7d749-105">Remarks</span></span>  
 <span data-ttu-id="7d749-106">結構還包含[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)、[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)、[欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)、[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[索引子](../../../csharp/programming-guide/indexers/index.md)、[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)、[事件](../../../csharp/programming-guide/events/index.md)和[巢狀型別](../../../csharp/programming-guide/classes-and-structs/nested-types.md)，不過如果需要數個這類成員，您應該考慮以類別來取代類型。</span><span class="sxs-lookup"><span data-stu-id="7d749-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="7d749-107">如需範例，請參閱[使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d749-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="7d749-108">結構可以實作介面，但無法繼承自其他結構。</span><span class="sxs-lookup"><span data-stu-id="7d749-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="7d749-109">因此，結構成員無法宣告為 `protected`。</span><span class="sxs-lookup"><span data-stu-id="7d749-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="7d749-110">如需詳細資訊，請參閱[結構](../../../csharp/programming-guide/classes-and-structs/structs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d749-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7d749-111">範例</span><span class="sxs-lookup"><span data-stu-id="7d749-111">Examples</span></span>  
 <span data-ttu-id="7d749-112">如需範例和詳細資訊，請參閱[使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d749-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7d749-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7d749-113">C# Language Specification</span></span>  
 <span data-ttu-id="7d749-114">如需範例，請參閱[使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="7d749-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d749-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d749-115">See Also</span></span>  
 [<span data-ttu-id="7d749-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7d749-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7d749-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7d749-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7d749-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="7d749-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7d749-119">預設值表</span><span class="sxs-lookup"><span data-stu-id="7d749-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="7d749-120">內建型別表</span><span class="sxs-lookup"><span data-stu-id="7d749-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="7d749-121">型別</span><span class="sxs-lookup"><span data-stu-id="7d749-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="7d749-122">實值型別</span><span class="sxs-lookup"><span data-stu-id="7d749-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="7d749-123">class</span><span class="sxs-lookup"><span data-stu-id="7d749-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="7d749-124">interface</span><span class="sxs-lookup"><span data-stu-id="7d749-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="7d749-125">類別和結構</span><span class="sxs-lookup"><span data-stu-id="7d749-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
