---
title: C# 結構 - C# 語言教學課程
description: 了解 C# 實值型別 (稱為結構) 的基本概念
ms.date: 08/10/2016
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: d22cb23fe095874f24d7c002dfdb3eefdde66722
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065956"
---
# <a name="structs"></a><span data-ttu-id="d1323-103">結構</span><span class="sxs-lookup"><span data-stu-id="d1323-103">Structs</span></span>

<span data-ttu-id="d1323-104">和類別一樣，***結構***是可包含資料成員和函式成員的資料結構，但不同於類別，結構是實值型別，不需要堆積配置。</span><span class="sxs-lookup"><span data-stu-id="d1323-104">Like classes, ***structs*** are data structures that can contain data members and function members, but unlike classes, structs are value types and do not require heap allocation.</span></span> <span data-ttu-id="d1323-105">結構型別的變數直接儲存結構的資料，而類別型別的變數則儲存動態配置物件的參考。</span><span class="sxs-lookup"><span data-stu-id="d1323-105">A variable of a struct type directly stores the data of the struct, whereas a variable of a class type stores a reference to a dynamically allocated object.</span></span> <span data-ttu-id="d1323-106">結構類型不支援使用者指定的繼承，且所有結構類型都隱含地繼承自 <xref:System.ValueType> 類型，而該類型又隱含地繼承自 `object`。</span><span class="sxs-lookup"><span data-stu-id="d1323-106">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type <xref:System.ValueType>, which in turn implicitly inherits from `object`.</span></span>

<span data-ttu-id="d1323-107">結構特別適用於含有實值語意的小型資料結構。</span><span class="sxs-lookup"><span data-stu-id="d1323-107">Structs are particularly useful for small data structures that have value semantics.</span></span> <span data-ttu-id="d1323-108">複數、座標系統中的點或字典中的索引鍵/值組都是結構的良好範例。</span><span class="sxs-lookup"><span data-stu-id="d1323-108">Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs.</span></span> <span data-ttu-id="d1323-109">針對小型資料結構使用結構而不使用類別，在應用程式執行的記憶體配置數目上有很大的差別。</span><span class="sxs-lookup"><span data-stu-id="d1323-109">The use of structs rather than classes for small data structures can make a large difference in the number of memory allocations an application performs.</span></span> <span data-ttu-id="d1323-110">比方說，下列程式會建立並初始化 100 個點的陣列。</span><span class="sxs-lookup"><span data-stu-id="d1323-110">For example, the following program creates and initializes an array of 100 points.</span></span> <span data-ttu-id="d1323-111">使用 `Point` 做為類別，會具現化 101 個不同的物件 — 一個代表陣列，剩下的每個代表 100 個元素。</span><span class="sxs-lookup"><span data-stu-id="d1323-111">With `Point` implemented as a class, 101 separate objects are instantiated—one for the array and one each for the 100 elements.</span></span>

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

<span data-ttu-id="d1323-112">替代方案是將 Point 變為結構。</span><span class="sxs-lookup"><span data-stu-id="d1323-112">An alternative is to make Point a struct.</span></span>

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

<span data-ttu-id="d1323-113">現在，只有一個物件會具現化 — 代表陣列的物件 — 而 `Point` 執行個體會以內嵌方式儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="d1323-113">Now, only one object is instantiated—the one for the array—and the `Point` instances are stored in-line in the array.</span></span>

<span data-ttu-id="d1323-114">結構建構函式是使用 `new` 運算子叫用，類似於類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="d1323-114">Struct constructors are invoked with the `new` operator, similar to a class constructor.</span></span> <span data-ttu-id="d1323-115">但是結構建構函式只會傳回結構值本身 (通常是在堆疊上的暫存位置)，然後再視需要複製此值，而不是在受控堆積上動態配置物件並傳回對該物件的參考。</span><span class="sxs-lookup"><span data-stu-id="d1323-115">But, instead of dynamically allocating an object on the managed heap and returning a reference to it, a struct constructor simply returns the struct value itself (typically in a temporary location on the stack), and this value is then copied as necessary.</span></span>

<span data-ttu-id="d1323-116">使用類別時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數參考的物件。</span><span class="sxs-lookup"><span data-stu-id="d1323-116">With classes, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="d1323-117">使用結構時，變數各有自己的資料複本，因此在某一個變數上進行的作業不可能會影響其他變數。</span><span class="sxs-lookup"><span data-stu-id="d1323-117">With structs, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other.</span></span> <span data-ttu-id="d1323-118">例如，下列程式碼片段所產生的輸出取決於點是類別或結構。</span><span class="sxs-lookup"><span data-stu-id="d1323-118">For example, the output produced by the following code fragment depends on whether Point is a class or a struct.</span></span>

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

<span data-ttu-id="d1323-119">如果 `Point` 是類別，則因為 `a` 和 `b` 參考相同的物件，所以輸出為 20。</span><span class="sxs-lookup"><span data-stu-id="d1323-119">If `Point` is a class, the output is 20 because `a` and `b` reference the same object.</span></span> <span data-ttu-id="d1323-120">如果 `Point` 是結構，則因為將 `a` 指派至 `b` 會建立值的複本，所以輸出為 10，而後續指派給 `a.x` 時，此複本不受影響。</span><span class="sxs-lookup"><span data-stu-id="d1323-120">If `Point` is a struct, the output is 10 because the assignment of `a` to `b` creates a copy of the value, and this copy is unaffected by the subsequent assignment to `a.x`.</span></span>

<span data-ttu-id="d1323-121">前一個範例會反白顯示結構的兩個限制。</span><span class="sxs-lookup"><span data-stu-id="d1323-121">The previous example highlights two of the limitations of structs.</span></span> <span data-ttu-id="d1323-122">首先，複製整個結構通常較複製物件參考沒有效率，因此，結構的指派和實值參數傳遞會比參考型別耗用更多資源。</span><span class="sxs-lookup"><span data-stu-id="d1323-122">First, copying an entire struct is typically less efficient than copying an object reference, so assignment and value parameter passing can be more expensive with structs than with reference types.</span></span> <span data-ttu-id="d1323-123">再者，除了 `in`、`ref` 和 `out` 參數外，不可能建立結構的參考，因此在許多情況下無法使用它們。</span><span class="sxs-lookup"><span data-stu-id="d1323-123">Second, except for `in`, `ref`, and `out` parameters, it is not possible to create references to structs, which rules out their usage in a number of situations.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d1323-124">[上一頁](classes-and-objects.md)
>[下一頁](arrays.md)</span><span class="sxs-lookup"><span data-stu-id="d1323-124">[Previous](classes-and-objects.md)
[Next](arrays.md)</span></span>
