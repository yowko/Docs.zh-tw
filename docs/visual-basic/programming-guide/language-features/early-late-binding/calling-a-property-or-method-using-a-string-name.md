---
title: 使用字串名稱呼叫屬性或方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 76be426049489bb58e50878822c03fa5cd5cca8e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911642"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="003f5-102">使用字串名稱呼叫屬性或方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="003f5-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="003f5-103">在大部分情況下，您可以在設計階段探索的屬性和方法的物件和撰寫程式碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="003f5-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="003f5-104">不過，在某些情況下您可能不知道物件的屬性和方法事先，或者您可能只想讓使用者指定的屬性，或在執行階段執行方法的彈性。</span><span class="sxs-lookup"><span data-stu-id="003f5-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="003f5-105">CallByName 函式</span><span class="sxs-lookup"><span data-stu-id="003f5-105">CallByName Function</span></span>  
 <span data-ttu-id="003f5-106">比方說，假設用戶端應用程式所評估的使用者輸入傳遞至 COM 元件的運算子的運算式。</span><span class="sxs-lookup"><span data-stu-id="003f5-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="003f5-107">假設您要不斷地將新函式項目新增至需要新的運算子元件。</span><span class="sxs-lookup"><span data-stu-id="003f5-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="003f5-108">當您使用標準的物件存取技術時，您必須重新編譯，並重新發佈用戶端應用程式，才能將能夠使用新的運算子。</span><span class="sxs-lookup"><span data-stu-id="003f5-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="003f5-109">若要避免這個問題，您可以使用`CallByName`為字串，傳遞新的運算子，而不需要變更應用程式的函式。</span><span class="sxs-lookup"><span data-stu-id="003f5-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="003f5-110">`CallByName`函式可讓您使用在執行階段指定的屬性或方法的字串。</span><span class="sxs-lookup"><span data-stu-id="003f5-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="003f5-111">簽章`CallByName`函式看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="003f5-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="003f5-112">*結果* = `CallByName`(*物件*，*程序名稱*， *CallType*，*引數*（)）</span><span class="sxs-lookup"><span data-stu-id="003f5-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="003f5-113">第一個引數，*物件*，會使用您想要處理之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="003f5-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="003f5-114">*程序名稱*引數包含要叫用方法或屬性程序名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="003f5-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="003f5-115">*CallType*引數的常數，表示要叫用的程序的類型： 一種方法 (`Microsoft.VisualBasic.CallType.Method`)，讀取的屬性 (`Microsoft.VisualBasic.CallType.Get`)，或將屬性設定 (`Microsoft.VisualBasic.CallType.Set`)。</span><span class="sxs-lookup"><span data-stu-id="003f5-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="003f5-116">*引數*引數，這是選擇性的採用陣列型別的`Object`，其中包含的程序的任何引數。</span><span class="sxs-lookup"><span data-stu-id="003f5-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="003f5-117">您可以使用`CallByName`類別中目前的方案中，但通常可用來存取 COM 物件或物件從[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="003f5-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="003f5-118">假設您將加入包含類別，名為組件的參考`MathClass`，其中包含新的函式，名為`SquareRoot`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="003f5-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 <span data-ttu-id="003f5-119">您的應用程式可以使用文字方塊控制項，以將呼叫哪一種方法的控制項和其引數。</span><span class="sxs-lookup"><span data-stu-id="003f5-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="003f5-120">比方說，如果`TextBox1`包含要評估的運算式並`TextBox2`是用來輸入函式的名稱，您可以使用下列程式碼來叫用`SquareRoot`函式中的運算式上`TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="003f5-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 <span data-ttu-id="003f5-121">如果您在中輸入"64 」 `TextBox1`，「 SquareRoot 」 中的`TextBox2`，然後呼叫`CallMath`程序、 數字的平方根`TextBox1`評估。</span><span class="sxs-lookup"><span data-stu-id="003f5-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="003f5-122">此範例中的程式碼會叫用`SquareRoot`函式 （其採用字串，包含評估為必要的引數的運算式），並傳回"8"中`TextBox1`（64 平方根）。</span><span class="sxs-lookup"><span data-stu-id="003f5-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="003f5-123">當然，如果使用者輸入無效的字串中`TextBox2`，如果字串包含名稱的屬性，而不是方法，或如果此方法會有其他必要的引數，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="003f5-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="003f5-124">您必須加入強固的錯誤處理程式碼，當您使用`CallByName`預期會發生這些或其他任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="003f5-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="003f5-125">雖然`CallByName`函式可能會很有用，在某些情況下，您必須衡量其實用性，對效能的影響 — 使用`CallByName`叫用程序會稍微慢一點比晚期繫結呼叫。</span><span class="sxs-lookup"><span data-stu-id="003f5-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="003f5-126">如果您叫用會重複呼叫，例如在迴圈內的函式`CallByName`可能會造成嚴重影響效能。</span><span class="sxs-lookup"><span data-stu-id="003f5-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003f5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="003f5-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [<span data-ttu-id="003f5-128">決定物件類型</span><span class="sxs-lookup"><span data-stu-id="003f5-128">Determining Object Type</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
