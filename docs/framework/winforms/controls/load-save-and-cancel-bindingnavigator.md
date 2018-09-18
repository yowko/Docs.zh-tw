---
title: 如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 97be77b6591e4b7fa3db8176222dcb1feb3481bc
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45972685"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="52c82-102">如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="52c82-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="52c82-103"><xref:System.Windows.Forms.BindingNavigator>控制項是特殊用途<xref:System.Windows.Forms.ToolStrip>適用於瀏覽和操作您的表單上繫結至資料的控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="52c82-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="52c82-104">因為它是<xref:System.Windows.Forms.ToolStrip>控制項，<xref:System.Windows.Forms.BindingNavigator>元件可以輕鬆地修改以包含使用者的額外或其他命令。</span><span class="sxs-lookup"><span data-stu-id="52c82-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="52c82-105">在下列程序中，<xref:System.Windows.Forms.TextBox>控制項繫結至資料，而<xref:System.Windows.Forms.ToolStrip>控制項加入至表單，會修改成包含載入、 儲存和取消按鈕。</span><span class="sxs-lookup"><span data-stu-id="52c82-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="52c82-106">若要將載入、 儲存，和 [取消] 按鈕至 BindingNavigator 元件</span><span class="sxs-lookup"><span data-stu-id="52c82-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="52c82-107">新增 <xref:System.Windows.Forms.TextBox> 控制項至表單。</span><span class="sxs-lookup"><span data-stu-id="52c82-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="52c82-108">繫結到<xref:System.Windows.Forms.BindingSource>，它會繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="52c82-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="52c82-109">此範例中，針對<xref:System.Windows.Forms.BindingSource>繫結至資料庫。</span><span class="sxs-lookup"><span data-stu-id="52c82-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="52c82-110">產生資料集和資料表配接器之後，請將<xref:System.Windows.Forms.BindingNavigator>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="52c82-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="52c82-111">設定<xref:System.Windows.Forms.BindingNavigator>控制項的<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>屬性設<xref:System.Windows.Forms.BindingSource>繫結至控制項在表單上。</span><span class="sxs-lookup"><span data-stu-id="52c82-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="52c82-112">選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。</span><span class="sxs-lookup"><span data-stu-id="52c82-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="52c82-113">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 因此**BindingNavigator 工作** 對話方塊隨即出現，並選取**編輯項目**.</span><span class="sxs-lookup"><span data-stu-id="52c82-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="52c82-114">**項目集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="52c82-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="52c82-115">在 **項目集合編輯器**，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="52c82-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="52c82-116">新增<xref:System.Windows.Forms.ToolStripSeparator>和三個<xref:System.Windows.Forms.ToolStripButton>藉由選取適當類型的項目<xref:System.Windows.Forms.ToolStripItem>，然後按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="52c82-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="52c82-117">設定<xref:System.Windows.Forms.ToolStripItem.Name%2A> 按鈕的屬性**LoadButton**， **SaveButton**，和**CancelButton**分別。</span><span class="sxs-lookup"><span data-stu-id="52c82-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="52c82-118">設定<xref:System.Windows.Forms.ToolStripItem.Text%2A> 按鈕的屬性**負載**，**儲存**，和**取消**。</span><span class="sxs-lookup"><span data-stu-id="52c82-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>  
  
    4.  <span data-ttu-id="52c82-119">設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 按鈕的每個屬性**文字**。</span><span class="sxs-lookup"><span data-stu-id="52c82-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="52c82-120">或者，您可以設定此屬性，**映像**或是**ImageAndText**，並設定要顯示在影像<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="52c82-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="52c82-121">按一下 **確定**以關閉對話方塊。按鈕會新增至<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="52c82-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="52c82-122">以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="52c82-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="52c82-123">在程式碼編輯器中，找到資料載入資料表配接器的程式碼的行。</span><span class="sxs-lookup"><span data-stu-id="52c82-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="52c82-124">當您設定在步驟 2 中的資料繫結時，所產生此程式碼。</span><span class="sxs-lookup"><span data-stu-id="52c82-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="52c82-125">程式碼應該類似下面的： `TableAdapterName.Fill(DataSetName.TableName)`。</span><span class="sxs-lookup"><span data-stu-id="52c82-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="52c82-126">它會最可能會出現在表單的<xref:System.Windows.Forms.Form.Load>事件。</span><span class="sxs-lookup"><span data-stu-id="52c82-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="52c82-127">建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件的**負載**<xref:System.Windows.Forms.ToolStripButton>您稍早建立，並將此資料載入程式碼移到它。</span><span class="sxs-lookup"><span data-stu-id="52c82-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="52c82-128">您的程式碼現在看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="52c82-128">Your code should now look similar to the following:</span></span>  
  
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
  
11. <span data-ttu-id="52c82-129">建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件的**儲存**<xref:System.Windows.Forms.ToolStripButton>您在稍早所建立，並撰寫程式碼來更新資料表控制項中的資料繫結至。</span><span class="sxs-lookup"><span data-stu-id="52c82-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
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
    > <span data-ttu-id="52c82-130">在某些情況下，<xref:System.Windows.Forms.BindingNavigator>元件已經**儲存** 按鈕，但沒有程式碼將產生的 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="52c82-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a **Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="52c82-131">在此情況下，您可以將上述程式碼中的放<xref:System.Windows.Forms.ToolStripItem.Click>該按鈕，而不是建立全新的按鈕上的事件處理常式<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="52c82-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="52c82-132">不過，按鈕預設會停用，因此您必須設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性的按鈕`true`正確有按鈕函式。</span><span class="sxs-lookup"><span data-stu-id="52c82-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>
  
12. <span data-ttu-id="52c82-133">建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件的**取消**<xref:System.Windows.Forms.ToolStripButton>您稍早建立，並撰寫程式碼來取消資料記錄顯示的任何變更。</span><span class="sxs-lookup"><span data-stu-id="52c82-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
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
    >  <span data-ttu-id="52c82-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的範圍為資料的資料列。</span><span class="sxs-lookup"><span data-stu-id="52c82-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="52c82-135">儲存您在檢視該個別記錄之前瀏覽至下一筆記錄時所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="52c82-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c82-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52c82-136">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="52c82-137">BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="52c82-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="52c82-138">BindingSource 元件概觀</span><span class="sxs-lookup"><span data-stu-id="52c82-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
