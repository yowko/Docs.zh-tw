---
title: 如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: c87ffadaef2842f10d40f6fd84eb1c70c6dfe37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530818"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="de3a3-102">如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="de3a3-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="de3a3-103">使用多重文件介面 (MDI) 建立應用程式，可以開啟數個文件在相同的時間和複製並貼至另一份文件內容。</span><span class="sxs-lookup"><span data-stu-id="de3a3-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="de3a3-104">此程序會示範如何建立父視窗功能表上的所有作用中的子表單清單。</span><span class="sxs-lookup"><span data-stu-id="de3a3-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="de3a3-105">若要在 MenuStrip 建立 MDI 視窗清單</span><span class="sxs-lookup"><span data-stu-id="de3a3-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1.  <span data-ttu-id="de3a3-106">建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="de3a3-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="de3a3-107">將 <xref:System.Windows.Forms.MenuStrip> 加入表單。</span><span class="sxs-lookup"><span data-stu-id="de3a3-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3.  <span data-ttu-id="de3a3-108">將兩個最上層功能表項目加入<xref:System.Windows.Forms.MenuStrip>並設定其<xref:System.Windows.Forms.Control.Text%2A>屬性`&File`和`&Window`。</span><span class="sxs-lookup"><span data-stu-id="de3a3-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4.  <span data-ttu-id="de3a3-109">將子功能表項目加入 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&Open`。</span><span class="sxs-lookup"><span data-stu-id="de3a3-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5.  <span data-ttu-id="de3a3-110">設定<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性<xref:System.Windows.Forms.MenuStrip>至`&Window` <xref:System.Windows.Forms.ToolStripMenuItem>。</span><span class="sxs-lookup"><span data-stu-id="de3a3-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6.  <span data-ttu-id="de3a3-111">將表單加入專案，並加入您想要的控制項，例如另一個<xref:System.Windows.Forms.MenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="de3a3-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7.  <span data-ttu-id="de3a3-112">為 `&New`<xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="de3a3-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8.  <span data-ttu-id="de3a3-113">在事件處理常式中，插入類似下列的建立和顯示的新執行個體的程式碼`Form2`的 MDI 子系`Form1`。</span><span class="sxs-lookup"><span data-stu-id="de3a3-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. <span data-ttu-id="de3a3-114">將放在下列類似的程式碼`&New`<xref:System.Windows.Forms.ToolStripMenuItem>以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="de3a3-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de3a3-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="de3a3-115">Compiling the Code</span></span>  
 <span data-ttu-id="de3a3-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="de3a3-116">This example requires:</span></span>  
  
-   <span data-ttu-id="de3a3-117">名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。</span><span class="sxs-lookup"><span data-stu-id="de3a3-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="de3a3-118">`Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="de3a3-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="de3a3-119"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="de3a3-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3a3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de3a3-120">See Also</span></span>  
 [<span data-ttu-id="de3a3-121">操作說明：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="de3a3-121">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="de3a3-122">操作說明：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="de3a3-122">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="de3a3-123">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="de3a3-123">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
