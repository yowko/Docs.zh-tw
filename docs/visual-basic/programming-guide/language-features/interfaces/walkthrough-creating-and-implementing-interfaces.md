---
title: "建立和實作介面 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="beade-102">逐步解說：建立和實作介面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="beade-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="beade-103">介面描述特性的屬性、 方法和事件，但保留最多結構或類別的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="beade-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="beade-104">本逐步解說示範如何宣告和實作介面。</span><span class="sxs-lookup"><span data-stu-id="beade-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="beade-105">此逐步解說不提供如何建立使用者介面的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="beade-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="beade-106">若要定義介面</span><span class="sxs-lookup"><span data-stu-id="beade-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="beade-107">開啟新的 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="beade-107">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="beade-108">加入專案中的新模組，依序按一下**加入模組**上**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="beade-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="beade-109">將新的模組`Module1.vb`按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="beade-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="beade-110">新模組的程式碼會顯示。</span><span class="sxs-lookup"><span data-stu-id="beade-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="beade-111">定義名為介面`TestInterface`內`Module1`輸入`Interface TestInterface`之間`Module`和`End Module`陳述式，並按 enter。</span><span class="sxs-lookup"><span data-stu-id="beade-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="beade-112">**程式碼編輯器**縮排`Interface`關鍵字，並將`End Interface`形成程式碼區塊的陳述式。</span><span class="sxs-lookup"><span data-stu-id="beade-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="beade-113">將下列程式碼之間定義屬性、 方法和事件的介面`Interface`和`End Interface`陳述式：</span><span class="sxs-lookup"><span data-stu-id="beade-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a><span data-ttu-id="beade-114">實作</span><span class="sxs-lookup"><span data-stu-id="beade-114">Implementation</span></span>  
 <span data-ttu-id="beade-115">您可能會注意到用來宣告介面成員不同於用來宣告類別成員宣告的語法。</span><span class="sxs-lookup"><span data-stu-id="beade-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="beade-116">這項差異會反映介面不能包含實作程式碼的事實。</span><span class="sxs-lookup"><span data-stu-id="beade-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="beade-117">若要實作介面</span><span class="sxs-lookup"><span data-stu-id="beade-117">To implement the interface</span></span>  
  
1.  <span data-ttu-id="beade-118">將類別命名為`ImplementationClass`加入下列陳述式`Module1`，之後`End Interface`陳述式之前`End Module`陳述式，並按 enter:</span><span class="sxs-lookup"><span data-stu-id="beade-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     <span data-ttu-id="beade-119">如果您要使用整合式的開發環境中，**程式碼編輯器**提供比對`End Class`陳述式，當您按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="beade-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="beade-120">加入下列`Implements`陳述式來`ImplementationClass`，其中的類別命名介面實作：</span><span class="sxs-lookup"><span data-stu-id="beade-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     <span data-ttu-id="beade-121">當從其他項目上方的類別或結構，分別列於`Implements`陳述式表示類別或結構實作介面。</span><span class="sxs-lookup"><span data-stu-id="beade-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="beade-122">如果您要使用整合式的開發環境中，**程式碼編輯器**實作所需的類別成員`TestInterface`當您按下 ENTER，以及您可以略過下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="beade-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="beade-123">如果您不使用整合式的開發環境中，您必須實作介面的所有成員`MyInterface`。</span><span class="sxs-lookup"><span data-stu-id="beade-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="beade-124">將下列程式碼加入`ImplementationClass`實作`Event1`， `Method1`，和`Prop1`:</span><span class="sxs-lookup"><span data-stu-id="beade-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     <span data-ttu-id="beade-125">`Implements`陳述式命名的介面和實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="beade-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="beade-126">完成的定義`Prop1`將私用欄位加入至儲存屬性值的類別：</span><span class="sxs-lookup"><span data-stu-id="beade-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     <span data-ttu-id="beade-127">傳回值的`pval`從屬性 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="beade-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     <span data-ttu-id="beade-128">值設定`pval`在屬性 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="beade-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  <span data-ttu-id="beade-129">完成的定義`Method1`加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="beade-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="beade-130">若要測試介面的實作</span><span class="sxs-lookup"><span data-stu-id="beade-130">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="beade-131">以滑鼠右鍵按一下 [啟動表單的專案中的**方案總管] 中**，然後按一下**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="beade-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="beade-132">編輯器會顯示啟動表單的類別。</span><span class="sxs-lookup"><span data-stu-id="beade-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="beade-133">根據預設，會呼叫啟動表單`Form1`。</span><span class="sxs-lookup"><span data-stu-id="beade-133">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="beade-134">加入下列`testInstance`欄位設為`Form1`類別：</span><span class="sxs-lookup"><span data-stu-id="beade-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     <span data-ttu-id="beade-135">藉由宣告`testInstance`為`WithEvents`、`Form1`類別可以處理的事件。</span><span class="sxs-lookup"><span data-stu-id="beade-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="beade-136">新增下列事件處理常式`Form1`處理所引發的事件類別`testInstance`:</span><span class="sxs-lookup"><span data-stu-id="beade-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  <span data-ttu-id="beade-137">加入名為的副程式`Test`至`Form1`測試實作類別的類別：</span><span class="sxs-lookup"><span data-stu-id="beade-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     <span data-ttu-id="beade-138">`Test`程序會建立實作類別的執行個體`MyInterface`，會指派至該執行個體`testInstance` 欄位中，設定屬性，並透過介面執行方法。</span><span class="sxs-lookup"><span data-stu-id="beade-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="beade-139">加入程式碼以呼叫`Test`程序從`Form1 Load`啟動表單的程序：</span><span class="sxs-lookup"><span data-stu-id="beade-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  <span data-ttu-id="beade-140">執行`Test`按 f5 鍵的程序。</span><span class="sxs-lookup"><span data-stu-id="beade-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="beade-141">會顯示訊息 「 Prop1 已設為 9"。</span><span class="sxs-lookup"><span data-stu-id="beade-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="beade-142">您按一下 [確定]，訊息 「 Method1 的 X 參數 」 5 之後隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="beade-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="beade-143">按一下 [確定]，並顯示 「 事件處理常式會攔截事件 」 的訊息。</span><span class="sxs-lookup"><span data-stu-id="beade-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beade-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beade-144">See Also</span></span>  
 [<span data-ttu-id="beade-145">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="beade-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="beade-146">介面</span><span class="sxs-lookup"><span data-stu-id="beade-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [<span data-ttu-id="beade-147">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="beade-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="beade-148">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="beade-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)
