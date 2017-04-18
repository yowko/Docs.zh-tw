---
title: "如何：使用設計工具設定 Windows Form DataGridView 控制項的替代資料列樣式 | Microsoft Docs"
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
  - "資料 [Windows Form], 顯示"
  - "DataGridView 控制項 [Windows Form], 資料列樣式替代條件"
  - "類似 Ledger 的格式"
  - "資料列, 替代"
  - "Windows Form, 資料列"
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用設計工具設定 Windows Form DataGridView 控制項的替代資料列樣式
表格式資料通常會顯示為類似 Ledger 的格式，其中替代資料列會有不同的背景色彩。  這個格式能讓使用者更容易分辨每一個資料列中的儲存格，特別是具有許多資料行的寬資料表。  
  
 藉由 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。  您可以使用背景色彩以外的樣式特性 \(例如，前景色彩和字型\)，區分替代資料列。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 定義替代資料列的樣式  
  
1.  在設計工具中選取 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 屬性旁邊的省略符號按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  
  
3.  在 \[**CellStyle 產生器**\] 對話方塊中，藉由設定屬性來定義樣式，並使用 \[**預覽**\] 窗格確認您的選擇。  您指定的樣式會使用在控制項中所顯示的資料列 \(以每隔一列的方式呈現\)，並從第二個資料列開始套用。  
  
4.  若要定義剩餘資料列的樣式，請使用 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 屬性重複執行步驟 2 和 3。  
  
    > [!NOTE]
    >  儲存格會使用繼承自多個屬性的樣式來加以顯示。  如需樣式繼承的詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [使用設計工具搭配 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)