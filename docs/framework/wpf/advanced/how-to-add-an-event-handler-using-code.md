---
title: "如何：使用程式碼加入事件處理常式 | Microsoft Docs"
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
  - "事件處理常式, 加入"
  - "XAML, 加入事件處理常式"
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用程式碼加入事件處理常式
本範例顯示如何使用程式碼，將事件處理常式加入到項目中。  
  
 如果您要將事件處理常式加入到 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 項目，而包含項目的標記頁面已經載入，就必須使用程式碼加入處理常式。  或者，如果您完全使用程式碼來建立應用程式的項目樹狀結構，而且沒有使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 宣告任何項目，就可以呼叫特定方法，將事件處理常式加入到建構的項目樹狀結構。  
  
## 範例  
 下列範例會將新的 <xref:System.Windows.Controls.Button> 加入到原本使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 定義的現有頁面。  程式碼後置 \(Code\-Behind\) 的檔案會實作事件處理常式方法，然後將該方法當做新的事件處理常式加入到 <xref:System.Windows.Controls.Button> 上。  
  
 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] 範例會使用 `+=` 運算子，將處理常式指派給事件。  [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 事件處理模型也會使用同樣的運算子來指派處理常式。  [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 不支援使用此運算子做為加入事件處理常式的方式。  它需要使用下列其中一種方式：  
  
-   使用 <xref:System.Windows.UIElement.AddHandler%2A> 方法再加上 `AddressOf` 運算子，以參考事件處理常式實作。  
  
-   使用 `Handles` 關鍵字做為事件處理常式定義的一部分。  這裡不說明此方式；請參閱 [Visual Basic 和 WPF 事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  在原本剖析的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面中加入事件處理常式要簡單許多。  在要加入事件處理常式的物件項目內，加入名稱與要處理的事件相符的屬性。  接著將該屬性的值指定為您在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面的程式碼後置檔案中所定義的事件處理常式方法的名稱。  如需詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)或[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
## 請參閱  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)