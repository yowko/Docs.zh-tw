---
title: HOW TO：建立新的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 86236f7e6f4821cc45dfab80273d82b6f167fba8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823281"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="547b4-102">HOW TO：建立新的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="547b4-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="547b4-103">您建立的變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="547b4-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="547b4-104">若要建立新變數</span><span class="sxs-lookup"><span data-stu-id="547b4-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="547b4-105">宣告中的變數`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="547b4-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="547b4-106">包含變數的特性的規格，例如[私人](../../../../visual-basic/language-reference/modifiers/private.md)，[靜態](../../../../visual-basic/language-reference/modifiers/static.md)， [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)，或[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="547b4-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="547b4-107">如需詳細資訊，請參閱 <<c0> [ 宣告的項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="547b4-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="547b4-108">您不需要`Dim`關鍵字，如果您在宣告中使用其他關鍵字。</span><span class="sxs-lookup"><span data-stu-id="547b4-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="547b4-109">請依照與變數的名稱，它必須遵照 Visual Basic 規則和慣例規格。</span><span class="sxs-lookup"><span data-stu-id="547b4-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="547b4-110">如需詳細資訊，請參閱 <<c0> [ 宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="547b4-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="547b4-111">在名稱後面加[做為](../../../../visual-basic/language-reference/statements/as-clause.md)子句來指定變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="547b4-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="547b4-112">如果您未指定的資料類型，它會使用預設值： `Object`。</span><span class="sxs-lookup"><span data-stu-id="547b4-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="547b4-113">請遵循`As`子句以等號 (`=`) 並遵循等號，以變數的初始值。</span><span class="sxs-lookup"><span data-stu-id="547b4-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="547b4-114">Visual Basic 會指派給變數指定的值每次執行`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="547b4-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="547b4-115">如果您未指定一個初始值，Visual Basic 會指派變數的資料類型的預設初始值第一次進入包含的程式碼時`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="547b4-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="547b4-116">如果變數是參考型別，您可以建立其類別的執行個體包括[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)中的關鍵字`As`子句。</span><span class="sxs-lookup"><span data-stu-id="547b4-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="547b4-117">如果您不要使用`New`，變數的初始值會是[Nothing](../../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="547b4-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="547b4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="547b4-118">See also</span></span>

- [<span data-ttu-id="547b4-119">變數</span><span class="sxs-lookup"><span data-stu-id="547b4-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="547b4-120">變數宣告</span><span class="sxs-lookup"><span data-stu-id="547b4-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="547b4-121">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="547b4-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="547b4-122">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="547b4-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="547b4-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="547b4-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="547b4-124">陳述式</span><span class="sxs-lookup"><span data-stu-id="547b4-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="547b4-125">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="547b4-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="547b4-126">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="547b4-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
