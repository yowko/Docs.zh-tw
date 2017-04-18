---
title: "如何：在樣式中建立動畫 | Microsoft Docs"
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
  - "動畫, 屬性, 樣式內"
  - "樣式, 建立屬性動畫"
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在樣式中建立動畫
本範例示範如何建立樣式內屬性的動畫。  當您在樣式內建立動畫時，只能直接以該樣式定義的架構項目做為目標。  若要以可凍結的物件當做目標，您必須從樣式化項目的屬性「向下延伸」。  
  
 下列範例在樣式內定義了幾個動畫效果，並將這些效果套用至 <xref:System.Windows.Controls.Button>。  當使用者將滑鼠移到按鈕上方時，按鈕便會產生從不透明變成半透明再變回不透明的重複淡出效果。  當使用者將滑鼠從按鈕上移開時，按鈕就會變成完全不透明。  按一下按鈕時，按鈕的背景色彩會從橙色成白色再變回橙色。  因為用來繪製按鈕的 <xref:System.Windows.Media.SolidColorBrush> 不能做為直接目標，所以它是從按鈕的 <xref:System.Windows.Controls.Control.Background%2A> 屬性向下延伸加以存取。  
  
## 範例  
 [!code-xml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 請注意，在樣式內建立動畫時，可以指定不存在的物件做為目標。  例如，假設您的樣式使用 <xref:System.Windows.Media.SolidColorBrush> 設定按鈕的背景屬性，但是您在某一點覆寫了該樣式，並以 <xref:System.Windows.Media.LinearGradientBrush> 設定按鈕的背景。  嘗試建立 <xref:System.Windows.Media.SolidColorBrush> 的動畫不會擲回例外狀況；動畫會自動失效。  
  
 如需腳本目標語法的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  如需樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。