---
title: "建立和實作介面 (Visual Basic) |Microsoft 文件"
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
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
ms.openlocfilehash: ef1ec16005bf0a7967d396054ae23c1023143c2a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="8bb34-102">逐步解說：建立和實作介面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bb34-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="8bb34-103">介面描述的特性屬性、 方法和事件，但保留最多結構或類別的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8bb34-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="8bb34-104">本逐步解說示範如何宣告和實作介面。</span><span class="sxs-lookup"><span data-stu-id="8bb34-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bb34-105">本逐步解說不提供有關如何建立使用者介面的資訊。</span><span class="sxs-lookup"><span data-stu-id="8bb34-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="8bb34-106">若要定義介面</span><span class="sxs-lookup"><span data-stu-id="8bb34-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="8bb34-107">開啟新[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="8bb34-107">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="8bb34-108">加入專案中的新模組，依序按一下**加入模組**上**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="8bb34-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="8bb34-109">將新的模組`Module1.vb`按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="8bb34-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="8bb34-110">隨即出現新模組的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8bb34-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="8bb34-111">定義名為介面`TestInterface`內`Module1`輸入`Interface TestInterface`之間`Module`和`End Module`陳述式，並按 enter。</span><span class="sxs-lookup"><span data-stu-id="8bb34-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="8bb34-112">**程式碼編輯器**縮排`Interface`關鍵字，並將`End Interface`表單的程式碼區塊的陳述式。</span><span class="sxs-lookup"><span data-stu-id="8bb34-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="8bb34-113">將下列程式碼之間定義屬性、 方法和事件的介面`Interface`和`End Interface`陳述式︰</span><span class="sxs-lookup"><span data-stu-id="8bb34-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     <span data-ttu-id="8bb34-114">[!code-vb[VbVbalrOOP #&98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-114">[!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="8bb34-115">實作</span><span class="sxs-lookup"><span data-stu-id="8bb34-115">Implementation</span></span>  
 <span data-ttu-id="8bb34-116">您可能會注意到用來宣告介面成員不同於用來宣告類別成員宣告的語法。</span><span class="sxs-lookup"><span data-stu-id="8bb34-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="8bb34-117">這項差異會反映介面不能包含實作程式碼的事實。</span><span class="sxs-lookup"><span data-stu-id="8bb34-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="8bb34-118">若要實作介面</span><span class="sxs-lookup"><span data-stu-id="8bb34-118">To implement the interface</span></span>  
  
1.  <span data-ttu-id="8bb34-119">新增名為`ImplementationClass`藉由新增下列陳述式`Module1`之後，`End Interface`陳述式之前`End Module`陳述式，並按 enter:</span><span class="sxs-lookup"><span data-stu-id="8bb34-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     <span data-ttu-id="8bb34-120">[!code-vb[VbVbalrOOP #&99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-120">[!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-121">如果您使用整合式的開發環境中，**程式碼編輯器**提供相對應的`End Class`陳述式，當您按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="8bb34-121">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="8bb34-122">新增下列`Implements`陳述式來`ImplementationClass`，它將類別命名介面實作︰</span><span class="sxs-lookup"><span data-stu-id="8bb34-122">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     <span data-ttu-id="8bb34-123">[!code-vb[VbVbalrOOP #&100;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-123">[!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-124">當類別或結構的最上方的其他項目分開列出`Implements`陳述式指出類別或結構實作的介面。</span><span class="sxs-lookup"><span data-stu-id="8bb34-124">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="8bb34-125">如果您使用整合式的開發環境中，**程式碼編輯器**實作所需的類別成員`TestInterface`當您按下 enter 鍵，並可以略過下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="8bb34-125">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="8bb34-126">如果您不使用整合式的開發環境中，您必須實作介面的所有成員`MyInterface`。</span><span class="sxs-lookup"><span data-stu-id="8bb34-126">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="8bb34-127">加入下列程式碼以`ImplementationClass`實作`Event1`， `Method1`，和`Prop1`:</span><span class="sxs-lookup"><span data-stu-id="8bb34-127">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     <span data-ttu-id="8bb34-128">[!code-vb[VbVbalrOOP #&101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-128">[!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-129">`Implements`陳述式名稱的介面和介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="8bb34-129">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="8bb34-130">完成的定義`Prop1`私用欄位加入至類別，以儲存屬性值︰</span><span class="sxs-lookup"><span data-stu-id="8bb34-130">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     <span data-ttu-id="8bb34-131">[!code-vb[VbVbalrOOP #&102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-131">[!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-132">傳回值的`pval`屬性 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="8bb34-132">Return the value of the `pval` from the property get accessor.</span></span>  
  
     <span data-ttu-id="8bb34-133">[!code-vb[VbVbalrOOP #&103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-133">[!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-134">設定的值`pval`在屬性 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="8bb34-134">Set the value of `pval` in the property set accessor.</span></span>  
  
     <span data-ttu-id="8bb34-135">[!code-vb[VbVbalrOOP #&104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-135">[!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span></span>  
  
5.  <span data-ttu-id="8bb34-136">完成的定義`Method1`加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="8bb34-136">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     <span data-ttu-id="8bb34-137">[!code-vb[VbVbalrOOP #&105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-137">[!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span></span>  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="8bb34-138">若要測試的介面實作</span><span class="sxs-lookup"><span data-stu-id="8bb34-138">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="8bb34-139">啟動表單的專案中以滑鼠右鍵按一下**方案總管 中**，然後按一下**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="8bb34-139">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="8bb34-140">編輯器會顯示啟動表單的類別。</span><span class="sxs-lookup"><span data-stu-id="8bb34-140">The editor displays the class for your startup form.</span></span> <span data-ttu-id="8bb34-141">根據預設，啟動表單稱為`Form1`。</span><span class="sxs-lookup"><span data-stu-id="8bb34-141">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="8bb34-142">新增下列`testInstance`欄位`Form1`類別︰</span><span class="sxs-lookup"><span data-stu-id="8bb34-142">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     <span data-ttu-id="8bb34-143">[!code-vb[VbVbalrOOP #&120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-143">[!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-144">藉由宣告`testInstance`為`WithEvents`、`Form1`類別可以處理其事件。</span><span class="sxs-lookup"><span data-stu-id="8bb34-144">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="8bb34-145">新增下列事件處理常式`Form1`類別來處理所引發的事件`testInstance`:</span><span class="sxs-lookup"><span data-stu-id="8bb34-145">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     <span data-ttu-id="8bb34-146">[!code-vb[VbVbalrOOP #&106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-146">[!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span></span>  
  
4.  <span data-ttu-id="8bb34-147">新增名為副程式`Test`至`Form1`測試實作類別的類別︰</span><span class="sxs-lookup"><span data-stu-id="8bb34-147">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     <span data-ttu-id="8bb34-148">[!code-vb[VbVbalrOOP #&107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-148">[!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span></span>  
  
     <span data-ttu-id="8bb34-149">`Test`程序會建立實作類別的執行個體`MyInterface`，指派至該執行個體`testInstance` 欄位中，設定屬性，並透過介面執行方法。</span><span class="sxs-lookup"><span data-stu-id="8bb34-149">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="8bb34-150">加入程式碼以呼叫`Test`程序從`Form1 Load`啟動表單的程序︰</span><span class="sxs-lookup"><span data-stu-id="8bb34-150">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     <span data-ttu-id="8bb34-151">[!code-vb[VbVbalrOOP #&108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bb34-151">[!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span></span>  
  
6.  <span data-ttu-id="8bb34-152">執行`Test`程序，按下 F5。</span><span class="sxs-lookup"><span data-stu-id="8bb34-152">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="8bb34-153">會顯示訊息 「 Prop1 已設定為 9"。</span><span class="sxs-lookup"><span data-stu-id="8bb34-153">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="8bb34-154">之後您按一下 [確定] 會顯示 「 Method1 的 X 參數是 5 」 的訊息。</span><span class="sxs-lookup"><span data-stu-id="8bb34-154">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="8bb34-155">按一下 [確定]，並顯示 「 事件處理常式會攔截事件 」 的訊息。</span><span class="sxs-lookup"><span data-stu-id="8bb34-155">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb34-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bb34-156">See Also</span></span>  
 <span data-ttu-id="8bb34-157">[Implements 陳述式](../../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8bb34-157">[Implements Statement](../../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="8bb34-158"> [介面](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="8bb34-158"> [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span></span>  
<span data-ttu-id="8bb34-159"> [Interface 陳述式](../../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8bb34-159"> [Interface Statement](../../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="8bb34-160"> [Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8bb34-160"> [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)</span></span>

