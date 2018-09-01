---
title: 如何：將 MenuStrip 附加至 MDI 父視窗 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: bfce2e5c787bd18321d1203286e98d8f75cbf173
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386074"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="fd852-102">如何：將 MenuStrip 附加至 MDI 父視窗 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="fd852-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="fd852-103">在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。</span><span class="sxs-lookup"><span data-stu-id="fd852-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="fd852-104">例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。</span><span class="sxs-lookup"><span data-stu-id="fd852-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="fd852-105">在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。</span><span class="sxs-lookup"><span data-stu-id="fd852-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="fd852-106">下列程序使用 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性，將 MDI 子功能表附加至 MDI 父功能表。</span><span class="sxs-lookup"><span data-stu-id="fd852-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="fd852-107">關閉 MDI 子視窗會將附加的功能表從 MDI 父視窗中移除。</span><span class="sxs-lookup"><span data-stu-id="fd852-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="fd852-108">另請參閱[多重文件介面 (MDI) 應用程式](https://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="fd852-108">Also see [Multiple-Document Interface (MDI) Applications](https://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="fd852-109">將功能表項目附加至 MDI 父視窗</span><span class="sxs-lookup"><span data-stu-id="fd852-109">To append a menu item to an MDI parent</span></span>  
  
1.  <span data-ttu-id="fd852-110">建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd852-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="fd852-111">將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd852-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="fd852-112">將 `Form1`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd852-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4.  <span data-ttu-id="fd852-113">將最上層功能表項目加入 `Form1`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File`。</span><span class="sxs-lookup"><span data-stu-id="fd852-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5.  <span data-ttu-id="fd852-114">將子功能表項目加入 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.Form.Text%2A> 屬性設定為 `&Open`。</span><span class="sxs-lookup"><span data-stu-id="fd852-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6.  <span data-ttu-id="fd852-115">將表單加入專案，將 <xref:System.Windows.Forms.MenuStrip> 加入表單，並將 `Form2`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd852-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="fd852-116">將最上層功能表項目加入 `Form2`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Form.Text%2A> 屬性設定為 `&Special`。</span><span class="sxs-lookup"><span data-stu-id="fd852-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8.  <span data-ttu-id="fd852-117">將兩個子功能表項目加入 `&Special` 功能表項目，並將其 <xref:System.Windows.Forms.Form.Text%2A> 屬性分別設定為 `Command&1` 和 `Command&2`。</span><span class="sxs-lookup"><span data-stu-id="fd852-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="fd852-118">將 `&Special`、`Command&1` 和 `Command&2` 功能表項目的 <xref:System.Windows.Forms.MergeAction> 屬性設定為 <xref:System.Windows.Forms.MergeAction.Append>。</span><span class="sxs-lookup"><span data-stu-id="fd852-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="fd852-119">為 `&New`<xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fd852-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="fd852-120">在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新執行個體，做為 `Form1` 的 MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="fd852-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
  
12. <span data-ttu-id="fd852-121">將類似下列程式碼範例的程式碼放入 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> 之中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fd852-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd852-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fd852-122">Compiling the Code</span></span>  
 <span data-ttu-id="fd852-123">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="fd852-123">This example requires:</span></span>  
  
-   <span data-ttu-id="fd852-124">名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。</span><span class="sxs-lookup"><span data-stu-id="fd852-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="fd852-125">`Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="fd852-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="fd852-126"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="fd852-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
