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
ms.openlocfilehash: 9f28548c27545d94dde38cef3e9c56f98a69b259
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086084"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="46ce0-102">使用字串名稱呼叫屬性或方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46ce0-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>

<span data-ttu-id="46ce0-103">在大部分的情況下，您可以在設計階段探索物件的屬性和方法，並撰寫程式碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="46ce0-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="46ce0-104">不過，在某些情況下，您可能不會事先知道物件的屬性和方法，或者您可能只想要讓使用者在執行時間指定屬性或執行方法的彈性。</span><span class="sxs-lookup"><span data-stu-id="46ce0-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="46ce0-105">CallByName 函式</span><span class="sxs-lookup"><span data-stu-id="46ce0-105">CallByName Function</span></span>  

 <span data-ttu-id="46ce0-106">例如，假設用戶端應用程式會藉由將運算子傳遞給 COM 元件，來評估使用者所輸入的運算式。</span><span class="sxs-lookup"><span data-stu-id="46ce0-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="46ce0-107">假設您不斷地將新的函式加入需要新操作員的元件中。</span><span class="sxs-lookup"><span data-stu-id="46ce0-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="46ce0-108">當您使用標準物件存取技術時，您必須先重新編譯和轉散發用戶端應用程式，才能使用新的操作員。</span><span class="sxs-lookup"><span data-stu-id="46ce0-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="46ce0-109">若要避免這種情況，您可以使用函式 `CallByName` 以字串的形式傳遞新的運算子，而不需要變更應用程式。</span><span class="sxs-lookup"><span data-stu-id="46ce0-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="46ce0-110">`CallByName`函數可讓您在執行時間使用字串來指定屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="46ce0-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="46ce0-111">函數的簽 `CallByName` 章看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="46ce0-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="46ce0-112">*Result*  =  結果 `CallByName` (*物件*、*程式名稱*、 *CallType*、*引數* ( # A2 # A3</span><span class="sxs-lookup"><span data-stu-id="46ce0-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="46ce0-113">第一個引數（ *Object*）接受您想要採取動作的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="46ce0-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="46ce0-114">*程式名稱*引數會採用包含要叫用之方法或屬性程式名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="46ce0-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="46ce0-115">*CallType*引數會使用常數來表示要叫用的程式類型：方法 (`Microsoft.VisualBasic.CallType.Method`) 、屬性讀取 (`Microsoft.VisualBasic.CallType.Get`) 或屬性集 (`Microsoft.VisualBasic.CallType.Set`) 。</span><span class="sxs-lookup"><span data-stu-id="46ce0-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="46ce0-116">*引數*引數是選擇性的，會採用類型的陣列， `Object` 其中包含程式的任何引數。</span><span class="sxs-lookup"><span data-stu-id="46ce0-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="46ce0-117">您可以使用 `CallByName` 與目前方案中的類別，但最常用來從 .NET Framework 元件存取 COM 物件或物件。</span><span class="sxs-lookup"><span data-stu-id="46ce0-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from .NET Framework assemblies.</span></span>  
  
 <span data-ttu-id="46ce0-118">假設您加入的元件參考包含名為的類別 `MathClass` ，該類別具有名為的新函式 `SquareRoot` ，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="46ce0-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 <span data-ttu-id="46ce0-119">您的應用程式可以使用文字方塊控制項來控制所要呼叫的方法及其引數。</span><span class="sxs-lookup"><span data-stu-id="46ce0-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="46ce0-120">例如，如果 `TextBox1` 包含要評估的運算式，而且 `TextBox2` 用來輸入函式的名稱，您可以使用下列程式碼， `SquareRoot` 在中的運算式上叫用函數 `TextBox1` ：</span><span class="sxs-lookup"><span data-stu-id="46ce0-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 <span data-ttu-id="46ce0-121">如果您在中輸入 "64" `TextBox1` ，並在中輸入 "SquareRoot"， `TextBox2` 然後呼叫 `CallMath` `TextBox1` 程式，則會評估中數位的平方根。</span><span class="sxs-lookup"><span data-stu-id="46ce0-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="46ce0-122">範例中的程式碼會叫用函式 `SquareRoot` (它會採用包含要評估為必要引數之運算式的字串) 並在 `TextBox1` 64) 的平方根 (中傳回 "8"。</span><span class="sxs-lookup"><span data-stu-id="46ce0-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="46ce0-123">當然，如果使用者在中輸入不正確字串 `TextBox2` ，則如果字串包含屬性的名稱而非方法，或如果方法有額外的必要引數，則會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="46ce0-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="46ce0-124">當您使用 `CallByName` 來預測這些或任何其他錯誤時，必須加入健全的錯誤處理常式代碼。</span><span class="sxs-lookup"><span data-stu-id="46ce0-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46ce0-125">雖然函式 `CallByName` 在某些情況下可能會很有用，但您必須針對效能含意來權衡其實用性（使用 `CallByName` 來叫用程式的速度會比晚期繫結呼叫稍微慢一點）。</span><span class="sxs-lookup"><span data-stu-id="46ce0-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="46ce0-126">如果您叫用重複呼叫的函式（例如在迴圈內部）， `CallByName` 可能會對效能產生嚴重的影響。</span><span class="sxs-lookup"><span data-stu-id="46ce0-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ce0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46ce0-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [<span data-ttu-id="46ce0-128">決定物件類型</span><span class="sxs-lookup"><span data-stu-id="46ce0-128">Determining Object Type</span></span>](determining-object-type.md)
