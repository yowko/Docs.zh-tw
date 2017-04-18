---
title: "如何：建立自訂路由事件 | Microsoft Docs"
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
  - "建立, 路由事件"
  - "事件, 傳送"
  - "路由事件, 建立"
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：建立自訂路由事件
為了讓自訂事件支援[事件路由](GTMT)，您必須使用 <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> 方法註冊 <xref:System.Windows.RoutedEvent>。  本範例示範建立自訂路由事件的基本觀念。  
  
## 範例  
 如下列範例所示，請先使用 <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> 方法註冊 <xref:System.Windows.RoutedEvent>。  依照慣例，<xref:System.Windows.RoutedEvent> 靜態欄位名稱應該以後置字元 ***Event*** 結尾。  在這個範例中，事件的名稱是 `Tap`，而事件的路由策略則是 <xref:System.Windows.RoutingStrategy>。  完成註冊呼叫之後，您可以為事件提供加入及移除 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 事件存取子。  
  
 請注意，雖然在這個範例中，事件是透過 `OnTap` 虛擬方法引發，但是引發事件的方式和事件回應變更的方式都是依據您的需求而定。  
  
 另外也請注意，基本上這個範例實作的是 <xref:System.Windows.Controls.Button> 的整個子類別；該子類別會建置成個別組件，然後再執行個體化為個別 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 頁面上的自訂類別。  這是為了說明子類別控制項可以插入由其他控制項組成之樹狀結構的概念，而在這種情況下，這些控制項上的自訂事件也具有與任何原生 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 項目完全相同的事件路由功能。  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 通道事件是以相同的方式建立，但是必須在註冊呼叫中將 <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> 設定為 <xref:System.Windows.RoutingStrategy>。  依照慣例，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的通道事件是以 "Preview" 這個字做為前置字元。  
  
 若要查看反昇事件如何運作的範例，請參閱 [處理路由事件](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)。  
  
## 請參閱  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)