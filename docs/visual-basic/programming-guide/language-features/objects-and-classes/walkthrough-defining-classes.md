---
title: 定義類別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: aac30a8b0272ae6c141138a91585953237ab8098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="47c8d-102">逐步解說：定義類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c8d-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="47c8d-103">本逐步解說示範如何定義類別，您可以使用它來建立物件。</span><span class="sxs-lookup"><span data-stu-id="47c8d-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="47c8d-104">它也示範如何將屬性和方法新增至新的類別，並示範如何初始化物件。</span><span class="sxs-lookup"><span data-stu-id="47c8d-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="47c8d-105">若要定義類別</span><span class="sxs-lookup"><span data-stu-id="47c8d-105">To define a class</span></span>
  
1.  <span data-ttu-id="47c8d-106">建立專案，依序按一下**新專案**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="47c8d-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="47c8d-107">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="47c8d-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="47c8d-108">從 Visual Basic 專案範本，以顯示新的專案清單中選取 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="47c8d-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="47c8d-109">將新類別加入專案，依序按一下**加入類別**上**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="47c8d-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="47c8d-110">[新增項目] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="47c8d-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="47c8d-111">選取**類別**範本。</span><span class="sxs-lookup"><span data-stu-id="47c8d-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="47c8d-112">將新類別`UserNameInfo.vb`，然後按一下 **新增**以顯示新類別的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47c8d-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  <span data-ttu-id="47c8d-113">您可以使用 Visual Basic**程式碼編輯器**若要將類別加入至啟動表單中，輸入`Class`關鍵字後面接著新類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="47c8d-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="47c8d-114">**程式碼編輯器**提供對應`End Class`為您的陳述式。</span><span class="sxs-lookup"><span data-stu-id="47c8d-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="47c8d-115">藉由加入下列程式碼之間定義類別的私用欄位`Class`和`End Class`陳述式：</span><span class="sxs-lookup"><span data-stu-id="47c8d-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="47c8d-116">宣告為欄位`Private`表示它可以只在類別內使用。</span><span class="sxs-lookup"><span data-stu-id="47c8d-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="47c8d-117">您可以提供欄位從類別外使用存取修飾詞，例如`Public`可提供更多的存取。</span><span class="sxs-lookup"><span data-stu-id="47c8d-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="47c8d-118">如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="47c8d-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="47c8d-119">加入下列程式碼定義類別的屬性：</span><span class="sxs-lookup"><span data-stu-id="47c8d-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  <span data-ttu-id="47c8d-120">加入下列程式碼定義類別的方法：</span><span class="sxs-lookup"><span data-stu-id="47c8d-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="47c8d-121">加入名為程序來定義新類別的參數化建構函式`Sub New`:</span><span class="sxs-lookup"><span data-stu-id="47c8d-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="47c8d-122">`Sub New`根據此類別的物件建立時自動呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="47c8d-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="47c8d-123">這個建構函式設定的保留使用者名稱欄位的值。</span><span class="sxs-lookup"><span data-stu-id="47c8d-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="47c8d-124">若要建立的按鈕來測試類別</span><span class="sxs-lookup"><span data-stu-id="47c8d-124">To create a button to test the class</span></span>
  
1.  <span data-ttu-id="47c8d-125">以滑鼠右鍵按一下其名稱變更為設計模式的啟動表單**方案總管] 中**，然後按一下 [**檢視表設計工具**。</span><span class="sxs-lookup"><span data-stu-id="47c8d-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="47c8d-126">根據預設，Windows 應用程式專案啟動表單名為 Form1.vb。</span><span class="sxs-lookup"><span data-stu-id="47c8d-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="47c8d-127">即會出現在主要表單。</span><span class="sxs-lookup"><span data-stu-id="47c8d-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="47c8d-128">將按鈕加入主要表單，然後按兩下以顯示的程式碼`Button1_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="47c8d-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="47c8d-129">加入下列程式碼來呼叫測試程序：</span><span class="sxs-lookup"><span data-stu-id="47c8d-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="47c8d-130">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="47c8d-130">To run your application</span></span>
  
1.  <span data-ttu-id="47c8d-131">按 F5 執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="47c8d-131">Run your application by pressing F5.</span></span> <span data-ttu-id="47c8d-132">按一下呼叫測試程序表單上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="47c8d-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="47c8d-133">它會顯示訊息，指出原始`UserName`是"暄 BOBBY"，因為該程序呼叫`Capitalize`物件的方法。</span><span class="sxs-lookup"><span data-stu-id="47c8d-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="47c8d-134">按一下**確定**來解除訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="47c8d-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="47c8d-135">`Button1 Click`程序的值變更`UserName`屬性，並顯示訊息，指出新的值`UserName`是"Worden Joe"。</span><span class="sxs-lookup"><span data-stu-id="47c8d-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c8d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c8d-136">See also</span></span>

[<span data-ttu-id="47c8d-137">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c8d-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
[<span data-ttu-id="47c8d-138">物件和類別</span><span class="sxs-lookup"><span data-stu-id="47c8d-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)