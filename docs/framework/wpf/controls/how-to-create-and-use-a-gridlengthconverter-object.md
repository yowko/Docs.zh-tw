---
title: "如何：建立和使用 GridLengthConverter 物件 | Microsoft Docs"
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
  - "Grid 控制項, 建立, GridLengthConverter 物件"
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立和使用 GridLengthConverter 物件
## 範例  
 下列範例會示範如何建立和使用 <xref:System.Windows.GridLengthConverter> 的執行個體。  此範例會先定義 `changeCol` 這個方法，將 <xref:System.Windows.Controls.ListBoxItem> 傳送到 <xref:System.Windows.GridLengthConverter> 來將 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 轉換為 <xref:System.Windows.GridLength> 的執行個體。  然後，已轉換的值會傳回為 <xref:System.Windows.Controls.ColumnDefinition> 項目的 <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 屬性。  
  
 此範例也會定義名為 `changeColVal` 第二個自訂方法。  這個自訂方法會將 <xref:System.Windows.Controls.Slider> 的 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 轉換為 <xref:System.String>，然後便會將該值傳回 <xref:System.Windows.Controls.ColumnDefinition>，做為項目的 <xref:System.Windows.Controls.ColumnDefinition.Width%2A>。  
  
 請注意，個別的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案會定義 <xref:System.Windows.Controls.ListBoxItem> 的內容。  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.GridLengthConverter>   
 <xref:System.Windows.GridLength>