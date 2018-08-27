---
title: 腳本概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: a7f9539cd3ac571977a91cd4e7dce07d641af3b6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932317"
---
# <a name="storyboards-overview"></a>分鏡腳本概觀
本主題說明如何使用<xref:System.Windows.Media.Animation.Storyboard>來組織和套用動畫的物件。 說明如何以互動方式操作<xref:System.Windows.Media.Animation.Storyboard>物件，並說明間接屬性目標語法。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉不同的動畫類型及其基本功能。 如需動畫的簡介，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。 您也應該了解如何使用附加屬性。 如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>什麼是分鏡腳本？  
 動畫不是唯一有用的時間軸型別。 還有其他時間軸類別可以協助您組織時間軸集合，以及將時間軸套用至屬性。 容器時間軸衍生自<xref:System.Windows.Media.Animation.TimelineGroup>類別，並包含<xref:System.Windows.Media.Animation.ParallelTimeline>和<xref:System.Windows.Media.Animation.Storyboard>。  
  
 A<xref:System.Windows.Media.Animation.Storyboard>是一種容器時間軸，提供它所包含的時間軸目標資訊。 分鏡腳本可以包含任何類型的<xref:System.Windows.Media.Animation.Timeline>，包括其他容器時間軸和動畫。 <xref:System.Windows.Media.Animation.Storyboard> 物件可讓您結合成單一時間軸的樹狀結構，輕鬆地組織和控制複雜的計時行為的各種不同的物件和屬性會影響到的時間軸。 例如，假設您想讓按鈕執行下列三個動作。  
  
-   在使用者選取按鈕時放大及變更色彩。  
  
-   按一下按鈕時縮小再放大回原本大小。  
  
-   在停用時縮小並淡化到 50% 的不透明度。  
  
 在此案例中，您有多組套用至同一個物件的動畫，並且想要視按鈕的狀態在不同時間播放。 <xref:System.Windows.Media.Animation.Storyboard> 物件可讓您組織動畫，並在群組中套用至一或多個物件。  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>何處可以使用分鏡腳本？  
 A<xref:System.Windows.Media.Animation.Storyboard>可用來以動畫顯示相依性屬性的動畫類別 (如需有關如何使類別可用來建立動畫的詳細資訊，請參閱 <<c2> [ 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md))。 不過，因為分鏡腳本是架構層級的功能，該物件必須屬於<xref:System.Windows.NameScope>的<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。  
  
 例如，您可以使用<xref:System.Windows.Media.Animation.Storyboard>執行下列動作：  
  
-   建立動畫<xref:System.Windows.Media.SolidColorBrush>（非架構元素），其會繪製按鈕的背景 (一種<xref:System.Windows.FrameworkElement>)，  
  
-   建立動畫<xref:System.Windows.Media.SolidColorBrush>（非架構元素） 繪製的填色<xref:System.Windows.Media.GeometryDrawing>使用的 （非架構元素） 顯示<xref:System.Windows.Controls.Image>(<xref:System.Windows.FrameworkElement>)。  
  
-   在程式碼中建立動畫<xref:System.Windows.Media.SolidColorBrush>宣告的類別，其中也包含<xref:System.Windows.FrameworkElement>，如果<xref:System.Windows.Media.SolidColorBrush>註冊其名稱與<xref:System.Windows.FrameworkElement>。  
  
 不過，您無法使用<xref:System.Windows.Media.Animation.Storyboard>來建立動畫<xref:System.Windows.Media.SolidColorBrush>並未註冊使用其名稱<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>，或不用來設定的屬性<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>如何以分鏡腳本套用動畫  
 若要使用<xref:System.Windows.Media.Animation.Storyboard>來組織和套用動畫，您必須將動畫加入為子時間軸<xref:System.Windows.Media.Animation.Storyboard>。 <xref:System.Windows.Media.Animation.Storyboard>類別會提供<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType>附加屬性。 您可以設定動畫的這些屬性以指定其目標物件和屬性。  
  
 若要將動畫套用到其目標，請先<xref:System.Windows.Media.Animation.Storyboard>使用觸發程序動作或方法。 在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您使用<xref:System.Windows.Media.Animation.BeginStoryboard>物件<xref:System.Windows.EventTrigger>， <xref:System.Windows.Trigger>，或<xref:System.Windows.DataTrigger>。 在程式碼中，您也可以使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法。  
  
 下表顯示不同的地方，每個<xref:System.Windows.Media.Animation.Storyboard>開始技術支援： 每個執行個體、 樣式、 控制項範本以及資料範本。 「每個執行個體」指的是將動畫或分鏡腳本直接套用至物件之執行個體，而非樣式、控制項範本或資料範本的技術。  
  
|開始分鏡腳本的方法…|每個執行個體|樣式|控制項範本|資料範本|範例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.EventTrigger>|[是]|是|是|[是]|[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和屬性 <xref:System.Windows.Trigger>|否|是|是|[是]|[在屬性值變更時觸發動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.DataTrigger>|否|是|是|[是]|[操作說明︰在資料變更時觸發動畫](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法|[是]|否|否|否|[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 下列範例會使用<xref:System.Windows.Media.Animation.Storyboard>來建立動畫<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>項目和<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用來繪製， <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 下列各節說明<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>更多詳細資料中的附加屬性。  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>以架構元素、架構內容元素和 Freezable 為目標  
 上一節提到，動畫若要尋找其目標，它必須知道目標的名稱和要建立動畫的屬性。 指定要繪製之屬性很簡單： 只要設定<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType>要繪製之屬性的名稱。  指定您想要藉由設定以動畫顯示其屬性的物件名稱<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>動畫的屬性。  
  
 針對<xref:System.Windows.Setter.TargetName%2A>屬性才能運作，目標的物件必須有名稱。 指派名稱給<xref:System.Windows.FrameworkElement>或是<xref:System.Windows.FrameworkContentElement>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]不同於指派名稱給<xref:System.Windows.Freezable>物件。  
  
 架構元素是繼承自這些類別<xref:System.Windows.FrameworkElement>類別。 架構元素的範例包括<xref:System.Windows.Window>， <xref:System.Windows.Controls.DockPanel>， <xref:System.Windows.Controls.Button>，和<xref:System.Windows.Shapes.Rectangle>。 基本上所有的視窗、面板和控制項都是元素。 架構內容元素是繼承自這些類別<xref:System.Windows.FrameworkContentElement>類別。 架構內容元素的範例包括<xref:System.Windows.Documents.FlowDocument>和<xref:System.Windows.Documents.Paragraph>。 如果您不確定某個型別是架構元素或架構內容元素，請檢查它是否具有 Name 屬性。 如果有，它可能是架構元素或架構內容元素。 為了安全起見，請檢查其型別頁面的＜繼承階層＞一節。  
  
 若要啟用以架構元素或架構內容元素中的目標[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您將設定其<xref:System.Windows.FrameworkElement.Name%2A>屬性。 在程式碼中，您也需要使用<xref:System.Windows.NameScope.RegisterName%2A>方法，以註冊項目的名稱與您已建立的項目<xref:System.Windows.NameScope>。  
  
 下列範例中，從上述範例中，將名稱指派`MyRectangle` <xref:System.Windows.Shapes.Rectangle>，一種<xref:System.Windows.FrameworkElement>。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 在元素具有名稱後，您就可以為該元素的屬性建立動畫。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> 型別是繼承自<xref:System.Windows.Freezable>類別。 範例<xref:System.Windows.Freezable>包括<xref:System.Windows.Media.SolidColorBrush>， <xref:System.Windows.Media.RotateTransform>，和<xref:System.Windows.Media.GradientStop>。  
  
 若要啟用的目標<xref:System.Windows.Freezable>中的動畫所[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您使用[X:name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)將它指派名稱。 在程式碼中，您會使用<xref:System.Windows.NameScope.RegisterName%2A>方法，以註冊其名稱與您已建立的項目<xref:System.Windows.NameScope>。  
  
 下列範例會將指派的名稱<xref:System.Windows.Freezable>物件。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 然後物件可以作為動畫的目標。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> 物件會使用名稱範圍，來解決<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>屬性。 如需 WPF 名稱範圍的詳細資訊，請參閱 [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。 如果<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>省略屬性，動畫的元素，其定義所在，或在樣式中，該樣式的元素為目標。  
  
 有時候無法將名稱指派給<xref:System.Windows.Freezable>物件。 例如，如果<xref:System.Windows.Freezable>是宣告為資源，或用來設定屬性值在樣式中，它不能指定名稱。 因為它沒有名稱，就無法直接做為目標，但可間接做為目標。 以下各節會說明如何使用間接目標。  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>間接目標  
 有些時候<xref:System.Windows.Freezable>動畫，例如當無法直接目標<xref:System.Windows.Freezable>是宣告為資源，或用來設定樣式中的屬性值。 在這些情況下，即使您不能直接目標，但您可以仍然以動畫顯示<xref:System.Windows.Freezable>物件。 而不是設定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>屬性的名稱取代<xref:System.Windows.Freezable>，您要提供它的項目名稱<xref:System.Windows.Freezable>「 所屬 」。 例如，<xref:System.Windows.Media.SolidColorBrush>用來設定<xref:System.Windows.Shapes.Shape.Fill%2A>之矩形的項目會屬於該矩形。 若要動畫顯示筆刷，您會設定動畫的<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>以開始架構元素或架構內容元素的屬性的屬性鏈結<xref:System.Windows.Freezable>用來設定，且結尾<xref:System.Windows.Freezable>以動畫顯示屬性。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 請注意，如果<xref:System.Windows.Freezable>已凍結，將會進行複製，並以複製項目建立動畫。 當發生這種情況，原始的物件<xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A>屬性會繼續傳回`false`，因為原始的物件未實際以動畫顯示。 如需有關複製的詳細資訊，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 另請注意，當使用間接屬性目標時，可能會以不存在的物件作為目標。 例如，您可能會假設<xref:System.Windows.Controls.Control.Background%2A>特定按鈕的設定<xref:System.Windows.Media.SolidColorBrush>，然後再試，以動畫顯示其色彩，當事實上<xref:System.Windows.Media.LinearGradientBrush>用來設定按鈕的背景。 在這些情況下，會擲不回任何例外狀況;有可見效果，因為無法動畫<xref:System.Windows.Media.LinearGradientBrush>不會回應變更<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性。  
  
 以下各節會詳細說明間接屬性目標語法。  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>在 XAML 中以 Freezable 屬性為間接目標  
 中以 freezable 屬性為目標[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用下列語法。  
  
| |  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 位置  
  
-   *ElementPropertyName*的屬性<xref:System.Windows.FrameworkElement>其中<xref:System.Windows.Freezable>用來設定，以及  
  
-   *FreezablePropertyName*的屬性<xref:System.Windows.Freezable>以動畫顯示。  
  
 下列程式碼示範如何建立動畫<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用來設定  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> 矩形元素。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 有時候您需要以集合或陣列中包含的 Freezable 為目標。  
  
 若要以集合中包含的 Freezable 為目標，請使用下列路徑語法。  
  
| |  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 何處*CollectionIndex*是其陣列或集合中物件的索引。  
  
 例如，假設矩形擁有<xref:System.Windows.Media.TransformGroup>資源套用至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性，而且您想要以動畫顯示它所包含的轉換的其中一個。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 下列程式碼示範如何建立動畫<xref:System.Windows.Media.RotateTransform.Angle%2A>屬性<xref:System.Windows.Media.RotateTransform>先前範例所示。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>在程式碼中以 Freezable 的屬性為間接目標  
 在程式碼中，您會建立<xref:System.Windows.PropertyPath>物件。 當您建立<xref:System.Windows.PropertyPath>，您指定<xref:System.Windows.PropertyPath.Path%2A>和<xref:System.Windows.PropertyPath.PathParameters%2A>。  
  
 若要建立<xref:System.Windows.PropertyPath.PathParameters%2A>，建立型別的陣列<xref:System.Windows.DependencyProperty>，其中包含一份相依性屬性識別碼欄位。 第一次的識別項欄位代表的屬性<xref:System.Windows.FrameworkElement>或是<xref:System.Windows.FrameworkContentElement>的<xref:System.Windows.Freezable>用來設定。 [下一步] 的 [識別碼] 欄位表示的屬性<xref:System.Windows.Freezable>為目標。 把它想成連接屬性的一連串<xref:System.Windows.Freezable>至<xref:System.Windows.FrameworkElement>物件。  
  
 以下是範例的目標相依性屬性鏈結<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用以設定<xref:System.Windows.Shapes.Shape.Fill%2A>矩形元素。  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 您也需要指定<xref:System.Windows.PropertyPath.Path%2A>。 A<xref:System.Windows.PropertyPath.Path%2A>已<xref:System.String>告訴<xref:System.Windows.PropertyPath.Path%2A>如何解譯其<xref:System.Windows.PropertyPath.PathParameters%2A>。 它會使用下列語法。  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 位置  
  
-   *OwnerPropertyArrayIndex*的索引<xref:System.Windows.DependencyProperty>陣列，其中包含的識別項<xref:System.Windows.FrameworkElement>物件的屬性，<xref:System.Windows.Freezable>用來設定，以及  
  
-   *FreezablePropertyArrayIndex*的索引<xref:System.Windows.DependencyProperty>陣列，其中包含目標屬性的識別項。  
  
 下列範例所示<xref:System.Windows.PropertyPath.Path%2A>，伴隨<xref:System.Windows.PropertyPath.PathParameters%2A>上述範例中所定義。
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 下列範例會結合以動畫顯示先前範例中的程式碼<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用以設定<xref:System.Windows.Shapes.Shape.Fill%2A>矩形元素。  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 有時候您需要以集合或陣列中包含的 Freezable 為目標。 例如，假設矩形擁有<xref:System.Windows.Media.TransformGroup>資源套用至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性，而且您想要以動畫顯示它所包含的轉換的其中一個。  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 目標<xref:System.Windows.Freezable>包含在集合中，使用下列路徑語法。  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 何處*CollectionIndex*是其陣列或集合中物件的索引。  
  
 目標<xref:System.Windows.Media.RotateTransform.Angle%2A>的屬性<xref:System.Windows.Media.RotateTransform>中的第二個轉換<xref:System.Windows.Media.TransformGroup>，您可以使用下列<xref:System.Windows.PropertyPath.Path%2A>和<xref:System.Windows.PropertyPath.PathParameters%2A>。  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 下列範例示範完整的程式碼建立動畫<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>內含<xref:System.Windows.Media.TransformGroup>。  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>以 Freezable 作為起點的間接目標  
 先前各節說明如何設定間接目標<xref:System.Windows.Freezable>開始<xref:System.Windows.FrameworkElement>或是<xref:System.Windows.FrameworkContentElement>並建立屬性鏈結連到<xref:System.Windows.Freezable>子屬性。 您也可以使用<xref:System.Windows.Freezable>做為開始點，並間接目標的其中一個其<xref:System.Windows.Freezable>子屬性。 在使用時，適用一個額外的限制<xref:System.Windows.Freezable>做為起點的間接目標： 起始<xref:System.Windows.Freezable>和每<xref:System.Windows.Freezable>它與間接做為目標的子屬性之間都不能凍結。  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>在 XAML 中以互動方式控制分鏡腳本  
 在中啟動分鏡腳本[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您使用<xref:System.Windows.Media.Animation.BeginStoryboard>觸發動作。 <xref:System.Windows.Media.Animation.BeginStoryboard> 會將這些物件和屬性，它們建立動畫，並啟動分鏡腳本動畫。 (如需此程序的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。)如果您賦予<xref:System.Windows.Media.Animation.BeginStoryboard>藉由指定的名稱及其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性，讓它可控制的分鏡腳本。 接著在分鏡腳本啟動後，您就可能以互動方式控制它。 以下是可控制之分鏡腳本動作的清單，您可以將這些動作與事件觸發程序搭配使用以控制分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>： 暫停分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>： 繼續已暫停的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>： 變更分鏡腳本的速度。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>： 如果有的話，請前進到其填滿期間中，結尾的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>： 停止分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>： 移除分鏡腳本。  
  
 在下列範例中，會使用可控制的分鏡腳本動作以互動方式控制分鏡腳本。  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>使用程式碼以互動方式控制分鏡腳本  
 前述範例顯示如何使用觸發動作顯示動畫。 程式碼中，您也可以控制使用互動方法分鏡腳本<xref:System.Windows.Media.Animation.Storyboard>類別。 針對<xref:System.Windows.Media.Animation.Storyboard>設為互動式程式碼中，您必須使用分鏡腳本的適當多載<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法並指定`true`進行控制。 請參閱<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>頁面以取得詳細的資訊。  
  
 下列清單顯示可用來操作的方法<xref:System.Windows.Media.Animation.Storyboard>啟動之後：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 使用這些方法的優點是，您不需要建立<xref:System.Windows.Trigger>或是<xref:System.Windows.TriggerAction>物件; 您只需要參考可控制<xref:System.Windows.Media.Animation.Storyboard>您想要操作。  
  
 **注意：** 上所執行的所有互動式動作<xref:System.Windows.Media.Animation.Clock>，，因此也在<xref:System.Windows.Media.Animation.Storyboard>會在計時引擎就會發生下一次轉譯之前的下一個刻度上進行。 例如，如果您使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>跳到另一個點的動畫，屬性值的方法不會立即變更，值而變更下一個刻度在計時引擎。  
  
 下列範例示範如何套用和控制動畫的互動式方法<xref:System.Windows.Media.Animation.Storyboard>類別。  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>在樣式中建立動畫  
 您可以使用<xref:System.Windows.Media.Animation.Storyboard>物件來定義中的動畫<xref:System.Windows.Style>。 使用建立動畫<xref:System.Windows.Media.Animation.Storyboard>中<xref:System.Windows.Style>類似於使用<xref:System.Windows.Media.Animation.Storyboard>其他地方，使用下列三個例外狀況：  
  
-   您未指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>;<xref:System.Windows.Media.Animation.Storyboard>永遠為目標的項目<xref:System.Windows.Style>套用。 目標<xref:System.Windows.Freezable>物件，您必須使用間接目標。 如需有關間接目標的詳細資訊，請參閱 <<c0> [ 間接目標](#pathsyntaxforchangeable)一節。  
  
-   您無法指定<xref:System.Windows.EventTrigger.SourceName%2A>for<xref:System.Windows.EventTrigger>或<xref:System.Windows.Trigger>。  
  
-   您無法使用動態資源參考或資料繫結運算式來設定<xref:System.Windows.Media.Animation.Storyboard>或動畫屬性值。 這是因為所有東西放<xref:System.Windows.Style>必須是安全執行緒，而且計時系統必須<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>物件，以使它們具備執行緒安全。 A<xref:System.Windows.Media.Animation.Storyboard>如果它或它的子時間軸包含動態資源參考或資料繫結運算式不能凍結。 如需凍結和其他<xref:System.Windows.Freezable>功能，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
-   在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您不能宣告事件處理常式<xref:System.Windows.Media.Animation.Storyboard>或動畫事件。  
  
 如需示範如何在樣式中定義分鏡腳本的範例，請參閱[在樣式中的建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md)範例。  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>在 ControlTemplate 中建立動畫  
 您可以使用<xref:System.Windows.Media.Animation.Storyboard>物件來定義中的動畫<xref:System.Windows.Controls.ControlTemplate>。 使用建立動畫<xref:System.Windows.Media.Animation.Storyboard>中<xref:System.Windows.Controls.ControlTemplate>類似於使用<xref:System.Windows.Media.Animation.Storyboard>其他地方，使用下列兩項例外狀況：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>只能參考到子物件的<xref:System.Windows.Controls.ControlTemplate>。 如果<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>未指定，動畫為目標的項目<xref:System.Windows.Controls.ControlTemplate>套用。  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> For<xref:System.Windows.EventTrigger>或是<xref:System.Windows.Trigger>只能參考到子物件的<xref:System.Windows.Controls.ControlTemplate>。  
  
-   您無法使用動態資源參考或資料繫結運算式來設定<xref:System.Windows.Media.Animation.Storyboard>或動畫屬性值。 這是因為所有東西放<xref:System.Windows.Controls.ControlTemplate>必須是安全執行緒，而且計時系統必須<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>物件，以使它們具備執行緒安全。 A<xref:System.Windows.Media.Animation.Storyboard>如果它或它的子時間軸包含動態資源參考或資料繫結運算式不能凍結。 如需凍結和其他<xref:System.Windows.Freezable>功能，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
-   在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您不能宣告事件處理常式<xref:System.Windows.Media.Animation.Storyboard>或動畫事件。  
  
 如需範例，示範如何定義中的分鏡腳本<xref:System.Windows.Controls.ControlTemplate>，請參閱 <<c2> [ 在 ControlTemplate 中的建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)範例。  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>在屬性值變更時建立動畫  
 在樣式和控制項範本中，您可以使用 Trigger 物件在屬性變更時啟動分鏡腳本。 如需範例，請參閱[動畫時在屬性值變更會觸發](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)並[在 ControlTemplate 中的建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)。  
  
 套用屬性的動畫<xref:System.Windows.Trigger>物件的行為更複雜的方式比<xref:System.Windows.EventTrigger>動畫開始使用<xref:System.Windows.Media.Animation.Storyboard>方法。  這些 「 傳遞 」 與動畫定義其他<xref:System.Windows.Trigger>物件，但以此撰寫<xref:System.Windows.EventTrigger>和方法觸發動畫。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
