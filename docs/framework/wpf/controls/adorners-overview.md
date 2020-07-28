---
title: 裝飾項概觀
description: 瞭解 Windows Presentation Foundation 的裝飾項，這是一種特殊類型的 FrameworkElement，可提供提示給使用者，例如元素的功能控制碼。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167733"
---
# <a name="adorners-overview"></a>裝飾項概觀

「裝飾項」是一種特殊類型的 <xref:System.Windows.FrameworkElement> ，可用來為使用者提供視覺提示。 除了其他用法，裝飾項還可用來將功能控點加入項目，或提供控制項的狀態資訊。

## <a name="about-adorners"></a>關於裝飾項

是系結 <xref:System.Windows.Documents.Adorner> 至的自訂 <xref:System.Windows.FrameworkElement> <xref:System.Windows.UIElement> 。 裝飾項會在中轉譯 <xref:System.Windows.Documents.AdornerLayer> ，這是一種呈現介面，一律在裝飾專案的頂端，或是裝飾專案的集合。 轉譯裝飾項與轉譯裝飾項所系結的呈現無關 <xref:System.Windows.UIElement> 。 裝飾項的位置通常是相對於其所系結的專案，使用位於裝飾元素左上方的標準2D 座標原點。

裝飾項的常見應用包括︰

- 將功能控制碼加入至 <xref:System.Windows.UIElement> ，讓使用者能夠以某種方式操作專案（調整大小、旋轉、重新置放等等）。
- 提供視覺化回應以表示各種狀態，或回應各種事件。
- 重迭上的視覺效果裝飾 <xref:System.Windows.UIElement> 。
- 以視覺化方式遮罩或覆寫部分或全部 <xref:System.Windows.UIElement> 。

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供基本的架構以便裝飾視覺項目。 下表列出在裝飾物件時所使用的主要類型，及其用途。 以下是幾個使用範例：

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|抽象基底類別，所有具體裝飾項實作都繼承自該類別。|
|<xref:System.Windows.Documents.AdornerLayer>|代表一個或多個裝飾項目的裝飾項轉譯層的類別。|
|<xref:System.Windows.Documents.AdornerDecorator>|可讓裝飾項層與項目集合相關聯的類別。|

## <a name="implementing-a-custom-adorner"></a>實作自訂裝飾項

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]　提供的裝飾項架構主要是為了支援建立自訂裝飾項。 自訂裝飾項是藉由執行繼承自抽象類別的類別來建立 <xref:System.Windows.Documents.Adorner> 。

> [!NOTE]
> 的父系 <xref:System.Windows.Documents.Adorner> 是呈現的，而不是所裝飾的專案 <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.Documents.Adorner> 。

下列範例顯示一個實作簡單裝飾項的類別。 範例裝飾項只會裝飾具有圓圈的圓角 <xref:System.Windows.UIElement> 。

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
下圖顯示適用于的 SimpleCircleAdorner <xref:System.Windows.Controls.TextBox> ：

![顯示已裝飾文字方塊的螢幕擷取畫面。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>裝飾項的轉譯行為

請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。 執行轉譯行為的常見方式是覆寫 <xref:System.Windows.UIElement.OnRender%2A> 方法，並視需要使用一或多個 <xref:System.Windows.Media.DrawingContext> 物件來呈現裝飾項的視覺效果（如上述範例所示）。

> [!NOTE]
> 放在裝飾項圖層中的任何項目會轉譯在您已設定的其餘任何樣式之上。 換句話說，裝飾項永遠是以視覺化方式在最上面，而且無法使用疊置順序覆寫。

## <a name="events-and-hit-testing"></a>事件和點擊測試

裝飾項會接收輸入事件，就像任何其他一樣 <xref:System.Windows.FrameworkElement> 。  由於裝飾項的迭置順序一律會高於它所裝飾的元素，因此，裝飾項 <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove> 會接收可能適用于基礎裝飾元素的輸入事件（例如或）。  裝飾項可以接聽特定的輸入事件，並藉由重新引發事件將它們傳送到基礎的被裝飾項目。

若要在裝飾項下啟用專案的傳遞點擊測試，請將 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 裝飾項上的點擊測試屬性設定為**false** 。  如需點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。

## <a name="adorning-a-single-uielement"></a>裝飾單一的 UIElement

若要將裝飾項系結至特定 <xref:System.Windows.UIElement> ，請遵循下列步驟：

1. 呼叫靜態方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> ，取得 <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.UIElement> 要裝飾之的物件。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>從指定的開始逐步解說視覺化樹狀結構， <xref:System.Windows.UIElement> 並傳回它找到的第一個裝飾項層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)

2. 呼叫 <xref:System.Windows.Documents.AdornerLayer.Add%2A> 方法，將裝飾項系結至目標 <xref:System.Windows.UIElement> 。

 下列範例會將 SimpleCircleAdorner （如上所示）系結至 <xref:System.Windows.Controls.TextBox> 名為的*myTextBox*：

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。

## <a name="adorning-the-children-of-a-panel"></a>裝飾 Panel 的子系

若要將裝飾項系結至的子系 <xref:System.Windows.Controls.Panel> ，請遵循下列步驟：

1. 呼叫 `static` 方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> ，尋找要裝飾其子系之元素的裝飾項層。

2. 列舉父元素的子系，並呼叫方法， <xref:System.Windows.Documents.AdornerLayer.Add%2A> 將裝飾項系結至每個子專案。

下列範例會將 SimpleCircleAdorner （如上所示）系結至 <xref:System.Windows.Controls.StackPanel> 名為*myStackPanel*的子系：

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF 中圖案和基本繪圖概觀](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [使用影像、繪圖和視覺效果繪製](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [繪圖物件概觀](../graphics-multimedia/drawing-objects-overview.md)
- [操作說明主題](adorners-how-to-topics.md)
