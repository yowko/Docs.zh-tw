---
title: HOW TO：將 MenuStrip 插入至 MDI 下拉式功能表 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 1b41699d8da1c99705f6796105dab6f3ab1d727d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341630"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="06019-102">HOW TO：將 MenuStrip 插入至 MDI 下拉式功能表 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="06019-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="06019-103">在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。</span><span class="sxs-lookup"><span data-stu-id="06019-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="06019-104">例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。</span><span class="sxs-lookup"><span data-stu-id="06019-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="06019-105">在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。</span><span class="sxs-lookup"><span data-stu-id="06019-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="06019-106">使用下列程序<xref:System.Windows.Forms.Form.IsMdiContainer%2A>， <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>， <xref:System.Windows.Forms.MergeAction>，和<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>屬性，以從 MDI 子功能表中插入 MDI 父功能表的下拉式部分的功能表項目群組。</span><span class="sxs-lookup"><span data-stu-id="06019-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="06019-107">關閉 MDI 子視窗，是在 MDI 父視窗中移除插入的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="06019-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="06019-108">若要將 MenuStrip 插入至 MDI 下拉式功能表</span><span class="sxs-lookup"><span data-stu-id="06019-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="06019-109">建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="06019-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="06019-110">將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="06019-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="06019-111">將最上層功能表項目加入 `Form1`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File`。</span><span class="sxs-lookup"><span data-stu-id="06019-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="06019-112">將三個的子功能表項目加入`&File`功能表項目和設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&Open`， `&Import from`，和`E&xit`。</span><span class="sxs-lookup"><span data-stu-id="06019-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="06019-113">將兩個的子功能表項目加入`&Import from`子功能表項目和設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&Word`和`&Excel`。</span><span class="sxs-lookup"><span data-stu-id="06019-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="06019-114">將表單加入專案，將 <xref:System.Windows.Forms.MenuStrip> 加入表單，並將 `Form2`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="06019-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="06019-115">將最上層功能表項目加入 `Form2`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&File`。</span><span class="sxs-lookup"><span data-stu-id="06019-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="06019-116">將子功能表項目加入`&File`功能表`Form2`順序如下： <xref:System.Windows.Forms.ToolStripSeparator>， `&Save`， `Save and &Close`，和另一個<xref:System.Windows.Forms.ToolStripSeparator>。</span><span class="sxs-lookup"><span data-stu-id="06019-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="06019-117">設定<xref:System.Windows.Forms.MergeAction>並<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>屬性的`Form2`下表所示的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="06019-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="06019-118">Form2 功能表項目</span><span class="sxs-lookup"><span data-stu-id="06019-118">Form2 menu item</span></span>|<span data-ttu-id="06019-119">MergeAction 值</span><span class="sxs-lookup"><span data-stu-id="06019-119">MergeAction value</span></span>|<span data-ttu-id="06019-120">MergeIndex 值</span><span class="sxs-lookup"><span data-stu-id="06019-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="06019-121">檔案</span><span class="sxs-lookup"><span data-stu-id="06019-121">File</span></span>|<span data-ttu-id="06019-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="06019-122">MatchOnly</span></span>|<span data-ttu-id="06019-123">-1</span><span class="sxs-lookup"><span data-stu-id="06019-123">-1</span></span>|  
    |<span data-ttu-id="06019-124">Separator</span><span class="sxs-lookup"><span data-stu-id="06019-124">Separator</span></span>|<span data-ttu-id="06019-125">Insert</span><span class="sxs-lookup"><span data-stu-id="06019-125">Insert</span></span>|<span data-ttu-id="06019-126">2</span><span class="sxs-lookup"><span data-stu-id="06019-126">2</span></span>|  
    |<span data-ttu-id="06019-127">儲存</span><span class="sxs-lookup"><span data-stu-id="06019-127">Save</span></span>|<span data-ttu-id="06019-128">Insert</span><span class="sxs-lookup"><span data-stu-id="06019-128">Insert</span></span>|<span data-ttu-id="06019-129">3</span><span class="sxs-lookup"><span data-stu-id="06019-129">3</span></span>|  
    |<span data-ttu-id="06019-130">儲存並關閉</span><span class="sxs-lookup"><span data-stu-id="06019-130">Save and Close</span></span>|<span data-ttu-id="06019-131">Insert</span><span class="sxs-lookup"><span data-stu-id="06019-131">Insert</span></span>|<span data-ttu-id="06019-132">4</span><span class="sxs-lookup"><span data-stu-id="06019-132">4</span></span>|  
    |<span data-ttu-id="06019-133">Separator</span><span class="sxs-lookup"><span data-stu-id="06019-133">Separator</span></span>|<span data-ttu-id="06019-134">Insert</span><span class="sxs-lookup"><span data-stu-id="06019-134">Insert</span></span>|<span data-ttu-id="06019-135">5</span><span class="sxs-lookup"><span data-stu-id="06019-135">5</span></span>|  
  
10. <span data-ttu-id="06019-136">為 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="06019-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="06019-137">在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新執行個體，做為 `Form1` 的 MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="06019-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="06019-138">將類似下列程式碼範例的程式碼放入 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> 之中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="06019-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06019-139">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="06019-139">Compiling the Code</span></span>  
 <span data-ttu-id="06019-140">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="06019-140">This example requires:</span></span>  
  
-   <span data-ttu-id="06019-141">名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。</span><span class="sxs-lookup"><span data-stu-id="06019-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="06019-142">`Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="06019-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="06019-143"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="06019-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06019-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06019-144">See also</span></span>

- [<span data-ttu-id="06019-145">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="06019-145">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="06019-146">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="06019-146">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="06019-147">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="06019-147">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
