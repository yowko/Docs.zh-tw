---
title: "如何：加強 ToolStripMenuItems 的功能 | Microsoft Docs"
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
  - "核取記號, 加入至功能表"
  - "命令 [Windows Form], 在功能表上群組"
  - "影像 [Windows Form], 加入至功能表"
  - "鍵盤快速鍵, 在功能表上顯示"
  - "功能表項目, 加入核取記號"
  - "功能表項目, 加入影像"
  - "功能表項目, 顯示便捷鍵"
  - "功能表項目, 顯示快速鍵"
  - "功能表項目, 顯示分隔符號"
  - "功能表, 群組命令"
  - "分隔符號, 在功能表上顯示"
  - "ToolStripMenuItems"
  - "ToolStripMenuItems, 加入核取記號"
  - "ToolStripMenuItems, 加入影像"
  - "ToolStripMenuItems, 顯示便捷鍵"
  - "ToolStripMenuItems, 顯示快速鍵"
  - "ToolStripMenuItems, 顯示分隔線"
  - "ToolStripSeparators, 在 MenuStrips 上顯示"
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：加強 ToolStripMenuItems 的功能
您可以使用下列方式增強 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 控制項的使用性：  
  
-   加入核取記號以指定功能是否為開啟或關閉狀態 \(例如，文字處理應用程式的尺規是否需要沿著邊界顯示\)，或指示顯示的是檔案清單中的哪個檔案 \(例如在 \[**視窗**\] 功能表上\)。  
  
-   加入視覺化表示功能表命令的影像。  
  
-   顯示快速鍵以提供執行命令的鍵盤替代方法給滑鼠。  例如，按下 CTRL\+C 可執行 **Copy** 命令。  
  
-   顯示快速鍵以提供功能表巡覽的鍵盤替代方法給滑鼠。  例如，按下 ALT\+F 會選擇 \[**檔案**\] 功能表。  
  
-   顯示分隔線以群組相關的命令，並使功能表更具可讀性。  
  
### 若要顯示功能表命令上的核取記號  
  
-   將 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 屬性設定為 `true`。  
  
     這也會將 <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> 屬性設定為 `true`。  只有當您希望功能表命令不論是否已經選取，都要根據預設顯示為已核取時，才使用這個程序。  
  
### 若要顯示每按一下就會變更狀態的核取記號  
  
-   將功能表命令的 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 屬性設定為 `true`。  
  
### 若要加入影像至功能表命令  
  
-   將功能表命令的 <xref:System.Windows.Forms.ToolStripItem.Image%2A> 屬性設定為影像名稱。  如果這個功能表命令的 <xref:System.Windows.Forms.ToolStripItemDisplayStyle> 屬性是設定為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle> 或 <xref:System.Windows.Forms.ToolStripItemDisplayStyle> 時，就不會顯示該影像。  
  
> [!NOTE]
>  如果您加以選擇的話，影像邊界也可以顯示核取記號。  此外，您可將影像的 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 屬性設定為 `true`，影像便會在執行階段時周圍會出現規劃的框線。  
  
### 若要顯示功能表命令的快速鍵  
  
-   將功能表命令的 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> 屬性設定為想要的鍵盤組合 \(例如 \[**開啟**\] 功能表的 CTRL\+O\)，並將 <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> 屬性設定為 `true`。  
  
### 若要顯示功能表命令的自訂快速鍵  
  
-   將功能表命令的 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> 屬性設定為想要的鍵盤組合 \(例如 CTRL\+SHIFT\+O，而不是 SHIFT\+CTRL\+O\)，並將 <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> 屬性設定為 `true`。  
  
### 若要顯示功能表命令的便捷鍵  
  
-   當您設定功能表命令的 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性時，請在想要加上底線做為便捷鍵 \(Access Key\) 的字母前面輸入連字號 \(&\)。  例如，輸入  `&Open`  做為功能表命令的 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性，將會產生以 \[開啟\(**O**\)\] 字樣出現的功能表命令。  
  
     若要巡覽至這個功能表命令，請按 ALT 鍵以提供焦點給 <xref:System.Windows.Forms.MenuStrip>，並按下功能表名稱的便捷鍵。  當功能表開啟並顯示具有便捷鍵的項目時，只需要按下便捷鍵即可選取該功能表命令。  
  
> [!NOTE]
>  避免定義重複的便捷鍵，例如在同一個功能表系統中定義兩次 ALT\+F。  無法保證重複便捷鍵的選取順序。  
  
### 若要顯示功能表命令之間的分隔線  
  
-   在您定義 <xref:System.Windows.Forms.MenuStrip> 和其包含的項目之後，請使用 <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> 或 <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> 方法，用您想要的順序將功能表命令和 <xref:System.Windows.Forms.ToolStripSeparator> 控制項加入至 <xref:System.Windows.Forms.MenuStrip>。  
  
     \[Visual Basic\]  
  
    ```  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
  
    ```  
  
     \[C\#\]  
  
    ```  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)