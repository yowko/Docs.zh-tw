---
title: 參數和引數之間的差異 (Visual Basic)
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
ms.openlocfilehash: a69b956c7cffcc2a26916d6fc92f23dd4e2322d7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838972"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="2a7c4-102">參數和引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a7c4-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="2a7c4-103">在大部分情況下，程序必須有一些情況在其中呼叫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="2a7c4-104">執行重複或共用工作的程序會針對每個呼叫中使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="2a7c4-105">這項資訊是由變數、 常數和您傳遞至程序時呼叫它的運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="2a7c4-106">若要將此資訊傳達給程序，程序會定義*參數*，並呼叫程式碼傳遞*引數*至該參數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="2a7c4-107">您可以想像成停車參數，為汽車的引數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="2a7c4-108">就如同不同汽車可以 park 停車位空間中，在不同的時間，則呼叫端程式碼可以在每一次，它會呼叫程序傳遞不同的引數至相同的參數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="2a7c4-109">參數</span><span class="sxs-lookup"><span data-stu-id="2a7c4-109">Parameters</span></span>  
 <span data-ttu-id="2a7c4-110">A*參數*表示程序必須有您在呼叫它時傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="2a7c4-111">程序的宣告會定義其參數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="2a7c4-112">當您定義`Function`或是`Sub`程序中，指定*參數清單*緊接在程序名稱的括號括住。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="2a7c4-113">針對每個參數，指定名稱、 資料類型和傳遞機制 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="2a7c4-114">您也可以指定參數為選擇性。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="2a7c4-115">這表示呼叫端程式碼不需要值傳給它。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="2a7c4-116">每個參數的名稱做為*區域變數*程序中。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="2a7c4-117">使用參數名稱相同的方式使用任何其他變數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="2a7c4-118">引數</span><span class="sxs-lookup"><span data-stu-id="2a7c4-118">Arguments</span></span>  
 <span data-ttu-id="2a7c4-119">*引數*表示當您呼叫程序時，您傳遞至程序參數的值。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="2a7c4-120">呼叫程序時，呼叫程式碼會提供引數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="2a7c4-121">當您呼叫`Function`或是`Sub`程序，包括*引數清單*緊接在程序名稱的括號括住。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="2a7c4-122">每個引數會對應至清單中的相同位置中的參數。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="2a7c4-123">相較於參數定義引數不會有名稱。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="2a7c4-124">每個引數是運算式，其中可以包含零或多個變數、 常數和常值。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="2a7c4-125">評估的運算式的資料類型通常應該符合定義之對應參數的資料類型，並在任何情況下，都必須是將它轉換成參數類型。</span><span class="sxs-lookup"><span data-stu-id="2a7c4-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7c4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a7c4-126">See also</span></span>

- [<span data-ttu-id="2a7c4-127">程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2a7c4-128">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="2a7c4-129">函式程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="2a7c4-130">屬性程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2a7c4-131">運算子程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2a7c4-132">如何：如需程序來定義參數</span><span class="sxs-lookup"><span data-stu-id="2a7c4-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="2a7c4-133">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="2a7c4-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="2a7c4-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="2a7c4-135">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="2a7c4-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="2a7c4-136">程序多載化</span><span class="sxs-lookup"><span data-stu-id="2a7c4-136">Procedure Overloading</span></span>](./procedure-overloading.md)
