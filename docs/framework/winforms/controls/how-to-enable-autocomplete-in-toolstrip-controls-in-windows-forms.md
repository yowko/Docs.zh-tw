---
title: "如何：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete | Microsoft Docs"
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
  - "AutoComplete, 在工具列中啟用"
  - "AutoComplete, 範例"
  - "範例 [Windows Form], 工具列"
  - "工具列 [Windows Form], AutoComplete"
  - "ToolStrip 控制項 [Windows Forms], AutoComplete"
  - "ToolStripComboBox 類別, 範例"
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete
下列程序將 <xref:System.Windows.Forms.ToolStripLabel> 與 <xref:System.Windows.Forms.ToolStripComboBox> 結合，後者可以下拉以顯示項目清單，例如最近瀏覽過的網站。  如果使用者所輸入的字元符合清單中某個項目的第一個字元，該項目會立即顯示。  
  
> [!NOTE]
>  `ToolStrip` 控制項的自動完成功能與傳統控制項 \(例如 <xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.TextBox>\) 的自動完成功能完全相同。  
  
### 若要啟用 ToolStrip 控制項中的 AutoComplete  
  
1.  建立 <xref:System.Windows.Forms.ToolStrip> 控制項並且在其中加入項目。  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
  
    ```  
  
2.  將標籤和下拉式方塊的 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemOverflow>，如此一來不論表單大小為何，清單將永遠可用。  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
  
    ```  
  
3.  將文字加入到 <xref:System.Windows.Forms.ToolStripComboBox> 控制項的項目集合中。  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
  
    ```  
  
4.  將下拉式方塊的 <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> 屬性設為 <xref:System.Windows.Forms.AutoCompleteMode>。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
  
    ```  
  
5.  將下拉式方塊的 <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> 屬性設為 <xref:System.Windows.Forms.AutoCompleteSource>。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripLabel>   
 <xref:System.Windows.Forms.ToolStripComboBox>   
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>   
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)