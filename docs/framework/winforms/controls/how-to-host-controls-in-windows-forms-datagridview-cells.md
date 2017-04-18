---
title: "如何：Windows Form DataGridView 儲存格中的主控制項 | Microsoft Docs"
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
  - "儲存格, 裝載控制項"
  - "控制項 [Windows Form], 在儲存格中裝載"
  - "DataGridView 控制項 [Windows Form], 在儲存格中裝載控制項"
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：Windows Form DataGridView 儲存格中的主控制項
<xref:System.Windows.Forms.DataGridView> 控制項提供許多資料行類型，讓使用者以各種不同的方式輸入和編輯值。  如果這些資料行類型不符合您輸入資料的需求，則您仍可用裝載您所選擇的控制項之儲存格來建立自己的資料行類型。  若要這樣做，您必須定義衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewCell> 的類別。  您也必須定義衍生自 <xref:System.Windows.Forms.Control> 的類別，並實作 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面。  
  
 下列程式碼範例示範如何建立行事曆資料行。  這個資料行的儲存格會在一般文字方塊中的儲存格顯示日期，但是當使用者編輯儲存格時，<xref:System.Windows.Forms.DateTimePicker> 控制項就會出現。  若要避免再次實作文字方塊顯示功能，則 `CalendarCell` 類別要衍生自 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 類別，而不是直接繼承 <xref:System.Windows.Forms.DataGridViewCell> 類別。  
  
> [!NOTE]
>  當您從 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 衍生並將新屬性加入衍生類別時，請務必覆寫 `Clone` 方法，以便於複製作業期間複製新屬性。  您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## 編譯程式碼  
 下列範例需要：  
  
-   System 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewCell>   
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>   
 <xref:System.Windows.Forms.IDataGridViewEditingControl>   
 <xref:System.Windows.Forms.DateTimePicker>   
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)