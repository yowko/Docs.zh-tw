---
title: "逐步解說：對表單提供標準功能表項目 | Microsoft Docs"
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
  - "功能表項目, 標準"
  - "StatusStrip 控制項 [Windows Form]"
  - "工具列 [Windows Form], 逐步解說"
  - "ToolStrip 控制項 [Windows Forms]"
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 逐步解說：對表單提供標準功能表項目
您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項在表單中提供標準的功能表。  
  
 此逐步解說將示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立標準功能表。  當使用者選取一個功能表項目時，表單也會有回應。  下列工作會在逐步解說中說明：  
  
-   建立 Windows Form 專案  
  
-   建立標準功能表  
  
-   建立 <xref:System.Windows.Forms.StatusStrip> 控制項  
  
-   處理功能表項目的選取動作  
  
 當您完成時，您的表單將具備一個標準功能表，並且以 <xref:System.Windows.Forms.StatusStrip> 控制項來顯示選取的功能表項目。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   具有足夠的權限，以便能夠在安裝了 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 的電腦上建立及執行 Windows Form 應用程式專案  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立稱為 StandardMenuForm 的 Windows 應用程式專案。  
  
     如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 Windows Form 設計工具中選取表單。  
  
## 建立標準功能表  
 Windows Form 設計工具可以自動在 <xref:System.Windows.Forms.MenuStrip> 控制項中填入標準功能表項目。  
  
#### 若要建立標準功能表  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.MenuStrip> 控制項拖曳到表單上。  
  
2.  按一下 <xref:System.Windows.Forms.MenuStrip> 控制項的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) 並選取 \[**插入標準項目**\]。  
  
     在 <xref:System.Windows.Forms.MenuStrip> 控制項中會填入標準的功能表項目。  
  
3.  按一下 \[**檔案**\] 功能表項目，檢查其預設的功能表項目和對應的圖示。  
  
## 建立 StatusStrip 控制項  
 您可以使用 <xref:System.Windows.Forms.StatusStrip> 控制項來顯示 Windows Form 應用程式的狀態。  在這個範例中，使用者所選取的功能表項目會顯示在 <xref:System.Windows.Forms.StatusStrip> 控制項中。  
  
#### 若要建立 StatusStrip 控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.StatusStrip> 控制項拖曳到表單上。  
  
     <xref:System.Windows.Forms.StatusStrip> 控制項會自動停駐在表單下方。  
  
2.  按一下 <xref:System.Windows.Forms.StatusStrip> 控制項的下拉式按鈕，選取 \[**StatusLabel**\] 以將一個 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項加入至 <xref:System.Windows.Forms.StatusStrip> 控制項。  
  
## 處理項目的選取動作  
 處理 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件以回應使用者對功能表項目的選取動作。  
  
#### 若要處理項目選取動作  
  
1.  按一下您在 \[建立標準功能表\] 區段中建立的 \[**檔案**\] 功能表項目。  
  
2.  在 \[**屬性**\] 視窗中，按一下 \[**事件**\]。  
  
3.  按兩下 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件。  
  
     Windows Form 設計工具會為 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件產生一個事件處理常式。  
  
4.  將下列程式碼插入至事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  將 `UpdateStatus` 公用程式方法定義插入至表單中。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## 檢查點  
  
#### 若要測試您的表單  
  
1.  按 F5 編譯並執行表單。  
  
2.  按一下 \[**檔案**\] 功能表項目以開啟功能表。  
  
3.  在 \[**檔案**\] 功能表上，按一下其中一個項目將其選取。  
  
     <xref:System.Windows.Forms.StatusStrip> 控制項會顯示選取的項目。  
  
## 後續步驟  
 在這個逐步解說中，您建立了一個使用標準功能表的表單。  您可以將 <xref:System.Windows.Forms.ToolStrip> 系列的控制項使用在許多其他用途上：  
  
-   使用 <xref:System.Windows.Forms.ContextMenuStrip> 來為您的控制項建立捷徑功能表。  如需詳細資訊，請參閱 [ContextMenu 控制項概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   建立一個具有停駐的 <xref:System.Windows.Forms.ToolStrip> 控制項的多重文件介面 \(MDI\)。  如需詳細資訊，請參閱 [逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
-   賦予您的 <xref:System.Windows.Forms.ToolStrip> 控制項專業的外觀。  如需詳細資訊，請參閱 [如何：設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)