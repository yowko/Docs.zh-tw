---
title: 如何：定義程序的參數
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 73b53dcf7cd732af1a4f1d23cd0d3b9ef5b5529b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087436"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="90f41-102">如何：定義程序的參數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90f41-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>

<span data-ttu-id="90f41-103">*參數*可讓呼叫程式碼在呼叫程式碼時，將值傳遞給程式。</span><span class="sxs-lookup"><span data-stu-id="90f41-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="90f41-104">您可以用宣告變數的相同方式來宣告程式的每個參數，並指定其名稱和資料類型。</span><span class="sxs-lookup"><span data-stu-id="90f41-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="90f41-105">您也可以指定傳遞機制，以及參數是否為選擇性。</span><span class="sxs-lookup"><span data-stu-id="90f41-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="90f41-106">如需詳細資訊，請參閱程式 [參數和引數](./procedure-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="90f41-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="90f41-107">若要定義 procedure 參數</span><span class="sxs-lookup"><span data-stu-id="90f41-107">To define a procedure parameter</span></span>  
  
1. <span data-ttu-id="90f41-108">在程式宣告中，將參數名稱新增至程式的參數清單中，並以逗號分隔不同的參數。</span><span class="sxs-lookup"><span data-stu-id="90f41-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2. <span data-ttu-id="90f41-109">決定參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="90f41-109">Decide the data type of the parameter.</span></span>  
  
3. <span data-ttu-id="90f41-110">在參數名稱後面加上 `As` 子句，以指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="90f41-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4. <span data-ttu-id="90f41-111">決定您要用於參數的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="90f41-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="90f41-112">通常您會以傳值方式傳遞參數，除非您希望程式能夠在呼叫程式碼中變更其值。</span><span class="sxs-lookup"><span data-stu-id="90f41-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5. <span data-ttu-id="90f41-113">在參數名稱前面加上 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) ，以指定傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="90f41-113">Precede the parameter name with [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="90f41-114">如需詳細資訊，請參閱以 [傳值方式傳遞引數和傳址方式之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="90f41-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6. <span data-ttu-id="90f41-115">如果參數是選擇性的，請在傳遞機制之前加上 [選擇性](../../../language-reference/modifiers/optional.md) ，並遵循具有等號 (`=`) 和預設值的參數資料類型。</span><span class="sxs-lookup"><span data-stu-id="90f41-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="90f41-116">下列範例會 `Sub` 使用三個參數來定義程式的外框。</span><span class="sxs-lookup"><span data-stu-id="90f41-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="90f41-117">前兩個是必要的，第三個則是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="90f41-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="90f41-118">參數宣告在參數清單中以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="90f41-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     <span data-ttu-id="90f41-119">第一個參數會接受 `customer` 物件，而且 `updateCustomer` 可以直接更新傳遞給的變數， `c` 因為引數是以 [ByRef](../../../language-reference/modifiers/byref.md)傳遞。</span><span class="sxs-lookup"><span data-stu-id="90f41-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="90f41-120">程式無法變更最後兩個引數的值，因為這些引數會傳遞給 [ByVal](../../../language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="90f41-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="90f41-121">如果呼叫程式碼未提供參數的值 `level` ，Visual Basic 會將它設定為預設值0。</span><span class="sxs-lookup"><span data-stu-id="90f41-121">If the calling code does not supply a value for the `level` parameter, Visual Basic sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="90f41-122">如果類型檢查參數 ([Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)) 是 `Off` ，則 `As` 當您定義參數時，子句是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="90f41-122">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="90f41-123">但是，如果有任何一個參數使用 `As` 子句，則所有參數都必須使用子句。</span><span class="sxs-lookup"><span data-stu-id="90f41-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="90f41-124">如果類型檢查參數是 `On` ，則 `As` 每個參數定義都需要子句。</span><span class="sxs-lookup"><span data-stu-id="90f41-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="90f41-125">指定所有程式設計專案的資料類型稱為 *強*型別。</span><span class="sxs-lookup"><span data-stu-id="90f41-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="90f41-126">當您設定時 `Option Strict On` ，Visual Basic 會強制執行強式類型。</span><span class="sxs-lookup"><span data-stu-id="90f41-126">When you set `Option Strict On`, Visual Basic enforces strong typing.</span></span> <span data-ttu-id="90f41-127">強烈建議您這麼做，原因如下：</span><span class="sxs-lookup"><span data-stu-id="90f41-127">This is strongly recommended, for the following reasons:</span></span>  
  
    - <span data-ttu-id="90f41-128">它可支援您的變數和參數的 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="90f41-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="90f41-129">當您在程式碼中輸入時，這可讓您查看其屬性和其他成員。</span><span class="sxs-lookup"><span data-stu-id="90f41-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    - <span data-ttu-id="90f41-130">它可讓編譯器執行類型檢查。</span><span class="sxs-lookup"><span data-stu-id="90f41-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="90f41-131">這有助於攔截在執行時間可能因為溢位之類的錯誤而失敗的語句。</span><span class="sxs-lookup"><span data-stu-id="90f41-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="90f41-132">它也會攔截對不支援它們之物件的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="90f41-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    - <span data-ttu-id="90f41-133">這會導致程式碼的執行速度更快。</span><span class="sxs-lookup"><span data-stu-id="90f41-133">It results in faster execution of your code.</span></span> <span data-ttu-id="90f41-134">其中一個原因是，如果您沒有指定程式設計專案的資料類型，Visual Basic 編譯器會為它指派 `Object` 型別。</span><span class="sxs-lookup"><span data-stu-id="90f41-134">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="90f41-135">您已編譯的程式碼可能必須在 `Object` 和其他資料類型之間來回轉換，以降低效能。</span><span class="sxs-lookup"><span data-stu-id="90f41-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f41-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90f41-136">See also</span></span>

- [<span data-ttu-id="90f41-137">程序</span><span class="sxs-lookup"><span data-stu-id="90f41-137">Procedures</span></span>](./index.md)
- [<span data-ttu-id="90f41-138">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="90f41-138">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="90f41-139">Function 程序</span><span class="sxs-lookup"><span data-stu-id="90f41-139">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="90f41-140">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="90f41-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="90f41-141">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="90f41-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="90f41-142">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="90f41-142">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="90f41-143">程序多載化</span><span class="sxs-lookup"><span data-stu-id="90f41-143">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="90f41-144">物件和類別</span><span class="sxs-lookup"><span data-stu-id="90f41-144">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="90f41-145">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90f41-145">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
