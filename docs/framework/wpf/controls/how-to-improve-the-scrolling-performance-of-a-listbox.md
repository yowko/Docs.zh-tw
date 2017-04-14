---
title: "如何：改善 ListBox 的捲動效能 | Microsoft Docs"
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
  - "ListBox 控制項 [WPF], 改善捲動效能"
  - "ListBox 控制項 [WPF], 重複使用項目容器"
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：改善 ListBox 的捲動效能
如果 <xref:System.Windows.Controls.ListBox> 包含許多項目，當使用者透過使用滑鼠滾輪或是拖曳捲軸的捲動方塊，捲動 <xref:System.Windows.Controls.ListBox> 時，使用者介面的回應可能會比較慢。  藉由將 <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> 附加屬性設為 <xref:System.Windows.Controls.VirtualizationMode>，即可以改善使用者捲動時的 <xref:System.Windows.Controls.ListBox> 效能。  
  
## 範例  
  
## 描述  
 下列範例會建立 <xref:System.Windows.Controls.ListBox> 並將 <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> 設為 <xref:System.Windows.Controls.VirtualizationMode>，以改善捲動期間的效能。  
  
## 程式碼  
 [!code-xml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 下列範例顯示前述範例使用的資料。  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]