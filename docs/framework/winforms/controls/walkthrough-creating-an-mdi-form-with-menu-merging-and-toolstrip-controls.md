---
title: "逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單 | Microsoft Docs"
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
  - "MDI 表單"
  - "MDI 表單, 建立"
  - "MDI 表單, 逐步解說"
  - "MDI, 建立表單"
  - "多文件介面表單"
  - "工具列 [Windows Form]"
  - "ToolStrip 控制項 [Windows Forms]"
  - "ToolStripPanel 控制項 [Windows Form]"
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
<xref:System.Windows.Forms?displayProperty=fullName> 命名空間支援多重文件介面 \(MDI\) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。  MDI 表單也可以使用 <xref:System.Windows.Forms.ToolStrip> 控制項建立。  
  
 此逐步解說會示範如何將 <xref:System.Windows.Forms.ToolStripPanel> 控制項與 MDI 表單搭配使用。  這個表單也支援與子功能表的功能表合併。  下列工作會在逐步解說中說明：  
  
-   建立 Windows Form 專案  
  
-   建立表單的主功能表  \(功能表的實際名稱將會不同\)  
  
-   將 <xref:System.Windows.Forms.ToolStripPanel> 控制項加入至 \[**工具箱**\]  
  
-   建立子表單  
  
-   依照疊置順序 \(Z\-order\) 排列 <xref:System.Windows.Forms.ToolStripPanel> 控制項  
  
 完成這些工作之後，您就會擁有支援功能表合併與可移動式 <xref:System.Windows.Forms.ToolStrip> 控制項的 MDI 表單。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   具有足夠的權限，以便能夠在安裝了 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 的電腦上建立及執行 Windows Form 應用程式專案  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立名為 MdiForm 的 Windows 應用程式專案。  
  
     如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 Windows Form 設計工具中選取表單。  
  
3.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 的值設定為 `true`。  
  
## 建立主功能表  
 MDI 父表單包含了主功能表。  主功能表中有一個名為 \[**視窗**\] 的功能表項目。  您可以用 \[**視窗**\] 功能表項目來建立子表單。  子表單中的功能表項目會合併到主功能表。  
  
#### 若要建立主功能表  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.MenuStrip> 控制項拖曳到表單上。  
  
2.  將 <xref:System.Windows.Forms.ToolStripMenuItem> 加入至 <xref:System.Windows.Forms.MenuStrip> 控制項並命名為 \[視窗\]。  
  
3.  選取 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
4.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性的值設定為 `ToolStripMenuItem1`。  
  
5.  在 \[**視窗**\] 功能表項目中加入一個子項目，然後將子項目命名為 \[新增\]。  
  
6.  在 \[屬性\] 視窗中，按一下 \[**事件**\]。  
  
7.  按兩下 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
     Windows Form 設計工具會為 <xref:System.Windows.Forms.ToolStripItem.Click> 事件產生一個事件處理常式。  
  
8.  將下列程式碼插入至事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## 將 ToolStripPanel 控制項加入至工具箱  
 當您在 MDI 表單中使用 <xref:System.Windows.Forms.MenuStrip> 控制項時，必須要有 <xref:System.Windows.Forms.ToolStripPanel> 控制項。  您必須將 <xref:System.Windows.Forms.ToolStripPanel> 控制項加入至 \[**工具箱**\]，才能在 Windows Form 設計工具中建置 MDI 表單。  
  
#### 若要將 ToolStripPanel 控制項加入至工具箱  
  
1.  開啟 \[**工具箱**\]，然後按一下 \[**所有 Windows Form**\] 索引標籤，以顯示可用的 Windows Form 控制項。  
  
2.  以滑鼠右鍵按一下，開啟捷徑功能表並選取 \[**選擇項目**\]。  
  
3.  在 \[**選擇工具箱項目**\] 對話方塊中，向下捲動 \[**名稱**\] 欄直到找到 \[**ToolStripPanel**\] 為止。  
  
4.  選取 \[**ToolStripPanel**\] 旁邊的核取方塊，然後按一下 \[**確定**\]。  
  
     <xref:System.Windows.Forms.ToolStripPanel> 控制項會出現在 \[**工具箱**\] 中。  
  
## 建立子表單  
 在這個程序中，您將會定義不同的子表單類別，這個類別有自己的 <xref:System.Windows.Forms.MenuStrip> 控制項。  這個表單的功能表項目會與父表單的功能表項目合併。  
  
#### 若要定義子表單  
  
1.  加入一個名為 `ChildForm` 的新表單至專案。  
  
     如需詳細資訊，請參閱 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/zh-tw/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。  
  
2.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.MenuStrip> 控制項拖曳到子表單上。  
  
3.  按一下 <xref:System.Windows.Forms.MenuStrip> 控制項的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯項目**\]。  
  
4.  在 \[**項目集合編輯器**\] 對話方塊中，將新的 <xref:System.Windows.Forms.ToolStripMenuItem> \(命名為 ChildMenuItem\) 加入至子功能表。  
  
     如需詳細資訊，請參閱 [ToolStrip Items Collection Editor](http://msdn.microsoft.com/zh-tw/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)。  
  
## 測試表單  
  
#### 若要測試您的表單  
  
1.  按 F5 編譯並執行表單。  
  
2.  按一下 \[**視窗**\] 功能表項目以開啟功能表，然後按一下 \[**新增**\]。  
  
     在表單的 MDI 工作區 \(Client Area\) 會建立一個新的子表單。  子表單的功能表會與主功能表合併。  
  
3.  關閉子表單。  
  
     子表單的功能表會從主功能表中移除。  
  
4.  按 \[**新增**\] 數次。  
  
     因為 <xref:System.Windows.Forms.MenuStrip> 控制項的 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性已經指定，新增的子表單會自動列出在 \[**視窗**\] 功能表項目底下。  
  
## 加入 ToolStrip 支援  
 在這個程序中，您會將四個 <xref:System.Windows.Forms.ToolStrip> 控制項加入至 MDI 父表單。  每個 <xref:System.Windows.Forms.ToolStrip> 控制項都是加在停駐於表單邊緣的 <xref:System.Windows.Forms.ToolStripPanel> 控制項內。  
  
#### 若要將 ToolStrip 控制項加入至 MDI 父表單  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.ToolStripPanel> 控制項拖曳到表單上。  
  
2.  在 <xref:System.Windows.Forms.ToolStripPanel> 控制項已選取的情況下，按兩下 \[**工具箱**\] 中的 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
     <xref:System.Windows.Forms.ToolStrip> 控制項會建立在 <xref:System.Windows.Forms.ToolStripPanel> 控制項中。  
  
3.  選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。  
  
4.  在 \[屬性\] 視窗中，將控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值變更為 <xref:System.Windows.Forms.DockStyle>。  
  
     <xref:System.Windows.Forms.ToolStripPanel> 控制項便會停駐在表單的左邊，主功能表的下方。  MDI 工作區會配合 <xref:System.Windows.Forms.ToolStripPanel> 控制項調整大小。  
  
5.  重複步驟 1 到 4。  
  
     將新的 <xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在表單的上方。  
  
     這個 <xref:System.Windows.Forms.ToolStripPanel> 控制項會停駐在主功能表的下方，但是在第一個 <xref:System.Windows.Forms.ToolStripPanel> 控制項的右邊。  這個步驟說明了疊置順序在正確定位的 <xref:System.Windows.Forms.ToolStripPanel> 控制項中的重要性。  
  
6.  重複步驟 1 到 4 兩次，加入兩個 <xref:System.Windows.Forms.ToolStripPanel> 控制項。  
  
     將新的 <xref:System.Windows.Forms.ToolStripPanel> 控制項分別停駐在表單的右側和下方。  
  
## 依照疊置順序排列 ToolStripPanel 控制項  
 <xref:System.Windows.Forms.ToolStripPanel> 控制項在 MDI 表單上的停駐位置，是根據該控制項在疊置順序中的位置來決定。  您可以在 \[文件大綱\] 視窗中輕鬆地排列控制項的疊置順序。  
  
#### 若要依照疊置順序排列 ToolStripPanel 控制項  
  
1.  在 \[**檢視**\] 功能表上，按一下 \[**其他視窗**\]，然後再按 \[**文件大綱**\]。  
  
     您在上一個程序中所做的 <xref:System.Windows.Forms.ToolStripPanel> 控制項排列是不標準的，  這是因為疊置順序不正確。  請使用 \[文件大綱\] 視窗變更控制項的疊置順序。  
  
2.  在 \[文件大綱\] 視窗中，選取 \[**ToolStripPanel4**\]。  
  
3.  重複按向下箭頭按鈕，直到 \[**ToolStripPanel4**\] 位於清單的底部。  
  
     \[**ToolStripPanel4**\] 控制項會停駐在表單的底部，其他控制項的下方。  
  
4.  選取 \[**ToolStripPanel2**\]。  
  
5.  按一次向下箭頭按鈕，將這個控制項放在清單中的第三個位置。  
  
     \[**ToolStripPanel2**\] 控制項會停駐在表單的最上方，主功能表的下方，以及其他控制項的上方。  
  
6.  在 \[**文件大綱**\] 視窗中選取不同的控制項，並將它們移至疊置順序中的不同位置。  請留意疊置順序對控制項停駐位置的影響。  若要復原變更，請使用 CTRL\-Z 或 \[**編輯**\] 功能表上的 \[**復原**\]。  
  
## 檢查點  
  
#### 若要測試您的表單  
  
1.  按 F5 編譯並執行表單。  
  
2.  按一下 <xref:System.Windows.Forms.ToolStrip> 控制項的底框，並將控制項拖曳至表單上的其他位置。  
  
     您可以將 <xref:System.Windows.Forms.ToolStrip> 控制項從一個 <xref:System.Windows.Forms.ToolStripPanel> 控制項拖曳至另一個。  
  
## 後續步驟  
 在這個逐步解說中，您建立了一個使用 <xref:System.Windows.Forms.ToolStrip> 控制項和功能表合併的 MDI 父表單。  您可以將 <xref:System.Windows.Forms.ToolStrip> 系列的控制項使用在許多其他用途上：  
  
-   使用 <xref:System.Windows.Forms.ContextMenuStrip> 來為您的控制項建立捷徑功能表。  如需詳細資訊，請參閱 [ContextMenu 控制項概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   使用自動填入的標準功能表來建立表單。  如需詳細資訊，請參閱 [逐步解說：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。  
  
-   賦予您的 <xref:System.Windows.Forms.ToolStrip> 控制項專業的外觀。  如需詳細資訊，請參閱 [如何：設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [如何：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [如何：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [如何：將 MenuStrip 插入至 MDI 下拉式功能表](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)