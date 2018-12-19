---
title: struct - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 2d0cba75e067e4d75ca5b544a664d7dede153c73
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237528"
---
# <a name="struct-c-reference"></a><span data-ttu-id="ad827-102">struct (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ad827-102">struct (C# Reference)</span></span>

<span data-ttu-id="ad827-103">`struct` 類型是實值類型，通常可用來封裝一小組相關變數，例如矩形的座標，或詳細目錄中某個項目的特性。</span><span class="sxs-lookup"><span data-stu-id="ad827-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="ad827-104">下列範例示範簡單結構宣告：</span><span class="sxs-lookup"><span data-stu-id="ad827-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="ad827-105">備註</span><span class="sxs-lookup"><span data-stu-id="ad827-105">Remarks</span></span>

<span data-ttu-id="ad827-106">結構還包含[建構函式](../../programming-guide/classes-and-structs/constructors.md)、[常數](../../programming-guide/classes-and-structs/constants.md)、[欄位](../../programming-guide/classes-and-structs/fields.md)、[方法](../../programming-guide/classes-and-structs/methods.md)、[屬性](../../programming-guide/classes-and-structs/properties.md)、[索引子](../../programming-guide/indexers/index.md)、[運算子](../../programming-guide/statements-expressions-operators/operators.md)、[事件](../../programming-guide/events/index.md)和[巢狀型別](../../programming-guide/classes-and-structs/nested-types.md)，不過如果需要數個這類成員，您應該考慮以類別來取代類型。</span><span class="sxs-lookup"><span data-stu-id="ad827-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="ad827-107">如需範例，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="ad827-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="ad827-108">結構可以實作介面，但無法繼承自其他結構。</span><span class="sxs-lookup"><span data-stu-id="ad827-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="ad827-109">因此，結構成員無法宣告為 `protected`。</span><span class="sxs-lookup"><span data-stu-id="ad827-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="ad827-110">如需詳細資訊，請參閱[結構](../../programming-guide/classes-and-structs/structs.md)。</span><span class="sxs-lookup"><span data-stu-id="ad827-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="ad827-111">範例</span><span class="sxs-lookup"><span data-stu-id="ad827-111">Examples</span></span>

<span data-ttu-id="ad827-112">如需範例和詳細資訊，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="ad827-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ad827-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ad827-113">C# language specification</span></span>

<span data-ttu-id="ad827-114">如需範例，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="ad827-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad827-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad827-115">See also</span></span>

- [<span data-ttu-id="ad827-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ad827-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad827-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ad827-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad827-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ad827-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ad827-119">預設值表</span><span class="sxs-lookup"><span data-stu-id="ad827-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="ad827-120">內建型別表</span><span class="sxs-lookup"><span data-stu-id="ad827-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="ad827-121">型別</span><span class="sxs-lookup"><span data-stu-id="ad827-121">Types</span></span>](types.md)
- [<span data-ttu-id="ad827-122">實值型別</span><span class="sxs-lookup"><span data-stu-id="ad827-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="ad827-123">class</span><span class="sxs-lookup"><span data-stu-id="ad827-123">class</span></span>](class.md)
- [<span data-ttu-id="ad827-124">interface</span><span class="sxs-lookup"><span data-stu-id="ad827-124">interface</span></span>](interface.md)
- [<span data-ttu-id="ad827-125">類別和結構</span><span class="sxs-lookup"><span data-stu-id="ad827-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)