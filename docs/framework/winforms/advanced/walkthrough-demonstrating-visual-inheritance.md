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
ms.openlocfilehash: 32df98852b28963ffb748895156f7d9977c74b92
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046142"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="58d04-102">逐步解說：示範視覺化繼承</span><span class="sxs-lookup"><span data-stu-id="58d04-102">Walkthrough: Demonstrating Visual Inheritance</span></span>

<span data-ttu-id="58d04-103">視覺化繼承可讓您查看基底表單上的控制項，並加入新的控制項。</span><span class="sxs-lookup"><span data-stu-id="58d04-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="58d04-104">在本逐步解說中，您將建立基底表單，並編譯為類別庫。</span><span class="sxs-lookup"><span data-stu-id="58d04-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="58d04-105">您將匯入此類別庫至另一個專案，並建立繼承自基底表單的新表單。</span><span class="sxs-lookup"><span data-stu-id="58d04-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="58d04-106">在這個逐步解說期間，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="58d04-106">During this walkthrough, you will learn how to:</span></span>

- <span data-ttu-id="58d04-107">建立包含基底表單的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="58d04-107">Create a class library project containing a base form.</span></span>

- <span data-ttu-id="58d04-108">加入屬性可由基底表單衍生類別修改的按鈕。</span><span class="sxs-lookup"><span data-stu-id="58d04-108">Add a button with properties that derived classes of the base form can modify.</span></span>

- <span data-ttu-id="58d04-109">加入無法由基底表單繼承者修改的按鈕。</span><span class="sxs-lookup"><span data-stu-id="58d04-109">Add a button that cannot be modified by inheritors of the base form.</span></span>

- <span data-ttu-id="58d04-110">建立包含繼承自 `BaseForm` 表單的專案。</span><span class="sxs-lookup"><span data-stu-id="58d04-110">Create a project containing a form that inherits from `BaseForm`.</span></span>

<span data-ttu-id="58d04-111">最後，本逐步解說將示範繼承的表單上私用和受保護控制項之間的差異。</span><span class="sxs-lookup"><span data-stu-id="58d04-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>

> [!CAUTION]
> <span data-ttu-id="58d04-112">並非所有控制項都支援來自基底表單的視覺化繼承。</span><span class="sxs-lookup"><span data-stu-id="58d04-112">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="58d04-113">下列控制項並不支援在此逐步解說中所描述的案例：</span><span class="sxs-lookup"><span data-stu-id="58d04-113">The following controls do not support the scenario described in this walkthrough:</span></span>
>
> - <xref:System.Windows.Forms.WebBrowser>
>
> - <xref:System.Windows.Forms.ToolStrip>
>
> - <xref:System.Windows.Forms.ToolStripPanel>
>
> - <xref:System.Windows.Forms.TableLayoutPanel>
>
> - <xref:System.Windows.Forms.FlowLayoutPanel>
>
> - <xref:System.Windows.Forms.DataGridView>
>
> <span data-ttu-id="58d04-114">繼承的表單中的這些控制項永遠唯讀，不論您使用的修飾詞為何 (`private``protected` 或 `public`)。</span><span class="sxs-lookup"><span data-stu-id="58d04-114">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>

## <a name="create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="58d04-115">建立包含基底表單的類別庫專案</span><span class="sxs-lookup"><span data-stu-id="58d04-115">Create a class library project containing a base form</span></span>

1. <span data-ttu-id="58d04-116">在 Visual Studio 中, 從 [檔案] 功能表選擇 [**新增** > **專案**], 開啟 [**新增專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="58d04-116">In Visual Studio, from the **File** menu, choose **New** > **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="58d04-117">建立名為`BaseFormLibrary`的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="58d04-117">Create a Windows Forms application named `BaseFormLibrary`.</span></span>

3. <span data-ttu-id="58d04-118">若要建立類別庫, 而不是標準 Windows Forms 應用程式, 請在**方案總管**中, 以滑鼠右鍵按一下**baseformlibrary**專案節點, 然後選取 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="58d04-118">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>

4. <span data-ttu-id="58d04-119">在專案的屬性中, 將 [**輸出類型**] 從 [ **Windows 應用程式**] 變更為 [**類別庫**]。</span><span class="sxs-lookup"><span data-stu-id="58d04-119">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>

5. <span data-ttu-id="58d04-120">從 [檔案] 功能表中, 選擇 [**全部儲存**], 將專案和檔案儲存到預設位置。</span><span class="sxs-lookup"><span data-stu-id="58d04-120">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>

<span data-ttu-id="58d04-121">下面兩個程序將按鈕加入至基底表單。</span><span class="sxs-lookup"><span data-stu-id="58d04-121">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="58d04-122">為了示範視覺化繼承，您將藉由設定 `Modifiers` 屬性，授與這些按鈕不同存取層級。</span><span class="sxs-lookup"><span data-stu-id="58d04-122">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="58d04-123">新增基底表單繼承者可以修改的按鈕</span><span class="sxs-lookup"><span data-stu-id="58d04-123">Add a button that inheritors of the base form can modify</span></span>

1. <span data-ttu-id="58d04-124">在設計工具中，開啟 **Form1**。</span><span class="sxs-lookup"><span data-stu-id="58d04-124">Open **Form1** in the designer.</span></span>

2. <span data-ttu-id="58d04-125">在 [**工具箱**] 的 [**所有 Windows Forms** ] 索引標籤上, 按兩下 [**按鈕**], 將按鈕新增至表單。</span><span class="sxs-lookup"><span data-stu-id="58d04-125">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="58d04-126">使用滑鼠來定位並調整按鈕的大小。</span><span class="sxs-lookup"><span data-stu-id="58d04-126">Use the mouse to position and resize the button.</span></span>

3. <span data-ttu-id="58d04-127">在屬性視窗中設定下列按鈕屬性：</span><span class="sxs-lookup"><span data-stu-id="58d04-127">In the Properties window, set the following properties of the button:</span></span>

    - <span data-ttu-id="58d04-128">將 [ **Text** ] 屬性設定為 [ **Hello**]。</span><span class="sxs-lookup"><span data-stu-id="58d04-128">Set the **Text** property to **Say Hello**.</span></span>

    - <span data-ttu-id="58d04-129">將 [ **(名稱)** ] 屬性設定為**btnProtected**。</span><span class="sxs-lookup"><span data-stu-id="58d04-129">Set the **(Name)** property to **btnProtected**.</span></span>

    - <span data-ttu-id="58d04-130">將 [修飾詞] 屬性設定為 [**受保護**]。</span><span class="sxs-lookup"><span data-stu-id="58d04-130">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="58d04-131">這讓繼承自**Form1**的表單能夠修改**btnProtected**的屬性。</span><span class="sxs-lookup"><span data-stu-id="58d04-131">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>

4. <span data-ttu-id="58d04-132">按兩下 [假設為**Hello** ] 按鈕, 以加入**click**事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="58d04-132">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>

5. <span data-ttu-id="58d04-133">將下列這行程式碼加入至事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="58d04-133">Add the following line of code to the event handler:</span></span>

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="58d04-134">加入無法由基底表單繼承者修改的按鈕</span><span class="sxs-lookup"><span data-stu-id="58d04-134">Add a button that cannot be modified by inheritors of the base form</span></span>

1. <span data-ttu-id="58d04-135">按一下 [程式碼編輯器] 上方的 [form1.vb **[design]]、[Form1.cs [design]] 或 [form1.jsl [design]** ] 索引標籤, 或按 F7 鍵, 切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="58d04-135">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>

2. <span data-ttu-id="58d04-136">加入第二個按鈕，並設定其屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="58d04-136">Add a second button and set its properties as follows:</span></span>

    - <span data-ttu-id="58d04-137">將 [ **Text** ] 屬性設定為 [**再見**]。</span><span class="sxs-lookup"><span data-stu-id="58d04-137">Set the **Text** property to **Say Goodbye**.</span></span>

    - <span data-ttu-id="58d04-138">將 [ **(名稱)** ] 屬性設定為**btnPrivate**。</span><span class="sxs-lookup"><span data-stu-id="58d04-138">Set the **(Name)** property to **btnPrivate**.</span></span>

    - <span data-ttu-id="58d04-139">將 [修飾詞] 屬性設定為 [**私**用]。</span><span class="sxs-lookup"><span data-stu-id="58d04-139">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="58d04-140">這使得繼承自**Form1**的表單不可能修改**btnPrivate**的屬性。</span><span class="sxs-lookup"><span data-stu-id="58d04-140">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>

3. <span data-ttu-id="58d04-141">按兩下 [**說再見**] 按鈕, 以加入**click**事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="58d04-141">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="58d04-142">將下列這行程式碼放在事件程序：</span><span class="sxs-lookup"><span data-stu-id="58d04-142">Place the following line of code in the event procedure:</span></span>

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. <span data-ttu-id="58d04-143">從 [**建立**] 功能表中, 選擇 [**組建 BaseForm 程式庫**] 以建立類別庫。</span><span class="sxs-lookup"><span data-stu-id="58d04-143">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>

     <span data-ttu-id="58d04-144">一旦建立程式庫之後，您可建立新專案，其繼承自剛建立的表單。</span><span class="sxs-lookup"><span data-stu-id="58d04-144">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="58d04-145">建立專案, 其中包含繼承自基底表單的表單</span><span class="sxs-lookup"><span data-stu-id="58d04-145">Create a project containing a form that inherits from the base form</span></span>

1. <span data-ttu-id="58d04-146">從 [檔案] 功能表中, 依序選擇 [**加入**] 和 [**新增專案**], 開啟 [**加入新的專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="58d04-146">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="58d04-147">建立名為`InheritanceTest`的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="58d04-147">Create a Windows Forms application named `InheritanceTest`.</span></span>

## <a name="add-an-inherited-form"></a><span data-ttu-id="58d04-148">加入繼承的表單</span><span class="sxs-lookup"><span data-stu-id="58d04-148">Add an inherited form</span></span>

1. <span data-ttu-id="58d04-149">在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案, 選取 **加入**, 然後選取 **新增專案**。</span><span class="sxs-lookup"><span data-stu-id="58d04-149">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>

2. <span data-ttu-id="58d04-150">在 [**加入新專案**] 對話方塊中, 選取 [ **Windows Forms** ] 類別 (如果您有一份類別清單), 然後選取 [**繼承的表單**] 範本。</span><span class="sxs-lookup"><span data-stu-id="58d04-150">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>

3. <span data-ttu-id="58d04-151">保留預設名稱`Form2` , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="58d04-151">Leave the default name of `Form2` and then click **Add**.</span></span>

4. <span data-ttu-id="58d04-152">在 **繼承選擇器** 對話方塊中, 從**baseformlibrary**專案選取  **Form1**  做為要繼承的表單, 然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="58d04-152">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>

     <span data-ttu-id="58d04-153">這會在**inheritancetest**專案中建立衍生自**baseformlibrary**中表單的表單。</span><span class="sxs-lookup"><span data-stu-id="58d04-153">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>

5. <span data-ttu-id="58d04-154">按兩下設計工具中的繼承表單 (**Form2**), 如果尚未開啟, 請將它開啟。</span><span class="sxs-lookup"><span data-stu-id="58d04-154">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>

    <span data-ttu-id="58d04-155">在設計工具中, 繼承的按鈕具有符號 (</span><span class="sxs-lookup"><span data-stu-id="58d04-155">In the designer, the inherited buttons have a symbol (</span></span>![Visual Basic 繼承符號的螢幕擷取畫面。](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="58d04-157">), 表示它們會被繼承。</span><span class="sxs-lookup"><span data-stu-id="58d04-157">) in their upper corner, indicating they are inherited.</span></span>

6. <span data-ttu-id="58d04-158">選取 [ **Hello** ] 按鈕, 並觀察調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="58d04-158">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="58d04-159">因為此按鈕已受到保護，所以繼承者可以移動它、調整大小、變更標題和進行其他修改。</span><span class="sxs-lookup"><span data-stu-id="58d04-159">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>

7. <span data-ttu-id="58d04-160">選取 [私用] [**再見**] 按鈕, 並注意它沒有調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="58d04-160">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="58d04-161">此外, 在 [**屬性**] 視窗中, 這個按鈕的屬性會呈現灰色, 表示無法修改它們。</span><span class="sxs-lookup"><span data-stu-id="58d04-161">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>

8. <span data-ttu-id="58d04-162">如果您使用的是C#視覺效果:</span><span class="sxs-lookup"><span data-stu-id="58d04-162">If you are using Visual C#:</span></span>

    1. <span data-ttu-id="58d04-163">在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案中的  **Form1** , 然後選擇 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="58d04-163">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="58d04-164">在出現的訊息方塊中, 按一下 **[確定]** 以確認刪除。</span><span class="sxs-lookup"><span data-stu-id="58d04-164">In the message box that appears, click **OK** to confirm the deletion.</span></span>

    2. <span data-ttu-id="58d04-165">開啟 Program.cs 檔案並變更 `Application.Run(new Form1());` 為 `Application.Run(new Form2());`。</span><span class="sxs-lookup"><span data-stu-id="58d04-165">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>

9. <span data-ttu-id="58d04-166">在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案, 然後選取 **設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="58d04-166">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>

10. <span data-ttu-id="58d04-167">在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案, 然後選取 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="58d04-167">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>

11. <span data-ttu-id="58d04-168">在  **inheritancetest**  屬性頁中, 將 **啟始物件** 設定為繼承的表單 (**Form2**)。</span><span class="sxs-lookup"><span data-stu-id="58d04-168">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>

12. <span data-ttu-id="58d04-169">按**F5**執行應用程式, 並觀察繼承表單的行為。</span><span class="sxs-lookup"><span data-stu-id="58d04-169">Press **F5** to run the application, and observe the behavior of the inherited form.</span></span>

## <a name="next-steps"></a><span data-ttu-id="58d04-170">後續步驟</span><span class="sxs-lookup"><span data-stu-id="58d04-170">Next steps</span></span>

<span data-ttu-id="58d04-171">使用者控制項的繼承以非常類似的方式運作。</span><span class="sxs-lookup"><span data-stu-id="58d04-171">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="58d04-172">開啟一個新的類別庫專案，並加入使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="58d04-172">Open a new class library project and add a user control.</span></span> <span data-ttu-id="58d04-173">將構成控制項放在上面，然後編譯專案。</span><span class="sxs-lookup"><span data-stu-id="58d04-173">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="58d04-174">開啟另一個新的類別庫專案，並加入已編譯類別程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="58d04-174">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="58d04-175">此外, 請嘗試加入繼承的控制項 (透過 [**加入新專案**] 對話方塊) 至專案, 並使用 [**繼承選擇器**]。</span><span class="sxs-lookup"><span data-stu-id="58d04-175">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="58d04-176">加入使用者控制項, 並變更`Inherits` (`:`在 Visual C#) 語句中。</span><span class="sxs-lookup"><span data-stu-id="58d04-176">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="58d04-177">如需詳細資訊，請參閱[如何：繼承 Windows Forms](how-to-inherit-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="58d04-177">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58d04-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58d04-178">See also</span></span>

- [<span data-ttu-id="58d04-179">如何：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58d04-179">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="58d04-180">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="58d04-180">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="58d04-181">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58d04-181">Windows Forms</span></span>](../index.md)
