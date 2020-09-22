---
title: '\= 運算子'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 6e749e13c0427354db9e361538d4bef10b6c6b04
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873400"
---
# <a name="-operator"></a><span data-ttu-id="802e4-102">\\= 運算子</span><span class="sxs-lookup"><span data-stu-id="802e4-102">\\= Operator</span></span>

<span data-ttu-id="802e4-103">將變數或屬性的值除以運算式的值，並將整數結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="802e4-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="802e4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="802e4-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="802e4-105">組件</span><span class="sxs-lookup"><span data-stu-id="802e4-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="802e4-106">必要。</span><span class="sxs-lookup"><span data-stu-id="802e4-106">Required.</span></span> <span data-ttu-id="802e4-107">任何數值變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="802e4-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="802e4-108">必要。</span><span class="sxs-lookup"><span data-stu-id="802e4-108">Required.</span></span> <span data-ttu-id="802e4-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="802e4-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="802e4-110">備註</span><span class="sxs-lookup"><span data-stu-id="802e4-110">Remarks</span></span>  

 <span data-ttu-id="802e4-111">運算子左邊的元素 `\=` 可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="802e4-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="802e4-112">變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="802e4-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="802e4-113">運算子會將 `\=` 變數或屬性的值除以其右邊的值，然後將整數結果指派給左邊的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="802e4-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="802e4-114">如需整數除法的詳細資訊，請參閱 [\ 運算子 (Visual Basic) ](integer-division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="802e4-114">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="802e4-115">多載化</span><span class="sxs-lookup"><span data-stu-id="802e4-115">Overloading</span></span>  

 <span data-ttu-id="802e4-116">可以多載 `\` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="802e4-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="802e4-117">多載 `\` 運算子會影響運算子的行為 `\=` 。</span><span class="sxs-lookup"><span data-stu-id="802e4-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="802e4-118">如果您的程式碼在多載的 `\=` 類別或結構上使用 `\` ，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="802e4-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="802e4-119">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="802e4-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="802e4-120">範例</span><span class="sxs-lookup"><span data-stu-id="802e4-120">Example</span></span>  

 <span data-ttu-id="802e4-121">下列範例會使用 `\=` 運算子將一個變數除以 `Integer` 第二個變數，然後將整數結果指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="802e4-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="802e4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="802e4-122">See also</span></span>

- [<span data-ttu-id="802e4-123">\ 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="802e4-123">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="802e4-124">/= 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="802e4-124">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="802e4-125">指派運算子</span><span class="sxs-lookup"><span data-stu-id="802e4-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="802e4-126">算術運算子</span><span class="sxs-lookup"><span data-stu-id="802e4-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="802e4-127">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="802e4-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="802e4-128">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="802e4-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="802e4-129">陳述式</span><span class="sxs-lookup"><span data-stu-id="802e4-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
