---
title: "如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd45b33fb1f99c280e126b9e601692a85da5dba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="d7988-102">如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="d7988-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="d7988-103"><xref:System.Windows.Forms.BindingNavigator>控制項是特殊用途<xref:System.Windows.Forms.ToolStrip>適用於巡覽及操作控制項在表單上的繫結至資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="d7988-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="d7988-104">因為它是<xref:System.Windows.Forms.ToolStrip>控制項，<xref:System.Windows.Forms.BindingNavigator>元件可以輕鬆地修改為包含使用者的其他或替代式命令。</span><span class="sxs-lookup"><span data-stu-id="d7988-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="d7988-105">在下列程序中，<xref:System.Windows.Forms.TextBox>控制項所繫結至資料，而<xref:System.Windows.Forms.ToolStrip>控制項加入至表單，會修改成包含載入、 儲存和取消按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7988-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="d7988-106">若要將載入、 儲存和取消按鈕 BindingNavigator 元件</span><span class="sxs-lookup"><span data-stu-id="d7988-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="d7988-107">新增 <xref:System.Windows.Forms.TextBox> 控制項至表單。</span><span class="sxs-lookup"><span data-stu-id="d7988-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="d7988-108">繫結至<xref:System.Windows.Forms.BindingSource>，它繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="d7988-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="d7988-109">例如，<xref:System.Windows.Forms.BindingSource>繫結至資料庫。</span><span class="sxs-lookup"><span data-stu-id="d7988-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="d7988-110">產生資料集和資料表配接器之後，請將<xref:System.Windows.Forms.BindingNavigator>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="d7988-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="d7988-111">設定<xref:System.Windows.Forms.BindingNavigator>控制項的<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>屬性<xref:System.Windows.Forms.BindingSource>繫結至控制項在表單上。</span><span class="sxs-lookup"><span data-stu-id="d7988-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="d7988-112">選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。</span><span class="sxs-lookup"><span data-stu-id="d7988-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="d7988-113">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 因此**BindingNavigator 工作**對話方塊出現，並選取**編輯項目**.</span><span class="sxs-lookup"><span data-stu-id="d7988-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="d7988-114">**項目集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d7988-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="d7988-115">在**項目集合編輯器**，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d7988-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="d7988-116">新增<xref:System.Windows.Forms.ToolStripSeparator>和三個<xref:System.Windows.Forms.ToolStripButton>選取適當類型的項目<xref:System.Windows.Forms.ToolStripItem>按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7988-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="d7988-117">設定<xref:System.Windows.Forms.ToolStripItem.Name%2A> 按鈕的屬性**LoadButton**，**SaveButton**，和**CancelButton**分別。</span><span class="sxs-lookup"><span data-stu-id="d7988-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to**LoadButton**,**SaveButton**, and**CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="d7988-118">設定<xref:System.Windows.Forms.ToolStripItem.Text%2A> 按鈕的屬性**負載**`,` **儲存**，和**取消**。</span><span class="sxs-lookup"><span data-stu-id="d7988-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to**Load**`,` **Save**, and**Cancel**.</span></span>  
  
    4.  <span data-ttu-id="d7988-119">設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性每個按鈕，**文字**。</span><span class="sxs-lookup"><span data-stu-id="d7988-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to**Text**.</span></span> <span data-ttu-id="d7988-120">或者，您可以將此屬性設定為**映像**或**ImageAndText**並設定要顯示在影像<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d7988-120">Alternatively, you can set this property to**Image**or**ImageAndText**and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="d7988-121">按一下**確定**以關閉對話方塊。若要加入按鈕<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="d7988-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="d7988-122">以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="d7988-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="d7988-123">在程式碼編輯器中，找到資料載入資料表配接器的程式碼的行。</span><span class="sxs-lookup"><span data-stu-id="d7988-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="d7988-124">您可以設定在步驟 2 中的資料繫結時，所產生此程式碼。</span><span class="sxs-lookup"><span data-stu-id="d7988-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="d7988-125">程式碼應該類似下列： `TableAdapterName.Fill(DataSetName.TableName)`。</span><span class="sxs-lookup"><span data-stu-id="d7988-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="d7988-126">將會使用最可能會出現在表單的<xref:System.Windows.Forms.Form.Load>事件。</span><span class="sxs-lookup"><span data-stu-id="d7988-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="d7988-127">建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**負載**<xref:System.Windows.Forms.ToolStripButton>您先前建立並將此資料載入程式碼移到它。</span><span class="sxs-lookup"><span data-stu-id="d7988-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Load**<xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="d7988-128">您的程式碼現在看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="d7988-128">Your code should now look similar to the following:</span></span>  
  
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
  
11. <span data-ttu-id="d7988-129">建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**儲存**<xref:System.Windows.Forms.ToolStripButton>您先前建立並撰寫程式碼來更新資料表控制項中的資料繫結至。</span><span class="sxs-lookup"><span data-stu-id="d7988-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
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
    >  <span data-ttu-id="d7988-130">在某些情況下，<xref:System.Windows.Forms.BindingNavigator>元件已經**儲存** 按鈕，但沒有程式碼會產生的 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="d7988-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a**Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="d7988-131">在此情況下，您可以在其中放置在上述程式碼<xref:System.Windows.Forms.ToolStripItem.Click>該按鈕，而不建立全新的按鈕上的事件處理常式<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="d7988-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="d7988-132">不過，按鈕預設會停用，因此您必須設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>按鈕的屬性`true`正確具有按鈕函式。</span><span class="sxs-lookup"><span data-stu-id="d7988-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>  
  
12. <span data-ttu-id="d7988-133">建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**取消**<xref:System.Windows.Forms.ToolStripButton>您先前建立並撰寫程式碼來取消任何顯示的資料記錄的變更。</span><span class="sxs-lookup"><span data-stu-id="d7988-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Cancel**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
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
    >  <span data-ttu-id="d7988-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的範圍為資料列。</span><span class="sxs-lookup"><span data-stu-id="d7988-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="d7988-135">儲存您在檢視該個別記錄之前瀏覽至下一筆記錄時所做的變更。</span><span class="sxs-lookup"><span data-stu-id="d7988-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7988-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7988-136">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="d7988-137">BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="d7988-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="d7988-138">BindingSource 元件概觀</span><span class="sxs-lookup"><span data-stu-id="d7988-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
