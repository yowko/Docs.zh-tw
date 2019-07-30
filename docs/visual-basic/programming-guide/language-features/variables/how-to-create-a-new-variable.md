---
title: 作法：建立新的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630894"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="c11aa-102">作法：建立新的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c11aa-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="c11aa-103">您可以使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)來建立變數。</span><span class="sxs-lookup"><span data-stu-id="c11aa-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="c11aa-104">若要建立新變數</span><span class="sxs-lookup"><span data-stu-id="c11aa-104">To create a new variable</span></span>

1. <span data-ttu-id="c11aa-105">在`Dim`語句中宣告變數。</span><span class="sxs-lookup"><span data-stu-id="c11aa-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="c11aa-106">包含變數特性的規格, 例如[私](../../../../visual-basic/language-reference/modifiers/private.md)用、[靜態](../../../../visual-basic/language-reference/modifiers/static.md)、[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)或[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="c11aa-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="c11aa-107">如需詳細資訊, 請參閱宣告的[元素特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="c11aa-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="c11aa-108">如果您在宣告中`Dim`使用其他關鍵字, 則不需要關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c11aa-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="c11aa-109">遵循具有變數名稱的規格, 這必須遵循 Visual Basic 規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="c11aa-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="c11aa-110">如需詳細資訊, 請參閱宣告的[元素名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c11aa-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="c11aa-111">請遵循名稱與[As](../../../../visual-basic/language-reference/statements/as-clause.md)子句, 以指定變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c11aa-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="c11aa-112">如果您未指定資料類型, 則會使用預設值: `Object`。</span><span class="sxs-lookup"><span data-stu-id="c11aa-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="c11aa-113">請在`As`子句後面加上等號`=`(), 並在等號後面加上變數的初始值。</span><span class="sxs-lookup"><span data-stu-id="c11aa-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="c11aa-114">Visual Basic 在每次執行`Dim`語句時, 將指定的值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="c11aa-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="c11aa-115">如果您未指定初始值, Visual Basic 會在第一次輸入包含`Dim`語句的程式碼時, 為變數的資料類型指派預設初始值。</span><span class="sxs-lookup"><span data-stu-id="c11aa-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="c11aa-116">如果變數是參考型別, 您可以在`As`子句中包含[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字, 以建立其類別的實例。</span><span class="sxs-lookup"><span data-stu-id="c11aa-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="c11aa-117">如果您不使用`New`, 則變數的初始值不是[任何](../../../../visual-basic/language-reference/nothing.md)值。</span><span class="sxs-lookup"><span data-stu-id="c11aa-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="c11aa-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c11aa-118">See also</span></span>

- [<span data-ttu-id="c11aa-119">變數</span><span class="sxs-lookup"><span data-stu-id="c11aa-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="c11aa-120">變數宣告</span><span class="sxs-lookup"><span data-stu-id="c11aa-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="c11aa-121">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="c11aa-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="c11aa-122">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="c11aa-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="c11aa-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="c11aa-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="c11aa-124">陳述式</span><span class="sxs-lookup"><span data-stu-id="c11aa-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="c11aa-125">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="c11aa-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="c11aa-126">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="c11aa-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
