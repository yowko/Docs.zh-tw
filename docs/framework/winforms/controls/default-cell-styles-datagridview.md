---
title: "如何：使用設計工具設定 Windows Form DataGridView 控制項的預設儲存格樣式和資料格式 | Microsoft Docs"
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
  - "儲存格, 設定樣式"
  - "資料 [Windows Form], 設定格式"
  - "資料格式"
  - "DataGridView 控制項 [Windows Form], 儲存格樣式"
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：使用設計工具設定 Windows Form DataGridView 控制項的預設儲存格樣式和資料格式
<xref:System.Windows.Forms.DataGridView> 控制項可讓您為整個控制項、特定的資料行、資料列和資料行行首及替代資料列指定預設儲存格樣式和儲存格資料格式，以建立 Ledger 效果。  資料行和替代資料列所設定的預設樣式，會覆寫為整個控制項設定的預設樣式。  此外，您在程式碼中為個別資料列和儲存格設定的樣式，將會覆寫預設樣式。  
  
 如需儲存格樣式的詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  若要設定替代資料列的樣式，請參閱 [如何：使用設計工具設定 Windows Form DataGridView 控制項的替代資料列樣式](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)。  
  
 您也可以使用 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性來影響將會加入至控制項的所有資料列。  如需資料列範本的詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中使用資料列範本自訂資料列](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)。  
  
 下列程序需要 \[**Windows 應用程式**\] 專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要為控制項中的所有儲存格設定預設樣式  
  
1.  在設計工具中選取 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下在 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> 或 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> 屬性旁邊的省略按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  \[**CellStyle 產生器**\] 對話方塊便會出現。  
  
3.  藉由設定屬性來定義樣式，使用 \[**預覽**\] 窗格確認您的選擇。  
  
> [!NOTE]
>  如果已啟用視覺化樣式，目前的主題會自動設定資料列行首和資料行行首 \(不包括 <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>\) 的樣式，覆寫 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> 屬性值。  
>   
>  您可以使用設計工具為多個選取的 <xref:System.Windows.Forms.DataGridView> 控制項設定儲存格樣式，但是只有在這些控制項具有相同的儲存格樣式屬性值 \(此屬性為您想修改的儲存格樣式屬性\) 的情況下，才能這麼做。  如果任何儲存格樣式不同於該屬性，\[**CellStyle 產生器**\] 對話方塊的 \[**屬性**\] 視窗將為空白。  
  
### 若要為個別資料行中的儲存格設定預設樣式  
  
1.  以滑鼠右鍵按一下設計工具中的 <xref:System.Windows.Forms.DataGridView> 控制項，然後選擇 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  在 \[**資料行屬性**\] 方格中，按一下 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性旁邊的省略按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  \[**CellStyle 產生器**\] 對話方塊便會出現。  
  
4.  藉由設定屬性來定義樣式，使用 \[**預覽**\] 窗格確認您的選擇。  
  
### 若要格式化儲存格中的資料  
  
1.  使用其中一個先前程序來顯示與預設儲存格樣式屬性相關的 \[**CellStyle 產生器**\] 對話方塊。  
  
2.  在 \[**CellStyle 產生器**\] 對話方塊中，按一下 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性旁邊的省略按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  \[**編輯字串**\] 對話方塊便會出現。  
  
3.  選取格式類型，然後修改類型的詳細資料 \(例如，要顯示的小數位數\)，使用 \[**範例**\] 方塊確認您的選擇。  
  
4.  如果您將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至可能包含 null 值的資料來源，請填入 \[**Null 值**\] 文字方塊。  當儲存格值等於 null 參考 \(Visual Basic 中的 `Nothing`\) 或 <xref:System.DBNull.Value?displayProperty=fullName> 時，便會顯示這個值。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [如何：使用設計工具設定 Windows Form DataGridView 控制項的替代資料列樣式](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)