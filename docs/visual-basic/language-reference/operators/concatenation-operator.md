---
title: '&amp; 運算子 (Visual Basic)'
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
ms.openlocfilehash: dd85363447e9b405241d608550d9484b4760a739
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817275"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="e58a9-102">&amp; 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e58a9-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="e58a9-103">會產生兩個運算式的字串串連。</span><span class="sxs-lookup"><span data-stu-id="e58a9-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e58a9-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e58a9-105">組件</span><span class="sxs-lookup"><span data-stu-id="e58a9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e58a9-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="e58a9-106">Required.</span></span> <span data-ttu-id="e58a9-107">任何`String`或`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="e58a9-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="e58a9-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="e58a9-108">Required.</span></span> <span data-ttu-id="e58a9-109">任何運算式資料類型可擴展為`String`。</span><span class="sxs-lookup"><span data-stu-id="e58a9-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="e58a9-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="e58a9-110">Required.</span></span> <span data-ttu-id="e58a9-111">任何運算式資料類型可擴展為`String`。</span><span class="sxs-lookup"><span data-stu-id="e58a9-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e58a9-112">備註</span><span class="sxs-lookup"><span data-stu-id="e58a9-112">Remarks</span></span>  
 <span data-ttu-id="e58a9-113">如果您的資料類型`expression1`或`expression2`不是`String`但可擴展為`String`，則會轉換成`String`。</span><span class="sxs-lookup"><span data-stu-id="e58a9-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="e58a9-114">如果其中一種資料類型不會不會擴展為`String`，編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e58a9-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="e58a9-115">資料類型`result`是`String`。</span><span class="sxs-lookup"><span data-stu-id="e58a9-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="e58a9-116">如果一或兩個運算式都評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或值為<xref:System.DBNull.Value?displayProperty=nameWithType>，它們會被視為值為字串""。</span><span class="sxs-lookup"><span data-stu-id="e58a9-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58a9-117">`&`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="e58a9-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e58a9-118">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="e58a9-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e58a9-119">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e58a9-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58a9-120">連字號 (&) 字元也可用來識別做為類型的變數`Long`。</span><span class="sxs-lookup"><span data-stu-id="e58a9-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="e58a9-121">如需詳細資訊，請參閱 <<c0> [ 類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="e58a9-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e58a9-122">範例</span><span class="sxs-lookup"><span data-stu-id="e58a9-122">Example</span></span>  
 <span data-ttu-id="e58a9-123">這個範例會使用`&`強制字串串連運算子。</span><span class="sxs-lookup"><span data-stu-id="e58a9-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="e58a9-124">結果是字串值，表示兩個字串運算元串連。</span><span class="sxs-lookup"><span data-stu-id="e58a9-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e58a9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e58a9-125">See also</span></span>

- [<span data-ttu-id="e58a9-126">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="e58a9-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="e58a9-127">串連運算子</span><span class="sxs-lookup"><span data-stu-id="e58a9-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="e58a9-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="e58a9-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e58a9-129">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="e58a9-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e58a9-130">在 Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="e58a9-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
