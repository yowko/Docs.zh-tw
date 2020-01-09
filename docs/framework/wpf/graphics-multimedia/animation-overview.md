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
ms.openlocfilehash: f0f55c948d10c61ebab57f47e3461531ccf5f610
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559712"
---
# <a name="animation-overview"></a>動畫概觀

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供一組強大的圖形和版面配置功能，可讓您建立吸引人的使用者介面和吸引人的檔。 動畫可以讓漂亮的使用者介面更美觀而實用。 只要以動畫顯示背景色彩或套用動畫 <xref:System.Windows.Media.Transform>，您就可以建立生動的螢幕轉換，或提供有用的視覺提示。

本總覽提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫和計時系統的簡介。 它著重在使用分鏡腳本 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件的動畫。

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>動畫簡介

動畫是快速循環一系列影像，而每個影像與上一個影像稍有不同所產生的一種錯覺。 大腦將一組影像認知為一個在變化的場景。 在影片中，此種錯覺是利用每秒拍攝許多照片或畫面的數位相機所產生。 當投影機播放畫面時，觀眾就會看到移動的圖片。

電腦上的動畫很類似如此。 例如，讓矩形繪圖淡出畫面的程式可能如下運作。

- 程式建立計時器。

- 程式檢查設定間隔處的計時器，以查看經過多少時間。

- 每當程式檢查計時器時，會根據經過多少時間來計算矩形目前的不透明度值。

- 然後程式使用新值更新矩形，並重新繪製矩形。

在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]之前，Microsoft Windows 開發人員必須建立和管理自己的計時系統，或使用特殊的自訂程式庫。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含有效率的計時系統，透過 managed 程式碼和 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 公開，而且已緊密整合到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構中。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫可讓您輕鬆以動畫顯示控制項和其他圖形物件。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會有效率地處理管理計時系統以及重新繪製畫面的所有幕後工作。 它提供的計時類別，可讓您專注在您想要建立的效果，而不是達成這些效果的技術。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也公開您的類別可以繼承的動畫基底類別，方便您建立您自己的動畫，以產生自訂的動畫。 這些自訂動畫可以獲得標準動畫類別的許多效能優勢。

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>WPF 屬性動畫系統

如果您瞭解有關計時系統的一些重要概念，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫可能比較容易使用。 最重要的是，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中，您可以藉由將動畫套用至其個別屬性來建立物件動畫。 例如，若要讓 framework 元素成長，您可以建立其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的動畫。 若要讓物件淡出視野，您可以建立其 <xref:System.Windows.UIElement.Opacity%2A> 屬性的動畫。

如果要讓屬性具備動畫功能，必須符合下列三個需求︰

- 必須是相依性屬性。

- 它必須屬於繼承自 <xref:System.Windows.DependencyObject> 並實 <xref:System.Windows.Media.Animation.IAnimatable> 介面的類別。

- 必須有相容的動畫類型。 （如果 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 沒有提供，您可以自行建立。 請參閱[自訂動畫總覽](custom-animations-overview.md)）。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含許多具有 <xref:System.Windows.Media.Animation.IAnimatable> 屬性的物件。 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.TabControl>等控制項，以及 <xref:System.Windows.Controls.Panel> 和 <xref:System.Windows.Shapes.Shape> 物件繼承自 <xref:System.Windows.DependencyObject>。 這些項目的大部分屬性是相依性屬性。

您幾乎可以在任何地方 (包括在樣式和控制項範本中) 使用動畫。 動畫不必是視覺物件。如果不屬於使用者介面部分的物件符合本節所描述的準則，也可以以動畫顯示這些物件。

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>範例︰讓元素淡入又淡出畫面

這個範例示範如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫，以動畫顯示相依性屬性的值。 它會使用 <xref:System.Windows.Media.Animation.DoubleAnimation>，這是產生 <xref:System.Double> 值的動畫類型，用來建立 <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.UIElement.Opacity%2A> 屬性的動畫。 因此，<xref:System.Windows.Shapes.Rectangle> 淡入和移出畫面。

範例的第一個部分會建立 <xref:System.Windows.Shapes.Rectangle> 元素。 接下來的步驟示範如何建立動畫，並將其套用至矩形的 <xref:System.Windows.UIElement.Opacity%2A> 屬性。

以下顯示如何在 XAML 的 <xref:System.Windows.Controls.StackPanel> 中建立 <xref:System.Windows.Shapes.Rectangle> 元素。

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

以下顯示如何在程式碼的 <xref:System.Windows.Controls.StackPanel> 中建立 <xref:System.Windows.Shapes.Rectangle> 元素。

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>第 1 部分︰建立 DoubleAnimation

讓元素淡入和移出視圖的其中一種方式，就是以動畫顯示其 <xref:System.Windows.UIElement.Opacity%2A> 屬性。 因為 <xref:System.Windows.UIElement.Opacity%2A> 屬性的類型為 <xref:System.Double>，所以您需要會產生雙精度浮點數的動畫。 <xref:System.Windows.Media.Animation.DoubleAnimation> 就是其中一個動畫。 <xref:System.Windows.Media.Animation.DoubleAnimation> 會建立兩個雙精度浮點數之間的轉換。 若要指定其起始值，請設定其 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性。 若要指定其結束值，請設定其 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性。

1. `1.0` 的不透明度值會使物件完全不透明，而不透明度值 `0.0` 會使其完全不可見。 若要讓動畫從 `1.0` 轉換成 `0.0` 您將其 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設為 `1.0`，並將其 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性設定為 [`0.0`]。 以下顯示如何在 XAML 中建立 <xref:System.Windows.Media.Animation.DoubleAnimation>。

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    以下顯示如何在程式碼中建立 <xref:System.Windows.Media.Animation.DoubleAnimation>。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. 接下來，您必須指定 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 會指定從起始值到其目的地值所需的時間。 以下顯示如何在 XAML 中將 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設定為五秒。

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    以下顯示如何在程式碼中將 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 設為5秒。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. 先前的程式碼示範了從 `1.0` 轉換為 `0.0`的動畫，這會導致目標元素從完全不透明淡出到完全不可見。 若要讓元素在會消失之後淡回視野，請將動畫的 [<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>] 屬性設定為 [`true`]。 若要無限期地重複動畫，請將其 [<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>] 屬性設定為 [<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>]。 以下顯示如何在 XAML 中設定 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 和 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性。

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    以下顯示如何在程式碼中設定 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 和 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>第 2 部分︰建立分鏡腳本

若要將動畫套用至物件，您可以建立 <xref:System.Windows.Media.Animation.Storyboard> 並使用 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 附加屬性來指定要建立動畫的物件和屬性。

1. 建立 <xref:System.Windows.Media.Animation.Storyboard> 並將動畫新增為其子系。 以下顯示如何在 XAML 中建立 <xref:System.Windows.Media.Animation.Storyboard>。

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    若要在程式碼中建立 <xref:System.Windows.Media.Animation.Storyboard>，請在類別層級宣告 <xref:System.Windows.Media.Animation.Storyboard> 變數。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    然後初始化 <xref:System.Windows.Media.Animation.Storyboard>，並將動畫新增為其子系。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. <xref:System.Windows.Media.Animation.Storyboard> 必須知道要將動畫套用至何處。 使用 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> 附加屬性來指定要建立動畫的物件。 以下顯示如何將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的目標名稱設定為 XAML 中 `MyRectangle`。

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    以下顯示如何在程式碼中將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的目標名稱設定為 `MyRectangle`。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. 使用 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 附加屬性來指定要建立動畫的屬性。 以下顯示動畫如何設定為以 XAML 中 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.UIElement.Opacity%2A> 屬性為目標。

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    以下顯示如何設定動畫以程式碼中 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.UIElement.Opacity%2A> 屬性為目標。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

如需 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 語法和其他範例的詳細資訊，請參閱分鏡腳本[總覽](storyboards-overview.md)。

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>第 3 部分 (XAML)︰將分鏡腳本與觸發程序建立關聯

在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中套用和啟動 <xref:System.Windows.Media.Animation.Storyboard> 最簡單的方式，就是使用事件觸發程式。 本節說明如何在 XAML 中將 <xref:System.Windows.Media.Animation.Storyboard> 與觸發程式產生關聯。

1. 建立 <xref:System.Windows.Media.Animation.BeginStoryboard> 物件，並將您的分鏡腳本與它建立關聯。 <xref:System.Windows.Media.Animation.BeginStoryboard> 是一種套用和啟動 <xref:System.Windows.Media.Animation.Storyboard>的 <xref:System.Windows.TriggerAction> 類型。

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. 建立 <xref:System.Windows.EventTrigger>，並將 <xref:System.Windows.Media.Animation.BeginStoryboard> 新增至其 <xref:System.Windows.EventTrigger.Actions%2A> 集合。 將 <xref:System.Windows.EventTrigger> 的 <xref:System.Windows.EventTrigger.RoutedEvent%2A> 屬性設定為您要啟動 <xref:System.Windows.Media.Animation.Storyboard>的路由事件。 （如需路由事件的詳細資訊，請參閱[路由事件總覽](../advanced/routed-events-overview.md)）。

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. 將 <xref:System.Windows.EventTrigger> 加入至矩形的 <xref:System.Windows.FrameworkElement.Triggers%2A> 集合。

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>第 3 部分 (程式碼)︰將分鏡腳本與事件處理常式建立關聯

在程式碼中套用和啟動 <xref:System.Windows.Media.Animation.Storyboard> 最簡單的方式，就是使用事件處理常式。 本節說明如何在程式碼中將 <xref:System.Windows.Media.Animation.Storyboard> 與事件處理常式產生關聯。

1. 註冊矩形的 <xref:System.Windows.FrameworkElement.Loaded> 事件。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. 宣告事件處理常式。 在事件處理常式中，使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法來套用分鏡腳本。

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>完整範例

下圖顯示如何建立在 XAML 中淡入和移出視圖的矩形。

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

下面顯示如何在程式碼中建立淡入又淡出畫面的矩形。

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>動畫類型

由於動畫會產生屬性值，因此不同的屬性類型有不同的動畫類型。 若要以動畫顯示採用 <xref:System.Double>的屬性（例如元素的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性），請使用會產生 <xref:System.Double> 值的動畫。 若要以動畫顯示接受 <xref:System.Windows.Point>的屬性，請使用會產生 <xref:System.Windows.Point> 值的動畫等等。 由於不同的屬性類型數目，<xref:System.Windows.Media.Animation> 命名空間中有數個動畫類別。 幸運的是，它們會遵循嚴格的命名慣例方便您區分︰

- \<*Type*>Animation

  稱為 "From/To/By" 或「基本」動畫，這些會以動畫顯示開始值到目的地值，或將位移值新增至其開始值。

  - 若要指定開始值，請設定動畫的 From 屬性。

  - 若要指定結束值，請設定動畫的 To 屬性。

  - 若要指定位移值，請設定動畫的 By 屬性。

  本概觀中的範例會使用這些動畫，因為最容易使用。 From/to/By 動畫會在 [從]/[至]/[按動畫] 總覽中詳細說明。

- \<*Type*>AnimationUsingKeyFrames

  主要畫面格動畫比 From/To/By 動畫更強大，因為您可以指定任意數目的目標值，甚至可以控制其插補方法。 某些類型只能使用主要畫面格動畫顯示動畫。 主要畫面格動畫會在[主要畫面格動畫總覽](key-frame-animations-overview.md)中詳細說明。

- \<*Type*>AnimationUsingPath

  路徑動畫可讓您使用幾何路徑以產生動畫的值。

- \<*Type*>AnimationBase

  當您實作時，以動畫顯示\<*Type*> 值的抽象類別。 此類別可做為 \<*Type*>Animation 和 \<*Type*>AnimationUsingKeyFrames 類別的基底類別。 只有當您想要建立您自己的自訂動畫時，才需要直接處理這些類別。 否則，請使用 \<*Type*>Animation 或 KeyFrame\<*Type*>Animation。

在大部分情況下，您會想要使用 \<*類型*> 動畫類別，例如 <xref:System.Windows.Media.Animation.DoubleAnimation> 和 <xref:System.Windows.Media.Animation.ColorAnimation>。

下表顯示數個常見的動畫類型和搭配使用的某些屬性。

|屬性類型|對應的基本 (From/To/By) 動畫|對應的主要畫面格動畫|對應的路徑動畫|使用範例|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|None|建立 <xref:System.Windows.Media.SolidColorBrush> 或 <xref:System.Windows.Media.GradientStop><xref:System.Windows.Media.SolidColorBrush.Color%2A> 的動畫。|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|以動畫顯示 <xref:System.Windows.Controls.DockPanel> 的 <xref:System.Windows.FrameworkElement.Width%2A> 或 <xref:System.Windows.Controls.Button>的 <xref:System.Windows.FrameworkElement.Height%2A>。|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|以動畫顯示 <xref:System.Windows.Media.EllipseGeometry>的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 位置。|
|<xref:System.String>|None|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|None|以動畫顯示 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Text%2A> 或 <xref:System.Windows.Controls.Button>的 <xref:System.Windows.Controls.ContentControl.Content%2A>。|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>動畫是時間軸

所有的動畫類型都會繼承自 <xref:System.Windows.Media.Animation.Timeline> 類別;因此，所有動畫都是特製化的時間軸類型。 <xref:System.Windows.Media.Animation.Timeline> 定義一段時間。 您可以指定時間軸的*計時行為*：其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>、重複的次數，以及更快速地進行的時間。

因為動畫是 <xref:System.Windows.Media.Animation.Timeline>，所以也代表一段時間。 動畫也會在其指定的時間區段（或 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>）時，計算輸出值。 隨著動畫進行 (或「播放」)，動畫會更新相關聯的屬性。

三個經常使用的計時屬性為 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>和 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>。

#### <a name="the-duration-property"></a>Duration 屬性

如先前所述，時間軸代表一段時間。 該區段的長度取決於時間軸的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>，通常是使用 <xref:System.Windows.Duration.TimeSpan%2A> 值來指定。 當時間軸到達其持續時間結尾時，就是已經完成反覆項目。

動畫會使用其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性來判斷其目前的值。 如果您未指定動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 值，則會使用1秒（預設值）。

下列語法顯示 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 屬性語法的簡化版本。

*小時*`:`*分鐘*`:`*秒*

下表顯示數個 <xref:System.Windows.Duration> 設定和其產生的值。

|設定|產生的值|
|-------------|---------------------|
|0:0:5.5|5.5 秒。|
|0:30:5.5|30 分鐘 5.5 秒。|
|1:30:5.5|1 小時 30 分鐘 5.5 秒。|

在程式碼中指定 <xref:System.Windows.Duration> 的方法之一，就是使用 <xref:System.TimeSpan.FromSeconds%2A> 方法來建立 <xref:System.TimeSpan>，然後使用該 <xref:System.TimeSpan>來宣告新的 <xref:System.Windows.Duration> 結構。

如需 <xref:System.Windows.Duration> 值和完整 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 語法的詳細資訊，請參閱 <xref:System.Windows.Duration> 結構。

#### <a name="autoreverse"></a>AutoReverse

<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性會指定時間軸是否會在到達其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>結尾後播放。 如果您將此動畫屬性設定為 [`true`]，動畫會在到達其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>結尾後反轉，並從其結束值播放回其起始值。 根據預設，此屬性為 `false`。

#### <a name="repeatbehavior"></a>RepeatBehavior

<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性會指定時間軸播放的次數。 根據預設，時間軸具有 `1.0`的反復專案計數，這表示它們會播放一次，而且完全不重複。

如需這些屬性和其他屬性的詳細資訊，請參閱[計時行為總覽](timing-behaviors-overview.md)。

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>對屬性套用動畫

前幾節說明不同類型的動畫及其計時屬性。 本節說明如何對您想要以動畫顯示的屬性套用動畫。 <xref:System.Windows.Media.Animation.Storyboard> 物件提供一種將動畫套用至屬性的方式。 <xref:System.Windows.Media.Animation.Storyboard> 是一種*容器時間軸*，它會為其所包含的動畫提供目標資訊。

### <a name="targeting-objects-and-properties"></a>以物件和屬性為目標

<xref:System.Windows.Media.Animation.Storyboard> 類別提供 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 附加的屬性。 您對動畫設定這些屬性，就可以告訴動畫要以動畫顯示的內容。 不過，在以物件為目標顯示動畫之前，物件通常必須要有名稱。

將名稱指派給 <xref:System.Windows.FrameworkElement> 不同于指派 <xref:System.Windows.Freezable> 物件的名稱。 大部分的控制項和面板是架構元素。不過，大部分純圖形物件 (例如筆刷、轉換和幾何) 則是 Freezable 物件。 如果您不確定類型是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.Freezable>，請參閱其參考檔的「**繼承**階層」一節。

- 若要讓 <xref:System.Windows.FrameworkElement> 動畫目標，您可以藉由設定其 <xref:System.Windows.FrameworkElement.Name%2A> 屬性來指定名稱。 在程式碼中，您也必須使用 <xref:System.Windows.FrameworkElement.RegisterName%2A> 方法，向它所屬的頁面註冊專案名稱。

- 若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中將 <xref:System.Windows.Freezable> 物件設為動畫目標，您可以使用[x：Name](../../../desktop-wpf/xaml-services/xname-directive.md)指示詞為其指派名稱。 在程式碼中，您只需使用 <xref:System.Windows.FrameworkElement.RegisterName%2A> 方法，將物件註冊到它所屬的頁面。

下列各節提供在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和程式碼中命名元素的範例。 如需命名和目標的詳細資訊，請參閱分鏡腳本[總覽](storyboards-overview.md)。

### <a name="applying-and-starting-storyboards"></a>套用和啟動分鏡腳本

若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中啟動分鏡腳本，請將它與 <xref:System.Windows.EventTrigger>產生關聯。 <xref:System.Windows.EventTrigger> 是物件，描述當指定的事件發生時所要採取的動作。 其中一個動作可以是 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作，您可以用來啟動分鏡腳本。 事件觸發程序在概念上類似事件處理常式，因為兩者都可讓您指定您的應用程式要如何回應特定事件。 與事件處理常式不同的是，事件觸發程式可以在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中完整描述;不需要其他程式碼。

若要在程式碼中啟動 <xref:System.Windows.Media.Animation.Storyboard>，您可以使用 <xref:System.Windows.EventTrigger>，或使用 <xref:System.Windows.Media.Animation.Storyboard> 類別的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>以互動方式控制分鏡腳本

上一個範例示範了如何在事件發生時啟動 <xref:System.Windows.Media.Animation.Storyboard>。 您也可以在啟動之後，以互動方式控制 <xref:System.Windows.Media.Animation.Storyboard>：您可以暫停、繼續、停止、將它前進到填滿期間、搜尋和移除 <xref:System.Windows.Media.Animation.Storyboard>。 如需顯示如何以互動方式控制 <xref:System.Windows.Media.Animation.Storyboard>的詳細資訊和範例，請參閱分鏡腳本[總覽](storyboards-overview.md)。

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>動畫結束後，會發生什麼事？

[<xref:System.Windows.Media.Animation.FillBehavior>] 屬性會指定時間軸結束時的運作方式。 根據預設，時間軸會在結束時開始 <xref:System.Windows.Media.Animation.ClockState.Filling>。 <xref:System.Windows.Media.Animation.ClockState.Filling> 的動畫會保存其最終輸出值。

上一個範例中的 <xref:System.Windows.Media.Animation.DoubleAnimation> 不會結束，因為其 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性設定為 [<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>]。 下列範例使用類似的動畫，以動畫顯示矩形。 與上一個範例不同的是，這個動畫的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 和 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> 屬性會保留其預設值。 因此，動畫在五秒內從 1 開始進行到 0，然後停止。

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

因為其 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 不會從 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>的預設值變更，所以動畫會在結束時保留其最終值0。 因此，在動畫結束後，矩形的 <xref:System.Windows.UIElement.Opacity%2A> 會維持在0。 如果您將矩形的 <xref:System.Windows.UIElement.Opacity%2A> 設定為另一個值，則您的程式碼看起來不會有任何作用，因為動畫仍然會影響 <xref:System.Windows.UIElement.Opacity%2A> 屬性。

若要在程式碼中重新取得動畫屬性的控制權，其中一種方法是使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法，並為 <xref:System.Windows.Media.Animation.AnimationTimeline> 參數指定 null。 如需詳細資訊和範例，請參閱[使用分鏡腳本建立屬性的動畫後進行設定](how-to-set-a-property-after-animating-it-with-a-storyboard.md)。

請注意，雖然設定具有 <xref:System.Windows.Media.Animation.ClockState.Active> 或 <xref:System.Windows.Media.Animation.ClockState.Filling> 動畫的屬性值不會有任何作用，但屬性值的確會變更。 如需詳細資訊，請參閱[動畫和計時系統總覽](animation-and-timing-system-overview.md)。

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>資料繫結和建立動畫

大部分的動畫屬性可以是資料系結或動畫;例如，您可以建立 <xref:System.Windows.Media.Animation.DoubleAnimation>之 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性的動畫。 不過，由於計時系統的運作方式，資料繫結或動畫顯示的動畫不像其他資料繫結或動畫物件。 若要了解其行為，了解對屬性套用動畫的意義會很有幫助。

請參閱上一節中的範例，示範如何以動畫顯示矩形的 <xref:System.Windows.UIElement.Opacity%2A>。 載入上一個範例中的矩形時，其事件觸發程式會套用 <xref:System.Windows.Media.Animation.Storyboard>。 計時系統會建立 <xref:System.Windows.Media.Animation.Storyboard> 和其動畫的複本。 這些複本會凍結（設為唯讀），並從它們建立 <xref:System.Windows.Media.Animation.Clock> 物件。 這些時鐘會執行以動畫顯示目標屬性的實際工作。

計時系統會為 <xref:System.Windows.Media.Animation.DoubleAnimation> 建立時鐘，並將其套用至 <xref:System.Windows.Media.Animation.DoubleAnimation>的 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 所指定的物件和屬性。 在此情況下，計時系統會將時鐘套用至名為 "MyRectangle" 之物件的 <xref:System.Windows.UIElement.Opacity%2A> 屬性。

雖然也會為 <xref:System.Windows.Media.Animation.Storyboard>建立時鐘，但時鐘不會套用至任何屬性。 其目的是要控制其子時鐘，這是針對 <xref:System.Windows.Media.Animation.DoubleAnimation>所建立的時鐘。

若要讓動畫反映出資料繫結或動畫變更，就必須重新產生動畫的時鐘。 時鐘不會自動產生。 若要讓動畫反映變更，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 或 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法來重新套用其分鏡腳本。 當您使用其中一種方法時，動畫會重新啟動。 在程式碼中，您可以使用 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法，將分鏡腳本移回先前的位置。

如需資料系結動畫的範例，請參閱[主要曲線動畫範例](https://go.microsoft.com/fwlink/?LinkID=160011)。 如需動畫和計時系統運作方式的詳細資訊，請參閱[動畫和計時系統總覽](animation-and-timing-system-overview.md)。

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>顯示動畫的其他方式

本概觀中的範例示範如何使用分鏡腳本顯示動畫。 當您使用程式碼時，可以使用其他幾種方式顯示動畫。 如需詳細資訊，請參閱[屬性動畫技術總覽](property-animation-techniques-overview.md)。

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
|[動畫和計時系統概觀](animation-and-timing-system-overview.md)|描述計時系統如何使用 <xref:System.Windows.Media.Animation.Timeline> 和 <xref:System.Windows.Media.Animation.Clock> 類別，這可讓您建立動畫。|
|[動畫祕訣和訣竅](animation-tips-and-tricks.md)|列出解決動畫問題 (例如效能) 的有用祕訣。|
|[自訂動畫概觀](custom-animations-overview.md)|描述如何使用主要畫面格、動畫類別或每個畫面格回呼來擴充動畫系統。|
|[From/To/By 動畫概觀](from-to-by-animations-overview.md)|描述如何建立在兩個值之間轉換的動畫。|
|[主要畫面格動畫概觀](key-frame-animations-overview.md)|描述如何建立有多個目標值的動畫，包括控制插補方法的能力。|
|[Easing 函式](easing-functions.md)|說明如何對動畫套用數學公式以獲得實際的行為，例如彈跳。|
|[路徑動畫概觀](path-animations-overview.md)|描述如何沿著複雜路徑移動或旋轉物件。|
|[屬性動畫技術概觀](property-animation-techniques-overview.md)|描述使用分鏡腳本的屬性動畫、本機動畫、時鐘和每個畫面格動畫。|
|[分鏡腳本概觀](storyboards-overview.md)|描述如何使用有多個時間軸的分鏡腳本建立複雜的動畫。|
|[計時行為概觀](timing-behaviors-overview.md)|描述動畫中使用的 <xref:System.Windows.Media.Animation.Timeline> 類型和屬性。|
|[計時事件概觀](timing-events-overview.md)|描述 <xref:System.Windows.Media.Animation.Timeline> 和 <xref:System.Windows.Media.Animation.Clock> 物件上可用的事件，以在時間軸中的點執行程式碼，例如 [開始]、[暫停]、[繼續]、[略過] 或 [停止]。|
|[「如何」主題](animation-and-timing-how-to-topics.md)|包含在應用程式中使用動畫及時間軸的程式碼範例。|
|[時鐘操作說明主題](clocks-how-to-topics.md)|包含在您的應用程式中使用 <xref:System.Windows.Media.Animation.Clock> 物件的程式碼範例。|
|[主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)|包含在應用程式中使用主要畫面格動畫的程式碼範例。|
|[路徑動畫操作說明主題](path-animation-how-to-topics.md)|包含在應用程式中使用路徑動畫的程式碼範例。|

<a name="reference"></a>

## <a name="reference"></a>參考資料

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
