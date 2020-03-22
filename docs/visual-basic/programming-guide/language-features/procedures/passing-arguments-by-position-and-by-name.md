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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400852"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="bca78-102">依位置和名稱傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bca78-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="bca78-103">調用`Sub`或`Function`過程時，可以*按位置*傳遞參數（按程序定義中顯示參數的順序）傳遞參數，也可以*按名稱*傳遞參數，而不考慮位置。</span><span class="sxs-lookup"><span data-stu-id="bca78-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="bca78-104">按名稱傳遞參數時，指定參數聲明的名稱後跟冒號和等號 （`:=`），後跟參數值。</span><span class="sxs-lookup"><span data-stu-id="bca78-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="bca78-105">您可以按任意順序提供具名引數。</span><span class="sxs-lookup"><span data-stu-id="bca78-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="bca78-106">例如，以下`Sub`過程採用三個參數：</span><span class="sxs-lookup"><span data-stu-id="bca78-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="bca78-107">調用此過程時，可以按位置、名稱或使用兩者的混合物提供參數。</span><span class="sxs-lookup"><span data-stu-id="bca78-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="bca78-108">按位置傳遞參數</span><span class="sxs-lookup"><span data-stu-id="bca78-108">Passing Arguments by Position</span></span>

<span data-ttu-id="bca78-109">可以調用`Display`該方法，其參數通過位置，並通過逗號分隔，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="bca78-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="bca78-110">如果在位置參數清單中省略可選參數，則必須使用逗號保留其位置。</span><span class="sxs-lookup"><span data-stu-id="bca78-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="bca78-111">下面的示例調用沒有`Display``age`參數的方法：</span><span class="sxs-lookup"><span data-stu-id="bca78-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="bca78-112">按名稱傳遞參數</span><span class="sxs-lookup"><span data-stu-id="bca78-112">Passing Arguments by Name</span></span>

<span data-ttu-id="bca78-113">或者，可以使用通過名稱`Display`傳遞的參數進行調用，也可以用逗號分隔，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="bca78-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="bca78-114">以這種方式按名稱傳遞參數在調用具有多個可選參數的過程時特別有用。</span><span class="sxs-lookup"><span data-stu-id="bca78-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="bca78-115">如果按名稱提供參數，則不必使用連續逗號來表示缺少的位置參數。</span><span class="sxs-lookup"><span data-stu-id="bca78-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="bca78-116">按名稱傳遞參數還便於跟蹤您傳遞的參數以及省略的參數。</span><span class="sxs-lookup"><span data-stu-id="bca78-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="bca78-117">按位置和名稱混合參數</span><span class="sxs-lookup"><span data-stu-id="bca78-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="bca78-118">您可以在單個程序呼叫中按位置和名稱提供參數，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="bca78-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="bca78-119">在前面的示例中，不需要額外的逗號來保留省略`age`的參數的位置，因為`birth`是按名稱傳遞的。</span><span class="sxs-lookup"><span data-stu-id="bca78-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="bca78-120">在 15.5 之前的 Visual Basic 版本中，當您通過位置和名稱的混合提供參數時，位置參數必須都放在第一位。</span><span class="sxs-lookup"><span data-stu-id="bca78-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="bca78-121">按名稱提供參數後，所有剩餘的參數都必須按名稱傳遞。</span><span class="sxs-lookup"><span data-stu-id="bca78-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="bca78-122">例如，對`Display`該方法的以下調用顯示編譯器錯誤[BC30241：具名引數預期](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="bca78-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="bca78-123">從 Visual Basic 15.5 開始，如果結束位置參數位於正確的位置，則位置參數可以遵循具名引數。</span><span class="sxs-lookup"><span data-stu-id="bca78-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="bca78-124">如果在 Visual Basic 15.5 下編譯，則對`Display`該方法的上一個調用將成功編譯，不再生成編譯器錯誤[BC30241](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="bca78-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="bca78-125">當您希望使用具名引數使代碼更具可讀性時，這種以任意順序混合和匹配具名引數和位置參數的能力特別有用。</span><span class="sxs-lookup"><span data-stu-id="bca78-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="bca78-126">例如，以下`Person`類建構函式需要兩個類型的`Person`參數，這兩個參數都可以。 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="bca78-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="bca78-127">使用混合命名和位置參數有助於在 和`father``mother`參數的值為`Nothing`時明確代碼的意圖：</span><span class="sxs-lookup"><span data-stu-id="bca78-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="bca78-128">要遵循具有具名引數的位置參數，必須向 Visual Basic 專案 （.vbproj）\*檔添加以下元素：</span><span class="sxs-lookup"><span data-stu-id="bca78-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="bca78-129">有關詳細資訊[，請參閱設置視覺化基礎語言版本](../../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="bca78-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="bca78-130">按名稱提供參數的限制</span><span class="sxs-lookup"><span data-stu-id="bca78-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="bca78-131">不能按名稱傳遞參數以避免輸入所需的參數。</span><span class="sxs-lookup"><span data-stu-id="bca78-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="bca78-132">只能省略可選參數。</span><span class="sxs-lookup"><span data-stu-id="bca78-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="bca78-133">不能按名稱傳遞參數陣列。</span><span class="sxs-lookup"><span data-stu-id="bca78-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="bca78-134">這是因為當您調用 過程時，為參數陣列提供無限數量的逗號分隔參數，並且編譯器不能將多個參數與單個名稱相關聯。</span><span class="sxs-lookup"><span data-stu-id="bca78-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="bca78-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bca78-135">See also</span></span>

- [<span data-ttu-id="bca78-136">程序</span><span class="sxs-lookup"><span data-stu-id="bca78-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bca78-137">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="bca78-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bca78-138">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="bca78-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="bca78-139">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="bca78-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bca78-140">可選參數</span><span class="sxs-lookup"><span data-stu-id="bca78-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="bca78-141">參數陣列</span><span class="sxs-lookup"><span data-stu-id="bca78-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="bca78-142">選</span><span class="sxs-lookup"><span data-stu-id="bca78-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="bca78-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="bca78-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
