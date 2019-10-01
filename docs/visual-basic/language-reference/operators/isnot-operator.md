---
title: IsNot 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 32e8f9532244679d2994b0e3d98279d75f7e77b4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701043"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="3f1a2-102">IsNot 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f1a2-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="3f1a2-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f1a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f1a2-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="3f1a2-105">組件</span><span class="sxs-lookup"><span data-stu-id="3f1a2-105">Parts</span></span>
 <span data-ttu-id="3f1a2-106">`result` 必要項。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-106">`result` Required.</span></span> <span data-ttu-id="3f1a2-107">`Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-107">A `Boolean` value.</span></span>

 <span data-ttu-id="3f1a2-108">`object1` 必要項。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-108">`object1` Required.</span></span> <span data-ttu-id="3f1a2-109">任何 @no__t 0 變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="3f1a2-110">`object2` 必要項。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-110">`object2` Required.</span></span> <span data-ttu-id="3f1a2-111">任何 @no__t 0 變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f1a2-112">備註</span><span class="sxs-lookup"><span data-stu-id="3f1a2-112">Remarks</span></span>
 <span data-ttu-id="3f1a2-113">@No__t-0 運算子會判斷兩個物件參考是否參考不同的物件。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="3f1a2-114">不過，它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="3f1a2-115">如果 `object1` 和 `object2` 都參考完全相同的物件實例，`result` 會 `False`;如果不是，`result` `True`。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="3f1a2-116">`IsNot` 是 `Is` 運算子的相反。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="3f1a2-117">@No__t-0 的優點是，您可以避免使用 `Not` 和 `Is` 的語法不好，這可能會很難閱讀。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="3f1a2-118">您可以使用 `Is` 和 @no__t 1 運算子來測試早期繫結和晚期繫結物件。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="3f1a2-119">範例</span><span class="sxs-lookup"><span data-stu-id="3f1a2-119">Example</span></span>
 <span data-ttu-id="3f1a2-120">下列程式碼範例會使用 `Is` 運算子和 `IsNot` 運算子來完成相同的比較。</span><span class="sxs-lookup"><span data-stu-id="3f1a2-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="3f1a2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f1a2-121">See also</span></span>

- [<span data-ttu-id="3f1a2-122">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="3f1a2-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="3f1a2-123">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="3f1a2-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="3f1a2-124">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="3f1a2-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- <span data-ttu-id="3f1a2-125">[如何：測試兩個物件是否相同 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="3f1a2-125">[How to: Test Whether Two Objects Are the Same](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)</span></span>
