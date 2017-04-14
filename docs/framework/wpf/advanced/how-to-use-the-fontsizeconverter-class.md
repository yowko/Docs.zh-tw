---
title: "如何：使用 FontSizeConverter 類別 | Microsoft Docs"
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
  - "FontSizeConverter 物件"
  - "印刷樣式, FontSizeConverter 物件"
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用 FontSizeConverter 類別
## 範例  
 本範例示範如何建立 <xref:System.Windows.FontSizeConverter> 的執行個體並用它來變更字型大小。  
  
 此範例會定義名為 `changeSize` 的自訂方法，將 <xref:System.Windows.Controls.ListBoxItem> 的內容 \(如另外的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案所定義\) 轉換為 <xref:System.Double> 的執行個體，再轉換為 <xref:System.String>。  這個方法會將 <xref:System.Windows.Controls.ListBoxItem> 傳遞至 <xref:System.Windows.FontSizeConverter> 物件，此物件再將 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 轉換為 <xref:System.Double> 的執行個體。  此值接著會以 <xref:System.Windows.Controls.TextBlock> 項目的 <xref:System.Windows.Controls.TextBlock.FontSize%2A> 屬性值傳回。  
  
 此範例會再定義第二個自訂方法，名為 `changeFamily`。  這個方法會將 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 轉換為 <xref:System.String>，然後將此值傳遞至 <xref:System.Windows.Controls.TextBlock> 項目的 <xref:System.Windows.Controls.TextBlock.FontFamily%2A> 屬性。  
  
 此範例不會執行。  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## 請參閱  
 <xref:System.Windows.FontSizeConverter>