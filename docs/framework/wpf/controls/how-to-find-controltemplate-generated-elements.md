---
title: "如何：尋找 ControlTemplate 產生的項目 | Microsoft Docs"
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
  - "ControlTemplates [WPF], 尋找項目"
  - "尋找 ControlTemplate 項目"
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：尋找 ControlTemplate 產生的項目
這個範例顯示如何尋找 <xref:System.Windows.Controls.ControlTemplate> 產生的項目。  
  
## 範例  
 下列範例顯示用以建立 <xref:System.Windows.Controls.Button> 類別之簡單 <xref:System.Windows.Controls.ControlTemplate> 的樣式：  
  
 [!code-xml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 若要在套用範本之後尋找該範本內的項目，則可以呼叫 <xref:System.Windows.Controls.Control.Template%2A> 的 <xref:System.Windows.FrameworkTemplate.FindName%2A> 方法。  下列範例會建立訊息方塊，以顯示控制項樣板內之 <xref:System.Windows.Controls.Grid> 的實際寬度值：  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## 請參閱  
 [尋找 DataTemplate 產生的項目](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)   
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)