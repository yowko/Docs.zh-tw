---
title: 作法：將 [載入]、[儲存] 和 [取消] 按鈕新增至 Windows Forms BindingNavigator 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991745"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="f767d-102">作法：將 [載入]、[儲存] 和 [取消] 按鈕新增至 Windows Forms BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="f767d-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="f767d-103">控制項是一個特殊用途<xref:System.Windows.Forms.ToolStrip>的控制項，用於導覽和操作表單上系結至資料的控制項。 <xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="f767d-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="f767d-104">因為它是<xref:System.Windows.Forms.ToolStrip>控制項<xref:System.Windows.Forms.BindingNavigator> ，所以可以輕鬆地修改元件以包含使用者的其他或替代命令。</span><span class="sxs-lookup"><span data-stu-id="f767d-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="f767d-105">在下列程式中， <xref:System.Windows.Forms.TextBox>控制項系結至資料， <xref:System.Windows.Forms.ToolStrip>而新增至表單的控制項則會修改為包含 [載入]、[儲存] 和 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f767d-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="f767d-106">將 [載入]、[儲存] 和 [取消] 按鈕新增至 BindingNavigator 元件</span><span class="sxs-lookup"><span data-stu-id="f767d-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="f767d-107">在 Visual Studio 中，將<xref:System.Windows.Forms.TextBox>控制項新增至表單。</span><span class="sxs-lookup"><span data-stu-id="f767d-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="f767d-108">將它系結<xref:System.Windows.Forms.BindingSource>至系結至資料來源的。</span><span class="sxs-lookup"><span data-stu-id="f767d-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="f767d-109">在<xref:System.Windows.Forms.BindingSource>此範例中，會系結至資料庫。</span><span class="sxs-lookup"><span data-stu-id="f767d-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="f767d-110">產生資料集和資料表介面卡之後，將<xref:System.Windows.Forms.BindingNavigator>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f767d-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="f767d-111">在系結至<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>控制項的表單上，將控制項的屬性設定為。<xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="f767d-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="f767d-112">選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f767d-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="f767d-113">按一下智慧標籤圖像（![智慧標籤](./media/vs-winformsmttagglyph.gif "圖像 VS_WinFormSmtTagGlyph")），讓**BindingNavigator** [工作] 對話方塊出現，然後選取 [**編輯專案**]。</span><span class="sxs-lookup"><span data-stu-id="f767d-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="f767d-114">[**專案集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f767d-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="f767d-115">在 [**專案集合編輯器**] 中，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f767d-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="f767d-116">選取適當<xref:System.Windows.Forms.ToolStripSeparator>的類型<xref:System.Windows.Forms.ToolStripButton> ，然後按一下 [新增] 按鈕，以新增 a 和三個專案<xref:System.Windows.Forms.ToolStripItem> 。</span><span class="sxs-lookup"><span data-stu-id="f767d-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="f767d-117">將按鈕的屬性分別設定為 LoadButton、SaveButton 和 CancelButton。 <xref:System.Windows.Forms.ToolStripItem.Name%2A></span><span class="sxs-lookup"><span data-stu-id="f767d-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="f767d-118">將按鈕的屬性設定為 [載入]、[儲存] 和 [取消]。 <xref:System.Windows.Forms.ToolStripItem.Text%2A></span><span class="sxs-lookup"><span data-stu-id="f767d-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="f767d-119">將每<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>個按鈕的屬性設為 [**文字**]。</span><span class="sxs-lookup"><span data-stu-id="f767d-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="f767d-120">或者，您可以將此屬性設定為**Image**或**ImageAndText**，並設定要在<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性中顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="f767d-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="f767d-121">按一下 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f767d-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="f767d-122">這些按鈕會新增至<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="f767d-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="f767d-123">以滑鼠右鍵按一下表單，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="f767d-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="f767d-124">在 [程式碼編輯器] 中，尋找將資料載入資料表介面卡的程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="f767d-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="f767d-125">當您在步驟2中設定資料系結時，就會產生此程式碼。</span><span class="sxs-lookup"><span data-stu-id="f767d-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="f767d-126">程式碼應如下所示： `TableAdapterName.Fill(DataSetName.TableName)`。</span><span class="sxs-lookup"><span data-stu-id="f767d-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="f767d-127">這很可能會在表單的<xref:System.Windows.Forms.Form.Load>事件中。</span><span class="sxs-lookup"><span data-stu-id="f767d-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="f767d-128">針對<xref:System.Windows.Forms.ToolStripItem.Click>您稍早建立之**負載** <xref:System.Windows.Forms.ToolStripButton>的事件建立事件處理常式，並將此資料載入程式碼移至其中。</span><span class="sxs-lookup"><span data-stu-id="f767d-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="f767d-129">您的程式碼現在看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="f767d-129">Your code should now look similar to the following:</span></span>

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. <span data-ttu-id="f767d-130">針對<xref:System.Windows.Forms.ToolStripItem.Click>您稍早建立之**儲存**<xref:System.Windows.Forms.ToolStripButton>的事件建立事件處理常式，並撰寫程式碼以更新控制項所系結之資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="f767d-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="f767d-131">在某些情況下， <xref:System.Windows.Forms.BindingNavigator>元件已經有 [**儲存**] 按鈕，但 Windows Form 設計工具未產生任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="f767d-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="f767d-132">在這種情況下，您可以將上述程式碼<xref:System.Windows.Forms.ToolStripItem.Click>放在該按鈕的事件處理常式中，而不是<xref:System.Windows.Forms.ToolStrip>在上建立全新的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f767d-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f767d-133">不過，按鈕預設為停用，因此您必須將按鈕的<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性設定為`true` ，才能讓按鈕正常運作。</span><span class="sxs-lookup"><span data-stu-id="f767d-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="f767d-134">針對<xref:System.Windows.Forms.ToolStripItem.Click>您稍早建立的**取消** <xref:System.Windows.Forms.ToolStripButton>事件建立事件處理常式，然後撰寫程式碼以取消對所顯示資料記錄所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="f767d-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="f767d-135"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的範圍是資料列。</span><span class="sxs-lookup"><span data-stu-id="f767d-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="f767d-136">在流覽至下一個記錄之前，請先儲存您在查看該個別記錄時所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="f767d-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="f767d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f767d-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="f767d-138">BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="f767d-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="f767d-139">BindingSource 元件概觀</span><span class="sxs-lookup"><span data-stu-id="f767d-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
