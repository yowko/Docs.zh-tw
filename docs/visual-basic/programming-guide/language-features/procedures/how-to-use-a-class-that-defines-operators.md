---
title: "如何：使用定義運算子的類別 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="5bbc2-102">如何：使用定義運算子的類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bbc2-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="5bbc2-103">如果您使用類別或結構，定義自己的運算子，您可以存取這些運算子，從[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="5bbc2-104">在類別或結構上定義運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bbc2-105">範例</span><span class="sxs-lookup"><span data-stu-id="5bbc2-105">Example</span></span>  
 <span data-ttu-id="5bbc2-106">下列範例會存取 SQL 結構<xref:System.Data.SqlTypes.SqlString>，它負責定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 之間的 SQL 字串雙向和[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]字串。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string.</span></span> <span data-ttu-id="5bbc2-107">使用`CType(` *SQL 字串運算式*，`String)`要轉換的 SQL 字串[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]字串和`CType(` *Visual Basic 字串運算式*， <xref:System.Data.SqlTypes.SqlString>`)`轉換中另一種方向。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="5bbc2-108"><xref:System.Data.SqlTypes.SqlString>結構會定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 從`String`至<xref:System.Data.SqlTypes.SqlString>，從另一個<xref:System.Data.SqlTypes.SqlString>至`String`。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="5bbc2-109">指派的陳述式`title`至`jobTitle`會使用第一個運算子，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式呼叫會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bbc2-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5bbc2-110">Compiling the Code</span></span>  
 <span data-ttu-id="5bbc2-111">請確定該類別或結構會使用定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="5bbc2-112">請勿假設類別或結構定義每個可用的多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="5bbc2-113">如需可用的運算子，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="5bbc2-114">包含適當`Imports`SQL 字串的開頭的陳述式的原始程式檔 (在此情況下<xref:System.Data.SqlTypes>)。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="5bbc2-115">您的專案必須已 System.Data 和 System.XML 參考。</span><span class="sxs-lookup"><span data-stu-id="5bbc2-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbc2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bbc2-116">See Also</span></span>  
 [<span data-ttu-id="5bbc2-117">運算子程序</span><span class="sxs-lookup"><span data-stu-id="5bbc2-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="5bbc2-118">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="5bbc2-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="5bbc2-119">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="5bbc2-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="5bbc2-120">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="5bbc2-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="5bbc2-121">Widening</span><span class="sxs-lookup"><span data-stu-id="5bbc2-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="5bbc2-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="5bbc2-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="5bbc2-123">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="5bbc2-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="5bbc2-124">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="5bbc2-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="5bbc2-125">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="5bbc2-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="5bbc2-126">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="5bbc2-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
