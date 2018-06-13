---
title: C# 陣列 - C# 語言教學課程
description: 陣列是 C# 語言中最基本的集合類型
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: c0fe65348ab2d41852ed9150571dcb0e5b8553f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351001"
---
# <a name="arrays"></a><span data-ttu-id="48d69-103">陣列</span><span class="sxs-lookup"><span data-stu-id="48d69-103">Arrays</span></span>

<span data-ttu-id="48d69-104">***陣列***是一種資料結構，其中包含一些可透過計算索引存取的變數。</span><span class="sxs-lookup"><span data-stu-id="48d69-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="48d69-105">陣列中包含的變數 (也稱為陣列的***元素***) 屬於相同的型別，這種型別稱為陣列的***元素型別***。</span><span class="sxs-lookup"><span data-stu-id="48d69-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="48d69-106">陣列型別是參考型別，而陣列變數的宣告只是預留空間給陣列執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="48d69-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="48d69-107">實際的陣列執行個體是執行階段期間使用 New 運算子動態建立。</span><span class="sxs-lookup"><span data-stu-id="48d69-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="48d69-108">新增作業會指定新陣列執行個體的***長度***，這在該執行個體的存留期是固定的。</span><span class="sxs-lookup"><span data-stu-id="48d69-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="48d69-109">陣列元素的索引範圍在 `0` 到 `Length - 1` 之間。</span><span class="sxs-lookup"><span data-stu-id="48d69-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="48d69-110">`new` 運算子會自動將陣列的元素初始化為其預設值，例如，針對所有數值型別，此值為零，而針對所有參考型別，此值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="48d69-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="48d69-111">下列範例會建立 `int` 元素的陣列、初始化陣列，並印出陣列的內容。</span><span class="sxs-lookup"><span data-stu-id="48d69-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="48d69-112">這個範例會建立並操作***一維陣列***。</span><span class="sxs-lookup"><span data-stu-id="48d69-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="48d69-113">C# 也支援***多維陣列***。</span><span class="sxs-lookup"><span data-stu-id="48d69-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="48d69-114">一個陣列型別的維度數目 (亦稱為陣列型別的***順位***)，是寫入陣列型別的方括弧之間的逗號數目加一。</span><span class="sxs-lookup"><span data-stu-id="48d69-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="48d69-115">下列範例會分別配置一個單維、一個二維和一個三維陣列。</span><span class="sxs-lookup"><span data-stu-id="48d69-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="48d69-116">`a1` 陣列包含 10 個元素、`a2`陣列包含 50 (10 × 5) 個元素，`a3` 陣列包含 100 (10 × 5 × 2) 個元素。</span><span class="sxs-lookup"><span data-stu-id="48d69-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="48d69-117">陣列的元素型別可以是任一型別，包括陣列型別。</span><span class="sxs-lookup"><span data-stu-id="48d69-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="48d69-118">包含陣列型別之元素的陣列有時稱為***不規則陣列***，因為元素陣列的長度不需完全相同。</span><span class="sxs-lookup"><span data-stu-id="48d69-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="48d69-119">下列範例會配置一個 `int` 型別的陣列：</span><span class="sxs-lookup"><span data-stu-id="48d69-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="48d69-120">第一行建立包含三個元素的陣列，每個元素的型別均為 `int[]`，每個元素的初始值均為 `null`。</span><span class="sxs-lookup"><span data-stu-id="48d69-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="48d69-121">接下來的幾行則使用不同長度的個別陣列執行個體的參考初始化三個元素。</span><span class="sxs-lookup"><span data-stu-id="48d69-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="48d69-122">New 運算子允許使用***陣列初始設定式***指定陣列元素的初始值，這是寫入分隔符號 `{` 和 `}` 之間的運算式清單。</span><span class="sxs-lookup"><span data-stu-id="48d69-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="48d69-123">下列範例使用三個元素配置並初始化 `int[]`。</span><span class="sxs-lookup"><span data-stu-id="48d69-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="48d69-124">請注意，陣列的長度是由 { 和 } 之間的運算式數目推斷。</span><span class="sxs-lookup"><span data-stu-id="48d69-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="48d69-125">本機變數與欄位宣告可以進一步縮短，就不需要重新敘述陣列型別。</span><span class="sxs-lookup"><span data-stu-id="48d69-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="48d69-126">先前的兩個範例等同於下列範例：</span><span class="sxs-lookup"><span data-stu-id="48d69-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
<span data-ttu-id="48d69-127">[上一頁](structs.md)
[下一頁](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="48d69-127">[Previous](structs.md)
[Next](interfaces.md)</span></span>
