---
title: 為運算子
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812259"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="0256c-102">是運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="0256c-102">Is operator (Visual Basic)</span></span>

<span data-ttu-id="0256c-103">比較兩個物件參考變數。</span><span class="sxs-lookup"><span data-stu-id="0256c-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="0256c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0256c-104">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="0256c-105">組件</span><span class="sxs-lookup"><span data-stu-id="0256c-105">Parts</span></span>

 `result`  
 <span data-ttu-id="0256c-106">必要。</span><span class="sxs-lookup"><span data-stu-id="0256c-106">Required.</span></span> <span data-ttu-id="0256c-107">任何 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="0256c-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="0256c-108">必要。</span><span class="sxs-lookup"><span data-stu-id="0256c-108">Required.</span></span> <span data-ttu-id="0256c-109">任何 `Object` 名稱。</span><span class="sxs-lookup"><span data-stu-id="0256c-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="0256c-110">必要。</span><span class="sxs-lookup"><span data-stu-id="0256c-110">Required.</span></span> <span data-ttu-id="0256c-111">任何 `Object` 名稱。</span><span class="sxs-lookup"><span data-stu-id="0256c-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0256c-112">備註</span><span class="sxs-lookup"><span data-stu-id="0256c-112">Remarks</span></span>

<span data-ttu-id="0256c-113">`Is`運算子會判斷兩個物件參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="0256c-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="0256c-114">但是，它不會執行值比較。</span><span class="sxs-lookup"><span data-stu-id="0256c-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="0256c-115">如果 `object1` 和 `object2` 兩者都參考完全相同的物件實例，則為 `result` `True` ; 如果沒有，則 `result` 為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="0256c-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="0256c-116">`Is`關鍵字也可用於[Select .。。Case 語句](../statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0256c-116">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0256c-117">範例</span><span class="sxs-lookup"><span data-stu-id="0256c-117">Example</span></span>

<span data-ttu-id="0256c-118">下列範例會使用 `Is` 運算子來比較物件參考的配對。</span><span class="sxs-lookup"><span data-stu-id="0256c-118">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="0256c-119">結果會指派給一個 `Boolean` 值，表示兩個物件是否相同。</span><span class="sxs-lookup"><span data-stu-id="0256c-119">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="0256c-120">如先前的範例所示，您可以使用 `Is` 運算子來測試早期繫結和晚期繫結的物件。</span><span class="sxs-lookup"><span data-stu-id="0256c-120">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="0256c-121">使用 TypeOf 運算子搭配 Is 運算子</span><span class="sxs-lookup"><span data-stu-id="0256c-121">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="0256c-122">`Is` 運算子也可以搭配 `TypeOf` 關鍵字使用，以建立一個 `TypeOf` ... `Is` 運算式，以測試物件變數是否與資料類型相容。</span><span class="sxs-lookup"><span data-stu-id="0256c-122">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="0256c-123">例如：</span><span class="sxs-lookup"><span data-stu-id="0256c-123">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="0256c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0256c-124">See also</span></span>

- [<span data-ttu-id="0256c-125">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="0256c-125">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="0256c-126">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="0256c-126">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="0256c-127">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0256c-127">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="0256c-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="0256c-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0256c-129">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="0256c-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0256c-130">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="0256c-130">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
