---
title: HOW TO：新增和移除使用 Windows Form TabControl 的索引標籤
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
ms.openlocfilehash: eb3c59a29c9539bcba8827e1a1e9ea807ed44826
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640726"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>HOW TO：新增和移除使用 Windows Form TabControl 的索引標籤
根據預設，<xref:System.Windows.Forms.TabControl>控制項包含兩個<xref:System.Windows.Forms.TabPage>控制項。 您可以存取這些索引標籤，透過<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。  
  
### <a name="to-add-a-tab-programmatically"></a>若要以程式設計方式加入索引標籤  
  
-   使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。  
  
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
  
### <a name="to-remove-a-tab-programmatically"></a>若要以程式設計方式移除工作索引標籤  
  
-   若要移除選取的索引標籤，請使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。  
  
     -或-  
  
-   若要移除所有索引標籤，請使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性。  
  
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
  
## <a name="see-also"></a>另請參閱
- [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)
- [如何：將控制項加入索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)
- [如何：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)
- [如何：變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
