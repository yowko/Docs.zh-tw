---
title: "如何：變更游標類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "游標 (滑鼠指標)"
  - "滑鼠指標 (游標), 游標類型"
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：變更游標類型
本範例示範如何為特定項目和應用程式變更滑鼠指標的 <xref:System.Windows.Input.Cursor>。  
  
 本範例包含一個 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案和一個程式碼後置 \(Code\-Behind\) 的檔案。  
  
## 範例  
 這會建立使用者介面，其中包含一個 <xref:System.Windows.Controls.ComboBox> \(可選取所需的 <xref:System.Windows.Input.Cursor>\)、一組 <xref:System.Windows.Controls.RadioButton> 物件 \(以決定游標變更是要套用到單一項目或整個應用程式\)，以及一個 <xref:System.Windows.Controls.Border>，這是要套用新游標的項目。  
  
 [!code-xml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 下列程式碼後置會建立一個 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 處理常式，當 <xref:System.Windows.Controls.ComboBox> 中的游標類型變更時，會呼叫該處理常式。  switch 陳述式會篩選游標名稱，並設定名為 *DisplayArea* 的 <xref:System.Windows.Controls.Border> 上的 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性。  
  
 如果游標變更為 "Entire Application"，<xref:System.Windows.Input.Mouse.OverrideCursor%2A> 屬性會設為 <xref:System.Windows.Controls.Border> 控制項的 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性。  這會強制整個應用程式的游標變更。  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## 請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)