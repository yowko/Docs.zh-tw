---
title: 裝飾項概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111175"
---
# <a name="adorners-overview"></a>裝飾項概觀

裝飾器是一種特殊的類型<xref:System.Windows.FrameworkElement>，用於向使用者提供視覺提示。 除了其他用法，裝飾項還可用來將功能控點加入項目，或提供控制項的狀態資訊。

## <a name="about-adorners"></a>關於裝飾項

是<xref:System.Windows.Documents.Adorner>綁定到<xref:System.Windows.FrameworkElement>的<xref:System.Windows.UIElement>自訂項。 裝飾器以 中呈現<xref:System.Windows.Documents.AdornerLayer>，這是始終位於修飾元素或修飾元素集合之上的呈現曲面。 修飾器的渲染獨立于修飾器綁定到的<xref:System.Windows.UIElement>渲染。 裝飾器通常相對於綁定的元素進行定位，使用位於修飾元素左上角的標準 2D 座標原點。

裝飾項的常見應用包括︰

- 將功能控制碼添加到<xref:System.Windows.UIElement>，使使用者能夠以某種方式操作元素（調整大小、旋轉、重新置放等）。
- 提供視覺化回應以表示各種狀態，或回應各種事件。
- 在 上疊加視覺裝飾<xref:System.Windows.UIElement>。
- 直觀地遮罩或覆蓋 部分或 全部<xref:System.Windows.UIElement>。

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供基本的架構以便裝飾視覺項目。 下表列出在裝飾物件時所使用的主要類型，及其用途。 以下幾個使用示例如下：

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|抽象基底類別，所有具體裝飾項實作都繼承自該類別。|
|<xref:System.Windows.Documents.AdornerLayer>|代表一個或多個裝飾項目的裝飾項轉譯層的類別。|
|<xref:System.Windows.Documents.AdornerDecorator>|可讓裝飾項層與項目集合相關聯的類別。|

## <a name="implementing-a-custom-adorner"></a>實作自訂裝飾項

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]　提供的裝飾項架構主要是為了支援建立自訂裝飾項。 自訂修飾器是通過實現從抽象<xref:System.Windows.Documents.Adorner>類繼承的類創建的。

> [!NOTE]
> 的父<xref:System.Windows.Documents.Adorner>級是<xref:System.Windows.Documents.AdornerLayer>呈現 的<xref:System.Windows.Documents.Adorner>， 而不是正在修飾的元素。

下列範例顯示一個實作簡單裝飾項的類別。 示例修飾器只是修飾帶有圓圈的角<xref:System.Windows.UIElement>。

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
下圖顯示了應用於 的<xref:System.Windows.Controls.TextBox>SimpleCircleAdorner：

![顯示修飾文字方塊的螢幕截圖。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>裝飾項的轉譯行為

請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。 實現呈現行為的常見方法是重寫<xref:System.Windows.UIElement.OnRender%2A>該方法，並使用一個或多個<xref:System.Windows.Media.DrawingContext>物件根據需要呈現修飾器的視覺效果（如上例所示）。

> [!NOTE]
> 放在裝飾項圖層中的任何項目會轉譯在您已設定的其餘任何樣式之上。 換句話說，裝飾項永遠是以視覺化方式在最上面，而且無法使用疊置順序覆寫。

## <a name="events-and-hit-testing"></a>事件和點擊測試

修飾器接收輸入事件就像任何其他<xref:System.Windows.FrameworkElement>一樣。  由於修飾器的 z 順序始終高於其修飾的元素，因此修飾器接收可能用於基礎修飾元素的輸入事件（如<xref:System.Windows.UIElement.Drop><xref:System.Windows.UIElement.MouseMove>或 ）。  裝飾項可以接聽特定的輸入事件，並藉由重新引發事件將它們傳送到基礎的被裝飾項目。

要啟用修飾器下元素的直通點擊測試，將點擊測試<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性設置為修飾器上的**false。**  有關點擊測試的詳細資訊，請參閱[視覺化圖層中的點擊測試](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。

## <a name="adorning-a-single-uielement"></a>裝飾單一的 UIElement

要將裝飾器綁定到特定<xref:System.Windows.UIElement>，請按照以下步驟操作：

1. 調用靜態方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>獲取<xref:System.Windows.Documents.AdornerLayer><xref:System.Windows.UIElement>要修飾的物件。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>向上走，從指定的<xref:System.Windows.UIElement>開始，然後返回它找到的第一個修飾器圖層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)

2. 調用<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法將修飾器綁定到目標<xref:System.Windows.UIElement>。

 下面的示例將 SimpleCircleAdorner（如上圖所示）綁定到<xref:System.Windows.Controls.TextBox>名為*myTextBox ：*

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。

## <a name="adorning-the-children-of-a-panel"></a>裝飾 Panel 的子系

要將裝飾器綁定到 子級<xref:System.Windows.Controls.Panel>，請按照以下步驟操作：

1. 調用`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>查找要修飾其子項目的元素的修飾器圖層。

2. 通過父元素的子項目枚舉，<xref:System.Windows.Documents.AdornerLayer.Add%2A>並調用 方法將修飾器綁定到每個子項目。

下面的示例將 SimpleCircleAdorner（如上圖所示）綁定到<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*的子級：

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF 中圖案和基本繪圖概觀](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [使用影像、繪圖和視覺效果繪製](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [繪圖物件概觀](../graphics-multimedia/drawing-objects-overview.md)
- [如何使用主題](adorners-how-to-topics.md)
