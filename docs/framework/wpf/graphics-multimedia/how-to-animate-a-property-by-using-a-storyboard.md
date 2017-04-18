---
title: "如何：使用腳本建立屬性的動畫 | Microsoft Docs"
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
  - "動畫, 分鏡腳本"
  - "分鏡腳本, 動畫"
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用腳本建立屬性的動畫
本範例說明如何使用 <xref:System.Windows.Media.Animation.Storyboard>，將屬性顯示為動畫。  若要使用 <xref:System.Windows.Media.Animation.Storyboard> 將屬性顯示為動畫，請針對要顯示為動畫的每個屬性建立動畫，另外再建立 <xref:System.Windows.Media.Animation.Storyboard> 來包含動畫。  
  
 屬性的型別會決定要使用的動畫型別。  例如，若要將接受 <xref:System.Double> 值的屬性顯示為動畫，請使用 <xref:System.Windows.Media.Animation.DoubleAnimation>。  <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> [附加屬性](GTMT)會指定要套用動畫的物件和屬性。  
  
 若要在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中啟動腳本，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作和 <xref:System.Windows.EventTrigger>。  當 <xref:System.Windows.EventTrigger.RoutedEvent%2A> 屬性指定的事件發生時，<xref:System.Windows.EventTrigger> 會開始進行 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作。  <xref:System.Windows.Media.Animation.BeginStoryboard> 動作即會啟動 <xref:System.Windows.Media.Animation.Storyboard>。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.Storyboard> 物件，將兩個 <xref:System.Windows.Controls.Button> 控制項顯示為動畫。  為了讓第一個按鈕變更大小，會將其 <xref:System.Windows.FrameworkElement.Width%2A> 顯示為動畫。  為了讓第二個按鈕變更色彩，會使用 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性，設定顯示為動畫之按鈕的 <xref:System.Windows.Controls.Control.Background%2A>。  
  
## 範例  
 [!code-xml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  雖然動畫可以同時將 <xref:System.Windows.FrameworkElement> 物件 \(<xref:System.Windows.Controls.Control> 或 <xref:System.Windows.Controls.Panel>\) 以及 <xref:System.Windows.Freezable> 物件 \(<xref:System.Windows.Media.Brush> 或 <xref:System.Windows.Media.Transform>\) 設為目標，但只有架構項目會有 <xref:System.Windows.FrameworkElement.Name%2A> 屬性。  若要將名稱指派給 Freezable，使其成為動畫的目標，請使用 [x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)，如前述範例所示。  
  
 如果您使用程式碼，則必須為 <xref:System.Windows.FrameworkElement> 建立 <xref:System.Windows.NameScope>，並將要顯示為動畫之物件的名稱向該 <xref:System.Windows.FrameworkElement> 註冊。  若要在程式碼中啟動動畫，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作和 <xref:System.Windows.EventTrigger>。  或者，您也可以使用事件處理常式和 <xref:System.Windows.Media.Animation.Storyboard> 的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  下列範例示範如何使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 如需動畫和腳本的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 如果您使用程式碼，則要將屬性顯示為動畫的方式，並不限於使用 <xref:System.Windows.Media.Animation.Storyboard> 物件。  如需詳細資訊與範例，請參閱 [不使用腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)與 [使用 AnimationClock 建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)。