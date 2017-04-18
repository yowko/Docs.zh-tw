---
title: "如何：使用 ThicknessConverter 物件 | Microsoft Docs"
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
  - "框線粗細"
  - "ThicknessConverter 物件"
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用 ThicknessConverter 物件
## 範例  
 本範例說明如何建立 <xref:System.Windows.ThicknessConverter> 的執行個體並用它來變更框線粗細。  
  
 這個範例會定義一個名為 `changeThickness` 的自訂方法；這個方法會先將 <xref:System.Windows.Controls.ListBoxItem> 的內容 \(如另一個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案所定義\) 轉換為 <xref:System.Windows.Thickness> 的執行個體，然後再將內容轉換為 <xref:System.String>。  這個方法會將 <xref:System.Windows.Controls.ListBoxItem> 傳遞至 <xref:System.Windows.ThicknessConverter> 物件，此物件再將 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 轉換為 <xref:System.Windows.Thickness> 的執行個體。  此值接著會以 <xref:System.Windows.Controls.Border> 的 <xref:System.Windows.Controls.Border.BorderThickness%2A> 屬性值傳回。  
  
 此範例不會執行。  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Thickness>   
 <xref:System.Windows.ThicknessConverter>   
 <xref:System.Windows.Controls.Border>   
 [How to: Change the Margin Property](http://msdn.microsoft.com/zh-tw/8a313efd-5f99-4097-b4c1-8fa49d8379a2)   
 [How to: Convert a ListBoxItem to a new Data Type](http://msdn.microsoft.com/zh-tw/7a080b88-184e-4b27-bb61-d42bafba9727)   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)