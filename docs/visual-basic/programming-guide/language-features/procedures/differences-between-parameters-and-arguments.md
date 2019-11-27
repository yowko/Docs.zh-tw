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
ms.openlocfilehash: c4249dbf86bd1bfa7ef08e94059d2880333e9a92
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341367"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="463a3-102">參數和引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="463a3-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="463a3-103">在大部分情況下，程式必須有一些有關已呼叫它的情況的資訊。</span><span class="sxs-lookup"><span data-stu-id="463a3-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="463a3-104">執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="463a3-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="463a3-105">這項資訊是由您在呼叫它時傳遞給程式的變數、常數和運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="463a3-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="463a3-106">為了將此資訊傳達給程式，此程式會定義一個*參數*，而呼叫的程式碼會將*引數*傳遞給該參數。</span><span class="sxs-lookup"><span data-stu-id="463a3-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="463a3-107">您可以將參數視為停車空間，並將引數視為汽車。</span><span class="sxs-lookup"><span data-stu-id="463a3-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="463a3-108">就如同不同的汽車可以在停車空間中的不同時間靜止，呼叫程式碼可以在每次呼叫程式時，將不同的引數傳遞至相同的參數。</span><span class="sxs-lookup"><span data-stu-id="463a3-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="463a3-109">參數</span><span class="sxs-lookup"><span data-stu-id="463a3-109">Parameters</span></span>  
 <span data-ttu-id="463a3-110">*參數*代表當您呼叫它時，程式預期會傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="463a3-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="463a3-111">程式的宣告會定義其參數。</span><span class="sxs-lookup"><span data-stu-id="463a3-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="463a3-112">當您定義 `Function` 或 `Sub` 程式時，您會緊接在程式名稱後面的括弧中指定*參數清單*。</span><span class="sxs-lookup"><span data-stu-id="463a3-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="463a3-113">針對每個參數，您可以指定名稱、資料類型和傳遞機制（[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)）。</span><span class="sxs-lookup"><span data-stu-id="463a3-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="463a3-114">您也可以指出參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="463a3-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="463a3-115">這表示呼叫程式碼不需要傳遞值給它。</span><span class="sxs-lookup"><span data-stu-id="463a3-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="463a3-116">在程式中，每個參數的名稱都可做為*區域變數*。</span><span class="sxs-lookup"><span data-stu-id="463a3-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="463a3-117">使用參數名稱的方式與使用任何其他變數相同。</span><span class="sxs-lookup"><span data-stu-id="463a3-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="463a3-118">引數</span><span class="sxs-lookup"><span data-stu-id="463a3-118">Arguments</span></span>  
 <span data-ttu-id="463a3-119">*引數*代表當您呼叫程式時，傳遞給 procedure 參數的值。</span><span class="sxs-lookup"><span data-stu-id="463a3-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="463a3-120">呼叫程式碼會在呼叫程式時提供引數。</span><span class="sxs-lookup"><span data-stu-id="463a3-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="463a3-121">當您呼叫 `Function` 或 `Sub` 程式時，您會緊接在程式名稱後面的括弧中包含*引數清單*。</span><span class="sxs-lookup"><span data-stu-id="463a3-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="463a3-122">每個引數都會對應至清單中相同位置的參數。</span><span class="sxs-lookup"><span data-stu-id="463a3-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="463a3-123">相對於參數定義，引數沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="463a3-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="463a3-124">每個引數都是運算式，其中可以包含零個或多個變數、常數和常值。</span><span class="sxs-lookup"><span data-stu-id="463a3-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="463a3-125">已評估運算式的資料類型通常應該符合針對對應參數所定義的資料類型，而且在任何情況下都必須可轉換為參數類型。</span><span class="sxs-lookup"><span data-stu-id="463a3-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463a3-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="463a3-126">See also</span></span>

- [<span data-ttu-id="463a3-127">程序</span><span class="sxs-lookup"><span data-stu-id="463a3-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="463a3-128">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="463a3-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="463a3-129">函式程序</span><span class="sxs-lookup"><span data-stu-id="463a3-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="463a3-130">屬性程序</span><span class="sxs-lookup"><span data-stu-id="463a3-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="463a3-131">運算子程序</span><span class="sxs-lookup"><span data-stu-id="463a3-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="463a3-132">如何：定義程序的參數</span><span class="sxs-lookup"><span data-stu-id="463a3-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="463a3-133">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="463a3-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="463a3-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="463a3-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="463a3-135">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="463a3-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="463a3-136">程序多載化</span><span class="sxs-lookup"><span data-stu-id="463a3-136">Procedure Overloading</span></span>](./procedure-overloading.md)
