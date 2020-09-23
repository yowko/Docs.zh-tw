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
ms.openlocfilehash: 083916a420bf4ad182536363ea46448f6b4c1da5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071348"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="1dd53-102">如何：使用定義運算子的類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dd53-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>

<span data-ttu-id="1dd53-103">如果您使用的類別或結構定義了自己的運算子，您可以從 Visual Basic 存取這些運算子。</span><span class="sxs-lookup"><span data-stu-id="1dd53-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="1dd53-104">在類別或結構上定義運算子 *也稱為多* 載運算子。</span><span class="sxs-lookup"><span data-stu-id="1dd53-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dd53-105">範例</span><span class="sxs-lookup"><span data-stu-id="1dd53-105">Example</span></span>  

 <span data-ttu-id="1dd53-106">下列範例會存取 SQL 結構，此結構會 <xref:System.Data.SqlTypes.SqlString> 定義 ([CType](../../../language-reference/functions/ctype-function.md) 函式的轉換運算子) sql 字串與 Visual Basic 字串之間的雙向函數。</span><span class="sxs-lookup"><span data-stu-id="1dd53-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="1dd53-107">使用 `CType(` *sql 字串運算式*，將 `String)` sql 字串轉換成 Visual Basic 字串，並將 `CType(` *Visual Basic 字串運算式*轉換成 <xref:System.Data.SqlTypes.SqlString> `)` 另一個方向。</span><span class="sxs-lookup"><span data-stu-id="1dd53-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="1dd53-108"><xref:System.Data.SqlTypes.SqlString>結構會定義轉換運算子 ([CType](../../../language-reference/functions/ctype-function.md)函式) 從 `String` 到 <xref:System.Data.SqlTypes.SqlString> ，另一個從轉換 <xref:System.Data.SqlTypes.SqlString> 為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="1dd53-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="1dd53-109">指派給的語句 `title` `jobTitle` 會使用第一個運算子，且 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式呼叫會使用第二個運算子。</span><span class="sxs-lookup"><span data-stu-id="1dd53-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="1dd53-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1dd53-110">Compile the code</span></span>  

 <span data-ttu-id="1dd53-111">請確定您使用的類別或結構定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="1dd53-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="1dd53-112">請勿假設類別或結構已定義每個可用於多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="1dd53-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="1dd53-113">如需可用運算子的清單，請參閱 [運算子語句](../../../language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd53-113">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="1dd53-114">`Imports`在原始程式檔的開頭包含適用于 SQL 字串的適當語句 (在此案例中 <xref:System.Data.SqlTypes>) 。</span><span class="sxs-lookup"><span data-stu-id="1dd53-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="1dd53-115">您的專案必須具有 system.string 和 System.XML 的參考。</span><span class="sxs-lookup"><span data-stu-id="1dd53-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd53-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd53-116">See also</span></span>

- [<span data-ttu-id="1dd53-117">運算子程序</span><span class="sxs-lookup"><span data-stu-id="1dd53-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="1dd53-118">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="1dd53-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="1dd53-119">How to: Define a Conversion Operator</span><span class="sxs-lookup"><span data-stu-id="1dd53-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="1dd53-120">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="1dd53-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="1dd53-121">Widening</span><span class="sxs-lookup"><span data-stu-id="1dd53-121">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="1dd53-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="1dd53-122">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="1dd53-123">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="1dd53-123">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="1dd53-124">作法：宣告結構</span><span class="sxs-lookup"><span data-stu-id="1dd53-124">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="1dd53-125">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="1dd53-125">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="1dd53-126">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="1dd53-126">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
