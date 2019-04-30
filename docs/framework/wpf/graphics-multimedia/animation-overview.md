---
title: 動畫概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 530f6cb8fbe80df3ad374f8ad0e4836be82830a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054324"
---
# <a name="animation-overview"></a>動畫概觀
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供一組強大的圖形和版面配置功能，可讓您建立漂亮的使用者介面和吸引人的文件。 動畫可以讓漂亮的使用者介面更美觀而實用。 藉由只背景色彩的動畫，或套用動畫<xref:System.Windows.Media.Transform>，您可以建立戲劇性的畫面轉換或提供實用的視覺提示。  
  
 本概觀介紹[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫和計時系統。 它著重的動畫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用分鏡腳本的物件。  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>動畫簡介  
 動畫是快速循環一系列影像，而每個影像與上一個影像稍有不同所產生的一種錯覺。 大腦將一組影像認知為一個在變化的場景。 在影片中，此種錯覺是利用每秒拍攝許多照片或畫面的數位相機所產生。 當投影機播放畫面時，觀眾就會看到移動的圖片。  
  
 電腦上的動畫很類似如此。 例如，讓矩形繪圖淡出畫面的程式可能如下運作。  
  
- 程式建立計時器。  
  
- 程式檢查設定間隔處的計時器，以查看經過多少時間。  
  
- 每當程式檢查計時器時，會根據經過多少時間來計算矩形目前的不透明度值。  
  
- 然後程式使用新值更新矩形，並重新繪製矩形。  
  
 之前[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]開發人員，就必須建立並管理他們自己的計時系統或使用特殊的自訂程式庫。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含會公開透過 managed 程式碼的高效率計時系統以及[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和已完全整合至[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]framework。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫可讓您輕鬆以動畫顯示控制項和其他圖形物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會有效率地處理管理計時系統以及重新繪製畫面的所有幕後工作。 它提供的計時類別，可讓您專注在您想要建立的效果，而不是達成這些效果的技術。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也公開您的類別可以繼承的動畫基底類別，方便您建立您自己的動畫，以產生自訂的動畫。 這些自訂動畫可以獲得標準動畫類別的許多效能優勢。  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>WPF 屬性動畫系統  
 如果您了解的一些重要的概念，計時系統中，有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫可以更輕鬆地使用。 最重要的是，在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，以動畫顯示物件將動畫套用至其個別的屬性。 例如，若要讓架構元素變大，您以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。 若要讓物件淡出畫面，您以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性。  
  
 如果要讓屬性具備動畫功能，必須符合下列三個需求︰  
  
- 必須是相依性屬性。  
  
- 它必須屬於繼承自類別<xref:System.Windows.DependencyObject>並實作<xref:System.Windows.Media.Animation.IAnimatable>介面。  
  
- 必須有相容的動畫類型。 (如果[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不提供，您可以建立您自己。 請參閱[自訂動畫概觀](custom-animations-overview.md)。)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含具有許多物件<xref:System.Windows.Media.Animation.IAnimatable>屬性。 控制這類<xref:System.Windows.Controls.Button>並<xref:System.Windows.Controls.TabControl>，以及<xref:System.Windows.Controls.Panel>並<xref:System.Windows.Shapes.Shape>物件繼承自<xref:System.Windows.DependencyObject>。 這些項目的大部分屬性是相依性屬性。  
  
 您幾乎可以在任何地方 (包括在樣式和控制項範本中) 使用動畫。 動畫不必是視覺物件。如果不屬於使用者介面部分的物件符合本節所描述的準則，也可以以動畫顯示這些物件。  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>範例：讓元素淡出，流入和流出檢視  
 此範例示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫來以動畫顯示相依性屬性的值。 它會使用<xref:System.Windows.Media.Animation.DoubleAnimation>，這是一種會產生的動畫<xref:System.Double>值，以動畫顯示<xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Shapes.Rectangle>。 如此一來，<xref:System.Windows.Shapes.Rectangle>淡。  
  
 此範例的第一個部分會建立<xref:System.Windows.Shapes.Rectangle>項目。 請依照下列步驟示範如何建立動畫，並將它套用到矩形的<xref:System.Windows.UIElement.Opacity%2A>屬性。
  
 下圖顯示如何建立<xref:System.Windows.Shapes.Rectangle>中的項目<xref:System.Windows.Controls.StackPanel>在 XAML 中。  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 下圖顯示如何建立<xref:System.Windows.Shapes.Rectangle>中的項目<xref:System.Windows.Controls.StackPanel>在程式碼中。  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>第 1 部份：建立 DoubleAnimation  
 讓元素淡的一個方式是以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性。 因為<xref:System.Windows.UIElement.Opacity%2A>屬性的類型是<xref:System.Double>，您需要產生雙精度浮點數值的動畫。 A<xref:System.Windows.Media.Animation.DoubleAnimation>是一個這類動畫。 A<xref:System.Windows.Media.Animation.DoubleAnimation>建立兩個雙精度浮點數值之間的轉換。 若要指定其開始值，您將其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性。 若要指定其結束值，您將其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。  
  
1. 不透明度值`1.0`可讓物件完全不透明的且不透明度值`0.0`就完全看不見。 若要從動畫轉換`1.0`來`0.0`您設定其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性設`1.0`及其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性設`0.0`。 下圖顯示如何建立<xref:System.Windows.Media.Animation.DoubleAnimation>在 XAML 中。  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     下圖顯示如何建立<xref:System.Windows.Media.Animation.DoubleAnimation>在程式碼中。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2. 接下來，您必須指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫的指定 從其起始值到其目的地值需要多久。 下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>為 XAML 中的五秒。  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>為程式碼中的五秒。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3. 先前的程式碼示範從轉換的動畫`1.0`至`0.0`，因而導致目標元素從完全不透明淡化為完全看不見。 若要讓消失之後又淡化回畫面的項目，設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性的動畫`true`。 若要讓動畫無限期地重複，設定其<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性設<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>。下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>和<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>XAML 中的屬性。  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     下圖顯示如何設定<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>和<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>在程式碼中的屬性。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>第 2 部分：建立分鏡腳本  
 若要套用至物件的動畫，您建立<xref:System.Windows.Media.Animation.Storyboard>並用<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>附加屬性來指定的物件以及以動畫顯示屬性。  
  
1. 建立<xref:System.Windows.Media.Animation.Storyboard>將動畫新增為其子系。 下圖顯示如何建立<xref:System.Windows.Media.Animation.Storyboard>在 XAML 中。  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     若要建立<xref:System.Windows.Media.Animation.Storyboard>程式碼中，宣告<xref:System.Windows.Media.Animation.Storyboard>類別層級變數。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     然後初始化<xref:System.Windows.Media.Animation.Storyboard>將動畫新增為其子系。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2. <xref:System.Windows.Media.Animation.Storyboard>必須知道要套用動畫的位置。 使用<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>附加屬性來指定要繪製的物件。 下圖顯示如何設定的目標名稱<xref:System.Windows.Media.Animation.DoubleAnimation>至`MyRectangle`在 XAML 中。  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     下圖顯示如何設定的目標名稱<xref:System.Windows.Media.Animation.DoubleAnimation>至`MyRectangle`在程式碼中。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3. 使用<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>附加屬性來指定要建立動畫的屬性。 下列範例示範如何設定動畫目標<xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Shapes.Rectangle>在 XAML 中。
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     下列範例示範如何設定動畫目標<xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Shapes.Rectangle>在程式碼中。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 如需詳細資訊<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>語法，如需其他範例，請參閱 <<c2> [ 分鏡腳本概觀](storyboards-overview.md)。  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>第 3 (XAML):觸發程序相關聯的分鏡腳本  
 最簡單的方式套用並開始<xref:System.Windows.Media.Animation.Storyboard>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是使用事件觸發程序。 本節說明如何建立關聯<xref:System.Windows.Media.Animation.Storyboard>以在 XAML 中的觸發程序。  
  
1. 建立<xref:System.Windows.Media.Animation.BeginStoryboard>物件，並讓您分鏡腳本與其產生關聯。 A<xref:System.Windows.Media.Animation.BeginStoryboard>是一種<xref:System.Windows.TriggerAction>會套用並開始<xref:System.Windows.Media.Animation.Storyboard>。  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2. 建立<xref:System.Windows.EventTrigger>並新增<xref:System.Windows.Media.Animation.BeginStoryboard>到其<xref:System.Windows.EventTrigger.Actions%2A>集合。 設定<xref:System.Windows.EventTrigger.RoutedEvent%2A>的屬性<xref:System.Windows.EventTrigger>您想要啟動的路由事件<xref:System.Windows.Media.Animation.Storyboard>。 (如需有關路由事件的詳細資訊，請參閱[路由事件概觀](../advanced/routed-events-overview.md)。)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3. 新增<xref:System.Windows.EventTrigger>至<xref:System.Windows.FrameworkElement.Triggers%2A>矩形的集合。  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>第 3 （程式碼）：事件處理常式相關聯的分鏡腳本  
 最簡單的方式套用並開始<xref:System.Windows.Media.Animation.Storyboard>在程式碼是使用事件處理常式。 本節說明如何建立關聯<xref:System.Windows.Media.Animation.Storyboard>與事件處理常式程式碼中。  
  
1. 報名<xref:System.Windows.FrameworkElement.Loaded>矩形的事件。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2. 宣告事件處理常式。 在 事件處理常式中，使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法套用分鏡腳本。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>完整範例  
 以下顯示如何建立在 XAML 中淡的矩形。  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 下面顯示如何在程式碼中建立淡入又淡出畫面的矩形。  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>動畫類型  
 由於動畫會產生屬性值，因此不同的屬性類型有不同的動畫類型。 若要動畫顯示採用的屬性<xref:System.Double>，這類<xref:System.Windows.FrameworkElement.Width%2A>屬性的項目，使用會產生動畫<xref:System.Double>值。 若要動畫顯示採用的屬性<xref:System.Windows.Point>，使用會產生動畫<xref:System.Windows.Point>值，並依此類推。 由於不同的屬性類型的數目，有數個動畫類別，在<xref:System.Windows.Media.Animation>命名空間。 幸運的是，它們會遵循嚴格的命名慣例方便您區分︰  
  
- \<*型別*> 動畫  
  
     稱為 "From/To/By" 或「基本」動畫，這些會以動畫顯示開始值到目的地值，或將位移值新增至其開始值。  
  
    - 若要指定開始值，請設定動畫的 From 屬性。  
  
    - 若要指定結束值，請設定動畫的 To 屬性。  
  
    - 若要指定位移值，請設定動畫的 By 屬性。  
  
     本概觀中的範例會使用這些動畫，因為最容易使用。 在 by 動畫概觀 > 中詳細說明 From/To/By 動畫。  
  
- \<*Type*>AnimationUsingKeyFrames  
  
     主要畫面格動畫比 From/To/By 動畫更強大，因為您可以指定任意數目的目標值，甚至可以控制其插補方法。 某些類型只能使用主要畫面格動畫顯示動畫。 主要畫面格動畫會詳述[主要畫面格動畫概觀](key-frame-animations-overview.md)。  
  
- \<*Type*>AnimationUsingPath  
  
     路徑動畫可讓您使用幾何路徑以產生動畫的值。  
  
- \<*Type*>AnimationBase  
  
     抽象類別，當您實作時，建立動畫\<*型別*> 值。 此類別可做為基底類別\<*型別*> 動畫並\<*型別*> animationusingkeyframes。 只有當您想要建立您自己的自訂動畫時，才需要直接處理這些類別。 否則，請使用\<*型別*> 動畫或主要畫面格\<*型別*> 動畫。  
  
 在大部分情況下，您會想要\<*型別*> 動畫類別，例如<xref:System.Windows.Media.Animation.DoubleAnimation>和<xref:System.Windows.Media.Animation.ColorAnimation>。  
  
 下表顯示數個常見的動畫類型和搭配使用的某些屬性。  
  
|屬性類型|對應的基本 (From/To/By) 動畫|對應的主要畫面格動畫|對應的路徑動畫|使用範例|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|None|建立動畫<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>或<xref:System.Windows.Media.GradientStop>。|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|建立動畫<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Controls.Button>。|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|建立動畫<xref:System.Windows.Media.EllipseGeometry.Center%2A>位置<xref:System.Windows.Media.EllipseGeometry>。|  
|<xref:System.String>|None|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|None|建立動畫<xref:System.Windows.Controls.TextBlock.Text%2A>的<xref:System.Windows.Controls.TextBlock>或<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.Button>。|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>動畫是時間軸  
 所有動畫類型都繼承自<xref:System.Windows.Media.Animation.Timeline>類別; 因此，所有動畫都是特殊的類型的時間軸。 A<xref:System.Windows.Media.Animation.Timeline>定義一段時間。 您可以指定*計時行為*時間軸： 其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>，它會重複，而平均速度的時間進行的次數。  
  
 因為動畫是<xref:System.Windows.Media.Animation.Timeline>，它也代表一段時間。 動畫也會計算輸出值進行其指定的一段時間 (或<xref:System.Windows.Media.Animation.Timeline.Duration%2A>)。 隨著動畫進行 (或「播放」)，動畫會更新相關聯的屬性。  
  
 三個常用的計時屬性是<xref:System.Windows.Media.Animation.Timeline.Duration%2A>， <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>，和<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>。  
  
#### <a name="the-duration-property"></a>Duration 屬性  
 如先前所述，時間軸代表一段時間。 該區段的長度由<xref:System.Windows.Media.Animation.Timeline.Duration%2A>時間軸，通常會使用指定的<xref:System.Windows.Duration.TimeSpan%2A>值。 當時間軸到達其持續時間結尾時，就是已經完成反覆項目。  
  
 動畫會使用其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性來判斷其目前的值。 如果您未指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>值的動畫，它會使用 1 秒，這是預設值。  
  
 下列語法顯示的簡化的版本[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性語法<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性。  
  
*hours* `:` *minutes* `:` *seconds*
  
 下表顯示數個<xref:System.Windows.Duration>設定和其產生的值。  
  
|設定|產生的值|  
|-------------|---------------------|  
|0:0:5.5|5.5 秒。|  
|0:30:5.5|30 分鐘 5.5 秒。|  
|1:30:5.5|1 小時 30 分鐘 5.5 秒。|  
  
 其中一種方式來指定<xref:System.Windows.Duration>在程式碼是使用<xref:System.TimeSpan.FromSeconds%2A>方法來建立<xref:System.TimeSpan>，然後宣告 new<xref:System.Windows.Duration>結構在使用該<xref:System.TimeSpan>。  
  
 如需詳細資訊<xref:System.Windows.Duration>值和完整[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]語法，請參閱<xref:System.Windows.Duration>結構。  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會指定是否之後結束的時間軸播放回溯其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 如果您將此動畫屬性設定為`true`，到達結束之後，動畫會反轉其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 從結束值播放回其開始值。 根據預設，這個屬性是`false`。  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性指定時間軸播放的次數。 根據預設，時間軸的計數為`1.0`，表示只播放一次，且完全不重複。  
  
 如需有關這些屬性等等的詳細資訊，請參閱 <<c0> [ 計時行為概觀](timing-behaviors-overview.md)。  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>對屬性套用動畫  
 前幾節說明不同類型的動畫及其計時屬性。 本節說明如何對您想要以動畫顯示的屬性套用動畫。 <xref:System.Windows.Media.Animation.Storyboard> 物件提供一種方式將動畫套用至屬性。 A<xref:System.Windows.Media.Animation.Storyboard>已*容器時間軸*，提供其包含之動畫的目標資訊。  
  
### <a name="targeting-objects-and-properties"></a>以物件和屬性為目標  
 <xref:System.Windows.Media.Animation.Storyboard>類別會提供<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>附加屬性。 您對動畫設定這些屬性，就可以告訴動畫要以動畫顯示的內容。 不過，在以物件為目標顯示動畫之前，物件通常必須要有名稱。  
  
 指派名稱給<xref:System.Windows.FrameworkElement>不同於指派名稱給<xref:System.Windows.Freezable>物件。 大部分的控制項和面板是架構元素。不過，大部分純圖形物件 (例如筆刷、轉換和幾何) 則是 Freezable 物件。 如果您不確定是否為型別<xref:System.Windows.FrameworkElement>或<xref:System.Windows.Freezable>，請參閱**繼承階層架構**其參考文件的章節。  
  
- 若要讓<xref:System.Windows.FrameworkElement>動畫目標，您賦予它一個名稱藉由設定其<xref:System.Windows.FrameworkElement.Name%2A>屬性。 在程式碼中，您必須也使用<xref:System.Windows.FrameworkElement.RegisterName%2A>方法，以其所屬的頁面註冊元素名稱。  
  
- 若要讓<xref:System.Windows.Freezable>物件成為動畫目標，在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您使用[X:name 指示詞](../../xaml-services/x-name-directive.md)將它指派名稱。 在程式碼，您只使用<xref:System.Windows.FrameworkElement.RegisterName%2A>方法，以其所屬的頁面註冊物件。  
  
 下列各節提供範例中的項目命名[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼。 命名與目標相關的詳細資訊，請參閱[分鏡腳本概觀](storyboards-overview.md)。  
  
### <a name="applying-and-starting-storyboards"></a>套用和啟動分鏡腳本  
 在中啟動分鏡腳本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其關聯<xref:System.Windows.EventTrigger>。 <xref:System.Windows.EventTrigger>是物件，描述指定的事件發生時要採取哪些動作。 其中一個這些動作可以是<xref:System.Windows.Media.Animation.BeginStoryboard>動作，用來啟動分鏡腳本。 事件觸發程序在概念上類似事件處理常式，因為兩者都可讓您指定您的應用程式要如何回應特定事件。 不同於事件處理常式，事件觸發程序可完全述[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 不不需要任何其他程式碼。  
  
 若要啟動<xref:System.Windows.Media.Animation.Storyboard>程式碼中，您可以使用<xref:System.Windows.EventTrigger>，或使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法<xref:System.Windows.Media.Animation.Storyboard>類別。  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>以互動方式控制分鏡腳本  
 先前範例所示範如何啟動<xref:System.Windows.Media.Animation.Storyboard>事件發生時。 您可以也以互動方式控制<xref:System.Windows.Media.Animation.Storyboard>啟動後： 您可以暫停、 繼續、 停止、 前進到其填滿期間、 搜尋及移除<xref:System.Windows.Media.Animation.Storyboard>。 如需詳細資訊和範例，示範如何以互動方式控制<xref:System.Windows.Media.Animation.Storyboard>，請參閱 <<c2> [ 分鏡腳本概觀](storyboards-overview.md)。  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>動畫結束後，會發生什麼事？  
 <xref:System.Windows.Media.Animation.FillBehavior>屬性會指定時間軸結束時的行為。 根據預設，啟動時間軸<xref:System.Windows.Media.Animation.ClockState.Filling>結束時。 動畫是<xref:System.Windows.Media.Animation.ClockState.Filling>保有最終輸出值。  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation>在上述範例中並不會結束因為其<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性設定為<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>。 下列範例使用類似的動畫，以動畫顯示矩形。 與上述範例中，不同<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>和<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>這個動畫的屬性會保留在其預設值。 因此，動畫在五秒內從 1 開始進行到 0，然後停止。  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 因為其<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>未變更其預設值，亦即從<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，則動畫會保留其最終的值為 0，結束時。 因此，<xref:System.Windows.UIElement.Opacity%2A>矩形維持在 0 之後動畫的結束。 如果您設定<xref:System.Windows.UIElement.Opacity%2A>的另一個值以矩形中，您的程式碼似乎沒有任何作用，因為動畫仍然在影響<xref:System.Windows.UIElement.Opacity%2A>屬性。  
  
 若要回復控制動畫的屬性在程式碼中的一個方式是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法並指定 null<xref:System.Windows.Media.Animation.AnimationTimeline>參數。 如需詳細資訊和範例，請參閱 <<c0> [ 設定屬性之後以動畫顯示使用分鏡腳本](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。  
  
 請注意，雖然設定屬性值不會有<xref:System.Windows.Media.Animation.ClockState.Active>或<xref:System.Windows.Media.Animation.ClockState.Filling>動畫看起來沒有任何作用，並變更屬性值。 如需詳細資訊，請參閱 <<c0> [ 動畫和計時系統概觀](animation-and-timing-system-overview.md)。  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>資料繫結和建立動畫  
 大部分的動畫屬性可以是資料繫結或以動畫顯示;例如，您可以建立動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>。 不過，由於計時系統的運作方式，資料繫結或動畫顯示的動畫不像其他資料繫結或動畫物件。 若要了解其行為，了解對屬性套用動畫的意義會很有幫助。  
  
 示範如何以動畫顯示上一節中的範例，請參閱<xref:System.Windows.UIElement.Opacity%2A>的矩形。 在上述範例中的矩形載入時，其事件觸發程序適用於<xref:System.Windows.Media.Animation.Storyboard>。 計時系統會建立一份<xref:System.Windows.Media.Animation.Storyboard>和它的動畫。 這些複本會被凍結 （變成唯讀狀態） 和<xref:System.Windows.Media.Animation.Clock>從中建立物件。 這些時鐘會執行以動畫顯示目標屬性的實際工作。  
  
 計時系統建立如時鐘<xref:System.Windows.Media.Animation.DoubleAnimation>並將其套用至的物件和所指定的屬性<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>並<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>的<xref:System.Windows.Media.Animation.DoubleAnimation>。 在此情況下，計時系統會套用至時鐘<xref:System.Windows.UIElement.Opacity%2A>屬性之物件的名稱為"MyRectangle"。  
  
 雖然也會建立時鐘<xref:System.Windows.Media.Animation.Storyboard>，時鐘不會套用到任何屬性。 其目的是要控制它的子系時鐘，針對所建立的時鐘<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 若要讓動畫反映出資料繫結或動畫變更，就必須重新產生動畫的時鐘。 時鐘不會自動產生。 若要讓動畫反映變更，重新套用分鏡腳本利用<xref:System.Windows.Media.Animation.BeginStoryboard>或<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法。 當您使用其中一種方法時，動畫會重新啟動。 在程式碼中，您可以使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法来移位的分鏡腳本回它先前的位置。  
  
 如需資料的範例繫結動畫，請參閱 <<c0> [ 主要曲線動畫範例](https://go.microsoft.com/fwlink/?LinkID=160011)。 如需動畫和計時系統的運作方式的詳細資訊，請參閱[動畫和計時系統概觀](animation-and-timing-system-overview.md)。  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>顯示動畫的其他方式  
 本概觀中的範例示範如何使用分鏡腳本顯示動畫。 當您使用程式碼時，可以使用其他幾種方式顯示動畫。 如需詳細資訊，請參閱 <<c0> [ 屬性動畫技術概觀](property-animation-techniques-overview.md)。  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>動畫範例  
 下列範例可以幫助您開始將動畫加入至您的應用程式。  
  
- [From、To 和 By 動畫目標值範例](https://go.microsoft.com/fwlink/?LinkID=159988)  
  
     示範不同 From/To/By 設定。  
  
- [動畫計時行為範例](https://go.microsoft.com/fwlink/?LinkID=159970)  
  
     示範您可以控制動畫計時行為的不同方式。 此範例也示範如何資料繫結動畫的目的地值。  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[動畫和計時系統概觀](animation-and-timing-system-overview.md)|描述計時系統如何使用<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>類別，可讓您建立動畫。|  
|[動畫祕訣和訣竅](animation-tips-and-tricks.md)|列出解決動畫問題 (例如效能) 的有用祕訣。|  
|[自訂動畫概觀](custom-animations-overview.md)|描述如何使用主要畫面格、動畫類別或每個畫面格回呼來擴充動畫系統。|  
|From/To/By 動畫概觀|描述如何建立在兩個值之間轉換的動畫。|  
|[主要畫面格動畫概觀](key-frame-animations-overview.md)|描述如何建立有多個目標值的動畫，包括控制插補方法的能力。|  
|[Easing 函式](easing-functions.md)|說明如何對動畫套用數學公式以獲得實際的行為，例如彈跳。|  
|[路徑動畫概觀](path-animations-overview.md)|描述如何沿著複雜路徑移動或旋轉物件。|  
|[屬性動畫技術概觀](property-animation-techniques-overview.md)|描述使用分鏡腳本的屬性動畫、本機動畫、時鐘和每個畫面格動畫。|  
|[分鏡腳本概觀](storyboards-overview.md)|描述如何使用有多個時間軸的分鏡腳本建立複雜的動畫。|  
|[計時行為概觀](timing-behaviors-overview.md)|描述<xref:System.Windows.Media.Animation.Timeline>型別和動畫中使用的屬性。|  
|[計時事件概觀](timing-events-overview.md)|描述用於事件<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>物件用來執行程式碼，在時間軸中的點，例如開始、 暫停、 繼續、 略過，或停止。|  
|[HOW-TO 主題](animation-and-timing-how-to-topics.md)|包含在應用程式中使用動畫及時間軸的程式碼範例。|  
|[時鐘操作說明主題](clocks-how-to-topics.md)|包含程式碼範例使用<xref:System.Windows.Media.Animation.Clock>應用程式中的物件。|  
|[主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)|包含在應用程式中使用主要畫面格動畫的程式碼範例。|  
|[路徑動畫操作說明主題](path-animation-how-to-topics.md)|包含在應用程式中使用路徑動畫的程式碼範例。|  
  
<a name="reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
