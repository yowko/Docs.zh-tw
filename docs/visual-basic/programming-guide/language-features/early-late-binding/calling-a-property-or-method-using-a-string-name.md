---
title: "呼叫屬性或方法使用字串名稱 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- passing operators
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls, strings
- methods [Visual Basic], calling with string names
- calling methods, string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6de5e655b3d4d42283b81507d7f08e0eb0b9424d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="5e616-102">使用字串名稱呼叫屬性或方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e616-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="5e616-103">在大部分情況下，可以在設計階段探索的屬性和方法的物件，並撰寫程式碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="5e616-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="5e616-104">不過，在某些情況下您可能不知道物件的屬性和方法的相關事先，或者您可能只想讓使用者指定的屬性，或在執行階段執行方法的彈性。</span><span class="sxs-lookup"><span data-stu-id="5e616-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="5e616-105">CallByName 函式</span><span class="sxs-lookup"><span data-stu-id="5e616-105">CallByName Function</span></span>  
 <span data-ttu-id="5e616-106">例如，假設用戶端應用程式評估使用者輸入傳遞至 COM 元件的運算子的運算式。</span><span class="sxs-lookup"><span data-stu-id="5e616-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="5e616-107">假設您經常要將新函式需要新的運算子的元件。</span><span class="sxs-lookup"><span data-stu-id="5e616-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="5e616-108">當您使用標準的物件存取方法時，您必須重新編譯並重新發佈用戶端應用程式，才能夠使用新的運算子。</span><span class="sxs-lookup"><span data-stu-id="5e616-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="5e616-109">若要避免這個問題，您可以使用`CallByName`而不需要變更應用程式將新運算子傳遞為字串，函式。</span><span class="sxs-lookup"><span data-stu-id="5e616-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="5e616-110">`CallByName`函式可讓您指定的屬性或方法，在執行階段使用的字串。</span><span class="sxs-lookup"><span data-stu-id="5e616-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="5e616-111">簽章`CallByName`函式看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="5e616-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="5e616-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span><span class="sxs-lookup"><span data-stu-id="5e616-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="5e616-113">第一個引數，*物件*，會想要作用的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="5e616-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="5e616-114">*m e*引數會接受字串，包含要叫用方法或屬性程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e616-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="5e616-115">*CallType*引數為常數，表示叫用的程序的類型︰ 一種方法 (`Microsoft.VisualBasic.CallType.Method`)，讀取屬性 (`Microsoft.VisualBasic.CallType.Get`)，或將屬性設定 (`Microsoft.VisualBasic.CallType.Set`)。</span><span class="sxs-lookup"><span data-stu-id="5e616-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="5e616-116">*引數*引數是選擇性的會採用型別的陣列`Object`，其中包含的程序的任何引數。</span><span class="sxs-lookup"><span data-stu-id="5e616-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="5e616-117">您可以使用`CallByName`中目前的方案，但它的類別最常用來存取 COM 物件或物件從[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="5e616-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="5e616-118">假設您將加入包含名為的類別的組件的參考`MathClass`，其具有名為的新函數`SquareRoot`，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="5e616-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 <span data-ttu-id="5e616-119">[!code-vb[VbVbalrOOP #&53;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e616-119">[!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]</span></span>  
  
 <span data-ttu-id="5e616-120">您的應用程式可以使用文字方塊控制項，以控制將要呼叫哪一種方法和其引數。</span><span class="sxs-lookup"><span data-stu-id="5e616-120">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="5e616-121">例如，如果`TextBox1`其中包含要評估的運算式和`TextBox2`是用來輸入函式的名稱，您可以使用下列程式碼來叫用`SquareRoot`函式之運算式上的`TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="5e616-121">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 <span data-ttu-id="5e616-122">[!code-vb[VbVbalrOOP #&54;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e616-122">[!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]</span></span>  
  
 <span data-ttu-id="5e616-123">如果您在輸入"64" `TextBox1`，「 SquareRoot 」 在`TextBox2`，然後呼叫`CallMath`程序、 數字的平方根`TextBox1`評估。</span><span class="sxs-lookup"><span data-stu-id="5e616-123">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="5e616-124">此範例中的程式碼會叫用`SquareRoot`函式 （這是一個字串，包含評估為必要的引數的運算式），並傳回"8"中`TextBox1`（64 平方根）。</span><span class="sxs-lookup"><span data-stu-id="5e616-124">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="5e616-125">當然，如果使用者輸入無效的字串中`TextBox2`，如果字串包含而不是一種方法，屬性的名稱，或如果方法具有其他必要的引數，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e616-125">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="5e616-126">您必須加入強固的錯誤處理程式碼，當您使用`CallByName`預期會發生這些或其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e616-126">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e616-127">雖然`CallByName`函式可能會很有用，在某些情況下，您必須衡量效能影響針對其可用性 — 使用`CallByName`叫用程序會稍微慢一點比晚期繫結呼叫。</span><span class="sxs-lookup"><span data-stu-id="5e616-127">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="5e616-128">如果您叫用的函式會重複呼叫，例如在迴圈內`CallByName`可能會嚴重影響效能。</span><span class="sxs-lookup"><span data-stu-id="5e616-128">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e616-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e616-129">See Also</span></span>  
 <span data-ttu-id="5e616-130"><xref:Microsoft.VisualBasic.Interaction.CallByName%2A></xref:Microsoft.VisualBasic.Interaction.CallByName%2A></span><span class="sxs-lookup"><span data-stu-id="5e616-130"><xref:Microsoft.VisualBasic.Interaction.CallByName%2A></span></span>   
<span data-ttu-id="5e616-131"> [決定物件類型](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)</span><span class="sxs-lookup"><span data-stu-id="5e616-131"> [Determining Object Type](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)</span></span>
