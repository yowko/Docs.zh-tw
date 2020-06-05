---
title: 如何：定義運算子
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
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388033"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="0338a-102">如何：定義運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0338a-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="0338a-103">如果您已定義類別或結構， `*` `<>` `And` 當其中一個或兩個運算元屬於您的類別或結構類型時，可以定義標準運算子的行為（例如、或）。</span><span class="sxs-lookup"><span data-stu-id="0338a-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="0338a-104">將標準運算子定義為類別或結構內的運算子程式。</span><span class="sxs-lookup"><span data-stu-id="0338a-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="0338a-105">所有的運算子程式都必須是 `Public` `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="0338a-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="0338a-106">在類別或結構上定義運算子*也稱為多*載運算子。</span><span class="sxs-lookup"><span data-stu-id="0338a-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0338a-107">範例</span><span class="sxs-lookup"><span data-stu-id="0338a-107">Example</span></span>  
 <span data-ttu-id="0338a-108">下列範例會定義 `+` 名為之結構的運算子 `height` 。</span><span class="sxs-lookup"><span data-stu-id="0338a-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="0338a-109">結構會使用以英尺和英寸測量的高度。</span><span class="sxs-lookup"><span data-stu-id="0338a-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="0338a-110">1*英寸*是2.54 釐米，而一*英尺*是12英寸。</span><span class="sxs-lookup"><span data-stu-id="0338a-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="0338a-111">為確保正規化的值（英寸 < 12.0），此函式會執行*模數*12 算數運算。</span><span class="sxs-lookup"><span data-stu-id="0338a-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="0338a-112">`+`運算子會使用此函數來產生正規化的值。</span><span class="sxs-lookup"><span data-stu-id="0338a-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="0338a-113">您可以使用下列程式碼來測試結構 `height` 。</span><span class="sxs-lookup"><span data-stu-id="0338a-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="0338a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0338a-114">See also</span></span>

- [<span data-ttu-id="0338a-115">運算子程序</span><span class="sxs-lookup"><span data-stu-id="0338a-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0338a-116">How to: Define a Conversion Operator</span><span class="sxs-lookup"><span data-stu-id="0338a-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="0338a-117">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="0338a-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="0338a-118">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="0338a-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="0338a-119">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="0338a-119">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="0338a-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0338a-120">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="0338a-121">作法：宣告結構</span><span class="sxs-lookup"><span data-stu-id="0338a-121">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="0338a-122">Mod 運算子</span><span class="sxs-lookup"><span data-stu-id="0338a-122">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
