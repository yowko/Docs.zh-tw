---
title: "如何：對控制項套用 FocusVisualStyle | Microsoft Docs"
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
  - "FocusVisualStyle 屬性"
  - "屬性, FocusVisualStyle"
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：對控制項套用 FocusVisualStyle
本範例示範如何使用 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性在資源中建立焦點視覺化樣式，並將該樣式套用至控制項。  
  
## 範例  
 下列範例定義可用來建立額外控制項複合的樣式；此複合只有當該控制項在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中取得鍵盤焦點時才適用。  這項作業的完成方式是使用 <xref:System.Windows.Controls.ControlTemplate> 定義樣式，然後在設定 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性時將該樣式當做資源參考。  
  
 矩形區域外面會加上類似框線的外圍矩形。  除非另行修改，否則樣式的大小都會使用已套用焦點視覺化樣式之矩形控制項的 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 和 <xref:System.Windows.FrameworkElement.ActualWidth%2A>。  這個範例會設定負數值做為 <xref:System.Windows.FrameworkElement.Margin%2A>，讓框線顯示在焦點控制項向外一點的位置。  
  
 [!code-xml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 可附加至來自明確樣式或佈景主題樣式的任何控制項樣板樣式；控制項的主要樣式仍然可以透過使用 <xref:System.Windows.Controls.ControlTemplate>，並將該樣式設定為 <xref:System.Windows.FrameworkElement.Style%2A> 屬性的方式來建立。  
  
 在整個主題佈景或 UI 中，應該使用一致的焦點視覺化樣式，而不是每個可焦點化項目分別使用一種不同的樣式。  如需詳細資訊，請參閱[設定控制項中焦點的樣式和 FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [設定控制項中焦點的樣式和 FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)