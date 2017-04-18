---
title: "Windows Form DataGridView 控制項中的資料格式 | Microsoft Docs"
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
  - "資料 [Windows Form], 在方格中格式化"
  - "資料格, 格式化資料"
  - "DataGridView 控制項 [Windows Form], 格式化資料"
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows Form DataGridView 控制項中的資料格式
<xref:System.Windows.Forms.DataGridView> 控制項提供儲存格值與父資料行顯示的資料型別之間的自動轉換。  例如，文字方塊資料行顯示了日期、時間、數字和列舉型別值的字串代表，並將使用者輸入的字串值轉換為資料儲存所需要的型別。  
  
## 使用 DataGridViewCellStyle 類別格式化  
 <xref:System.Windows.Forms.DataGridView> 控制項透過 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別提供儲存格值的基本資料格式化。  您可以使用 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性，利用[格式化類型](../../../../docs/standard/base-types/formatting-types.md)所描述的格式規範，為目前的預設文化特性 \(Culture\) 格式化日期、時間、數字和列舉型別值。  您也可以使用 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> 屬性，格式化特定文化特性的這些值。  指定格式是用來顯示資料，以及剖析使用者透過指定格式所輸入的資料。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別提供了自動換行、文字對齊，以及 null 資料庫值的自訂顯示等等的其他格式化屬性。  如需詳細資訊，請參閱 [如何：格式化 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)。  
  
## 使用 CellFormatting 事件格式化  
 如果基本的格式化不符合您的需求，您可以在 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> 事件的處理常式中提供自訂資料格式化。  傳遞至 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> 的處理常式具有初始時包含儲存格值的 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性。  一般而言，這個值會自動轉換成顯示類型。  若要自行轉換該值，請將 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性設定為顯示類型的值。  
  
> [!NOTE]
>  如果格式字串對儲存格生效，便會覆寫您對 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性值所做的變更，除非將 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> 屬性設定為 `true`。  
  
 如果想要根據儲存格的值，為個別儲存格設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性，<xref:System.Windows.Forms.DataGridView.CellFormatting> 事件也很有用。  如需詳細資訊，請參閱 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
 如果使用者指定的值的預設剖析不符合您的需求，可以處理 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellParsing> 事件以提供自訂剖析。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [如何：格式化 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)   
 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)