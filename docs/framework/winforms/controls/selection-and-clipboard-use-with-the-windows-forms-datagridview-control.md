---
title: "選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用 | Microsoft Docs"
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
  - "儲存格, 在方格中選取"
  - "剪貼簿, 在 DataGridView 控制項中"
  - "資料格, 選取儲存格"
  - "DataGridView 控制項 [Windows Form], 剪貼簿使用"
  - "DataGridView 控制項 [Windows Form], 選取儲存格"
  - "選取範圍, 在 DataGridView 控制項中"
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用
`DataGridView` 控制項提供您各種選項，以設定使用者所能用來選取儲存格、資料列和資料行的方式。  例如，您可以啟用單一或多重選取，在使用者按下儲存格時即選取整個資料列或資料行，或只有當使用者按下行首 \(這也會啟用儲存格選取\) 時才選取整個資料列或資料行。  如果您想要在選取時提供您自己的介面，可以停用一般的選取動作，再以程式設計方式處理所有的選取動作。  此外，您也可以讓使用者將選取的值複製到剪貼簿。  
  
## 在本節中  
 [Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 描述控制項中的使用者選取和程式設計選取選項。  
  
 [如何：設定 Windows Form DataGridView 控制項的選取模式](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 描述如何設定控制項，以在使用者按下儲存格時，啟用單一資料列的選取。  
  
 [如何：取得 Windows Form DataGridView 控制項中選取的儲存格、資料列和資料行](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 描述如何使用選取的儲存格、資料列和資料行集合。  
  
 [如何：讓使用者從 Windows Form DataGridView 控制項將多個儲存格複製至剪貼簿](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 描述如何在控制項中啟用剪貼簿支援。  
  
## 參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName>  
 提供 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 提供 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> 屬性的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 提供 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> 類別的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 提供 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> 類別的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 提供 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> 類別的參考文件。  
  
## 請參閱  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows Form DataGridView 控制項中的預設鍵盤和滑鼠處理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)