---
title: "如何：使用 Windows Form TabControl 加入和移除索引標籤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "索引標籤頁"
  - "TabControl 控制項 [Windows Form], 加入和移除索引標籤"
  - "TabPage 控制項"
  - "索引標籤, 加入至網頁"
  - "索引標籤, 從頁面中移除"
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用 Windows Form TabControl 加入和移除索引標籤
依據預設，<xref:System.Windows.Forms.TabControl> 控制項包含兩個 <xref:System.Windows.Forms.TabPage> 控制項。  您可以透過 <xref:System.Windows.Forms.TabControl.TabPages%2A> 屬性存取這些索引標籤。  
  
### 若要以程式設計方式加入索引標籤  
  
-   使用 <xref:System.Windows.Forms.TabControl.TabPages%2A> 屬性的 <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> 方法。  
  
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
  
### 若要以程式設計方式移除索引標籤  
  
-   若要移除選取的索引標籤，請使用 <xref:System.Windows.Forms.TabControl.TabPages%2A> 屬性的 <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> 方法。  
  
     \-或\-  
  
-   若要移除所有索引標籤，請使用 <xref:System.Windows.Forms.TabControl.TabPages%2A> 屬性的 <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> 方法。  
  
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
  
## 請參閱  
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [如何：將控制項加入至索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [如何：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [如何：變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)