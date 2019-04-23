---
title: HOW TO：定義運算子 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 14aa25de78eb357f8474d3828aa45e48e7a4f9c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126109"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="e9dd8-102">HOW TO：定義運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9dd8-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="e9dd8-103">如果您已定義類別或結構，您可以定義標準運算式的行為 (例如`*`， `<>`，或`And`) 當一或兩個運算元屬於您自己的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="e9dd8-104">標準的運算子定義為類別或結構中的運算子程序。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="e9dd8-105">必須是所有的運算子程序`Public` `Shared`。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="e9dd8-106">類別或結構上定義的運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9dd8-107">範例</span><span class="sxs-lookup"><span data-stu-id="e9dd8-107">Example</span></span>  
 <span data-ttu-id="e9dd8-108">下列範例會定義`+`結構的運算子稱為`height`。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="e9dd8-109">結構會使用以英呎和英吋為單位的高度。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="e9dd8-110">一*英吋*是 2.54 公分為單位，而另一個*步行*12 英吋。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="e9dd8-111">若要確保正規化的值 (英吋為單位 < 12.0)，建構函式會執行*模數*12 算術。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="e9dd8-112">`+`運算子使用建構函式來產生正規化的值。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="e9dd8-113">您可以測試結構`height`為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9dd8-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="e9dd8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9dd8-114">See also</span></span>

- [<span data-ttu-id="e9dd8-115">運算子程序</span><span class="sxs-lookup"><span data-stu-id="e9dd8-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e9dd8-116">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="e9dd8-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="e9dd8-117">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="e9dd8-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e9dd8-118">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="e9dd8-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="e9dd8-119">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="e9dd8-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="e9dd8-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="e9dd8-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="e9dd8-121">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="e9dd8-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e9dd8-122">Mod 運算子</span><span class="sxs-lookup"><span data-stu-id="e9dd8-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
