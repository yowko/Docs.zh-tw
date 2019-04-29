---
title: 選擇性參數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 4ae2366552426af0107c8d7a35bb5368fe30c8a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791959"
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="951ae-102">選擇性參數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="951ae-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="951ae-103">您可以將程序參數指定為選擇項，當該程序被呼叫時就不必提供引數。</span><span class="sxs-lookup"><span data-stu-id="951ae-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="951ae-104">*選擇性參數*由`Optional`程序定義中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="951ae-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="951ae-105">可套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="951ae-105">The following rules apply:</span></span>  
  
- <span data-ttu-id="951ae-106">程序定義中的每一個選擇性參數都必須指定一個預設值。</span><span class="sxs-lookup"><span data-stu-id="951ae-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
- <span data-ttu-id="951ae-107">選擇性參數的預設值必須是常數運算式。</span><span class="sxs-lookup"><span data-stu-id="951ae-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
- <span data-ttu-id="951ae-108">在程序定義中，每一個跟在選擇性參數之後的參數也必須是選擇項。</span><span class="sxs-lookup"><span data-stu-id="951ae-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="951ae-109">以下的語法顯示具有選擇性參數的程序宣告：</span><span class="sxs-lookup"><span data-stu-id="951ae-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="951ae-110">以選擇性參數呼叫程序</span><span class="sxs-lookup"><span data-stu-id="951ae-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="951ae-111">當您以選擇性參數呼叫程序時，可以選擇是否提供引數。</span><span class="sxs-lookup"><span data-stu-id="951ae-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="951ae-112">如果不提供，則該程序會使用該參數所宣告的預設值。</span><span class="sxs-lookup"><span data-stu-id="951ae-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="951ae-113">當您省略引數清單中的一個或多個選擇性引數時，必須用連續逗號來標示它們的位置。</span><span class="sxs-lookup"><span data-stu-id="951ae-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="951ae-114">下列呼叫範例提供第一個和第四個引數，而不提供第二個或第三個引數：</span><span class="sxs-lookup"><span data-stu-id="951ae-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="951ae-115">下列範例會建立數個對 `MsgBox` 函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="951ae-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="951ae-116">`MsgBox` 會有一個必要參數和兩個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="951ae-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="951ae-117">第一個對 `MsgBox` 的呼叫會依照 `MsgBox` 定義的引數順序提供這三個引數。</span><span class="sxs-lookup"><span data-stu-id="951ae-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="951ae-118">第二個呼叫只會提供必要引數。</span><span class="sxs-lookup"><span data-stu-id="951ae-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="951ae-119">第三個和第四個呼叫會提供第一個和第三個引數。</span><span class="sxs-lookup"><span data-stu-id="951ae-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="951ae-120">第三個呼叫會依位置執行這個動作，第四個呼叫則會依名稱執行。</span><span class="sxs-lookup"><span data-stu-id="951ae-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="951ae-121">判斷是否有選擇性引數</span><span class="sxs-lookup"><span data-stu-id="951ae-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="951ae-122">程序在執行階段時無法偵測指定的引數是否已省略，或者呼叫程式碼已明確提供預設值。</span><span class="sxs-lookup"><span data-stu-id="951ae-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="951ae-123">如果您需要有所區別，可以將一個不常用的值設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="951ae-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="951ae-124">下列程序定義選擇性參數`office`，並為其預設值的測試`QJZ`，以查看是否在呼叫中將其省略：</span><span class="sxs-lookup"><span data-stu-id="951ae-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 <span data-ttu-id="951ae-125">如果選擇性參數是 `String` 之類的參考類型，您就可以用 `Nothing` 做為預設值，只要不是引數需要的值即可。</span><span class="sxs-lookup"><span data-stu-id="951ae-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="951ae-126">選擇性參數和多載化</span><span class="sxs-lookup"><span data-stu-id="951ae-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="951ae-127">另一個用選擇性參數定義程序的方式是使用多載化 (Overloading)。</span><span class="sxs-lookup"><span data-stu-id="951ae-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="951ae-128">如果您有一個選擇性參數，您可以定義程序的兩個多載版本，其中一個接受該參數，而另一個則不接受。</span><span class="sxs-lookup"><span data-stu-id="951ae-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="951ae-129">隨著選擇性參數數目的增加，這個方法會變得比較複雜。</span><span class="sxs-lookup"><span data-stu-id="951ae-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="951ae-130">但是，它的優點是可以完全確定呼叫程式是否提供每一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="951ae-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951ae-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="951ae-131">See also</span></span>

- [<span data-ttu-id="951ae-132">程序</span><span class="sxs-lookup"><span data-stu-id="951ae-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="951ae-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="951ae-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="951ae-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="951ae-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="951ae-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="951ae-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="951ae-136">參數陣列</span><span class="sxs-lookup"><span data-stu-id="951ae-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="951ae-137">程序多載化</span><span class="sxs-lookup"><span data-stu-id="951ae-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="951ae-138">Optional</span><span class="sxs-lookup"><span data-stu-id="951ae-138">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="951ae-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="951ae-139">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
