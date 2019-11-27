---
title: 如何：使用定義運算子的類別
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
ms.openlocfilehash: 9ec4b4c07910100dd02cc86e882b44aa7dbd2ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346043"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="4d60a-102">如何：使用定義運算子的類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d60a-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="4d60a-103">如果您使用的類別或結構定義自己的運算子，您可以從 Visual Basic 存取這些運算子。</span><span class="sxs-lookup"><span data-stu-id="4d60a-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="4d60a-104">在類別或結構上定義運算子*也稱為多*載運算子。</span><span class="sxs-lookup"><span data-stu-id="4d60a-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d60a-105">範例</span><span class="sxs-lookup"><span data-stu-id="4d60a-105">Example</span></span>  
 <span data-ttu-id="4d60a-106">下列範例會存取 SQL 結構 <xref:System.Data.SqlTypes.SqlString>，這會在 SQL 字串和 Visual Basic 字串之間的兩個方向定義轉換運算子（[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)）。</span><span class="sxs-lookup"><span data-stu-id="4d60a-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="4d60a-107">使用 `CType(`*sql 字串運算式*，`String)` 將 SQL 字串轉換為 Visual Basic 字串，並 `CType(`*Visual Basic 字串運算式*，<xref:System.Data.SqlTypes.SqlString>`)` 以另一個方向轉換。</span><span class="sxs-lookup"><span data-stu-id="4d60a-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="4d60a-108"><xref:System.Data.SqlTypes.SqlString> 結構定義從 `String` 到 <xref:System.Data.SqlTypes.SqlString> 的轉換運算子（[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)），另一個則是從 <xref:System.Data.SqlTypes.SqlString> 到 `String`。</span><span class="sxs-lookup"><span data-stu-id="4d60a-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="4d60a-109">將 `title` 指派給 `jobTitle` 的語句會使用第一個運算子，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式呼叫會使用第二個運算子。</span><span class="sxs-lookup"><span data-stu-id="4d60a-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d60a-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4d60a-110">Compiling the Code</span></span>  
 <span data-ttu-id="4d60a-111">請確定您所使用的類別或結構會定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="4d60a-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="4d60a-112">請勿假設類別或結構已定義每個可用於多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="4d60a-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="4d60a-113">如需可用的運算子清單，請參閱[Operator 語句](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4d60a-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="4d60a-114">在原始程式檔的開頭包含 SQL 字串的適當 `Imports` 語句（在此案例中為 <xref:System.Data.SqlTypes>）。</span><span class="sxs-lookup"><span data-stu-id="4d60a-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="4d60a-115">您的專案必須參考 System.web 和 system.string。</span><span class="sxs-lookup"><span data-stu-id="4d60a-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d60a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d60a-116">See also</span></span>

- [<span data-ttu-id="4d60a-117">運算子程序</span><span class="sxs-lookup"><span data-stu-id="4d60a-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="4d60a-118">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="4d60a-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="4d60a-119">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="4d60a-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="4d60a-120">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="4d60a-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="4d60a-121">Widening</span><span class="sxs-lookup"><span data-stu-id="4d60a-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="4d60a-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="4d60a-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="4d60a-123">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d60a-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4d60a-124">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="4d60a-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="4d60a-125">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="4d60a-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="4d60a-126">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="4d60a-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
