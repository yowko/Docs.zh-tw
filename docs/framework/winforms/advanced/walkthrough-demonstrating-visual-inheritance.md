---
title: 逐步解說：示範視覺化繼承
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: bc91e3bde54eedb4d9dbcfcb9f7faa0ccc98e397
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398689"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="8f5b9-102">逐步解說：示範視覺化繼承</span><span class="sxs-lookup"><span data-stu-id="8f5b9-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="8f5b9-103">視覺化繼承可讓您查看基底表單上的控制項，並加入新的控制項。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="8f5b9-104">在本逐步解說中，您將建立基底表單，並編譯為類別庫。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="8f5b9-105">您將匯入此類別庫至另一個專案，並建立繼承自基底表單的新表單。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="8f5b9-106">在這個逐步解說期間，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="8f5b9-107">建立包含基底表單的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="8f5b9-108">加入屬性可由基底表單衍生類別修改的按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="8f5b9-109">加入無法由基底表單繼承者修改的按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="8f5b9-110">建立包含繼承自 `BaseForm` 表單的專案。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="8f5b9-111">最後，本逐步解說將示範繼承的表單上私用和受保護控制項之間的差異。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f5b9-112">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8f5b9-113">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8f5b9-114">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8f5b9-115">並非所有控制項都支援來自基底表單的視覺化繼承。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="8f5b9-116">下列控制項並不支援在此逐步解說中所描述的案例：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  <span data-ttu-id="8f5b9-117">繼承的表單中的這些控制項永遠唯讀，不論您使用的修飾詞為何 (`private``protected` 或 `public`)。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="8f5b9-118">案例步驟</span><span class="sxs-lookup"><span data-stu-id="8f5b9-118">Scenario Steps</span></span>  
 <span data-ttu-id="8f5b9-119">第一個步驟是建立基底表單。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="8f5b9-120">建立包含基底表單的類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-120">To create a class library project containing a base form</span></span>  
  
1.  <span data-ttu-id="8f5b9-121">從**檔案**功能表上，選擇**新增**，然後**專案**以開啟**新專案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="8f5b9-122">建立名為 Windows Forms 應用程式`BaseFormLibrary`。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3.  <span data-ttu-id="8f5b9-123">在中建立類別庫，而不是標準的 Windows Forms 應用程式中，**方案總管**，以滑鼠右鍵按一下**BaseFormLibrary**專案節點，然後選取**屬性**.</span><span class="sxs-lookup"><span data-stu-id="8f5b9-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="8f5b9-124">在專案屬性中，變更**輸出型別**從**Windows 應用程式**來**類別庫**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5.  <span data-ttu-id="8f5b9-125">從**檔案**功能表上，選擇**全部儲存**，將專案和檔案儲存至預設位置。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="8f5b9-126">下面兩個程序將按鈕加入至基底表單。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="8f5b9-127">為了示範視覺化繼承，您將藉由設定 `Modifiers` 屬性，授與這些按鈕不同存取層級。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="8f5b9-128">加入基底表單繼承者可以修改的按鈕：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-128">To add a button that inheritors of the base form can modify</span></span>  
  
1.  <span data-ttu-id="8f5b9-129">開啟**Form1**設計工具中。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-129">Open **Form1** in the designer.</span></span>  
  
2.  <span data-ttu-id="8f5b9-130">在上**所有的 Windows Form**索引標籤**工具箱**，按兩下**按鈕**將按鈕新增至表單。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="8f5b9-131">使用滑鼠來定位並調整按鈕的大小。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-131">Use the mouse to position and resize the button.</span></span>  
  
3.  <span data-ttu-id="8f5b9-132">在屬性視窗中設定下列按鈕屬性：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="8f5b9-133">設定**文字**屬性設**Say Hello**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="8f5b9-134">設定 **（名稱）** 屬性設**為 btnProtected**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="8f5b9-135">設定**修飾詞**屬性設**受保護**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-135">Set the**Modifiers** property to **Protected**.</span></span> <span data-ttu-id="8f5b9-136">這可讓繼承的表單**Form1**若要修改的屬性**為 btnProtected**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4.  <span data-ttu-id="8f5b9-137">按兩下**Say Hello**按鈕以新增事件處理常式**按一下**事件。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5.  <span data-ttu-id="8f5b9-138">將下列這行程式碼加入至事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="8f5b9-139">加入無法由基底表單繼承者修改的按鈕：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1.  <span data-ttu-id="8f5b9-140">切換到設計檢視，即可**Form1.vb [設計]]、 [Form1.cs [Design] 或 [Form1.jsl [Design]** ] 索引標籤上方的程式碼編輯器中，或按下 f7 鍵。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2.  <span data-ttu-id="8f5b9-141">加入第二個按鈕，並設定其屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="8f5b9-142">設定**文字**屬性設**Say Goodbye**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="8f5b9-143">設定 **（名稱）** 屬性設**為 btnPrivate**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="8f5b9-144">設定**修飾詞**屬性設**私人**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="8f5b9-145">這無法讓繼承的表單**Form1**若要修改的屬性**為 btnPrivate**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3.  <span data-ttu-id="8f5b9-146">按兩下**Say Goodbye**按鈕以新增事件處理常式**按一下**事件。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="8f5b9-147">將下列這行程式碼放在事件程序：</span><span class="sxs-lookup"><span data-stu-id="8f5b9-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  <span data-ttu-id="8f5b9-148">從**建置**功能表上，選擇**建置 BaseForm 程式庫**建置類別庫。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="8f5b9-149">一旦建立程式庫之後，您可建立新專案，其繼承自剛建立的表單。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="8f5b9-150">若要建立包含表單的專案，其表單繼承自基底表單</span><span class="sxs-lookup"><span data-stu-id="8f5b9-150">To create a project containing a form that inherits from the base form</span></span>  
  
1.  <span data-ttu-id="8f5b9-151">從**檔案**功能表上，選擇**新增**，然後**新專案**以開啟**加入新的專案** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="8f5b9-152">建立名為 Windows Forms 應用程式`InheritanceTest`。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="8f5b9-153">若要加入繼承的表單</span><span class="sxs-lookup"><span data-stu-id="8f5b9-153">To add an inherited form</span></span>  
  
1.  <span data-ttu-id="8f5b9-154">在**方案總管**，以滑鼠右鍵按一下**InheritanceTest**專案，然後選取**新增**，然後選取**新項目**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select**New Item**.</span></span>  
  
2.  <span data-ttu-id="8f5b9-155">在 **加入新項目**對話方塊中，選取**Windows Forms**類別目錄 （如果您有一個類別目錄清單），然後選取**繼承的表單**範本。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3.  <span data-ttu-id="8f5b9-156">保留預設名稱`Form2`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="8f5b9-157">在 **繼承選取器**對話方塊中，選取**Form1**從**BaseFormLibrary**表單繼承，並按一下 專案**確定**.</span><span class="sxs-lookup"><span data-stu-id="8f5b9-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="8f5b9-158">這會建立在表單**InheritanceTest**衍生自的表單中的專案**BaseFormLibrary**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5.  <span data-ttu-id="8f5b9-159">開啟繼承的表單 (**Form2**) 在設計工具中按兩下它，如果它尚未開啟。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="8f5b9-160">在設計師中，繼承的按鈕有符號 (![VisualBasicInheritanceSymbol 螢幕擷取畫面](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) 在其上方角落，表示受到繼承。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-160">In the designer, the inherited buttons have a symbol (![VisualBasicInheritanceSymbol screenshot](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) in their upper corner, indicating they are inherited.</span></span>  
  
6.  <span data-ttu-id="8f5b9-161">選取  **Say Hello**按鈕，並觀察調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-161">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="8f5b9-162">因為此按鈕已受到保護，所以繼承者可以移動它、調整大小、變更標題和進行其他修改。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-162">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7.  <span data-ttu-id="8f5b9-163">選取 私用**Say Goodbye**按鈕，並注意它沒有調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-163">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="8f5b9-164">此外，在**屬性** 視窗中，這個按鈕的屬性會呈現灰色，表示無法修改它們。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-164">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8.  <span data-ttu-id="8f5b9-165">如果您使用的 Visual C#:</span><span class="sxs-lookup"><span data-stu-id="8f5b9-165">If you are using Visual C#:</span></span>  
  
    1.  <span data-ttu-id="8f5b9-166">在 **方案總管**，以滑鼠右鍵按一下**Form1**中**InheritanceTest**專案，然後選擇**刪除**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-166">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="8f5b9-167">在隨即出現訊息方塊中，按一下**確定**以確認刪除。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-167">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="8f5b9-168">開啟 Program.cs 檔案並變更 `Application.Run(new Form1());` 為 `Application.Run(new Form2());`。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-168">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="8f5b9-169">在 **方案總管**，以滑鼠右鍵按一下**InheritanceTest**專案，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-169">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="8f5b9-170">在 **方案總管**，以滑鼠右鍵按一下**InheritanceTest**專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-170">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="8f5b9-171">在  **InheritanceTest**屬性頁，設定**啟始物件**要繼承的表單 (**Form2**)。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-171">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="8f5b9-172">按 F5 執行應用程式，並觀察繼承的表單之行為。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-172">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f5b9-173">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8f5b9-173">Next Steps</span></span>  
 <span data-ttu-id="8f5b9-174">使用者控制項的繼承以非常類似的方式運作。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-174">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="8f5b9-175">開啟一個新的類別庫專案，並加入使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-175">Open a new class library project and add a user control.</span></span> <span data-ttu-id="8f5b9-176">將構成控制項放在上面，然後編譯專案。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-176">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="8f5b9-177">開啟另一個新的類別庫專案，並加入已編譯類別程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-177">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="8f5b9-178">此外，請嘗試加入繼承的控制項 (透過**加入新項目** 對話方塊中) 至專案並使用**繼承選取器**。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-178">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="8f5b9-179">將使用者控制項，並將變更`Inherits`(`:` Visual C#) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-179">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="8f5b9-180">如需詳細資訊，請參閱 <<c0> [ 如何： 繼承 Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="8f5b9-180">For more information, see [How to: Inherit Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5b9-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f5b9-181">See Also</span></span>  
 [<span data-ttu-id="8f5b9-182">如何：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f5b9-182">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="8f5b9-183">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="8f5b9-183">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="8f5b9-184">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f5b9-184">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
