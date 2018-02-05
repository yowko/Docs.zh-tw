---
title: "依位置和名稱傳遞引數 (Visual Basic)"
ms.custom: 
ms.date: 02/01/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f5e5a8da6a899d4920a25b250ca88b2a21f559
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="e93e1-102">依位置和名稱傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e93e1-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="e93e1-103">當您呼叫`Sub`或`Function`程序中，您可以傳遞引數*依位置*— 在程序的定義中的出現順序，或您可以將其傳遞*依名稱*，而不考慮位置。</span><span class="sxs-lookup"><span data-stu-id="e93e1-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="e93e1-104">當您依名稱傳遞引數時，您指定的引數的宣告名稱後接冒號和等號 (`:=`)，後面接著引數值。</span><span class="sxs-lookup"><span data-stu-id="e93e1-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="e93e1-105">您可以提供以任何順序指定的引數。</span><span class="sxs-lookup"><span data-stu-id="e93e1-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="e93e1-106">例如，下列`Sub`程序會採用三個引數：</span><span class="sxs-lookup"><span data-stu-id="e93e1-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="e93e1-107">當您呼叫此程序時，您可以提供的引數的位置、 名稱，或使用兩者的混合。</span><span class="sxs-lookup"><span data-stu-id="e93e1-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="e93e1-108">依位置傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e93e1-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="e93e1-109">您可以呼叫`Display`依位置傳遞的引數的方法，並以逗號分隔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e93e1-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="e93e1-110">如果您省略選擇性引數位置引數清單中的，您必須保留其所在位置，請使用逗號。</span><span class="sxs-lookup"><span data-stu-id="e93e1-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="e93e1-111">下列範例會呼叫`Display`方法，而不`age`引數：</span><span class="sxs-lookup"><span data-stu-id="e93e1-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="e93e1-112">依名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e93e1-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="e93e1-113">或者，您可以呼叫`Display`依名稱傳遞引數時，也以逗號分隔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e93e1-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="e93e1-114">當您呼叫具有一個以上的選擇性引數的程序時，在這種方式中依名稱傳遞引數會特別有用。</span><span class="sxs-lookup"><span data-stu-id="e93e1-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="e93e1-115">如果您依名稱提供引數，您不必用連續逗號來表示遺漏位置引數。</span><span class="sxs-lookup"><span data-stu-id="e93e1-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="e93e1-116">依名稱傳遞引數也可讓您更輕鬆地追蹤您傳遞和哪些省略了哪些引數。</span><span class="sxs-lookup"><span data-stu-id="e93e1-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="e93e1-117">混合位置和名稱引數</span><span class="sxs-lookup"><span data-stu-id="e93e1-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="e93e1-118">您可以提供引數位置和名稱，在單一程序呼叫中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e93e1-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="e93e1-119">在上述範例中，沒有額外的逗號是為了保留位置省略`age`引數，因為`birth`依名稱傳遞。</span><span class="sxs-lookup"><span data-stu-id="e93e1-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="e93e1-120">在 Visual Basic 的 15.5 之前的版本，提供引數位置和名稱、 位置引數的混合時，必須放在第一次。</span><span class="sxs-lookup"><span data-stu-id="e93e1-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="e93e1-121">一旦您依名稱提供引數，任何其餘引數必須全部是依名稱傳遞。</span><span class="sxs-lookup"><span data-stu-id="e93e1-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="e93e1-122">例如，下列呼叫`Display`方法會顯示編譯器錯誤[BC30241： 具名引數必須是](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="e93e1-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="e93e1-123">從 Visual Basic 15.5 開始，位置引數可以依照具名引數的結束位置的引數是否在正確的位置。</span><span class="sxs-lookup"><span data-stu-id="e93e1-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="e93e1-124">如果在 Visual Basic 15.5，上次呼叫底下編譯`Display`方法會編譯成功，並不會再產生編譯器錯誤[BC30241](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="e93e1-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="e93e1-125">當您想要使用具名引數，讓您的程式碼更容易閱讀，混合和比對具名和位置引數，依任何順序的功能是特別有用。</span><span class="sxs-lookup"><span data-stu-id="e93e1-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="e93e1-126">例如，下列`Person`類別建構函式需要兩個引數的型別`Person`，兩者都可以是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="e93e1-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="e93e1-127">使用混合的具名和位置引數可協助的程式碼意圖清除時的值`father`和`mother`引數是`Nothing`:</span><span class="sxs-lookup"><span data-stu-id="e93e1-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="e93e1-128">若要依照具有具名引數的位置引數，您必須將下列項目加入 Visual Basic 專案 (\*.vbproj) 檔案：</span><span class="sxs-lookup"><span data-stu-id="e93e1-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="e93e1-129">依名稱提供引數的限制</span><span class="sxs-lookup"><span data-stu-id="e93e1-129">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="e93e1-130">您無法使用名稱來避免輸入必要的引數傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="e93e1-130">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="e93e1-131">您可以省略選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="e93e1-131">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="e93e1-132">您無法依名稱傳遞參數陣列。</span><span class="sxs-lookup"><span data-stu-id="e93e1-132">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="e93e1-133">這是因為當您呼叫程序，提供了不定數量的參數陣列中，以逗號分隔的引數，編譯器無法將多個引數，與單一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e93e1-133">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93e1-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="e93e1-134">See Also</span></span>  
 [<span data-ttu-id="e93e1-135">程序</span><span class="sxs-lookup"><span data-stu-id="e93e1-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="e93e1-136">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="e93e1-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e93e1-137">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="e93e1-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="e93e1-138">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e93e1-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="e93e1-139">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="e93e1-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="e93e1-140">參數陣列</span><span class="sxs-lookup"><span data-stu-id="e93e1-140">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="e93e1-141">Optional</span><span class="sxs-lookup"><span data-stu-id="e93e1-141">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="e93e1-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="e93e1-142">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
