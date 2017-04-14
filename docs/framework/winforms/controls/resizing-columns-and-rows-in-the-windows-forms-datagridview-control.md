---
title: "調整 Windows Form DataGridView 控制項中資料行和資料列的大小 | Microsoft Docs"
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
  - "資料行 [Windows Form], 在方格中調整大小"
  - "資料格, 調整資料行和資料列的大小"
  - "DataGridView 控制項 [Windows Form], 調整資料列和資料行的大小"
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 調整 Windows Form DataGridView 控制項中資料行和資料列的大小
`DataGridView` 控制項提供許多選項，用來自訂其資料行和資料列的調整大小行為。  通常，`DataGridView` 儲存格不會根據其內容來調整大小。  相反的，它們會裁剪掉任何大於儲存格的顯示值。  如果內容可以顯示為字串，儲存格會將它顯示在工具提示中。  
  
 依據預設，使用者可以使用滑鼠拖曳資料列、資料行和行首分割線，以顯示更多的資訊。  使用者也可以按兩下分割線，根據其內容自動調整關聯的資料列、資料行或行首群組列的大小。  
  
 `DataGridView` 控制項提供屬性、方法和事件，讓您自訂或停用所有的這些使用者操作行為。  此外，您可以用程式設計的方式調整資料列、資料行和行首的大小以符合其內容，或者您可以將它們設定為在內容變更時自動調整其大小。  您也可以將資料行設定為依據所指定的比例，自動分割控制項的可用寬度。  
  
## 在本節中  
 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 描述用來調整資料列、資料行和行首的選項。  同時，也提供與調整大小相關的屬性和方法的詳細資料，並描述常見的使用案例。  
  
 [在 Windows Form DataGridView 控制項中的資料行填入模式](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 詳細描述資料行填滿模式，並提供示範程式碼，讓您用來實驗資料行填滿模式和其他模式。  
  
 [如何：設定 Windows Form DataGridView 控制項的縮放模式](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 描述如何設定常見用途的調整大小模式。  
  
 [如何：以程式設計方式調整儲存格大小以符合 Windows Form DataGridView 控制項的內容](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 提供示範程式碼，讓您用來實驗程式設計方式的調整大小。  
  
 [如何：在 Windows Form DataGridView 控制項的內容變更時自動調整儲存格大小](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 提供示範程式碼，讓您用來實驗自動調整大小模式。  
  
## 參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
## 請參閱  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)