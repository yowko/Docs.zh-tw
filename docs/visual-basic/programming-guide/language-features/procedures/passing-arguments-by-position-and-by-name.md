---
title: 依位置和名稱傳遞引數
ms.date: 02/01/2018
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
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352612"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="ddc3f-102">依位置和名稱傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddc3f-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="ddc3f-103">當您呼叫 `Sub` 或 `Function` 程式時，您可以*依位置*傳遞引數（以它們出現在程式定義中的順序），也可以*依名稱*傳遞它們，而不考慮位置。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="ddc3f-104">當您依名稱傳遞引數時，您可以指定引數的宣告名稱，後面接著冒號和等號（`:=`），後面接著引數值。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="ddc3f-105">您可以依任何順序提供具名引數。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="ddc3f-106">例如，下列 `Sub` 程式會採用三個引數：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="ddc3f-107">當您呼叫此程式時，您可以依位置、名稱或混合使用兩者來提供引數。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="ddc3f-108">依位置傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ddc3f-108">Passing Arguments by Position</span></span>

<span data-ttu-id="ddc3f-109">您可以呼叫 `Display` 方法，其其引數是由位置傳遞，並以逗號分隔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="ddc3f-110">如果您省略位置引數清單中的選擇性引數，則必須使用逗號來保存其位置。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="ddc3f-111">下列範例會呼叫不含 `age` 引數的 `Display` 方法：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="ddc3f-112">依名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ddc3f-112">Passing Arguments by Name</span></span>

<span data-ttu-id="ddc3f-113">或者，您可以使用以名稱傳遞的引數（也以逗號分隔）來呼叫 `Display`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="ddc3f-114">當您呼叫具有多個選擇性引數的程式時，以這種方式依名稱傳遞引數特別有用。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="ddc3f-115">如果您依名稱提供引數，則不需要使用連續的逗號來表示遺漏的位置引數。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="ddc3f-116">以名稱傳遞引數也能讓您更輕鬆地追蹤您要傳遞的引數，以及您要省略哪一個。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="ddc3f-117">依位置和名稱來混合引數</span><span class="sxs-lookup"><span data-stu-id="ddc3f-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="ddc3f-118">您可以在單一程序呼叫中，依位置和名稱提供引數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="ddc3f-119">在上述範例中，不需要額外的逗號來保存省略之 `age` 引數的位置，因為 `birth` 是以名稱傳遞。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="ddc3f-120">在15.5 之前的 Visual Basic 版本中，當您以位置和名稱的混合來提供引數時，位置引數必須全部排在最前面。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="ddc3f-121">當您依名稱提供引數之後，所有剩餘的引數都必須以名稱傳遞。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="ddc3f-122">例如，下列對 `Display` 方法的呼叫會顯示編譯器錯誤[BC30241：預期的具名引數](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="ddc3f-123">從 Visual Basic 15.5 開始，如果結束位置引數位於正確的位置，位置引數就可以跟隨具名引數。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="ddc3f-124">如果在 Visual Basic 15.5 下編譯，則先前對 `Display` 方法的呼叫會編譯成功，且不再產生編譯器錯誤[BC30241](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="ddc3f-125">當您想要使用具名引數，讓程式碼更容易閱讀時，這項混合和比對名稱和位置引數的功能特別有用。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="ddc3f-126">例如，下列 `Person` 類別的函式需要 `Person`類型的兩個引數，兩者都可以 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="ddc3f-127">當 `father` 和 `mother` 引數的值 `Nothing`時，使用混合名稱和位置引數有助於讓程式碼的意圖清楚明瞭：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="ddc3f-128">若要遵循具有具名引數的位置引數，您必須將下列專案加入至您的 Visual Basic 專案（\*. vbproj）檔案：</span><span class="sxs-lookup"><span data-stu-id="ddc3f-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="ddc3f-129">如需詳細資訊，請參閱[設定 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="ddc3f-130">依名稱提供引數的限制</span><span class="sxs-lookup"><span data-stu-id="ddc3f-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="ddc3f-131">您無法依名稱傳遞引數，以避免輸入必要的引數。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="ddc3f-132">您只能省略選擇性的引數。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="ddc3f-133">您無法依名稱傳遞參數陣列。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="ddc3f-134">這是因為當您呼叫程式時，會為參數陣列提供不限數目的逗點分隔引數，而且編譯器無法將多個引數與單一名稱建立關聯。</span><span class="sxs-lookup"><span data-stu-id="ddc3f-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddc3f-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddc3f-135">See also</span></span>

- [<span data-ttu-id="ddc3f-136">程序</span><span class="sxs-lookup"><span data-stu-id="ddc3f-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ddc3f-137">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="ddc3f-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ddc3f-138">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="ddc3f-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="ddc3f-139">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ddc3f-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="ddc3f-140">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="ddc3f-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="ddc3f-141">參數陣列</span><span class="sxs-lookup"><span data-stu-id="ddc3f-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="ddc3f-142">Optional</span><span class="sxs-lookup"><span data-stu-id="ddc3f-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="ddc3f-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="ddc3f-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
