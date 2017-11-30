---
title: "如何：建立新的變數 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="f96a2-102">如何：建立新的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f96a2-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="f96a2-103">您建立的變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f96a2-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="f96a2-104">若要建立新變數</span><span class="sxs-lookup"><span data-stu-id="f96a2-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="f96a2-105">宣告中的變數`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f96a2-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="f96a2-106">包含變數的特性的規格，例如[私人](../../../../visual-basic/language-reference/modifiers/private.md)，[靜態](../../../../visual-basic/language-reference/modifiers/static.md)，[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)，或[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="f96a2-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="f96a2-107">如需詳細資訊，請參閱[宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="f96a2-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="f96a2-108">您不需要`Dim`關鍵字，如果您使用宣告中的其他關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f96a2-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="f96a2-109">變數的名稱，必須遵循與規格[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="f96a2-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rules and conventions.</span></span> <span data-ttu-id="f96a2-110">如需詳細資訊，請參閱[宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="f96a2-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="f96a2-111">在名稱後面加[為](../../../../visual-basic/language-reference/statements/as-clause.md)子句來指定變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f96a2-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="f96a2-112">如果您未指定的資料類型，它會使用預設值： `Object`。</span><span class="sxs-lookup"><span data-stu-id="f96a2-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="f96a2-113">請遵循`As`子句以等號 (`=`) 和變數的初始值與等號後面。</span><span class="sxs-lookup"><span data-stu-id="f96a2-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="f96a2-114">將指定的值指派給變數，它一次`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f96a2-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="f96a2-115">如果您未指定一個初始值，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會先進入包含的程式碼時，變數的資料類型的預設初始值`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f96a2-115">If you do not specify an initial value, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="f96a2-116">如果變數是參考類型，您可以建立其類別的執行個體包括[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字`As`子句。</span><span class="sxs-lookup"><span data-stu-id="f96a2-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="f96a2-117">如果您未使用`New`，變數的初始值會是[Nothing](../../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="f96a2-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f96a2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f96a2-118">See Also</span></span>  
 [<span data-ttu-id="f96a2-119">變數</span><span class="sxs-lookup"><span data-stu-id="f96a2-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="f96a2-120">變數宣告</span><span class="sxs-lookup"><span data-stu-id="f96a2-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="f96a2-121">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="f96a2-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="f96a2-122">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="f96a2-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="f96a2-123">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="f96a2-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="f96a2-124">陳述式</span><span class="sxs-lookup"><span data-stu-id="f96a2-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="f96a2-125">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="f96a2-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="f96a2-126">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="f96a2-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
