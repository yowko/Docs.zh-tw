---
title: 參數和引數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: 0ad9104f347205cebc6e078aac246a413c0d9b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057841"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="55424-102">參數和引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55424-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="55424-103">在大部分情況下，程式必須有一些有關呼叫它的情況的資訊。</span><span class="sxs-lookup"><span data-stu-id="55424-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="55424-104">執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="55424-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="55424-105">這項資訊是由您在呼叫過程中傳遞給程式的變數、常數和運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="55424-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="55424-106">為了將此資訊傳達給程式，程式會定義 *參數*，呼叫程式碼會將 *引數* 傳遞給該參數。</span><span class="sxs-lookup"><span data-stu-id="55424-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="55424-107">您可以將參數視為停車空間，而將引數視為汽車。</span><span class="sxs-lookup"><span data-stu-id="55424-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="55424-108">如同不同的汽車可以在不同時間的停車空間中駐留，呼叫程式碼可以在每次呼叫程式時，將不同的引數傳遞至相同的參數。</span><span class="sxs-lookup"><span data-stu-id="55424-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="55424-109">參數</span><span class="sxs-lookup"><span data-stu-id="55424-109">Parameters</span></span>  

 <span data-ttu-id="55424-110">*參數*代表程式要求您在呼叫時傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="55424-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="55424-111">程式的宣告會定義其參數。</span><span class="sxs-lookup"><span data-stu-id="55424-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="55424-112">當您定義或程式時 `Function` `Sub` ，您可以緊接在程式名稱後面的括弧中指定 *參數清單* 。</span><span class="sxs-lookup"><span data-stu-id="55424-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="55424-113">針對每個參數，您可以指定名稱、資料類型，以及 ([ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md)) 的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="55424-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="55424-114">您也可以指出參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="55424-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="55424-115">這表示呼叫程式碼不需要傳遞值給它。</span><span class="sxs-lookup"><span data-stu-id="55424-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="55424-116">每個參數的名稱會當做程式中的 *區域變數* 。</span><span class="sxs-lookup"><span data-stu-id="55424-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="55424-117">您可以使用參數名稱，就像使用任何其他變數一樣。</span><span class="sxs-lookup"><span data-stu-id="55424-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="55424-118">引數</span><span class="sxs-lookup"><span data-stu-id="55424-118">Arguments</span></span>  

 <span data-ttu-id="55424-119">*引數*代表當您呼叫程式時，您傳遞給程式參數的值。</span><span class="sxs-lookup"><span data-stu-id="55424-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="55424-120">呼叫程式碼會在呼叫程式時提供引數。</span><span class="sxs-lookup"><span data-stu-id="55424-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="55424-121">當您呼叫 `Function` 或 `Sub` 程式時，您會在程式名稱後面緊接著括弧中包含 *引數清單* 。</span><span class="sxs-lookup"><span data-stu-id="55424-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="55424-122">每個引數都對應至清單中相同位置的參數。</span><span class="sxs-lookup"><span data-stu-id="55424-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="55424-123">相對於參數定義，引數沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="55424-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="55424-124">每個引數都是一個運算式，它可以包含零或多個變數、常數和常值。</span><span class="sxs-lookup"><span data-stu-id="55424-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="55424-125">評估運算式的資料類型通常應該符合為對應參數定義的資料類型，而且在任何情況下，它必須可轉換為參數類型。</span><span class="sxs-lookup"><span data-stu-id="55424-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55424-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55424-126">See also</span></span>

- [<span data-ttu-id="55424-127">程序</span><span class="sxs-lookup"><span data-stu-id="55424-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="55424-128">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="55424-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="55424-129">Function 程序</span><span class="sxs-lookup"><span data-stu-id="55424-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="55424-130">屬性程序</span><span class="sxs-lookup"><span data-stu-id="55424-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="55424-131">運算子程序</span><span class="sxs-lookup"><span data-stu-id="55424-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="55424-132">如何：定義程序的參數</span><span class="sxs-lookup"><span data-stu-id="55424-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="55424-133">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="55424-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="55424-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="55424-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="55424-135">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="55424-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="55424-136">程序多載化</span><span class="sxs-lookup"><span data-stu-id="55424-136">Procedure Overloading</span></span>](./procedure-overloading.md)
