---
title: "腳本概觀 | Microsoft Docs"
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
  - "腳本語法"
  - "語法, 分鏡腳本"
  - "時刻表"
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# 腳本概觀
本主題顯示如何使用 <xref:System.Windows.Media.Animation.Storyboard> 物件組織和套用動畫。  內容說明如何以互動方式管理 <xref:System.Windows.Media.Animation.Storyboard> 物件，並且說明間接屬性目標語法。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要條件  
 若要了解本主題，您應該熟悉不同的動畫類型及其基本功能。  如需動畫功能的簡介，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  您也應該知悉如何使用附加屬性。  如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
<a name="whatisatimeline"></a>   
## 什麼是腳本  
 動畫不是唯一有用的時間表類型，  還有其他時間表類別可以協助您組織時間表集合，以及將時間表套用至屬性。  容器 \(Container\) 時間表衍生自 <xref:System.Windows.Media.Animation.TimelineGroup> 類別，並且包含 <xref:System.Windows.Media.Animation.ParallelTimeline> 和 <xref:System.Windows.Media.Animation.Storyboard>。  
  
 <xref:System.Windows.Media.Animation.Storyboard> 是一種容器時間表，可提供所含時間表的目標資訊。  腳本可以包含任何類型的 <xref:System.Windows.Media.Animation.Timeline>，包括其他容器時間表和動畫。  <xref:System.Windows.Media.Animation.Storyboard> 物件可以讓您將影響各項物件和屬性的時間表合併成單一時間表樹狀目錄，以更輕鬆地組織和控制複雜的時間行為。  例如，假設您想要某個按鈕執行下列三項動作。  
  
-   在使用者選取按鈕時放大及變更色彩。  
  
-   在按一下時縮小再放大回原始大小。  
  
-   在按鈕停用時縮小並呈現 50 % 不透明度。  
  
 在這個案例中，您有多組動畫套用至同一個物件，並且想要視按鈕的狀態在不同時間加以播放。  <xref:System.Windows.Media.Animation.Storyboard> 物件可以讓您組織動畫，並且將動畫以群組套用至一個或多個物件。  
  
<a name="wherecanyouuseastoryboard"></a>   
## 何處可以使用腳本  
 <xref:System.Windows.Media.Animation.Storyboard> 可以利用可展示動畫的類別的[相依性屬性](GTMT)建立動畫 \(如需可展示動畫的類別有何特色的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)\)。  但是，因為腳本是架構層級的功能，所以物件必須屬於 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的 <xref:System.Windows.NameScope>。  
  
 例如，您可以使用 <xref:System.Windows.Media.Animation.Storyboard> 達到下列目的：  
  
-   顯示 <xref:System.Windows.Media.SolidColorBrush> \(非架構項目\) 的動畫，繪製按鈕 \(Button\) \(一種 <xref:System.Windows.FrameworkElement>\) 的背景 \(Background\)，  
  
-   顯示 <xref:System.Windows.Media.SolidColorBrush> \(非架構項目\) 的動畫，使用 <xref:System.Windows.Controls.Image> \(<xref:System.Windows.FrameworkElement>\) 繪製所顯示 <xref:System.Windows.Media.GeometryDrawing> \(非架構項目\) 的填滿部分。  
  
-   在程式碼中，以類別所宣告的 <xref:System.Windows.Media.SolidColorBrush> 對該類別中包含的另一個 <xref:System.Windows.FrameworkElement> 建立動畫，前提是這個 <xref:System.Windows.Media.SolidColorBrush> 必須已向該 <xref:System.Windows.FrameworkElement> 註冊其名稱。  
  
 但是，您無法在 <xref:System.Windows.Media.Animation.Storyboard> 中使用符合下列兩種情況的 <xref:System.Windows.Media.SolidColorBrush> 來建立動畫：未向 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 註冊其名稱，或未用以設定 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的屬性。  
  
<a name="applyanimationswithastoryboard"></a>   
## 如何以腳本套用動畫  
 若要使用 <xref:System.Windows.Media.Animation.Storyboard> 組織和套用動畫，請將動畫加入為 <xref:System.Windows.Media.Animation.Storyboard> 的子時間表。  <xref:System.Windows.Media.Animation.Storyboard> 類別提供 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=fullName> 附加屬性。  設定動畫的這些屬性以指定動畫的目標物件和屬性。  
  
 若要將動畫套用至其目標，請使用觸發程序動作或方法來開始 <xref:System.Windows.Media.Animation.Storyboard>。  在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，可以使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 物件並搭配 <xref:System.Windows.EventTrigger>、<xref:System.Windows.Trigger> 或 <xref:System.Windows.DataTrigger>。  在程式碼中，則還可以使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  
  
 下表顯示每種 <xref:System.Windows.Media.Animation.Storyboard> 開始技術適用的不同位置：個別執行個體、樣式、控制項樣板及資料範本。 「  「個別執行個體」是指將動畫或腳本直接套用至物件執行個體 \(而非樣式、控制項樣板或資料範本\) 的技術。  
  
|開始使用腳本的方法…|個別執行個體|樣式|控制項樣板|資料範本|範例|  
|----------------|------------|--------|-----------|----------|--------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.EventTrigger>|是|是|是|是|[使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和屬性 <xref:System.Windows.Trigger>|否|是|是|是|[當屬性值變更時觸發動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.DataTrigger>|否|是|是|是|[How to: Trigger an Animation When Data Changes](http://msdn.microsoft.com/zh-tw/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法|是|否|否|否|[使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.Storyboard> 以 <xref:System.Windows.Shapes.Rectangle> 項目的 <xref:System.Windows.FrameworkElement.Width%2A>，以及用於繪製該 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Media.SolidColorBrush> 之 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 來建立動畫。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 下列章節會詳細說明 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> 附加屬性。  
  
<a name="targetingelementsandfreezables"></a>   
## 以架構項目、架構內容項目和 Freezable 為目標  
 前面一節曾提到，動畫要找到目標，就必須知悉目標的名稱和要建立動畫的屬性。  指定要建立動畫的屬性相當簡單，只要以要建立動畫的屬性名稱設定 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=fullName> 即可。  至於要建立動畫的屬性所屬的物件名稱，則是透過設定動畫的 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> 屬性來指定。  
  
 若要成功使用 <xref:System.Windows.Setter.TargetName%2A> 屬性，目標物件必須有名稱。  指派名稱給 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>，與指派名稱給 <xref:System.Windows.Freezable> 物件是不同的。  
  
 架構項目是繼承自 <xref:System.Windows.FrameworkElement> 類別的類別。  架構項目的範例包括 <xref:System.Windows.Window>、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Shapes.Rectangle>。  基本上所有視窗、面板和控制項都是項目。  架構內容項目是繼承自 <xref:System.Windows.FrameworkContentElement> 類別的類別。  架構內容項目的範例包括 <xref:System.Windows.Documents.FlowDocument> 和 <xref:System.Windows.Documents.Paragraph>。  如果您不確定某個型別是否為架構項目或架構內容項目，請檢查其是否有 Name 屬性。  如果有，可能是架構項目或架構內容項目。  若要進一步確定，請檢查其型別頁面的＜繼承階層架構＞一節。  
  
 若要能夠在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中以架構項目或架構內容項目為目標，請設定該項目的 <xref:System.Windows.FrameworkElement.Name%2A> 屬性。  在程式碼中，您也必須使用 <xref:System.Windows.NameScope.RegisterName%2A> 方法，將項目名稱註冊至您已建立 <xref:System.Windows.NameScope> 的項目。  
  
 下列取自上一個範例的範例會指派名稱 `MyRectangle` 給 <xref:System.Windows.Shapes.Rectangle>，這是一種 <xref:System.Windows.FrameworkElement>。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 指派名稱給項目之後，就可以用該項目的屬性建立動畫。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> 型別是繼承自 <xref:System.Windows.Freezable> 類別的類別。  <xref:System.Windows.Freezable> 的範例包括 <xref:System.Windows.Media.SolidColorBrush>、<xref:System.Windows.Media.RotateTransform> 和 <xref:System.Windows.Media.GradientStop>。  
  
 若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中使 <xref:System.Windows.Freezable> 能夠做為動畫的目標，請使用 [x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)指派名稱。  在程式碼中，則是使用 <xref:System.Windows.NameScope.RegisterName%2A> 方法，將名稱註冊至您已建立 <xref:System.Windows.NameScope> 的項目。  
  
 下列範例會指派名稱給 <xref:System.Windows.Freezable> 物件。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 然後物件可以就做為動畫的目標。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> 物件會使用名稱範圍來解析 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 屬性。  如需 WPF 名稱範圍的詳細資訊，請參閱 [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  如果省略 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 屬性，則動畫會以定義了該動畫的項目為目標，如果動畫定義在樣式中，則以套用該樣式的項目為目標。  
  
 有時候無法指派名稱給 <xref:System.Windows.Freezable> 物件。  例如，如果 <xref:System.Windows.Freezable> 被宣告為資源或是被用於設定樣式中的屬性值，就不能有名稱。  沒有名稱就不能直接做為目標，但是可以間接做為目標。  下列章節說明如何使用間接目標。  
  
<a name="pathsyntaxforchangeable"></a>   
## 間接目標  
 有時候 <xref:System.Windows.Freezable> 無法讓動畫直接做為目標，例如當 <xref:System.Windows.Freezable> 被宣告為資源或是被用於設定樣式中的屬性值的時候。  在這些情況中，即使無法直接做為目標，仍然可以以 <xref:System.Windows.Freezable> 物件建立動畫，  方法是指定 <xref:System.Windows.Freezable> 所屬項目的名稱，而不是以 <xref:System.Windows.Freezable> 的名稱設定 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 屬性。 例如，有個 <xref:System.Windows.Media.SolidColorBrush> 用於設定矩形項目的 <xref:System.Windows.Shapes.Shape.Fill%2A> 並且屬於該矩形。  若要建立這個筆刷的動畫，可以用屬性鏈結設定動畫的 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>，這個屬性鏈結以 <xref:System.Windows.Freezable> 所設定之架構項目或架構內容項目的屬性開始，以要建立動畫的 <xref:System.Windows.Freezable> 屬性結尾。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 請注意，如果 <xref:System.Windows.Freezable> 凍結，則會建立複製品 \(Clone\)，並以該複製品建立動畫。  發生這種情況時，原始物件的 <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> 屬性會繼續傳回 `false`，因為實際並未以原始物件建立動畫。  如需複製 \(Clone\) 的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 同時請注意，使用間接屬性目標時可以以不存在的物件為目標。  例如，您可能會假設特定按鈕的 <xref:System.Windows.Controls.Control.Background%2A> 是以 <xref:System.Windows.Media.SolidColorBrush> 設定，而嘗試以這個筆刷的色彩 \(Color\) 建立動畫，但實際上 <xref:System.Windows.Media.LinearGradientBrush> 是用於設定按鈕的背景 \(Background\)。  在這些情況中，不會擲回例外狀況，而動畫不會產生視覺效果，因為 <xref:System.Windows.Media.LinearGradientBrush> 不會回應 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性的變更。  
  
 下列章節會詳細說明間接屬性目標語法。  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### 在 XAML 中間接以 Freezable 的屬性為目標  
 若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中以 Freezable 的屬性為目標，請使用下列語法。  
  
||  
|-|  
|*ElementPropertyName*`.`*FreezablePropertyName*|  
  
 其中  
  
-   *ElementPropertyName* 是 <xref:System.Windows.Freezable> 用來設定之 <xref:System.Windows.FrameworkElement> 的屬性，以及  
  
-   *FreezablePropertyName* 是要用於建立動畫的 <xref:System.Windows.Freezable> 的屬性。  
  
 下列程式碼顯示如何以用於設定下列項目之 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 來建立動畫：  
  
 矩形項目的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  
  
  
  
 有時候您需要以包含在集合或陣列中的 Freezable 為目標。  
  
 若要以包含在集合中的 Freezable 為目標，請使用下列路徑語法。  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 其中 *CollectionIndex* 是物件在其陣列或集合中的索引。  
  
 例如，假設矩形的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性套用了 <xref:System.Windows.Media.TransformGroup> 資源，而您想要以該資源包含的其中一個轉換建立動畫。  
  
  
  
 下列程式碼顯示如何以上一個範例中 <xref:System.Windows.Media.RotateTransform> 的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 屬性建立動畫。  
  
  
  
<a name="targetingpropertyofchangeableincode"></a>   
### 在程式碼中間接以 Freezable 的屬性為目標  
 在程式碼中，請建立 <xref:System.Windows.PropertyPath> 物件。  當您建立 <xref:System.Windows.PropertyPath> 時，會指定 <xref:System.Windows.PropertyPath.Path%2A> 和 <xref:System.Windows.PropertyPath.PathParameters%2A>。  
  
 若要建立 <xref:System.Windows.PropertyPath.PathParameters%2A>，請建立 <xref:System.Windows.DependencyProperty> 型別的陣列，其中要包含相依性屬性識別項欄位的清單。  第一個識別項欄位代表用以設定 <xref:System.Windows.Freezable> 之 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的屬性。  下一個識別項欄位代表要做為目標之 <xref:System.Windows.Freezable> 的屬性。  請將它想像為連接 <xref:System.Windows.Freezable> 與 <xref:System.Windows.FrameworkElement> 物件的屬性鏈結。  
  
 以下是以 <xref:System.Windows.Media.SolidColorBrush> \(這個筆刷用以設定矩形項目的 <xref:System.Windows.Shapes.Shape.Fill%2A>\) 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>為目標的相依性屬性鏈結範例。  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 您也需要指定 <xref:System.Windows.PropertyPath.Path%2A>。  <xref:System.Windows.PropertyPath.Path%2A> 是 <xref:System.String>，負責告知 <xref:System.Windows.PropertyPath.Path%2A> 如何解譯其 <xref:System.Windows.PropertyPath.PathParameters%2A>。  它會使用下列語法。  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex*`).(`*FreezablePropertyArrayIndex*`)`|  
  
 其中  
  
-   *OwnerPropertyArrayIndex* 是 <xref:System.Windows.DependencyProperty> 陣列的索引，這個陣列包含 <xref:System.Windows.Freezable> 用以設定之 <xref:System.Windows.FrameworkElement> 物件屬性的識別項，以及  
  
-   *FreezablePropertyArrayIndex* 是 <xref:System.Windows.DependencyProperty> 陣列的索引，這個陣列包含要做為目標之屬性的識別項  
  
 下列範例顯示伴隨上一個範例中定義之 <xref:System.Windows.PropertyPath.PathParameters%2A> 的 <xref:System.Windows.PropertyPath.Path%2A>。  
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 下列範例結合前述範例的程式碼，會以 <xref:System.Windows.Media.SolidColorBrush> \(這個筆刷用以設定矩形項目的 <xref:System.Windows.Shapes.Shape.Fill%2A>\) 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 建立動畫。  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 有時候您需要以包含在集合或陣列中的 Freezable 為目標。  例如，假設矩形的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性套用了 <xref:System.Windows.Media.TransformGroup> 資源，而您想要以該資源包含的其中一個轉換建立動畫。  
  
 [!code-xml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 若要以包含在集合中的 <xref:System.Windows.Freezable> 為目標，請使用下列路徑語法。  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex*`).(` *CollectionChildrenPropertyArrayIndex*`)` `[`*CollectionIndex* `].(`*FreezablePropertyArrayIndex*`)`|  
  
 其中 *CollectionIndex* 是物件在其陣列或集合中的索引。  
  
 若要以 <xref:System.Windows.Media.RotateTransform> \(<xref:System.Windows.Media.TransformGroup> 中的第二個轉換\) 的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 屬性為目標，請使用下列 <xref:System.Windows.PropertyPath.Path%2A> 和 <xref:System.Windows.PropertyPath.PathParameters%2A>。  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 下列範例顯示以 <xref:System.Windows.Media.TransformGroup> 中之 <xref:System.Windows.Media.RotateTransform> 的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 建立動畫時的完整程式碼。  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### 以 Freezable 做為開始點的間接目標  
 前面幾節說明了一種間接以 <xref:System.Windows.Freezable> 為目標的方式，也就是以 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 為開頭，然後建立屬性鏈結連到 <xref:System.Windows.Freezable> 子屬性。  您也可以使用 <xref:System.Windows.Freezable> 做為開始點，然後間接以其中一個 <xref:System.Windows.Freezable> 子屬性做為間接目標。  使用 <xref:System.Windows.Freezable> 做為間接目標的開始點時還有一個額外的限制：做為開始點的 <xref:System.Windows.Freezable>，以及在它與要間接做為目標子屬性之間的每個 <xref:System.Windows.Freezable> 都不能凍結。  
  
<a name="controllable_storyboards"></a>   
## 在 XAML 中以互動方式控制腳本  
 若要在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中開始腳本，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 觸發程序動作。  <xref:System.Windows.Media.Animation.BeginStoryboard> 會將動畫散發至顯示為動畫的物件和屬性，並接著啟動腳本。  \(如需這個程序的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)\)。 如果您藉由指定 <xref:System.Windows.Media.Animation.BeginStoryboard> 的 <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> 屬性來指派名稱，它就會成為可控制的腳本。  在腳本啟動後，您就可以用互動方式控制腳本。  以下是可控制的腳本動作的清單，您可以將這些動作與事件觸發搭配使用以控制腳本。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>：暫停腳本。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>：繼續暫停的腳本。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：變更腳本速度。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>：讓腳本前進至填滿期間結尾 \(如果有的話\)。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>：停止腳本。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>：移除腳本。  
  
 下列範例中會使用可控制的腳本動作以互動方式控制腳本。  
  
 [!code-xml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## 使用程式碼以互動方式控制腳本  
 前述範例顯示如何使用觸發程序動作進行動畫顯示。  在程式碼中，您也可以使用 <xref:System.Windows.Media.Animation.Storyboard> 類別的互動方法來控制腳本。  對於要在程式碼中以互動方式控制的 <xref:System.Windows.Media.Animation.Storyboard>，必須使用腳本之 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法的適當多載，並指定 `true` 使該腳本變成可控制的。  如需詳細資訊，請參閱 <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> 頁面。  
  
 下列清單顯示的方法，可用於管理已啟動的 <xref:System.Windows.Media.Animation.Storyboard>：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 使用這些方法的優點是您不需要建立 <xref:System.Windows.Trigger> 或 <xref:System.Windows.TriggerAction> 物件，只要參考您要管理的可控制的 <xref:System.Windows.Media.Animation.Storyboard> 即可。  
  
 **注意**：所有在 <xref:System.Windows.Media.Animation.Clock> 上執行的互動動作 \(也等於是在 <xref:System.Windows.Media.Animation.Storyboard> 上執行的互動動作\) 會在時間引擎跳到下一個時間時執行，然後很快就會執行下次的呈現作業。  例如，如果您使用 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法跳至動畫中的其他點，屬性值不會立即變更，而是在時間引擎跳到下一個時間時變更。  
  
 下列範例顯示如何使用 <xref:System.Windows.Media.Animation.Storyboard> 類別的互動方法套用和控制動畫。  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## 在樣式中使用動畫  
 您可以在 <xref:System.Windows.Style> 中使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來定義動畫。  在 <xref:System.Windows.Style> 中使用 <xref:System.Windows.Media.Animation.Storyboard> 建立動畫，與在別處使用 <xref:System.Windows.Media.Animation.Storyboard> 類似，除了下列三點例外：  
  
-   您不會指定 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>，<xref:System.Windows.Media.Animation.Storyboard> 一律會以套用該 <xref:System.Windows.Style> 的屬性為目標。  若要以 <xref:System.Windows.Freezable> 物件為目標，您必須使用間接目標。  如需間接目標的詳細資訊，請參閱[間接目標](#pathsyntaxforchangeable)一節。  
  
-   您不能指定 <xref:System.Windows.EventTrigger> 或 <xref:System.Windows.Trigger> 的 <xref:System.Windows.EventTrigger.SourceName%2A>。  
  
-   您不能使用動態資源參考或資料繫結運算式設定 <xref:System.Windows.Media.Animation.Storyboard> 或動畫屬性值。  這是因為 <xref:System.Windows.Style> 內的每個項目都必須是安全執行緒 \(Thread\-Safe\) 的，而且計時系統必須凍結 \(<xref:System.Windows.Freezable.Freeze%2A>\) <xref:System.Windows.Media.Animation.Storyboard> 物件才能讓這些項目是安全執行緒的。  <xref:System.Windows.Media.Animation.Storyboard> 或其子時間表如果包含動態資源參考或資料繫結運算式，就不能凍結。  如需凍結和其他 <xref:System.Windows.Freezable> 功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
-   在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您不能針對 <xref:System.Windows.Media.Animation.Storyboard> 或動畫事件宣告事件處理常式。  
  
 如需如何在樣式中定義腳本的範例，請參閱 [在樣式中建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md)範例。  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## 在 ControlTemplate 中建立動畫  
 您可以在 <xref:System.Windows.Controls.ControlTemplate> 中使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來定義動畫。  在 <xref:System.Windows.Controls.ControlTemplate> 中使用 <xref:System.Windows.Media.Animation.Storyboard> 建立動畫，與在別處使用 <xref:System.Windows.Media.Animation.Storyboard> 類似，除了下列三點例外：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 只能參考 <xref:System.Windows.Controls.ControlTemplate> 的子物件。  如果未指定 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>，動畫會以套用該 <xref:System.Windows.Controls.ControlTemplate> 的項目為目標。  
  
-   <xref:System.Windows.EventTrigger> 或 <xref:System.Windows.Trigger> 的 <xref:System.Windows.EventTrigger.SourceName%2A> 只能參考 <xref:System.Windows.Controls.ControlTemplate> 的子物件。  
  
-   您不能使用動態資源參考或資料繫結運算式設定 <xref:System.Windows.Media.Animation.Storyboard> 或動畫屬性值。  這是因為 <xref:System.Windows.Controls.ControlTemplate> 內的每個項目都必須是安全執行緒的，而且計時系統必須凍結 \(<xref:System.Windows.Freezable.Freeze%2A>\) <xref:System.Windows.Media.Animation.Storyboard> 物件才能讓這些項目是安全執行緒的。  <xref:System.Windows.Media.Animation.Storyboard> 或其子時間表如果包含動態資源參考或資料繫結運算式，就不能凍結。  如需凍結和其他 <xref:System.Windows.Freezable> 功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
-   在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您不能針對 <xref:System.Windows.Media.Animation.Storyboard> 或動畫事件宣告事件處理常式。  
  
 如需如何在 <xref:System.Windows.Controls.ControlTemplate> 中定義腳本的範例，請參閱 [在 ControlTemplate 中建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)範例。  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## 在屬性值變更時產生動畫  
 在樣式和控制項樣板中，您可以使用 Trigger 物件在屬性變更時啟動腳本。  如需範例，請參閱[當屬性值變更時觸發動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) 和[在 ControlTemplate 中建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)。  
  
 由屬性 <xref:System.Windows.Trigger> 物件套用的動畫，行為比 <xref:System.Windows.EventTrigger> 動畫或使用 <xref:System.Windows.Media.Animation.Storyboard> 方法啟動的動畫更為複雜。  它們以其他 <xref:System.Windows.Trigger> 物件定義，但是是由 <xref:System.Windows.EventTrigger> 和方法觸發動畫組成的動畫「傳遞」。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)