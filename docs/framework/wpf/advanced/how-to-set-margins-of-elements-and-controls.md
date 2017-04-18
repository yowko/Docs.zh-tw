---
title: "如何：設定項目和控制項的邊界 | Microsoft Docs"
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
  - "Margin 屬性, 設定"
  - "屬性, Margin 屬性"
  - "設定, Margin 屬性"
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：設定項目和控制項的邊界
本範例說明如何變更程式碼後置 \(Code\-Behind\) 中任何現有的邊界屬性值，以便設定 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性。  <xref:System.Windows.FrameworkElement.Margin%2A> 屬性是 <xref:System.Windows.FrameworkElement> 基底項目的屬性，因此各種控制項和其他項目都會繼承這個屬性。  
  
 這個範例是以[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 撰寫，其中包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 所參考的程式碼後置檔案。  該程式碼後置同時顯示成 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 和 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 版本。  
  
## 範例  
 [!code-xml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]