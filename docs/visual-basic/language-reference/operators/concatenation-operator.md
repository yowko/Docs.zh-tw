---
title: '&amp;運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="7b3bc-102">&amp;運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b3bc-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="7b3bc-103">產生的字串串連兩個運算式。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b3bc-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="7b3bc-105">組件</span><span class="sxs-lookup"><span data-stu-id="7b3bc-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7b3bc-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-106">Required.</span></span> <span data-ttu-id="7b3bc-107">任何`String`或`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="7b3bc-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-108">Required.</span></span> <span data-ttu-id="7b3bc-109">任何運算式資料類型可擴展成`String`。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="7b3bc-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-110">Required.</span></span> <span data-ttu-id="7b3bc-111">任何運算式資料類型可擴展成`String`。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b3bc-112">備註</span><span class="sxs-lookup"><span data-stu-id="7b3bc-112">Remarks</span></span>  
 <span data-ttu-id="7b3bc-113">資料類型，是否`expression1`或`expression2`不`String`但可擴展為`String`，它會轉換成`String`。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="7b3bc-114">如果資料類型並不會擴展為`String`，編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="7b3bc-115">資料型別`result`是`String`。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="7b3bc-116">如果一或兩個運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或具有值為<xref:System.DBNull.Value?displayProperty=nameWithType>，則會視為字串，其值為""。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b3bc-117">`&`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7b3bc-118">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7b3bc-119">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b3bc-120">連字號 (&) 字元也可用來識別變數類型為`Long`。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="7b3bc-121">如需詳細資訊，請參閱[型別字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b3bc-122">範例</span><span class="sxs-lookup"><span data-stu-id="7b3bc-122">Example</span></span>  
 <span data-ttu-id="7b3bc-123">這個範例會使用`&`以強制字串串連運算子。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="7b3bc-124">結果是字串值，表示兩個字串運算元的串連。</span><span class="sxs-lookup"><span data-stu-id="7b3bc-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b3bc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b3bc-125">See Also</span></span>  
 [<span data-ttu-id="7b3bc-126">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="7b3bc-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="7b3bc-127">串連運算子</span><span class="sxs-lookup"><span data-stu-id="7b3bc-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="7b3bc-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7b3bc-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="7b3bc-129">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="7b3bc-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="7b3bc-130">在 Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="7b3bc-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
