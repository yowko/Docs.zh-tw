---
title: "自訂 Windows Form DataGridView 控制項 | Microsoft Docs"
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
  - "資料格, 自訂"
  - "DataGridView 控制項 [Windows Form], 自訂"
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 自訂 Windows Form DataGridView 控制項
`DataGridView` 控制項提供幾個屬性，可以用來調整其儲存格、資料列和資料行的外觀及基本行為 \(外觀及操作\)。  然而，如果您有超出 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的能力以外的特殊需求，您也可以透過建立自訂的儲存格、資料行和資料列，實作控制項的主控描繪或擴充它的能力。  
  
 若要自行繪製儲存格和資料列，您可以處理各種的 `DataGridView` 繪製事件。  若要修改現有的功能或提供新的功能，您可以從現有的 `DataGridViewCell`、`DataGridViewColumn` 和 `DataGridViewRow` 型別衍生以建立自己的型別。  您也可以建立衍生型別 \(Derived Type\)，在儲存格處於編輯模式時顯示所選擇的控制項，以提供新的編輯能力。  
  
## 在本節中  
 [如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 描述如何處理 <xref:System.Windows.Forms.DataGridView.CellPainting> 事件，以便手動繪製儲存格。  
  
 [如何：在 Windows Form DataGridView 控制項中自訂資料列的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 描述如何處理 <xref:System.Windows.Forms.DataGridView.RowPrePaint> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint> 事件，以便繪製具有自訂的漸層背景的資料列以及合併多個資料行的內容。  
  
 [如何：擴充儲存格和資料行的行為和外觀以自訂 Windows Form DataGridView 控制項中的儲存格和資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 描述如何建立衍生自 `DataGridViewCell` 和 `DataGridViewColumn` 的自訂型別，以便在滑鼠指標停留在儲存格上時加以反白顯示。  
  
 [如何：停用 Windows Form DataGridView 控制項按鈕資料行中的按鈕](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 描述如何建立衍生自 <xref:System.Windows.Forms.DataGridViewButtonCell> 和 <xref:System.Windows.Forms.DataGridViewButtonColumn> 的自訂型別，以便在按鈕資料行中顯示停用的按鈕。  
  
 [如何：Windows Form DataGridView 儲存格中的主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 描述如何實作 `IDataGridViewEditingControl` 介面和建立衍生自 `DataGridViewCell` 和 `DataGridViewColumn` 的自訂型別，在儲存格處於編輯模式時顯示 <xref:System.Windows.Forms.DateTimePicker> 控制項。  
  
## 參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 提供 <xref:System.Windows.Forms.DataGridViewCell> 類別的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 提供 <xref:System.Windows.Forms.DataGridViewRow> 類別的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 提供 <xref:System.Windows.Forms.DataGridViewColumn> 類別的參考文件。  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 提供 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面的參考文件。  
  
## 相關章節  
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 提供說明如何修改控制項基本外觀，以及儲存格資料之顯示格式的主題。  
  
## 請參閱  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)