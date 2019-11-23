---
title: IsNot 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336067"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="003f2-102">IsNot 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="003f2-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="003f2-103">Compares two object reference variables.</span><span class="sxs-lookup"><span data-stu-id="003f2-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="003f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="003f2-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="003f2-105">組件</span><span class="sxs-lookup"><span data-stu-id="003f2-105">Parts</span></span>
 <span data-ttu-id="003f2-106">需要 `result`。</span><span class="sxs-lookup"><span data-stu-id="003f2-106">`result` Required.</span></span> <span data-ttu-id="003f2-107">`Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="003f2-107">A `Boolean` value.</span></span>

 <span data-ttu-id="003f2-108">需要 `object1`。</span><span class="sxs-lookup"><span data-stu-id="003f2-108">`object1` Required.</span></span> <span data-ttu-id="003f2-109">Any `Object` variable or expression.</span><span class="sxs-lookup"><span data-stu-id="003f2-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="003f2-110">需要 `object2`。</span><span class="sxs-lookup"><span data-stu-id="003f2-110">`object2` Required.</span></span> <span data-ttu-id="003f2-111">Any `Object` variable or expression.</span><span class="sxs-lookup"><span data-stu-id="003f2-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="003f2-112">備註</span><span class="sxs-lookup"><span data-stu-id="003f2-112">Remarks</span></span>
 <span data-ttu-id="003f2-113">The `IsNot` operator determines if two object references refer to different objects.</span><span class="sxs-lookup"><span data-stu-id="003f2-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="003f2-114">However, it does not perform value comparisons.</span><span class="sxs-lookup"><span data-stu-id="003f2-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="003f2-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span><span class="sxs-lookup"><span data-stu-id="003f2-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="003f2-116">`IsNot` is the opposite of the `Is` operator.</span><span class="sxs-lookup"><span data-stu-id="003f2-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="003f2-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span><span class="sxs-lookup"><span data-stu-id="003f2-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="003f2-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span><span class="sxs-lookup"><span data-stu-id="003f2-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="003f2-119">範例</span><span class="sxs-lookup"><span data-stu-id="003f2-119">Example</span></span>
 <span data-ttu-id="003f2-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span><span class="sxs-lookup"><span data-stu-id="003f2-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="003f2-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="003f2-121">See also</span></span>

- [<span data-ttu-id="003f2-122">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="003f2-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="003f2-123">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="003f2-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="003f2-124">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="003f2-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="003f2-125">如何：測試兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="003f2-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
