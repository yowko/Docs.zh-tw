---
title: "依位置和名稱傳遞引數 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="4ccfb-102">依位置和名稱傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ccfb-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="4ccfb-103">當您呼叫`Sub`或`Function`程序中，您可以傳遞引數*依位置*— 在程序的定義中的出現順序，或您可以將其傳遞*依名稱*，而不考慮位置。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="4ccfb-104">當您依名稱傳遞引數時，您指定的引數的宣告名稱後接冒號和等號 (`:=`)，後面接著引數值。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="4ccfb-105">您可以提供以任何順序指定的引數。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="4ccfb-106">例如，下列`Sub`程序會採用三個引數：</span><span class="sxs-lookup"><span data-stu-id="4ccfb-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="4ccfb-107">當您呼叫此程序時，您可以提供的引數的位置、 名稱，或使用兩者的混合。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="4ccfb-108">依位置傳遞引數</span><span class="sxs-lookup"><span data-stu-id="4ccfb-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="4ccfb-109">您可以呼叫此程序`studentInfo`的引數依位置傳遞，並以逗號分隔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4ccfb-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="4ccfb-110">如果您省略選擇性引數位置引數清單中的，您必須保留其所在位置，請使用逗號。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="4ccfb-111">下列範例會呼叫`studentInfo`沒有`age`引數：</span><span class="sxs-lookup"><span data-stu-id="4ccfb-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="4ccfb-112">依名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="4ccfb-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="4ccfb-113">或者，您可以呼叫`studentInfo`依名稱傳遞引數時，也以逗號分隔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4ccfb-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="4ccfb-114">混合位置和名稱引數</span><span class="sxs-lookup"><span data-stu-id="4ccfb-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="4ccfb-115">您可以提供引數位置和名稱，在單一程序呼叫中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4ccfb-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="4ccfb-116">在上述範例中，沒有額外的逗號是為了保留位置省略`age`引數，因為`birth`依名稱傳遞。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="4ccfb-117">混合位置和名稱、 位置引數提供的引數時，必須放在第一次。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="4ccfb-118">一旦您依名稱提供引數，其餘的引數都必須依名稱。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="4ccfb-119">提供選擇性引數名稱</span><span class="sxs-lookup"><span data-stu-id="4ccfb-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="4ccfb-120">當您呼叫具有一個以上的選擇性引數的程序時，依名稱傳遞引數會特別有用。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="4ccfb-121">如果您依名稱提供引數，您不必用連續逗號來表示遺漏位置引數。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="4ccfb-122">依名稱傳遞引數也可讓您更輕鬆地追蹤您傳遞和哪些省略了哪些引數。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="4ccfb-123">依名稱提供引數的限制</span><span class="sxs-lookup"><span data-stu-id="4ccfb-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="4ccfb-124">您無法使用名稱來避免輸入必要的引數傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="4ccfb-125">您可以省略選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="4ccfb-126">您無法依名稱傳遞參數陣列。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="4ccfb-127">這是因為當您呼叫程序，提供了不定數量的參數陣列中，以逗號分隔的引數，編譯器無法將多個引數，與單一的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ccfb-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ccfb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ccfb-128">See Also</span></span>  
 [<span data-ttu-id="4ccfb-129">程序</span><span class="sxs-lookup"><span data-stu-id="4ccfb-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="4ccfb-130">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="4ccfb-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="4ccfb-131">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="4ccfb-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="4ccfb-132">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="4ccfb-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="4ccfb-133">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="4ccfb-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="4ccfb-134">參數陣列</span><span class="sxs-lookup"><span data-stu-id="4ccfb-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="4ccfb-135">Optional</span><span class="sxs-lookup"><span data-stu-id="4ccfb-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="4ccfb-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="4ccfb-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
