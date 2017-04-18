---
title: "如何：建立項目或筆刷不透明效果的動畫 | Microsoft Docs"
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
  - "動畫, Opacity 屬性"
  - "不透明度, 動畫"
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立項目或筆刷不透明效果的動畫
若要讓架構項目淡入及淡出畫面，您可以建立其 <xref:System.Windows.UIElement.Opacity%2A> 屬性的動畫，或是建立用來繪製該項目之 <xref:System.Windows.Media.Brush> \(或筆刷\) 的 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性動畫。  建立項目不透明度動畫可以讓項目及其子項目淡入及淡出畫面，但是建立用來繪製項目的筆刷動畫則讓您在決定要讓項目的哪個部分淡出時，能夠有更多的選擇。  例如，您可以建立用來繪製按鈕背景的筆刷不透明度動畫。  這個動作可以讓按鈕的背景淡入及淡出畫面，同時讓按鈕的文字完全不透明。  
  
> [!NOTE]
>  建立 <xref:System.Windows.Media.Brush> 的 <xref:System.Windows.Media.Brush.Opacity%2A> 動畫在效能上的優勢大於建立項目的 <xref:System.Windows.UIElement.Opacity%2A> 屬性動畫。  
  
 下列範例會建立兩個按鈕的動畫，使其淡入及淡出畫面。  第一個 <xref:System.Windows.Controls.Button> 的不透明度會在五秒的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 內，產生從 `1.0` 變成 `0.0` 的動畫效果。  第二個按鈕也會產生動畫，但是動畫效果是在用來繪製其 <xref:System.Windows.Controls.Control.Background%2A> 之 SolidColorBrush 的不透明度，而不是整個按鈕的不透明度上。  執行此範例時，第一個按鈕會完全淡入及淡出畫面，而第二個按鈕則只有背景會淡出及淡出畫面，  它的文字和框線仍然是完全不透明。  
  
## 範例  
 [!code-xml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 這個範例省略了程式碼。  完整的範例另外還示範如何建立 <xref:System.Windows.Media.LinearGradientBrush> 內 <xref:System.Windows.Media.Color> 的不透明度動畫。  如需完整範例，請參閱[建立項目不透明度動畫範例](http://go.microsoft.com/fwlink/?LinkID=159968) \(英文\)。