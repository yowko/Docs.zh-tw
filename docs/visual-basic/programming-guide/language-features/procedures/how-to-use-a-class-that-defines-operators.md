---
title: "如何︰ 使用類別定義運算子 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator procedures, calling
- procedures, operator
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e4d76788346e08123102d56088c0a1e0f5f2238f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="7690e-102">如何：使用定義運算子的類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7690e-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="7690e-103">如果您使用的類別或結構定義自己的運算子，您可以存取這些運算子，從[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7690e-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="7690e-104">在類別或結構上定義運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="7690e-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7690e-105">範例</span><span class="sxs-lookup"><span data-stu-id="7690e-105">Example</span></span>  
 <span data-ttu-id="7690e-106">下列範例會存取 SQL 結構<xref:System.Data.SqlTypes.SqlString>，以定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 中的 SQL 字串之間進行雙向和[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字串。</xref:System.Data.SqlTypes.SqlString></span><span class="sxs-lookup"><span data-stu-id="7690e-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string.</span></span> <span data-ttu-id="7690e-107">使用`CType(` *SQL 字串運算式*，`String)`要轉換的 SQL 字串[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字串，和`CType(` *Visual Basic 字串運算式*，<xref:System.Data.SqlTypes.SqlString>`)`將另一個方向。</xref:System.Data.SqlTypes.SqlString></span><span class="sxs-lookup"><span data-stu-id="7690e-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 <span data-ttu-id="7690e-108">[!code-vb[VbVbcnProcedures #&30;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7690e-108">[!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="7690e-109">[!code-vb[VbVbcnProcedures #&31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7690e-109">[!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="7690e-110"><xref:System.Data.SqlTypes.SqlString>結構定義的轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 從`String`至<xref:System.Data.SqlTypes.SqlString>，從另一個<xref:System.Data.SqlTypes.SqlString>到`String`。</xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString></span><span class="sxs-lookup"><span data-stu-id="7690e-110">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="7690e-111">指派的陳述式`title`至`jobTitle`會使用第一個運算子，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式呼叫會使用第二個。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="7690e-111">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7690e-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7690e-112">Compiling the Code</span></span>  
 <span data-ttu-id="7690e-113">請確定您使用的結構或類別定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="7690e-113">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="7690e-114">請勿假設類別或結構定義每個可用的多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="7690e-114">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="7690e-115">如需可用的運算子，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7690e-115">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="7690e-116">包含適當`Imports`SQL 字串開頭的陳述式的原始程式檔 (在此情況下<xref:System.Data.SqlTypes>)。</xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="7690e-116">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="7690e-117">您的專案必須參考 System.Data 和 System.XML 等。</span><span class="sxs-lookup"><span data-stu-id="7690e-117">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7690e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7690e-118">See Also</span></span>  
 <span data-ttu-id="7690e-119">[運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-119">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="7690e-120"> [如何︰ 定義運算子](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-120"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="7690e-121"> [如何︰ 定義轉換運算子](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-121"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="7690e-122"> [如何︰ 呼叫運算子程序](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-122"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="7690e-123"> [擴展](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-123"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="7690e-124"> [縮小](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-124"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="7690e-125"> [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-125"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="7690e-126"> [如何︰ 宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-126"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="7690e-127"> [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="7690e-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="7690e-128"> [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="7690e-128"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
