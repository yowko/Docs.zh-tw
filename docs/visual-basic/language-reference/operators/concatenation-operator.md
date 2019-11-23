---
title: '&amp; 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336061"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="5d096-102">&amp; Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d096-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="5d096-103">Generates a string concatenation of two expressions.</span><span class="sxs-lookup"><span data-stu-id="5d096-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d096-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d096-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="5d096-105">組件</span><span class="sxs-lookup"><span data-stu-id="5d096-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="5d096-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="5d096-106">Required.</span></span> <span data-ttu-id="5d096-107">Any `String` or `Object` variable.</span><span class="sxs-lookup"><span data-stu-id="5d096-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="5d096-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="5d096-108">Required.</span></span> <span data-ttu-id="5d096-109">Any expression with a data type that widens to `String`.</span><span class="sxs-lookup"><span data-stu-id="5d096-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="5d096-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="5d096-110">Required.</span></span> <span data-ttu-id="5d096-111">Any expression with a data type that widens to `String`.</span><span class="sxs-lookup"><span data-stu-id="5d096-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d096-112">備註</span><span class="sxs-lookup"><span data-stu-id="5d096-112">Remarks</span></span>  
 <span data-ttu-id="5d096-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span><span class="sxs-lookup"><span data-stu-id="5d096-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="5d096-114">If either of the data types does not widen to `String`, the compiler generates an error.</span><span class="sxs-lookup"><span data-stu-id="5d096-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="5d096-115">The data type of `result` is `String`.</span><span class="sxs-lookup"><span data-stu-id="5d096-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="5d096-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span><span class="sxs-lookup"><span data-stu-id="5d096-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d096-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="5d096-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5d096-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="5d096-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5d096-119">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="5d096-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d096-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span><span class="sxs-lookup"><span data-stu-id="5d096-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="5d096-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="5d096-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d096-122">範例</span><span class="sxs-lookup"><span data-stu-id="5d096-122">Example</span></span>  
 <span data-ttu-id="5d096-123">This example uses the `&` operator to force string concatenation.</span><span class="sxs-lookup"><span data-stu-id="5d096-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="5d096-124">The result is a string value representing the concatenation of the two string operands.</span><span class="sxs-lookup"><span data-stu-id="5d096-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5d096-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d096-125">See also</span></span>

- [<span data-ttu-id="5d096-126">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="5d096-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="5d096-127">串連運算子</span><span class="sxs-lookup"><span data-stu-id="5d096-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="5d096-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="5d096-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5d096-129">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="5d096-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5d096-130">Concatenation Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d096-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
