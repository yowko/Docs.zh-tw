---
title: 使用字串名稱呼叫屬性或方法
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
ms.openlocfilehash: 29072479db36f9f8a81ffd7f3f5b10208ebaa984
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410653"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="78494-102">使用字串名稱呼叫屬性或方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78494-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="78494-103">在大部分的情況下，您可以在設計階段探索物件的屬性和方法，並撰寫程式碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="78494-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="78494-104">不過，在某些情況下，您可能不會事先知道物件的屬性和方法，或者您可能只想要讓使用者在執行時間指定屬性或執行方法的彈性。</span><span class="sxs-lookup"><span data-stu-id="78494-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="78494-105">CallByName 函式</span><span class="sxs-lookup"><span data-stu-id="78494-105">CallByName Function</span></span>  
 <span data-ttu-id="78494-106">例如，假設用戶端應用程式會將運算子傳遞至 COM 元件，以評估使用者所輸入的運算式。</span><span class="sxs-lookup"><span data-stu-id="78494-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="78494-107">假設您持續將新的函式加入至需要新運算子的元件。</span><span class="sxs-lookup"><span data-stu-id="78494-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="78494-108">當您使用標準物件存取技術時，必須先重新編譯和轉散發用戶端應用程式，才能使用新的運算子。</span><span class="sxs-lookup"><span data-stu-id="78494-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="78494-109">若要避免這種情況，您可以使用函式 `CallByName` ，以字串形式傳遞新的運算子，而不需要變更應用程式。</span><span class="sxs-lookup"><span data-stu-id="78494-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="78494-110">函式 `CallByName` 可讓您在執行時間使用字串來指定屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="78494-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="78494-111">函數的簽 `CallByName` 章看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="78494-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="78494-112">*Result*  =  結果 `CallByName`（*Object*、*程式名稱*、 *CallType*、 *Arguments*（））</span><span class="sxs-lookup"><span data-stu-id="78494-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="78494-113">第一個引數（ *Object*）會採用您想要採取動作的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="78494-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="78494-114">*程式名稱*引數會採用包含要叫用之方法或屬性程式名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="78494-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="78494-115">*CallType*引數會採用常數，代表要叫用的程式類型：方法（ `Microsoft.VisualBasic.CallType.Method` ）、屬性讀取（ `Microsoft.VisualBasic.CallType.Get` ）或屬性集（ `Microsoft.VisualBasic.CallType.Set` ）。</span><span class="sxs-lookup"><span data-stu-id="78494-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="78494-116">*引數*引數是選擇性的，它會採用類型的陣列， `Object` 其中包含程式的任何引數。</span><span class="sxs-lookup"><span data-stu-id="78494-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="78494-117">您可以 `CallByName` 在目前的方案中使用和類別，但它最常用來從 .NET Framework 元件存取 COM 物件或物件。</span><span class="sxs-lookup"><span data-stu-id="78494-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from .NET Framework assemblies.</span></span>  
  
 <span data-ttu-id="78494-118">假設您新增的元件參考包含名為的類別 `MathClass` ，其中具有名為的新函式 `SquareRoot` ，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="78494-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 <span data-ttu-id="78494-119">您的應用程式可以使用文字方塊控制項來控制將呼叫的方法及其引數。</span><span class="sxs-lookup"><span data-stu-id="78494-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="78494-120">例如，如果 `TextBox1` 包含要評估的運算式，並且 `TextBox2` 用來輸入函數的名稱，您可以使用下列程式碼， `SquareRoot` 在的運算式上叫用函數 `TextBox1` ：</span><span class="sxs-lookup"><span data-stu-id="78494-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 <span data-ttu-id="78494-121">如果您在中輸入 "64"，在中輸入 " `TextBox1` SquareRoot"，然後 `TextBox2` 呼叫 `CallMath` 程式，則會評估中數位的 `TextBox1` 平方根。</span><span class="sxs-lookup"><span data-stu-id="78494-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="78494-122">範例中的程式碼會叫用函式 `SquareRoot` （它採用包含要評估為必要引數之運算式的字串），並在 `TextBox1` （64的平方根）中傳回 "8"。</span><span class="sxs-lookup"><span data-stu-id="78494-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="78494-123">當然，如果使用者在中輸入不正確字串 `TextBox2` ，如果字串包含屬性的名稱，而不是方法，或如果方法有額外的必要引數，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="78494-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="78494-124">當您使用 `CallByName` 來預期這些或任何其他錯誤時，您必須加入健全的錯誤處理常式代碼。</span><span class="sxs-lookup"><span data-stu-id="78494-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78494-125">雖然在 `CallByName` 某些情況下，函式可能很有用，但您必須對效能影響權衡其實用性，使用 `CallByName` 來叫用程式比晚期繫結呼叫稍微慢一點。</span><span class="sxs-lookup"><span data-stu-id="78494-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="78494-126">如果您叫用重複呼叫的函式，例如在迴圈內， `CallByName` 可能會對效能產生嚴重的影響。</span><span class="sxs-lookup"><span data-stu-id="78494-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78494-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78494-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [<span data-ttu-id="78494-128">決定物件類型</span><span class="sxs-lookup"><span data-stu-id="78494-128">Determining Object Type</span></span>](determining-object-type.md)
