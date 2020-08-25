---
title: IsNot 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811037"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="c8c94-102">IsNot 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8c94-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="c8c94-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="c8c94-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8c94-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8c94-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="c8c94-105">組件</span><span class="sxs-lookup"><span data-stu-id="c8c94-105">Parts</span></span>

- `result`

  <span data-ttu-id="c8c94-106">必要。</span><span class="sxs-lookup"><span data-stu-id="c8c94-106">Required.</span></span> <span data-ttu-id="c8c94-107">`Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="c8c94-107">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="c8c94-108">必要。</span><span class="sxs-lookup"><span data-stu-id="c8c94-108">Required.</span></span> <span data-ttu-id="c8c94-109">任何 `Object` 變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="c8c94-109">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="c8c94-110">必要。</span><span class="sxs-lookup"><span data-stu-id="c8c94-110">Required.</span></span> <span data-ttu-id="c8c94-111">任何 `Object` 變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="c8c94-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8c94-112">備註</span><span class="sxs-lookup"><span data-stu-id="c8c94-112">Remarks</span></span>

<span data-ttu-id="c8c94-113">`IsNot`運算子會判斷兩個物件參考是否參考不同的物件。</span><span class="sxs-lookup"><span data-stu-id="c8c94-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="c8c94-114">但是，它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="c8c94-114">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="c8c94-115">如果 `object1` 和 `object2` 兩者都參考完全相同的物件實例，則為 `result` `False` ; 如果不是，則 `result` 為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="c8c94-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="c8c94-116">`IsNot` 這是運算子的相反 `Is` 。</span><span class="sxs-lookup"><span data-stu-id="c8c94-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="c8c94-117">的優點 `IsNot` 是您可以避免使用和的語法不 `Not` `Is` 困難，這可能很難閱讀。</span><span class="sxs-lookup"><span data-stu-id="c8c94-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="c8c94-118">您可以使用 `Is` 和 `IsNot` 運算子來測試早期繫結和晚期繫結的物件。</span><span class="sxs-lookup"><span data-stu-id="c8c94-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="c8c94-119">範例</span><span class="sxs-lookup"><span data-stu-id="c8c94-119">Example</span></span>

<span data-ttu-id="c8c94-120">下列程式碼範例會使用 `Is` 運算子和 `IsNot` 運算子來完成相同的比較。</span><span class="sxs-lookup"><span data-stu-id="c8c94-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="c8c94-121">使用 TypeOf 運算子搭配 IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="c8c94-121">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="c8c94-122">從 Visual Basic 14 開始，您可以使用 `TypeOf` 運算子搭配 `IsNot` 運算子來測試物件是否與資料類型 *不* 相容。</span><span class="sxs-lookup"><span data-stu-id="c8c94-122">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="c8c94-123">例如：</span><span class="sxs-lookup"><span data-stu-id="c8c94-123">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="c8c94-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8c94-124">See also</span></span>

- [<span data-ttu-id="c8c94-125">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="c8c94-125">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="c8c94-126">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="c8c94-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="c8c94-127">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="c8c94-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c8c94-128">如何：測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="c8c94-128">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
