---
title: "如何：定義程序的參數 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="95f27-102">如何：定義程序的參數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95f27-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="95f27-103">A*參數*允許將值傳遞至程序呼叫它時，如果呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="95f27-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="95f27-104">您宣告一個變數，指定其名稱和資料類型的相同方式宣告的程序的每個參數。</span><span class="sxs-lookup"><span data-stu-id="95f27-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="95f27-105">您也可以指定傳遞機制，以及參數是否為選擇性。</span><span class="sxs-lookup"><span data-stu-id="95f27-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="95f27-106">如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="95f27-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="95f27-107">若要定義程序參數</span><span class="sxs-lookup"><span data-stu-id="95f27-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="95f27-108">在程序宣告中，新增至程序的參數清單中，將其與其他參數逗點分隔的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="95f27-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="95f27-109">決定參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="95f27-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="95f27-110">參數名稱之後加`As`子句來指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="95f27-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="95f27-111">決定您想要用於參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="95f27-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="95f27-112">通常參數傳值方式傳遞，除非您想要能夠變更它的值，呼叫程式碼中的程序。</span><span class="sxs-lookup"><span data-stu-id="95f27-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="95f27-113">參數名稱前加[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)指定的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="95f27-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="95f27-114">如需詳細資訊，請參閱[差異之間傳遞引數的值和依參考](./differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="95f27-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="95f27-115">如果參數是選擇性的在之前的傳遞機制，與[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)並遵循參數資料類型，以等號 (`=`) 和預設值。</span><span class="sxs-lookup"><span data-stu-id="95f27-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="95f27-116">下列範例會定義外框的`Sub`具有三個參數的程序。</span><span class="sxs-lookup"><span data-stu-id="95f27-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="95f27-117">前兩個所需和第三個是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="95f27-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="95f27-118">參數宣告會以逗號分隔的參數清單中。</span><span class="sxs-lookup"><span data-stu-id="95f27-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     <span data-ttu-id="95f27-119">第一個參數接受`customer`物件，和`updateCustomer`可以直接更新變數傳遞給`c`因為引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="95f27-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="95f27-120">此程序無法變更最後兩個引數的值，因為它們會傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="95f27-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="95f27-121">如果呼叫程式碼並不提供的值`level`參數，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]將其設為預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="95f27-121">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="95f27-122">如果類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off`、`As`子句是選擇性的當您定義的參數。</span><span class="sxs-lookup"><span data-stu-id="95f27-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="95f27-123">不過，如果任何一個參數使用`As`子句，全部都必須使用它。</span><span class="sxs-lookup"><span data-stu-id="95f27-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="95f27-124">類型檢查參數是否`On`、`As`子句是必要的每個參數定義。</span><span class="sxs-lookup"><span data-stu-id="95f27-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="95f27-125">指定資料類型的所有程式設計項目稱為*強型別*。</span><span class="sxs-lookup"><span data-stu-id="95f27-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="95f27-126">當您將`Option Strict On`，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會強制執行強式類型。</span><span class="sxs-lookup"><span data-stu-id="95f27-126">When you set `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforces strong typing.</span></span> <span data-ttu-id="95f27-127">這強烈建議使用，原因如下：</span><span class="sxs-lookup"><span data-stu-id="95f27-127">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="95f27-128">它可讓您的變數和參數的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="95f27-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="95f27-129">這可讓您查看其屬性和其他成員，當您輸入程式碼中。</span><span class="sxs-lookup"><span data-stu-id="95f27-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="95f27-130">它可讓編譯器執行類型檢查。</span><span class="sxs-lookup"><span data-stu-id="95f27-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="95f27-131">這有助於 catch 陳述式可在執行階段因為例如溢位錯誤而失敗。</span><span class="sxs-lookup"><span data-stu-id="95f27-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="95f27-132">它也會對方法的呼叫攔截不支援它們的物件。</span><span class="sxs-lookup"><span data-stu-id="95f27-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="95f27-133">這樣可以更快地執行您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="95f27-133">It results in faster execution of your code.</span></span> <span data-ttu-id="95f27-134">其中一個原因是，如果您未指定資料類型的程式設計項目，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器將其指派`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="95f27-134">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="95f27-135">可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。</span><span class="sxs-lookup"><span data-stu-id="95f27-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f27-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f27-136">See Also</span></span>  
 [<span data-ttu-id="95f27-137">程序</span><span class="sxs-lookup"><span data-stu-id="95f27-137">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="95f27-138">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="95f27-138">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="95f27-139">函式程序</span><span class="sxs-lookup"><span data-stu-id="95f27-139">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="95f27-140">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="95f27-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="95f27-141">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="95f27-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="95f27-142">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="95f27-142">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="95f27-143">程序多載化</span><span class="sxs-lookup"><span data-stu-id="95f27-143">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="95f27-144">物件和類別</span><span class="sxs-lookup"><span data-stu-id="95f27-144">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="95f27-145">物件導向程式設計</span><span class="sxs-lookup"><span data-stu-id="95f27-145">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
