---
title: "定義類別 (Visual Basic) |Microsoft 文件"
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
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
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
ms.openlocfilehash: 5b470b8ba9b60dfb1cd1bbb207e02217f5311c27
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="23df0-102">逐步解說：定義類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23df0-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="23df0-103">本逐步解說示範如何定義類別，您可以用它來建立物件。</span><span class="sxs-lookup"><span data-stu-id="23df0-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="23df0-104">它也說明如何將屬性和方法新增至新的類別，並示範如何初始化物件。</span><span class="sxs-lookup"><span data-stu-id="23df0-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="23df0-105">若要定義類別</span><span class="sxs-lookup"><span data-stu-id="23df0-105">To define a class</span></span>  
  
1.  <span data-ttu-id="23df0-106">按一下 建立專案**新的專案**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="23df0-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="23df0-107">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23df0-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="23df0-108">從清單選取 Windows 應用程式[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案範本，以顯示新的專案。</span><span class="sxs-lookup"><span data-stu-id="23df0-108">Select Windows Application from the list of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="23df0-109">將新類別加入專案，依序按一下**加入類別**上**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="23df0-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="23df0-110">**加入新項目** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23df0-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="23df0-111">選取**類別**範本。</span><span class="sxs-lookup"><span data-stu-id="23df0-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="23df0-112">將新類別`UserNameInfo.vb`，然後按一下 **新增**以顯示新的類別的程式碼。</span><span class="sxs-lookup"><span data-stu-id="23df0-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     <span data-ttu-id="23df0-113">[!code-vb[VbVbalrOOP #&5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="23df0-113">[!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23df0-114">您可以使用[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]**程式碼編輯器**將類別加入至啟動表單中，輸入`Class`關鍵字後面加上新類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="23df0-114">You can use the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="23df0-115">**程式碼編輯器**提供對應`End Class`為您的陳述式。</span><span class="sxs-lookup"><span data-stu-id="23df0-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="23df0-116">藉由加入下列程式碼之間定義類別的私用欄位`Class`和`End Class`陳述式︰</span><span class="sxs-lookup"><span data-stu-id="23df0-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     <span data-ttu-id="23df0-117">[!code-vb[VbVbalrOOP #&7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="23df0-117">[!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span></span>  
  
     <span data-ttu-id="23df0-118">宣告欄位設為`Private`表示中，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="23df0-118">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="23df0-119">您可以讓欄位可從類別外使用存取修飾詞，例如`Public`可提供更多存取權。</span><span class="sxs-lookup"><span data-stu-id="23df0-119">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="23df0-120">如需詳細資訊，請參閱[在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="23df0-120">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="23df0-121">藉由加入下列程式碼中定義類別的屬性︰</span><span class="sxs-lookup"><span data-stu-id="23df0-121">Define a property for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="23df0-122">[!code-vb[VbVbalrOOP #&8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="23df0-122">[!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span></span>  
  
8.  <span data-ttu-id="23df0-123">定義類別的方法，加入下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="23df0-123">Define a method for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="23df0-124">[!code-vb[VbVbalrOOP #&9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="23df0-124">[!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span></span>  
  
9. <span data-ttu-id="23df0-125">加入名為程序來定義新類別的參數化建構函式`Sub New`:</span><span class="sxs-lookup"><span data-stu-id="23df0-125">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     <span data-ttu-id="23df0-126">[!code-vb[VbVbalrOOP #&10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="23df0-126">[!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span></span>  
  
     <span data-ttu-id="23df0-127">`Sub New`根據此類別的物件建立時自動呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="23df0-127">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="23df0-128">這個建構函式設定的保留使用者名稱欄位的值。</span><span class="sxs-lookup"><span data-stu-id="23df0-128">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="23df0-129">若要建立一個按鈕來測試類別</span><span class="sxs-lookup"><span data-stu-id="23df0-129">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="23df0-130">以滑鼠右鍵按一下其名稱變更為設計模式的啟動表單**方案總管] 中**，然後按一下 [**檢視表設計工具**。</span><span class="sxs-lookup"><span data-stu-id="23df0-130">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="23df0-131">根據預設，Windows 應用程式專案啟動表單稱為 Form1.vb。</span><span class="sxs-lookup"><span data-stu-id="23df0-131">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="23df0-132">接著會出現在主要表單。</span><span class="sxs-lookup"><span data-stu-id="23df0-132">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="23df0-133">將按鈕加入至主表單，然後按兩下以顯示的程式碼`Button1_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="23df0-133">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="23df0-134">新增下列程式碼來呼叫測試程序︰</span><span class="sxs-lookup"><span data-stu-id="23df0-134">Add the following code to call the test procedure:</span></span>  
  
     <span data-ttu-id="23df0-135">[!code-vb[VbVbalrOOP #&12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="23df0-135">[!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span></span>  
  
### <a name="to-run-your-application"></a><span data-ttu-id="23df0-136">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="23df0-136">To run your application</span></span>  
  
1.  <span data-ttu-id="23df0-137">按 f5 鍵執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="23df0-137">Run your application by pressing F5.</span></span> <span data-ttu-id="23df0-138">按一下表單上的按鈕來呼叫測試程序。</span><span class="sxs-lookup"><span data-stu-id="23df0-138">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="23df0-139">它會顯示訊息，指出原始`UserName`是 「 摩爾 BOBBY 」，因為呼叫此程序`Capitalize`物件的方法。</span><span class="sxs-lookup"><span data-stu-id="23df0-139">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="23df0-140">按一下 **確定**來解除訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="23df0-140">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="23df0-141">`Button1 Click`程序變更的值`UserName`屬性，並顯示訊息，指出新的值`UserName`是 「 Worden Joe 」。</span><span class="sxs-lookup"><span data-stu-id="23df0-141">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23df0-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23df0-142">See Also</span></span>  
 <span data-ttu-id="23df0-143">[物件導向程式設計](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span><span class="sxs-lookup"><span data-stu-id="23df0-143">[Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span></span>  
<span data-ttu-id="23df0-144"> [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="23df0-144"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>

