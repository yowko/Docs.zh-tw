---
title: 裝飾項概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 6dd38b9e24b42de8945c0e9729f8f30cf901fc3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557117"
---
# <a name="adorners-overview"></a>裝飾項概觀
裝飾項是一種特殊型別的<xref:System.Windows.FrameworkElement>，用來提供視覺提示給使用者。 除了其他用法，裝飾項還可用來將功能控點加入項目，或提供控制項的狀態資訊。  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>關於裝飾項  
 <xref:System.Windows.Documents.Adorner>是 custom<xref:System.Windows.FrameworkElement>繫結至<xref:System.Windows.UIElement>。 裝飾項會呈現在<xref:System.Windows.Documents.AdornerLayer>，這是永遠是裝飾項目或裝飾項目集合的最上方的呈現表面。 轉譯的裝飾項無關的轉譯<xref:System.Windows.UIElement>裝飾項繫結至。 裝飾項的位置通常會相對於它繫結到的項目，並使用標準 2D 座標，原點位於裝飾項目的左上角。  
  
 裝飾項的常見應用包括︰  
  
-   新增功能的控制代碼<xref:System.Windows.UIElement>可讓使用者操作以某種方式 （重新調整大小、 旋轉、 重新定位等等） 的項目。  
  
-   提供視覺化回應以表示各種狀態，或回應各種事件。  
  
-   上重疊 visual 裝飾<xref:System.Windows.UIElement>。  
  
-   以視覺化方式加上遮罩或覆寫的部分或全部<xref:System.Windows.UIElement>。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供基本的架構以便裝飾視覺項目。 下表列出在裝飾物件時所使用的主要類型，及其用途。 以下是幾個使用方式的範例。  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|抽象基底類別，所有具體裝飾項實作都繼承自該類別。|  
|<xref:System.Windows.Documents.AdornerLayer>|代表一個或多個裝飾項目的裝飾項轉譯層的類別。|  
|<xref:System.Windows.Documents.AdornerDecorator>|可讓裝飾項層與項目集合相關聯的類別。|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>實作自訂裝飾項  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]　提供的裝飾項架構主要是為了支援建立自訂裝飾項。 藉由實作繼承自抽象類別建立的自訂裝飾項<xref:System.Windows.Documents.Adorner>類別。  
  
> [!NOTE]
>  父代<xref:System.Windows.Documents.Adorner>是<xref:System.Windows.Documents.AdornerLayer>呈現<xref:System.Windows.Documents.Adorner>不所裝飾的項目。  
  
 下列範例顯示一個實作簡單裝飾項的類別。 範例裝飾項只 adorns 角落<xref:System.Windows.UIElement>使用圓形。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 下圖顯示套用至 SimpleCircleAdorner <xref:System.Windows.Controls.TextBox>。  
  
 ![裝飾項範例：已裝飾的文字方塊](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>裝飾項的轉譯行為  
 請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。   實作轉譯行為的常見方式是覆寫<xref:System.Windows.UIElement.OnRender%2A>方法並使用一或多個<xref:System.Windows.Media.DrawingContext>物件來呈現裝飾項的視覺效果視 （如上述範例所示）。  
  
> [!NOTE]
>  放在裝飾項圖層中的任何項目會轉譯在您已設定的其餘任何樣式之上。 換句話說，裝飾項永遠是以視覺化方式在最上面，而且無法使用疊置順序覆寫。  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>事件和點擊測試  
 裝飾項接收就像任何其他的輸入的事件<xref:System.Windows.FrameworkElement>。  裝飾項裝飾項一律具有較高疊置順序比它 adorns 的項目，因為接收輸入的事件 (例如<xref:System.Windows.UIElement.Drop>或<xref:System.Windows.UIElement.MouseMove>)，可能為了提供給基礎裝飾項目。  裝飾項可以接聽特定的輸入事件，並藉由重新引發事件將它們傳送到基礎的被裝飾項目。  
  
 若要啟用的裝飾項下的項目傳遞點擊測試，設定的點擊的測試<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性**false**上裝飾項。  如需點擊測試的詳細資訊，請參閱  
  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)。  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>裝飾單一的 UIElement  
 若要將裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：  
  
1.  呼叫靜態方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>至會裝飾。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 開始於指定的視覺化樹狀結構會進入<xref:System.Windows.UIElement>，並傳回它發現的第一個裝飾項層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)  
  
2.  呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至目標<xref:System.Windows.UIElement>。  
  
 下列範例會將繫結 （如上所示） 以 SimpleCircleAdorner<xref:System.Windows.Controls.TextBox>名為*myTextBox*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>裝飾 Panel 的子系  
 若要繫結的項目子系的裝飾項<xref:System.Windows.Controls.Panel>，請遵循下列步驟：  
  
1.  呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>找不到裝飾項層，其子系要被裝飾項目。  
  
2.  列舉的子系的父項目並呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至每個子項目。  
  
 下列範例會將繫結 （如上所示） 的項目子系 SimpleCircleAdorner<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
