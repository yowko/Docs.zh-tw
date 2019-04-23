---
title: HOW TO：使用 Windows Forms TabControl 新增和移除索引標籤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 723e05803b1f7d2bc56476248987085dbe5e23f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101597"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="c78ca-102">HOW TO：使用 Windows Forms TabControl 新增和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="c78ca-102">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="c78ca-103">根據預設，<xref:System.Windows.Forms.TabControl>控制項包含兩個<xref:System.Windows.Forms.TabPage>控制項。</span><span class="sxs-lookup"><span data-stu-id="c78ca-103">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="c78ca-104">您可以存取這些索引標籤，透過<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c78ca-104">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="c78ca-105">若要以程式設計方式加入索引標籤</span><span class="sxs-lookup"><span data-stu-id="c78ca-105">To add a tab programmatically</span></span>  
  
-   <span data-ttu-id="c78ca-106">使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c78ca-106">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="c78ca-107">若要以程式設計方式移除工作索引標籤</span><span class="sxs-lookup"><span data-stu-id="c78ca-107">To remove a tab programmatically</span></span>  
  
-   <span data-ttu-id="c78ca-108">若要移除選取的索引標籤，請使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c78ca-108">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="c78ca-109">-或-</span><span class="sxs-lookup"><span data-stu-id="c78ca-109">-or-</span></span>  
  
-   <span data-ttu-id="c78ca-110">若要移除所有索引標籤，請使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c78ca-110">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c78ca-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c78ca-111">See also</span></span>

- [<span data-ttu-id="c78ca-112">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="c78ca-112">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="c78ca-113">如何：將控制項加入索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="c78ca-113">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="c78ca-114">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="c78ca-114">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="c78ca-115">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="c78ca-115">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
