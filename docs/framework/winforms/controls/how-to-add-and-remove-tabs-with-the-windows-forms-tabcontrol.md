---
title: 使用 TabControl 新增和移除索引標籤
description: 瞭解如何使用 Windows Forms TabControl 控制項來新增和移除索引標籤，其中包含兩個 TabPage 控制項。 透過 TabPages 屬性存取這些索引標籤。
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
ms.openlocfilehash: 7e67d0bbc13bd7d9c8835dc6fb9b9c5c9333b8bf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618073"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="33503-104">如何：使用 Windows Form TabControl 加入和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="33503-104">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="33503-105">根據預設， <xref:System.Windows.Forms.TabControl> 控制項包含兩個 <xref:System.Windows.Forms.TabPage> 控制項。</span><span class="sxs-lookup"><span data-stu-id="33503-105">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="33503-106">您可以透過屬性存取這些索引標籤 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="33503-106">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="33503-107">以程式設計方式新增索引標籤</span><span class="sxs-lookup"><span data-stu-id="33503-107">To add a tab programmatically</span></span>  
  
- <span data-ttu-id="33503-108">使用 <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> 屬性的方法 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="33503-108">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="33503-109">以程式設計方式移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="33503-109">To remove a tab programmatically</span></span>  
  
- <span data-ttu-id="33503-110">若要移除選取的索引標籤，請使用 <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> 屬性的方法 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="33503-110">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="33503-111">-或-</span><span class="sxs-lookup"><span data-stu-id="33503-111">-or-</span></span>  
  
- <span data-ttu-id="33503-112">若要移除所有索引標籤，請使用 <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> 屬性的方法 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="33503-112">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33503-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33503-113">See also</span></span>

- [<span data-ttu-id="33503-114">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="33503-114">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="33503-115">如何：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="33503-115">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="33503-116">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="33503-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="33503-117">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="33503-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
