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
ms.openlocfilehash: 45214b5f0e6827c36f87a4d45592ff0989c9a877
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890806"
---
# <a name="imaging-overview"></a>影像處理概觀
本主題提供 [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)] 的簡介。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 可讓開發人員顯示、 轉換和格式化映像。  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>WPF 影像處理元件  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 提供顯著的增強功能，在映像中的功能[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]。 之前的影像處理功能 (例如顯示點陣圖或在通用控制項上使用影像) 要依賴 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 或 [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] 程式庫運作。 這些 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 提供基本影像處理功能，但是缺少一些功能，例如支援轉碼器擴充性和高畫質影像支援。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 若要克服的缺點設計[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]並[!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]，並提供一組新的[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]顯示，並使用您的應用程式的映像。  
  
 有兩種方式可以存取 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]，Managed 元件和 Unmanaged 元件。 Unmanaged 元件提供下列功能。  
  
-   新的或專屬影像格式的擴充性模型。  
  
-   [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)]、[!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]、[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]、[!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]、[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]、[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] 和圖示 (.ico) 等原生影像格式的改善效能及安全性。  
  
-   高位元深度影像資料最多可保留每色頻 8 位元 (每像素 32 位元)。  
  
-   非破壞性的影像縮放、裁剪及旋轉。  
  
-   簡化的色彩管理。  
  
-   支援檔案內、專屬中繼資料。  
  
-   Managed 元件會利用 Unmanaged 基礎結構來提供影像與其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 功能 (例如 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、動畫和圖形) 的緊密整合。 受管理的元件也受益於 Windows Presentation Foundation (WPF) 影像轉碼器擴充性模型可讓新映像中的格式自動辨識[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式。  
  
 大部分的 managed [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]位於<xref:System.Windows.Media.Imaging?displayProperty=nameWithType>命名空間，不過幾個重要型別，例如<xref:System.Windows.Media.ImageBrush>並<xref:System.Windows.Media.ImageDrawing>位於<xref:System.Windows.Media?displayProperty=nameWithType>命名空間和<xref:System.Windows.Controls.Image>位於<xref:System.Windows.Controls?displayProperty=nameWithType>命名空間。  
  
 本主題提供 Managed 元件的詳細資訊。 如需 Unmanaged [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 的詳細資訊，請參閱 [Unmanaged WPF 影像處理元件 (英文)](/windows/desktop/wic/-wic-lh) 文件。  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF 影像格式  
 轉碼器可以用來將特定媒體格式解碼或編碼。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 包含的轉碼器[!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]， [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]， [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]， [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]， [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]， [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]，和 ICON 影像格式。 每個轉碼器都可以讓應用程式解碼和編碼各自的影像格式 (但 ICON 在編碼部分是例外)。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> 重要的類別用於解碼和編碼的映像。 它是 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 管線的基本建置組塊，代表在特定大小和解析度下的單一固定像素集。 A<xref:System.Windows.Media.Imaging.BitmapSource>可以是多重框架影像中，個別畫面格，或可以執行轉換的結果<xref:System.Windows.Media.Imaging.BitmapSource>。 它是父項中使用的主要類別的許多[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]這類映像<xref:System.Windows.Media.Imaging.BitmapFrame>。  
  
 A<xref:System.Windows.Media.Imaging.BitmapFrame>用來儲存影像格式的實際點陣圖資料。 許多影像格式只支援單一<xref:System.Windows.Media.Imaging.BitmapFrame>，不過這類格式[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]和[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]支援每個影像的多個框架。 畫面格會由解碼器作為輸入資料並傳遞至編碼器以建立影像檔。  
  
 下列範例示範如何<xref:System.Windows.Media.Imaging.BitmapFrame>從建立<xref:System.Windows.Media.Imaging.BitmapSource>再加入[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]映像。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>影像格式解碼  
 影像解碼是指將影像格式變成系統可用之影像資料的轉譯作業。 接著可使用影像資料來顯示、處理，或編碼成不同格式。 選取的解碼器是根據影像格式而定。 除非指定特定的解碼器，否則會自動選取轉碼器。 [在 WPF 中顯示影像](#_displayingimages)一節中的範例示範自動解碼。 使用 Unmanaged [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 介面開發並向系統註冊的自訂格式解碼器，會自動參與解碼器選取作業。 這可讓自訂格式自動在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中顯示。  
  
 下列範例示範使用點陣圖解碼器將 [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 格式影像解碼。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>影像格式編碼  
 影像編碼是指將影像資料變成特定影像格式的轉換作業。 接著可使用已編碼的影像資料建立新的影像檔。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 針對每個上述的影像格式提供編碼器。  
  
 下列範例示範使用編碼器儲存新建立的點陣圖影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>在 WPF 中顯示影像  
 有數種方式可在 Windows Presentation Foundation (WPF) 應用程式中顯示影像。 可以使用顯示映像<xref:System.Windows.Controls.Image>控制項中，使用 visual 繪製<xref:System.Windows.Media.ImageBrush>，或使用繪製<xref:System.Windows.Media.ImageDrawing>。  
  
### <a name="using-the-image-control"></a>使用影像控制項  
 <xref:System.Windows.Controls.Image> 是架構元素，而且在應用程式中顯示影像的主要方式。 在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，<xref:System.Windows.Controls.Image>可以用於兩種方式; 屬性語法或屬性的語法。 下列範例顯示如何使用屬性 (Attribute) 語法和屬性 (Property) 標記語法呈現 200 像素寬的影像。 如需屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 許多範例都使用<xref:System.Windows.Media.Imaging.BitmapImage>物件以參考的映像檔。 <xref:System.Windows.Media.Imaging.BitmapImage> 是特製化<xref:System.Windows.Media.Imaging.BitmapSource>，最適合用於[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]載入，並輕鬆地顯示為影像<xref:System.Windows.Controls.Image.Source%2A>的<xref:System.Windows.Controls.Image>控制項。  
  
 下列範例示範如何使用程式碼呈現 200 像素寬的影像。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> 實作<xref:System.ComponentModel.ISupportInitialize>介面以最佳化多個屬性的初始化。 只有在物件初始化期間，才會發生屬性變更。 呼叫<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>發出信號表示初始化已經開始和<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>發出信號表示初始化已完成。 初始化之後，所做的屬性變更都會被忽略。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>旋轉、轉換和裁剪影像  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓使用者使用的屬性轉換映像<xref:System.Windows.Media.Imaging.BitmapImage>或使用其他<xref:System.Windows.Media.Imaging.BitmapSource>物件，例如<xref:System.Windows.Media.Imaging.CroppedBitmap>或<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>。 這些影像轉換作業可以縮放或旋轉影像、變更影像的像素格式，或裁剪影像。  
  
 使用執行影像旋轉<xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A>屬性<xref:System.Windows.Media.Imaging.BitmapImage>。 只能以 90 度遞增的角度旋轉。 在下列範例中，影像會旋轉 90 度。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 將影像轉換成不同的像素格式，例如灰階使用<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>。 在下列範例中，影像會轉換成<xref:System.Windows.Media.PixelFormats.Gray4%2A>。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 若要裁剪影像，或是<xref:System.Windows.UIElement.Clip%2A>的屬性<xref:System.Windows.Controls.Image>或<xref:System.Windows.Media.Imaging.CroppedBitmap>可用。 一般而言，如果您只想要顯示的影像，一部分<xref:System.Windows.UIElement.Clip%2A>應該使用。 如果您需要編碼並儲存裁剪的影像，<xref:System.Windows.Media.Imaging.CroppedBitmap>應該使用。 在下列範例中，映像會裁剪剪輯屬性使用<xref:System.Windows.Media.EllipseGeometry>。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>縮放影像  
 <xref:System.Windows.Controls.Image.Stretch%2A>屬性可讓您控制影像如何縮放以填滿容器。 <xref:System.Windows.Controls.Image.Stretch%2A>屬性可以接受下列值所定義<xref:System.Windows.Media.Stretch>列舉型別：  
  
-   <xref:System.Windows.Media.Stretch.None>:映像不會自動縮放以填滿輸出區域。 如果影像大於輸出區域，會將影像繪製到輸出區域，並裁剪超過的部分。  
  
-   <xref:System.Windows.Media.Stretch.Fill>:影像會縮放以符合輸出區域。 因為影像的高度和寬度是分開縮放，所以可能不會維持影像的原始外觀比例。 也就是說，影像可能會變形以完全填滿輸出容器。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>:影像會縮放，以完全符合輸出區域。 會維持影像的外觀比例。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>:影像會縮放，使它完全填滿輸出區域，同時維持影像的原始外觀比例。  
  
 下列範例適用於每個可用<xref:System.Windows.Media.Stretch>列舉型別的<xref:System.Windows.Controls.Image>。  
  
 下圖顯示範例的輸出，並且示範不同的影響<xref:System.Windows.Controls.Image.Stretch%2A>設定具有時套用至映像。  
  
 ![不同的 TileBrush Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
不同的縮放設定  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>以影像繪製  
 映像也可以顯示應用程式中使用的繪製<xref:System.Windows.Media.Brush>。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件。 若要以影像繪製，使用<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.ImageBrush>是一種<xref:System.Windows.Media.TileBrush>，定義其內容以點陣圖影像。 <xref:System.Windows.Media.ImageBrush>會顯示單一的映像，以指定其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性。 您可以控制影像縮放、對齊及並排的方式，以防止扭曲並且創造出圖樣和其他效果。 下圖顯示一些可達到的效果<xref:System.Windows.Media.ImageBrush>。  
  
 ![ImageBrush 輸出範例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
影像筆刷可以填滿圖形、控制項、文字等等  
  
 下列範例示範如何繪製背景影像使用的按鈕之<xref:System.Windows.Media.ImageBrush>。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 如需詳細資訊<xref:System.Windows.Media.ImageBrush>繪製影像看[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>影像中繼資料  
 某些影像檔包含描述檔案內容或特性的中繼資料。 例如，大部分數位相機建立的影像，會包含用來擷取影像之相機廠牌與型號的中繼資料。 每種影像格式處理中繼資料的方式也有所不同，但 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 可針對每種支援的影像格式提供統一的中繼資料儲存及擷取方式。  
  
 中繼資料的存取透過提供<xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>屬性<xref:System.Windows.Media.Imaging.BitmapSource>物件。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 傳回<xref:System.Windows.Media.Imaging.BitmapMetadata>物件，其中包含映像所包含的所有中繼資料。 此資料可能位於單一的中繼資料結構描述，或不同結構描述的組合中。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 支援下列影像中繼資料結構描述： [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)]，tEXt （PNG 文字型的資料）， [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)]， [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)]，和[!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]。  
  
 為了簡化讀取中繼資料的程序<xref:System.Windows.Media.Imaging.BitmapMetadata>提供數個具名的屬性可輕鬆地存取這類<xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>， <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>，和<xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>。 許多具名屬性也可以用於寫入中繼資料。 讀取中繼資料的其他支援是由中繼資料查詢讀取器提供。 <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>方法來擷取中繼資料查詢讀取器所提供的字串查詢，例如 *"/ app1/exif /"*。 在下列範例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>用來取得文字儲存於 *"/text/description"* 位置。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 若要寫入中繼資料，必須使用中繼資料查詢寫入器。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> 取得查詢寫入者，並設定所需的值。 在下列範例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>用來寫入儲存在文字 *"/text/description"* 位置。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>轉碼器擴充性  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 的核心功能是新影像轉碼器的擴充性模型。 這些 Unmanaged 介面可讓轉碼器開發人員整合轉碼器與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，以便 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式可以自動使用新的影像格式。  
  
 如需擴充性 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 的範例，請參閱 [Win32 範例轉碼器 (英文)](https://go.microsoft.com/fwlink/?LinkID=160052)。 此範例示範如何針對自訂影像格式建立解碼器和編碼器。  
  
> [!NOTE]
>  轉碼器必須經過數位簽署，系統才能辨識它。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D 圖形和影像](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 範例轉碼器](https://go.microsoft.com/fwlink/?LinkID=160052)
