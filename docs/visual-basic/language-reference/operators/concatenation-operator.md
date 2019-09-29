---
title: '&amp;運算子（Visual Basic）'
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
ms.openlocfilehash: aaa7c1b9ab7f6c920180d97b55c3bdeb23f00e02
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592249"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="12426-102">&amp;運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="12426-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="12426-103">產生兩個運算式的字串串連。</span><span class="sxs-lookup"><span data-stu-id="12426-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12426-104">語法</span><span class="sxs-lookup"><span data-stu-id="12426-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="12426-105">組件</span><span class="sxs-lookup"><span data-stu-id="12426-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="12426-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="12426-106">Required.</span></span> <span data-ttu-id="12426-107">任何 `String` 或 @no__t 1 的變數。</span><span class="sxs-lookup"><span data-stu-id="12426-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="12426-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="12426-108">Required.</span></span> <span data-ttu-id="12426-109">具有擴展為 `String` 之資料類型的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="12426-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="12426-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="12426-110">Required.</span></span> <span data-ttu-id="12426-111">具有擴展為 `String` 之資料類型的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="12426-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12426-112">備註</span><span class="sxs-lookup"><span data-stu-id="12426-112">Remarks</span></span>  
 <span data-ttu-id="12426-113">如果 `expression1` 或 `expression2` 的資料類型不是 `String` 但擴大至 `String`，則會轉換成 `String`。</span><span class="sxs-lookup"><span data-stu-id="12426-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="12426-114">如果其中一種資料類型不會擴展為 `String`，則編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="12426-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="12426-115">@No__t-0 的資料類型是 `String`。</span><span class="sxs-lookup"><span data-stu-id="12426-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="12426-116">如果其中一個或兩個運算式評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值，或其值為 <xref:System.DBNull.Value?displayProperty=nameWithType>，則會將它們視為字串，其值為 ""。</span><span class="sxs-lookup"><span data-stu-id="12426-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12426-117">@No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="12426-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="12426-118">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="12426-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="12426-119">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="12426-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12426-120">& 符號（&）字元也可以用來將變數識別為類型 `Long`。</span><span class="sxs-lookup"><span data-stu-id="12426-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="12426-121">如需詳細資訊，請參閱[類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="12426-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12426-122">範例</span><span class="sxs-lookup"><span data-stu-id="12426-122">Example</span></span>  
 <span data-ttu-id="12426-123">這個範例會使用 `&` 運算子來強制執行字串串連。</span><span class="sxs-lookup"><span data-stu-id="12426-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="12426-124">結果為字串值，表示兩個字串運算元的串連。</span><span class="sxs-lookup"><span data-stu-id="12426-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="12426-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12426-125">See also</span></span>

- [<span data-ttu-id="12426-126">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="12426-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="12426-127">串連運算子</span><span class="sxs-lookup"><span data-stu-id="12426-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="12426-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="12426-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="12426-129">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="12426-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="12426-130">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="12426-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
