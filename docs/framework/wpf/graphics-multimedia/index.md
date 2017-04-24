---
title: "圖形和多媒體 | Microsoft Docs"
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
  - "動畫, 功能"
  - "圖形功能"
  - "媒體, 功能"
  - "音效"
  - "轉換效果"
  - "視訊效果"
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# 圖形和多媒體
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了多媒體、向量圖形、動畫和內容撰寫的支援，讓開發人員可以更容易地建立有趣的使用者介面和內容。  您可以使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，建立向量圖形或複雜的動畫，並將媒體整合到您的應用程式中。  
  
 本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，這些功能讓您可以在您的應用程式中加入圖形、轉換效果、音效和視訊。  
  
> [!NOTE]
>  我們非常不建議您在 Windows 服務中使用 WPF 型別。  如果您嘗試在 Windows 服務中使用 WPF 型別，服務可能無法如預期般運作。  
  
   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## WPF 4 圖形和多媒體的新功能  
 圖形與動畫已有了數項變更。  
  
-   配置進位  
  
     當物件邊緣落在像素裝置中央時，與 DPI 無關的圖形系統可能會建立轉譯疊影，例如模糊或半透明的邊緣。  舊版的 WPF 包含像素格線編排，可協助處理此情況。  Silverlight 2 引進了配置進位，這是移動項目使邊緣落在整個像素界限內的另一種方式。  現在，WPF 透過 <xref:System.Windows.FrameworkElement> 上的 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 附加屬性支援配置進位。  
  
-   快取複合  
  
     使用新的 <xref:System.Windows.Media.BitmapCache> 和 <xref:System.Windows.Media.BitmapCacheBrush> 類別，您就可以快取複雜的視覺化樹狀結構部分做為點陣圖，並且大幅改善轉譯的時間。  點陣圖會持續回應使用者輸入，例如滑鼠點選，而且您可以將它繪製到其他項目上，就如同筆刷一般。  
  
-   支援 Pixel Shader 3  
  
     WPF 4 建置於 <xref:System.Windows.Media.Effects.ShaderEffect> 支援之上，這項支援於 WPF 3.5 SP1 引進，可讓應用程式使用像素著色器 \(PS\) 3.0 版撰寫效果。  PS 3.0 著色器模式比 PS 2.0 更為複雜，可在支援的硬體上提供更多效果。  
  
-   Easing 函式  
  
     您可以使用 easing 函式增強動畫，這類函式可讓您進一步掌控動畫的行為。  例如，您可以將 <xref:System.Windows.Media.Animation.ElasticEase> 套用至動畫，讓動畫執行輕快跳動的行為。  如需詳細資訊，請參閱 <xref:System.Windows.Media.Animation> 命名空間中的 easing 型別。  
  
<a name="graphics_and_rendering"></a>   
## 圖形和轉譯  
 WPF 包含高品質 2D 動畫的支援。  功能包括筆刷、幾何、影像、圖案和轉換。  如需詳細資訊，請參閱[圖形](../../../../docs/framework/wpf/graphics-multimedia/graphics.md)。  圖形項目的轉譯以 <xref:System.Windows.Media.Visual> 類別為基礎。  畫面上視覺化物件的結構以視覺化結構來描述。  如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
### 2D 圖案  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供常用的向量繪製 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖案庫，如下圖所示的矩形和橢圓形。  
  
 ![橢圓形和矩形](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.png "WPFIntroFigure4")  
  
 這些內建 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖案不只是形狀而已：它們是可程式化的項目，會實作許多您希望最常見的控制項所需具備的功能，包括鍵盤和滑鼠輸入。  下列範例顯示如何處理由按一下 <xref:System.Windows.Shapes.Ellipse> 項目所引起的 <xref:System.Windows.UIElement.MouseUp> 事件。  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  x:Class="Window1" >  
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />  
</Window>  
```  
  
```csharp  
public partial class Window1  : Window  
{  
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)  
    {  
        MessageBox.Show("You clicked the ellipse!");  
    }  
}  
```  
  
```vb  
Partial Public Class Window1  
    Inherits Window  
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)  
        MessageBox.Show("You clicked the ellipse!")  
    End Sub  
End Class  
  
```  
  
 下圖顯示上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記的輸出及程式碼後置 \(Code\-Behind\)。  
  
 ![包含「您已經按一下這個橢圓形！」文字的視窗](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)。  如需入門範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。  
  
### 2D 幾何  
 如果 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖案不敷使用，您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的幾何圖形和路徑支援來自行建立 2\-D 圖案。  下圖顯示如何用幾何圖形來建立圖案、做為繪圖筆刷，以及裁剪其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 項目。  
  
 ![Path 的各種用法](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.png "WPFIntroFigure5")  
  
 如需詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  如需入門範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989) \(英文\)。  
  
### 2D 效果  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 類別的程式庫，可供您建立各種效果。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 呈現功能可繪製具有漸層、點陣圖、繪圖和視訊的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目，並能利用旋轉、縮放和[傾斜](GTMT)來操控這些項目。  下圖示範許多可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 筆刷做出的效果。  
  
 ![不同筆刷的圖例](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.png "WPFIntroFigure6")  
  
 如需詳細資訊，請參閱 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)。  如需入門範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  
  
<a name="rendering"></a>   
## 立體呈現  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供一組[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]呈現功能，這些功能已與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形支援整合，可讓您建立更具吸引力的配置、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和資料視覺效果。  最後，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 還可讓您在[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]圖案的表面上呈現 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 影像，如下圖所示。  
  
 ![Visual3D 範例螢幕擷取畫面](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 如需詳細資訊，請參閱[立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)。  如需入門範例，請參閱[立體實體範例](http://go.microsoft.com/fwlink/?LinkID=159964) \(英文\)。  
  
<a name="animation"></a>   
## 動畫  
 動畫可以讓控制項和項目變大、搖晃、旋轉和淡出，以及建立有趣的頁面轉換等。  因為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可以讓您對大部分屬性建立動畫，所以您不只可以建立大部分 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 物件的動畫，還可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 建立所建立之自訂物件的動畫。  
  
 ![立方體動畫的影像](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  如需入門範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969) \(英文\)。  
  
<a name="media"></a>   
## 媒體  
 影像、視訊和音訊都是一種運用媒體來傳達資訊和營造豐富使用者經驗的方式。  
  
### 影像  
 影像 \(包括圖示、背景，甚至是動畫的一部分\) 是大多數應用程式的核心。  因為您經常需要使用影像，所以 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供了以各種方式運用影像的能力。  下圖只顯示其中一種方式。  
  
 ![設定樣式範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro\_EventTriggers")  
  
 如需詳細資訊，請參閱[影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。  
  
### 視訊和音訊  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形能力的核心功能是提供使用多媒體的原生支援，包括視訊和音訊。  下列範例顯示如何在應用程式中插入媒體播放程式。  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> 可以同時播放視訊和音訊，且具有足夠的延伸性來輕易建立自訂的 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。  
  
 如需詳細資訊，請參閱 [多媒體概觀](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Media3D>   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [3\-D Graphics](http://msdn.microsoft.com/zh-tw/565c1f3c-235b-47de-b05b-3b53ed63f1b8)   
 [Multimedia](http://msdn.microsoft.com/zh-tw/44a8dcd0-80cb-4db0-a222-87cde68c2fac)