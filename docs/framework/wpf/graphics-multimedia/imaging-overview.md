---
title: 影像處理概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: d1fcf15db750167a93344ff8efd5957933bed6c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629852"
---
# <a name="imaging-overview"></a>影像處理概觀
本主題提供 [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)] 的簡介。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 可讓開發人員顯示、轉換及格式化影像。  

<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>WPF 影像處理元件  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 提供 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 內重要的影像處理增強功能。 之前的影像處理功能 (例如顯示點陣圖或在通用控制項上使用影像) 要依賴 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 或 [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] 程式庫運作。 這些 API 提供基準影像處理功能, 但缺少支援編解碼器擴充性和高精確度影像支援等功能。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]的設計目的是要克服[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]和[!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]的缺點, 並提供一組新的 API, 在您的應用程式內顯示及使用影像。  
  
 有兩種方式可存取[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] API, 也就是受管理元件和非受控元件。 Unmanaged 元件提供下列功能。  
  
- 新的或專屬影像格式的擴充性模型。  
  
- 改善原生映射格式的效能和安全性, 包括點陣圖 (BMP [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]) [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]、 [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]、、、、和圖示 (.ico)。  
  
- 高位元深度影像資料最多可保留每色頻 8 位元 (每像素 32 位元)。  
  
- 非破壞性的影像縮放、裁剪及旋轉。  
  
- 簡化的色彩管理。  
  
- 支援檔案內、專屬中繼資料。  
  
- Managed 元件會利用 Unmanaged 基礎結構來提供影像與其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 功能 (例如 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、動畫和圖形) 的緊密整合。 受控元件也受益于 Windows Presentation Foundation (WPF) 影像處理編解碼器擴充性模型, 可讓您在應用程式中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]自動辨識新的影像格式。  
  
 大部分的[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]受控 API 都位於<xref:System.Windows.Media.Imaging?displayProperty=nameWithType>命名空間中, 但有數個<xref:System.Windows.Media.ImageBrush>重要的類型 (例如<xref:System.Windows.Media.ImageDrawing>和) 位於<xref:System.Windows.Media?displayProperty=nameWithType>命名空間<xref:System.Windows.Controls.Image>中, 而且<xref:System.Windows.Controls?displayProperty=nameWithType>位於命名空間.  
  
 本主題提供 Managed 元件的詳細資訊。 如需非受控 API 的詳細資訊, 請參閱[非受控 WPF 影像處理元件](/windows/desktop/wic/-wic-lh)檔。  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF 影像格式  
 轉碼器可以用來將特定媒體格式解碼或編碼。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]包含[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]BMP、、 [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]、、 、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]和[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]圖示影像格式的編解碼器。 每個轉碼器都可以讓應用程式解碼和編碼各自的影像格式 (但 ICON 在編碼部分是例外)。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>是用於解碼和編碼影像的重要類別。 它是 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 管線的基本建置組塊，代表在特定大小和解析度下的單一固定像素集。 可以是多個框架影像的個別框架, 也可以是<xref:System.Windows.Media.Imaging.BitmapSource>在上執行之轉換的結果。 <xref:System.Windows.Media.Imaging.BitmapSource> 這是影像中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]所使用之許多主要類別的父系, <xref:System.Windows.Media.Imaging.BitmapFrame>例如。  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame>是用來儲存影像格式的實際點陣圖資料。 許多影像格式僅支援單一<xref:System.Windows.Media.Imaging.BitmapFrame>, 雖然[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]和[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]之類的格式支援每個影像的多個畫面格。 畫面格會由解碼器作為輸入資料並傳遞至編碼器以建立影像檔。  
  
 下列範例示範如何<xref:System.Windows.Media.Imaging.BitmapFrame> <xref:System.Windows.Media.Imaging.BitmapSource>從建立[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] , 然後新增至影像。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>影像格式解碼  
 影像解碼是指將影像格式變成系統可用之影像資料的轉譯作業。 接著可使用影像資料來顯示、處理，或編碼成不同格式。 選取的解碼器是根據影像格式而定。 除非指定特定的解碼器，否則會自動選取轉碼器。 [在 WPF 中顯示影像](#_displayingimages)一節中的範例示範自動解碼。 使用 Unmanaged [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 介面開發並向系統註冊的自訂格式解碼器，會自動參與解碼器選取作業。 這可讓自訂格式自動在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中顯示。  
  
 下列範例示範如何使用點陣圖解碼器來解碼 BMP 格式影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>影像格式編碼  
 影像編碼是指將影像資料變成特定影像格式的轉換作業。 接著可使用已編碼的影像資料建立新的影像檔。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 為上述每一種影像格式提供編碼器。  
  
 下列範例示範使用編碼器儲存新建立的點陣圖影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>在 WPF 中顯示影像  
 有數種方式可以在 Windows Presentation Foundation (WPF) 應用程式中顯示影像。 影像可以使用<xref:System.Windows.Controls.Image>控制項來顯示、 <xref:System.Windows.Media.ImageBrush>使用繪製在視覺效果上<xref:System.Windows.Media.ImageDrawing>, 或使用繪製。  
  
### <a name="using-the-image-control"></a>使用影像控制項  
 <xref:System.Windows.Controls.Image>是一個架構元素, 以及在應用程式中顯示影像的主要方式。 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中<xref:System.Windows.Controls.Image> , 可以透過兩種方式來使用: 屬性語法或屬性語法。 下列範例顯示如何使用屬性 (Attribute) 語法和屬性 (Property) 標記語法呈現 200 像素寬的影像。 如需屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 許多範例都使用<xref:System.Windows.Media.Imaging.BitmapImage>物件來參考影像檔案。 <xref:System.Windows.Media.Imaging.BitmapImage>是針對載入<xref:System.Windows.Media.Imaging.BitmapSource>優化的特製化[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , 可讓您輕鬆地將<xref:System.Windows.Controls.Image>影像顯示為控制項<xref:System.Windows.Controls.Image.Source%2A>的。  
  
 下列範例示範如何使用程式碼呈現 200 像素寬的影像。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>會執行<xref:System.ComponentModel.ISupportInitialize>介面, 以優化多個屬性的初始化。 只有在物件初始化期間，才會發生屬性變更。 呼叫<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>以表示初始化已開始, 並<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>指出初始化已完成。 初始化之後，所做的屬性變更都會被忽略。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>旋轉、轉換和裁剪影像  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可<xref:System.Windows.Media.Imaging.BitmapImage>讓使用者使用或之類<xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.CroppedBitmap>的其他物件來轉換影像。 <xref:System.Windows.Media.Imaging.FormatConvertedBitmap> 這些影像轉換作業可以縮放或旋轉影像、變更影像的像素格式，或裁剪影像。  
  
 影像旋轉是使用<xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A>的<xref:System.Windows.Media.Imaging.BitmapImage>屬性來執行。 只能以 90 度遞增的角度旋轉。 在下列範例中，影像會旋轉 90 度。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 將影像轉換成不同的像素格式 (例如灰階) 是使用<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>來完成。 在下列範例中, 會將影像轉換成<xref:System.Windows.Media.PixelFormats.Gray4%2A>。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 若要裁剪影像, 可以使用<xref:System.Windows.UIElement.Clip%2A> <xref:System.Windows.Controls.Image>或<xref:System.Windows.Media.Imaging.CroppedBitmap>的屬性。 一般來說, 如果您只想要顯示影像的一部分, <xref:System.Windows.UIElement.Clip%2A>就應該使用。 如果您需要編碼並儲存裁剪的影像, 則<xref:System.Windows.Media.Imaging.CroppedBitmap>應該使用。 在下列範例中, 會使用剪輯屬性來<xref:System.Windows.Media.EllipseGeometry>裁剪影像。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>縮放影像  
 <xref:System.Windows.Controls.Image.Stretch%2A>屬性會控制如何伸展影像以填滿其容器。 屬性會接受<xref:System.Windows.Media.Stretch>列舉所定義的下列值: <xref:System.Windows.Controls.Image.Stretch%2A>  
  
- <xref:System.Windows.Media.Stretch.None>：影像不會伸展以填滿輸出區域。 如果影像大於輸出區域，會將影像繪製到輸出區域，並裁剪超過的部分。  
  
- <xref:System.Windows.Media.Stretch.Fill>：影像會縮放以符合輸出區域。 因為影像的高度和寬度是分開縮放，所以可能不會維持影像的原始外觀比例。 也就是說，影像可能會變形以完全填滿輸出容器。  
  
- <xref:System.Windows.Media.Stretch.Uniform>：影像會進行縮放, 使其完全符合輸出區域的範圍。 會維持影像的外觀比例。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>：影像會進行縮放, 使其完全填滿輸出區域, 同時保留影像的原始外觀比例。  
  
 下列範例會將每個可用<xref:System.Windows.Media.Stretch>的列舉套用<xref:System.Windows.Controls.Image>至。  
  
 下圖顯示範例的輸出, 並示範在套用至影像時, <xref:System.Windows.Controls.Image.Stretch%2A>不同設定的影響。  
  
 ![不同的 TileBrush Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
不同的縮放設定  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>以影像繪製  
 影像也可以在應用程式中顯示, 方法是使用<xref:System.Windows.Media.Brush>繪製。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件。 若要繪製影像, 請使用<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.ImageBrush>是的<xref:System.Windows.Media.TileBrush>類型, 會將其內容定義為點陣圖影像。 會顯示由其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性指定的單一影像。 <xref:System.Windows.Media.ImageBrush> 您可以控制影像縮放、對齊及並排的方式，以防止扭曲並且創造出圖樣和其他效果。 下圖顯示可<xref:System.Windows.Media.ImageBrush>透過來達成的一些效果。  
  
 ![ImageBrush 輸出範例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
影像筆刷可以填滿圖形、控制項、文字等等  
  
 下列範例示範如何使用<xref:System.Windows.Media.ImageBrush>來繪製具有影像之按鈕的背景。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 如需<xref:System.Windows.Media.ImageBrush>和繪製影像的詳細資訊, 請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>影像中繼資料  
 某些影像檔包含描述檔案內容或特性的中繼資料。 例如，大部分數位相機建立的影像，會包含用來擷取影像之相機廠牌與型號的中繼資料。 每種影像格式處理中繼資料的方式也有所不同，但 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 可針對每種支援的影像格式提供統一的中繼資料儲存及擷取方式。  
  
 中繼資料的存取是透過<xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> <xref:System.Windows.Media.Imaging.BitmapSource>物件的屬性來提供。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A><xref:System.Windows.Media.Imaging.BitmapMetadata>傳回物件, 其中包含影像所包含的所有中繼資料。 此資料可能位於單一的中繼資料結構描述，或不同結構描述的組合中。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]支援下列影像中繼資料架構:交換影像檔案 (Exif)、文字 (PNG 文字資料) [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)]、 [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)]、和[!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]。  
  
 為了簡化讀取中繼資料的程式<xref:System.Windows.Media.Imaging.BitmapMetadata> , 提供了數個名為的屬性, 可以輕鬆地存取<xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, 例如、 <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A> <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>和。 許多具名屬性也可以用於寫入中繼資料。 讀取中繼資料的其他支援是由中繼資料查詢讀取器提供。 方法是藉由提供字串查詢 (例如 *"/app1/exif/"* ), 用來抓取中繼資料查詢讀取器。 <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> 在下列範例中, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>是用來取得儲存在 *"/Text/Description"* 位置的文字。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 若要寫入中繼資料，必須使用中繼資料查詢寫入器。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>取得查詢寫入器, 並設定所需的值。 在下列範例中, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>是用來寫入儲存在 *"/Text/Description"* 位置的文字。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>轉碼器擴充性  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 的核心功能是新影像轉碼器的擴充性模型。 這些 Unmanaged 介面可讓轉碼器開發人員整合轉碼器與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，以便 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式可以自動使用新的影像格式。  
  
 如需擴充性 API 的範例, 請參閱[Win32 範例編解碼器](https://go.microsoft.com/fwlink/?LinkID=160052)。 此範例示範如何針對自訂影像格式建立解碼器和編碼器。  
  
> [!NOTE]
>  轉碼器必須經過數位簽署，系統才能辨識它。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 範例轉碼器 (英文)](https://go.microsoft.com/fwlink/?LinkID=160052)
