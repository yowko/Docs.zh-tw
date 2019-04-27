---
title: HOW TO：使用一個類別來定義運算子 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863489"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="620d0-102">HOW TO：使用一個類別來定義運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="620d0-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="620d0-103">如果您使用的類別或結構，定義自己的運算子，您可以從 Visual Basic 中存取這些運算子。</span><span class="sxs-lookup"><span data-stu-id="620d0-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="620d0-104">類別或結構上定義的運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="620d0-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="620d0-105">範例</span><span class="sxs-lookup"><span data-stu-id="620d0-105">Example</span></span>  
 <span data-ttu-id="620d0-106">下列範例會存取 SQL 結構<xref:System.Data.SqlTypes.SqlString>，其定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 中的 SQL 字串和 Visual Basic 字串之間的兩個方向。</span><span class="sxs-lookup"><span data-stu-id="620d0-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="620d0-107">使用`CType(` *SQL 字串運算式*，`String)`將 SQL 字串轉換成 Visual Basic 字串，並`CType(` *Visual Basic 字串運算式*， <xref:System.Data.SqlTypes.SqlString> `)`另一個方向的轉換。</span><span class="sxs-lookup"><span data-stu-id="620d0-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="620d0-108"><xref:System.Data.SqlTypes.SqlString>結構會定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 從`String`來<xref:System.Data.SqlTypes.SqlString>，從另一種<xref:System.Data.SqlTypes.SqlString>至`String`。</span><span class="sxs-lookup"><span data-stu-id="620d0-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="620d0-109">指派的陳述式`title`要`jobTitle`會使用第一個運算子，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式呼叫會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="620d0-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="620d0-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="620d0-110">Compiling the Code</span></span>  
 <span data-ttu-id="620d0-111">請務必在類別或您使用的結構會定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="620d0-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="620d0-112">請勿假設類別或結構定義每個適用於多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="620d0-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="620d0-113">如需可用的運算子，請參閱[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="620d0-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="620d0-114">包含適當`Imports`原始程式檔的 SQL 字串開頭的陳述式 (在此情況下<xref:System.Data.SqlTypes>)。</span><span class="sxs-lookup"><span data-stu-id="620d0-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="620d0-115">您的專案必須參考 System.Data 和 System.XML。</span><span class="sxs-lookup"><span data-stu-id="620d0-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620d0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="620d0-116">See also</span></span>

- [<span data-ttu-id="620d0-117">運算子程序</span><span class="sxs-lookup"><span data-stu-id="620d0-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="620d0-118">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="620d0-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="620d0-119">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="620d0-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="620d0-120">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="620d0-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="620d0-121">Widening</span><span class="sxs-lookup"><span data-stu-id="620d0-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="620d0-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="620d0-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="620d0-123">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="620d0-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="620d0-124">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="620d0-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="620d0-125">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="620d0-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="620d0-126">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="620d0-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
