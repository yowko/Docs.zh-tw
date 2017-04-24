---
title: "動畫概觀 | Microsoft Docs"
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
  - "分鏡腳本 [WPF] 中動畫"
  - "動畫 [WPF] 概觀"
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
caps.latest.revision: 73
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 73
---
# 動畫概觀
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供一組強大的圖形和版面配置功能，可讓您建立吸引人的使用者介面和吸引人的文件。 動畫可以吸引人的使用者介面，更美觀而實用。 藉由只製作背景色彩，或套用動態<xref:System.Windows.Media.Transform>，您可以建立大幅畫面轉換或提供很有幫助的視覺提示。  
  
 本概觀介紹[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫和計時系統。 將重點放在動畫效果的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件使用的分鏡腳本。  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>動畫簡介  
 動畫是建立快速循環，透過一系列的映像，最後一個稍有不同的視覺效果。 大腦會視為單一變化場景中之影像的群組。 在影片中，會使用數位相機會記錄許多照片或框架，每秒建立此假象。 當畫面格播放投影機時，觀眾所看到的移動圖片。  
  
 動畫的電腦上很類似。 比方說，讓繪製的矩形區域淡出檢視之外的程式可能運作，如下所示。  
  
-   程式會建立計時器。  
  
-   程式會檢查計時器設定的間隔，以查看經過多少時間。  
  
-   每當，程式會檢查計時器，它會計算目前的不透明度值經過多少時間為基礎的矩形。  
  
-   然後程式更新為新值的矩形，並重新繪製。  
  
 之前[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]開發人員必須建立及管理自己的計時系統或使用特殊的自訂程式庫。                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]包含透過 managed 程式碼公開一個有效率的計時系統以及[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和已完全整合至[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]架構。                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫可讓您輕鬆地建立控制項和其他圖形物件的動畫。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]處理管理計時系統以及有效地重繪螢幕的幕後工作。 它提供時間類別，可讓您專注於您想要建立，而不是專注在達成這些效果的效果。                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也方便您建立您自己的動畫，藉由公開動畫類別可以繼承的基底類別，以產生自訂的動畫。 這些自訂動畫獲得許多標準的動畫類別的效能優勢。  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>WPF 屬性動畫系統  
 如果您了解一些重要概念的計時系統[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫可能會更容易使用。 最重要的是，在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您將動畫套用至其個別的屬性動畫顯示物件。 比方說，若要讓架構項目的成長，您以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。 若要讓物件淡出畫面，您以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性。  
  
 對於具備動畫功能的屬性，它必須符合下列三個需求︰  
  
-   它必須是相依性屬性。  
  
-   它必須屬於類別繼承自<xref:System.Windows.DependencyObject>並實作<xref:System.Windows.Media.Animation.IAnimatable>介面。  
  
-   必須有相容的動畫類型使用。 (如果[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不提供憑證，您可以建立您自己。 請參閱[自訂動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)。)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]包含許多物件具有<xref:System.Windows.Media.Animation.IAnimatable>屬性。 控制項例如<xref:System.Windows.Controls.Button>和<xref:System.Windows.Controls.TabControl>，以及<xref:System.Windows.Controls.Panel>和<xref:System.Windows.Shapes.Shape>物件繼承自<xref:System.Windows.DependencyObject>。 大部分的屬性是相依性屬性。  
  
 您可以使用動畫幾乎任何地方，其中包括樣式和控制項範本中。 動畫就不必是視覺化。您可以動畫顯示它們是否符合本節所述的準則不屬於使用者介面的物件。  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>範例︰ 使項目淡出，或離開檢視表  
 這個範例示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫來製作動畫的相依性屬性的值。 它會使用<xref:System.Windows.Media.Animation.DoubleAnimation>，這是一種會產生的動畫<xref:System.Double>值，以動畫顯示<xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Shapes.Rectangle>。 如此一來，<xref:System.Windows.Shapes.Rectangle>淡入和移出檢視。  
  
 此範例的第一個部分會建立<xref:System.Windows.Shapes.Rectangle>項目。 請依照下列步驟示範如何建立動畫，並將它套用到矩形<xref:System.Windows.UIElement.Opacity%2A>屬性。  
  
 下圖顯示如何建立<xref:System.Windows.Shapes.Rectangle>中的項目<xref:System.Windows.Controls.StackPanel>在 XAML 中。  
  
 [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 下圖顯示如何建立<xref:System.Windows.Shapes.Rectangle>中的項目<xref:System.Windows.Controls.StackPanel>程式碼中。  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>第 1 部份︰ 建立 DoubleAnimation  
 若要讓淡入和移出檢視項目之一是以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性。 因為<xref:System.Windows.UIElement.Opacity%2A>屬性屬於型別<xref:System.Double>，您需要的動畫，會產生雙精度浮點數值。 A <xref:System.Windows.Media.Animation.DoubleAnimation>是一個這類動畫。 A <xref:System.Windows.Media.Animation.DoubleAnimation>會建立兩個雙精度浮點數值之間的轉換。 若要指定起始值，設定其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性。 若要指定其結束值，設定其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。  
  
1.  不透明度值`1.0`讓物件完全不透明和不透明度值`0.0`使完全不可見。 To make the animation transition from                                  `1.0` to                                  `0.0` you set its                                  <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> property to                                  `1.0` and its                                  <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> property to                                  `0.0`. 下圖顯示如何建立<xref:System.Windows.Media.Animation.DoubleAnimation>在 XAML 中。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     下圖顯示如何建立<xref:System.Windows.Media.Animation.DoubleAnimation>程式碼中。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  接下來，您必須指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫的指定起始值到其目的地值花多少時間。 下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>到 XAML 中的五秒。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>為程式碼中的五秒。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  先前的程式碼示範從轉換的動畫`1.0`至`0.0`，如此便會從完全不透明淡出為完全透明的目標項目。 若要讓它消失後，回到檢視淡出的項目，設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性動畫`true`。 若要製作動畫重複無限期，設定其<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>。下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>和<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>在 XAML 中的屬性。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>和<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>程式碼中的屬性。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>第 2 部份︰ 建立分鏡腳本  
 若要套用至物件的動畫，您建立<xref:System.Windows.Media.Animation.Storyboard>並用<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>附加指定的物件的屬性和屬性，以製作動畫。  
  
1.  建立<xref:System.Windows.Media.Animation.Storyboard>並將動畫加入做為其子系。 下圖顯示如何建立<xref:System.Windows.Media.Animation.Storyboard>在 XAML 中。  
  
     <!-- TODO: review snippet reference [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]  -->  
  
     若要建立<xref:System.Windows.Media.Animation.Storyboard>在程式碼中，宣告<xref:System.Windows.Media.Animation.Storyboard>類別層級變數。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     然後初始化<xref:System.Windows.Media.Animation.Storyboard>並將動畫加入做為其子系。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  <xref:System.Windows.Media.Animation.Storyboard>必須知道要套用動畫的位置。 使用<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName>附加屬性來指定要製作動畫的物件。 下圖顯示如何設定的目標名稱<xref:System.Windows.Media.Animation.DoubleAnimation>至`MyRectangle`在 XAML 中。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     下圖顯示如何設定的目標名稱<xref:System.Windows.Media.Animation.DoubleAnimation>至`MyRectangle`程式碼中。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  使用<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>附加屬性來指定要顯示動畫屬性。 下圖顯示如何設定動畫目標<xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Shapes.Rectangle>在 XAML 中。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     下圖顯示如何設定動畫目標<xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Shapes.Rectangle>程式碼中。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 如需詳細資訊<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>語法和其他範例，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>第 3 (XAML) 部分︰ 關聯腳本與觸發程序  
 最簡單的方式套用，啟動<xref:System.Windows.Media.Animation.Storyboard>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是使用事件觸發程序。                          本節說明如何建立關聯<xref:System.Windows.Media.Animation.Storyboard>以 XAML 觸發程序。  
  
1.  建立<xref:System.Windows.Media.Animation.BeginStoryboard>物件，並將您的腳本與其關聯。 A <xref:System.Windows.Media.Animation.BeginStoryboard>是一種<xref:System.Windows.TriggerAction> ，適用於並啟動<xref:System.Windows.Media.Animation.Storyboard>。  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  建立<xref:System.Windows.EventTrigger> ，並新增<xref:System.Windows.Media.Animation.BeginStoryboard>至其<xref:System.Windows.EventTrigger.Actions%2A>集合。 設定<xref:System.Windows.EventTrigger.RoutedEvent%2A>屬性<xref:System.Windows.EventTrigger>路由事件，您想要啟動<xref:System.Windows.Media.Animation.Storyboard>。 (如需路由事件的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。)  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  新增<xref:System.Windows.EventTrigger>至<xref:System.Windows.FrameworkElement.Triggers%2A>矩形的集合。  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>第 3 （程式碼） 部份︰ 建立腳本與事件處理常式的關聯  
 最簡單的方式套用，啟動<xref:System.Windows.Media.Animation.Storyboard>在程式碼是使用事件處理常式。 本節說明如何建立關聯<xref:System.Windows.Media.Animation.Storyboard>與事件處理常式程式碼中。  
  
1.  註冊<xref:System.Windows.FrameworkElement.Loaded>矩形的事件。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  宣告事件處理常式。 在事件處理常式中，使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法，以套用腳本。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>完整範例  
 下圖顯示如何建立一個矩形，會在 XAML 中的檢視。  
  
 [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 下圖顯示如何建立一個矩形，會在程式碼中的檢視。  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>動畫類型  
 動畫會產生屬性值，因為不同的動畫類型存在於不同的屬性類型。 若要建立採用屬性的動畫<xref:System.Double>，例如<xref:System.Windows.FrameworkElement.Width%2A>屬性的項目，可使用的動畫，會產生<xref:System.Double>值。 若要建立採用屬性的動畫<xref:System.Windows.Point>，使用的動畫，會產生<xref:System.Windows.Point>值，依此類推。 由於不同的屬性類型的數目，包含數種動畫類別中的<xref:System.Windows.Media.Animation>命名空間。 幸運的是，它們會遵循嚴格的命名慣例，方便您區分它們︰  
  
-   \<                         *型別*> 動畫  
  
     這些稱為 「 From/To/By 」 或 「 基本 」 動畫，動畫之間起始及目的的值，或將位移的值加入至其起始值。  
  
    -   若要指定起始值，設定動畫的 From 屬性。  
  
    -   若要指定結束值，設定動畫的 To 屬性。  
  
    -   若要指定位移的值，設定 By 屬性的動畫。  
  
     本概觀中的範例會使用這些動畫，因為它們是最容易使用。 From/To/By 動畫 From/To/By 動畫概觀詳細說明。  
  
-   \<                         *型別*> g  
  
     主要畫面格動畫會比 From/To/By 動畫的功能更強大，因為您可以指定任意數目的目標值，甚至控制其插補方法。 只可以使用主要畫面格動畫顯示某些類型的動畫效果。 主要畫面格動畫會詳細說明[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
-   \<                         *型別*> AnimationUsingPath  
  
     路徑動畫可讓您使用幾何路徑，以產生動畫的值。  
  
-   \<                         *型別*> a  
  
     抽象類別，當您實作動畫<>*類型*> 值。 這個類別可做為基底類別<>*類型*> 動畫和<>*類型*> 簡的單類別。 您必須直接處理這些類別只有當您想要建立您自己的自訂動畫。 否則，請使用<>*類型*> 動畫或主要畫面格<>*類型*> 動畫。  
  
 在大部分情況下，您會想要使用<>*類型*> 動畫類別，例如<xref:System.Windows.Media.Animation.DoubleAnimation>和<xref:System.Windows.Media.Animation.ColorAnimation>。  
  
 下表顯示數個常見的動畫類型和使用的某些屬性。  
  
|屬性類型|對應 (From/To/By) 的基本動畫|對應的主要畫面格動畫|對應的路徑動畫|使用範例|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|無|Animate the                                  <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a                                  <xref:System.Windows.Media.SolidColorBrush> or a                                  <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animate the                                  <xref:System.Windows.FrameworkElement.Width%2A> of a                                  <xref:System.Windows.Controls.DockPanel> or the                                  <xref:System.Windows.FrameworkElement.Height%2A> of a                                  <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|建立動畫<xref:System.Windows.Media.EllipseGeometry.Center%2A>位置<xref:System.Windows.Media.EllipseGeometry>。|  
|<xref:System.String>|無|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|無|Animate the                                  <xref:System.Windows.Controls.TextBlock.Text%2A> of a                                  <xref:System.Windows.Controls.TextBlock> or the                                  <xref:System.Windows.Controls.ContentControl.Content%2A> of a                                  <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>動畫是時間軸  
 所有動畫型別都繼承自<xref:System.Windows.Media.Animation.Timeline>類別; 因此，所有的動畫時間軸的特製化型別。 A<xref:System.Windows.Media.Animation.Timeline>定義一段時間。 您可以指定*計時行為*的時間軸︰ 其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>，它會重複，而平均速度的時間進行它的次數。  
  
 因為動畫<xref:System.Windows.Media.Animation.Timeline>，它也代表一段時間。 動畫會計算輸出值執行時透過其指定的一段時間 (或<xref:System.Windows.Media.Animation.Timeline.Duration%2A>)。 身為動畫的進度，或 「 播放 」，它會更新相關聯的屬性。  
  
 有三個常用的計時屬性<xref:System.Windows.Media.Animation.Timeline.Duration%2A>， <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>，和<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>。  
  
#### <a name="the-duration-property"></a>Duration 屬性  
 如先前所述，在時間軸代表一段時間。 該區段的長度由<xref:System.Windows.Media.Animation.Timeline.Duration%2A>時間軸，通常會使用指定的<xref:System.Windows.Duration.TimeSpan%2A>值。 當時刻表到達其持續時間結束時，它已經完成反覆項目。  
  
 動畫會使用其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性來判斷目前的值。 如果您未指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>值動畫，它會使用 1 秒，這是預設值。  
  
 下列語法顯示簡化的版的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性語法<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性。  
  
||  
|-|  
|*hours* `:` *minutes* `:` *seconds*|  
  
 下表顯示幾個<xref:System.Windows.Duration>設定，以及其產生的值。  
  
|設定|產生的值|  
|-------------|---------------------|  
|0:0:5.5|5.5 秒。|  
|0:30:5.5|30 分鐘又 5.5 秒。|  
|1:30:5.5|1 小時 30 分鐘的時間，和 5.5 秒。|  
  
 其中一種方式指定<xref:System.Windows.Duration>在程式碼是使用<xref:System.TimeSpan.FromSeconds%2A>方法來建立<xref:System.TimeSpan>，然後將宣告新<xref:System.Windows.Duration>結構使用， <xref:System.TimeSpan>。  
  
 如需詳細資訊<xref:System.Windows.Duration>值和完整[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]語法，請參閱<xref:System.Windows.Duration>結構。  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會指定是否之後結束的時間軸播放回溯其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 如果您將這個動畫屬性設定為`true`，結束之後，動畫會反轉其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 播放的結束值傳回給起始值。 根據預設，這個屬性是`false`。  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性指定的時間軸播放的次數。 根據預設，時間軸會有的反覆計數為`1.0`，表示播放一次和不要重複。  
  
 如需這些屬性等等的詳細資訊，請參閱[計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)。  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>套用至屬性的動畫  
 前幾節說明不同類型的動畫和計時屬性。 本節說明如何將動畫套用至您想要製作動畫的屬性。                  <xref:System.Windows.Media.Animation.Storyboard>物件會提供一個方式，將套用至屬性的動畫。 A<xref:System.Windows.Media.Animation.Storyboard>是*容器時刻表*提供包含動畫的目標資訊。  
  
### <a name="targeting-objects-and-properties"></a>目標物件和屬性  
 <xref:System.Windows.Media.Animation.Storyboard>類別提供<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>附加屬性。 藉由設定這些屬性動畫，可以讓動畫要製作動畫的項目。 不過，動畫可以鎖定物件之前，物件必須通常要給予名稱。  
  
 將名稱指派給<xref:System.Windows.FrameworkElement>不同於將名稱指派給<xref:System.Windows.Freezable>物件。 大部分的控制項和面板是架構項目。不過，大部分純粹圖形化的物件，例如筆刷、 轉換和幾何是 freezable 物件。 如果您不確定是否為型別<xref:System.Windows.FrameworkElement>或<xref:System.Windows.Freezable>，請參閱**繼承階層架構**其參考文件的區段。  
  
-   若要讓<xref:System.Windows.FrameworkElement>動畫目標，您賦予它一個名稱藉由設定其<xref:System.Windows.FrameworkElement.Name%2A>屬性。 在程式碼中，您必須也使用<xref:System.Windows.FrameworkElement.RegisterName%2A>方法，登錄項目名稱與屬於哪個頁面。  
  
-   若要讓<xref:System.Windows.Freezable>物件在動畫目標[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您使用[X:name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)為它指派名稱。 在程式碼中，您只使用<xref:System.Windows.FrameworkElement.RegisterName%2A>登錄物件頁面所屬的方法。  
  
 以下各節將提供範例，在項目命名[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼。 命名與目標相關的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
### <a name="applying-and-starting-storyboards"></a>套用及啟動腳本  
 啟動腳本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您關聯<xref:System.Windows.EventTrigger>。 <xref:System.Windows.EventTrigger>是物件，描述指定的事件發生時要採取的動作。 這些動作可以是<xref:System.Windows.Media.Animation.BeginStoryboard>動作，用來啟動您的腳本。 事件觸發程序是在概念上類似事件處理常式，因為它們可讓您指定您的應用程式如何回應特定事件。 不同於事件處理常式，事件觸發程序可以是完整的描述中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 不需要其他的程式碼。  
  
 若要啟動<xref:System.Windows.Media.Animation.Storyboard>在程式碼中，您可以使用<xref:System.Windows.EventTrigger>或使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法<xref:System.Windows.Media.Animation.Storyboard>類別。  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>以互動方式控制腳本  
 之前的範例顯示如何啟動<xref:System.Windows.Media.Animation.Storyboard>事件發生時。 您也以互動方式控制<xref:System.Windows.Media.Animation.Storyboard>它啟動後︰ 您可以暫停、 繼續、 停止、 前往其填滿期間，搜尋，並移除<xref:System.Windows.Media.Animation.Storyboard>。 如需詳細資訊和範例，示範如何以互動方式控制<xref:System.Windows.Media.Animation.Storyboard>，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>動畫結束後，會發生什麼事？  
 <xref:System.Windows.Media.Animation.FillBehavior>屬性會指定結束時，時間軸的操作方式。 根據預設，啟動時間軸<xref:System.Windows.Media.Animation.ClockState>結束時。 動畫是<xref:System.Windows.Media.Animation.ClockState>保有最終輸出值。  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation>前一個範例中就不會結束因為其<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性設定為<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>。 下列範例使用類似的動畫，動畫矩形。 不同於前例， <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>和<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>這個動畫的屬性會保留其預設值。 因此，動畫從開始進展 1 至 0 在五秒內，然後停止。  
  
 [!code-xml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 因為其<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>未變更其預設值，亦即從<xref:System.Windows.Media.Animation.FillBehavior>，動畫保留最後一個值為 0 時，它何時結束。 因此，<xref:System.Windows.UIElement.Opacity%2A>0 之後動畫矩形維持的結束。 如果您設定<xref:System.Windows.UIElement.Opacity%2A>的矩形中為另一個值，您的程式碼並沒有任何作用，因為動畫仍然會影響<xref:System.Windows.UIElement.Opacity%2A>屬性。  
  
 若要回復控制動畫的屬性，在程式碼中的一個方式是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法及指定 null <xref:System.Windows.Media.Animation.AnimationTimeline>參數。 如需詳細資訊和範例，請參閱[設定屬性之後建立動畫腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
 請注意，雖然設定屬性值有<xref:System.Windows.Media.Animation.ClockState>或<xref:System.Windows.Media.Animation.ClockState>動畫並沒有任何作用，並變更屬性值。 如需詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>資料繫結和建立動畫  
 大部分的動畫屬性可以是資料繫結或動畫。例如，您可以動畫顯示<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>。 不過，由於計時系統的運作的方式，資料繫結或動畫行為不像其他資料繫結或動畫的物件。 若要了解其行為，它有助於了解動畫套用至屬性的意義。  
  
 說明如何以動畫顯示上一節中的範例，請參閱<xref:System.Windows.UIElement.Opacity%2A>的矩形。 在上述範例中的矩形載入時，其事件觸發程序適用於<xref:System.Windows.Media.Animation.Storyboard>。 計時系統會建立一份<xref:System.Windows.Media.Animation.Storyboard>和它的動畫。 這些複本會凍結 （進行唯讀） 和<xref:System.Windows.Media.Animation.Clock>會從中建立物件。 這些時鐘會執行建立動畫的目標的屬性的實際工作。  
  
 計時系統建立如時鐘<xref:System.Windows.Media.Animation.DoubleAnimation>並將其套用到物件和屬性所指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>的<xref:System.Windows.Media.Animation.DoubleAnimation>。 計時系統在此情況下，套用至時鐘<xref:System.Windows.UIElement.Opacity%2A>屬性的物件，名為 「 MyRectangle 」。  
  
 雖然也會建立時鐘<xref:System.Windows.Media.Animation.Storyboard>，時鐘不會套用到任何屬性。 其目的是要控制它的子時鐘，建立如時鐘<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 反映資料繫結或動畫變更動畫，就必須重新產生它的時鐘。 時鐘會不自動產生。 若要讓動畫反映的變更，重新套用其腳本使用<xref:System.Windows.Media.Animation.BeginStoryboard>或<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法。 當您使用其中一種方法時，會重新啟動動畫。 在程式碼中，您可以使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法來移動腳本回它先前的位置。  
  
 如範例中的資料繫結動畫，請參閱[金鑰曲線動畫範例](http://go.microsoft.com/fwlink/?LinkID=160011)。                  如需動畫和計時系統的運作方式的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>其他的方式建立動畫  
 本概觀中的範例示範如何使用腳本建立的動畫。 當您使用程式碼時，您可以動畫顯示幾個其他方法。 如需詳細資訊，請參閱[屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>動畫範例  
 下列範例可以幫助您開始將動畫加入至您的應用程式。  
  
-   [From、 To 和動畫目標值範例](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     示範不同 From/To/By 的設定。  
  
-   [動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     示範不同的方式，您可以控制動畫的時間行為。 這個範例也顯示如何資料繫結動畫的目的值。  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|描述如何使用計時系統<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>類別，可以讓您建立動畫。|  
|[動畫秘訣和訣竅](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|列出祕訣，以便解決動畫，例如效能問題。|  
|[自訂動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|說明如何擴充動畫系統使用主要畫面格動畫類別的每個畫面格回呼。|  
|From/To/By 動畫概觀|描述如何建立兩個值之間轉換的動畫。|  
|[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|描述如何建立動畫，具有多個目標值，包括控制插補方法的能力。|  
|[Easing 函式](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|說明如何將數學公式套用至以取得實際的行為，例如彈跳動畫。|  
|[路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|描述如何移動或旋轉複雜路徑物件。|  
|[屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|描述使用腳本的屬性動畫、 本機動畫、 時鐘和每個畫面格動畫。|  
|[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|描述如何使用腳本建立包含多個時間軸，建立複雜的動畫。|  
|[計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|描述<xref:System.Windows.Media.Animation.Timeline>型別和用於動畫的屬性。|  
|[計時事件概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|描述用於事件<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>物件來執行程式碼，在時間軸中的點開始、 暫停、 繼續、 略過，或停止。|  
|[How to 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|包含應用程式中使用動畫及時間表的程式碼範例。|  
|[時鐘 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|包含程式碼範例使用<xref:System.Windows.Media.Animation.Clock>應用程式中的物件。|  
|[主要畫面格 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|包含應用程式中使用主要畫面格動畫的程式碼範例。|  
|[路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|包含應用程式中使用路徑動畫的程式碼範例。|  
  
<a name="reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>