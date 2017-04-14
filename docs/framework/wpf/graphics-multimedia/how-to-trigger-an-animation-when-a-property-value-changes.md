---
title: "如何：當屬性值變更時觸發動畫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動畫, 在屬性值變更時啟動"
  - "分鏡腳本, 在屬性值變更時啟動"
  - "觸發動畫"
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：當屬性值變更時觸發動畫
本範例顯示如何使用 <xref:System.Windows.Trigger>，在屬性值變更時啟動 <xref:System.Windows.Media.Animation.Storyboard>。  您可以在 <xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate> 或 <xref:System.Windows.DataTemplate> 內使用 <xref:System.Windows.Trigger>。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Trigger>，在 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.UIElement.IsMouseOver%2A> 屬性變成 `true` 時將它的 <xref:System.Windows.UIElement.Opacity%2A> 顯示為動畫。  
  
 [!code-xml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 由屬性 <xref:System.Windows.Trigger> 物件套用的動畫，行為比 <xref:System.Windows.EventTrigger> 動畫或使用 <xref:System.Windows.Media.Animation.Storyboard> 方法啟動的動畫更為複雜。  它們以其他 <xref:System.Windows.Trigger> 物件定義，但是是由 <xref:System.Windows.EventTrigger> 和方法觸發動畫組成的動畫「傳遞」。  
  
## 請參閱  
 <xref:System.Windows.Trigger>   
 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)