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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186687"
---
# <a name="imaging-overview"></a>影像處理概觀
本主題介紹了 Microsoft Windows 演示文稿基礎映射元件。 WPF 成像使開發人員能夠顯示、轉換和格式化圖像。  

## <a name="wpf-imaging-component"></a>WPF 影像處理元件  
 WPF 映射在 Microsoft Windows 中提供了映射功能的重大增強。 映射功能（如顯示點陣圖或使用公共控制項上的圖像）以前依賴于 Microsoft Windows 圖形裝置介面 （GDI） 或 Microsoft Windows GDI+ 庫。 這些 API 提供基線映射功能，但缺少支援編解碼器擴充性和高保真圖像支援等功能。 WPF 成像旨在克服 GDI 和 GDI+ 的缺點，並提供一組新的 API 來在應用程式中顯示和使用圖像。  
  
 有兩種方法可以訪問 WPF 映射 API、託管元件和非託管元件。 Unmanaged 元件提供下列功能。  
  
- 新的或專屬影像格式的擴充性模型。  
  
- 改進了本機圖像格式的性能和安全性，包括點陣圖 （BMP）、聯合攝影專家組 （JPEG）、可擕式網狀圖形 （PNG）、標記的圖像檔案格式 （TIFF）、微軟 Windows 媒體照片、圖形交換格式 （GIF）、和圖示 （.ico）。  
  
- 高位元深度影像資料最多可保留每色頻 8 位元 (每像素 32 位元)。  
  
- 非破壞性的影像縮放、裁剪及旋轉。  
  
- 簡化的色彩管理。  
  
- 支援檔案內、專屬中繼資料。  
  
- 託管元件利用非託管基礎結構提供圖像與其他 WPF 功能（如 、動畫和圖形）[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]的無縫集成。 託管元件還受益于 Windows 演示基礎 （WPF） 成像編解碼器擴展模型，該模型允許在 WPF 應用程式中自動識別新的映射格式。  
  
 大多數託管的 WPF 映射 API 都駐<xref:System.Windows.Media.Imaging?displayProperty=nameWithType>留在命名空間中，但有幾個重要類型，<xref:System.Windows.Media.ImageBrush>如<xref:System.Windows.Media.ImageDrawing>並駐留在<xref:System.Windows.Media?displayProperty=nameWithType>命名空間中<xref:System.Windows.Controls.Image>並駐留在<xref:System.Windows.Controls?displayProperty=nameWithType>命名空間中。  
  
 本主題提供 Managed 元件的詳細資訊。 有關非託管 API 的詳細資訊，請參閱[非託管 WPF 映射元件](/windows/desktop/wic/-wic-lh)文檔。  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>WPF 影像格式  

 轉碼器可以用來將特定媒體格式解碼或編碼。 WPF 成像包括用於 BMP、JPEG、PNG、TIFF、Windows 媒體照片、GIF 和 ICON 圖像格式的編解碼器。 每個轉碼器都可以讓應用程式解碼和編碼各自的影像格式 (但 ICON 在編碼部分是例外)。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>是圖像解碼和編碼中的重要類。 它是 WPF 成像管道的基本構建基塊，表示一組具有特定大小和解析度的圖元。 可以是<xref:System.Windows.Media.Imaging.BitmapSource>多個幀圖像的單個幀，也可以是 對 執行轉換的結果<xref:System.Windows.Media.Imaging.BitmapSource>。 它是 WPF 映射中使用的許多主類的父類，例如<xref:System.Windows.Media.Imaging.BitmapFrame>。  
  
 A<xref:System.Windows.Media.Imaging.BitmapFrame>用於存儲圖像格式的實際點陣圖資料。 許多圖像格式僅支援單個<xref:System.Windows.Media.Imaging.BitmapFrame>，儘管 GIF 和 TIFF 等格式支援每個圖像的多個幀。 畫面格會由解碼器作為輸入資料並傳遞至編碼器以建立影像檔。  
  
 下面的示例演示如何<xref:System.Windows.Media.Imaging.BitmapFrame>從 創建<xref:System.Windows.Media.Imaging.BitmapSource>，然後添加到 TIFF 映射。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>影像格式解碼  
 影像解碼是指將影像格式變成系統可用之影像資料的轉譯作業。 接著可使用影像資料來顯示、處理，或編碼成不同格式。 選取的解碼器是根據影像格式而定。 除非指定特定的解碼器，否則會自動選取轉碼器。 [在 WPF 中顯示影像](#_displayingimages)一節中的範例示範自動解碼。 使用非託管 WPF 映射介面開發的自訂格式解碼器，並在系統中註冊，可自動參與解碼器選擇。 這允許自訂格式自動顯示在 WPF 應用程式中。  
  
 下面的示例演示了使用點陣圖解碼器解碼 BMP 格式圖像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>影像格式編碼  
 影像編碼是指將影像資料變成特定影像格式的轉換作業。 接著可使用已編碼的影像資料建立新的影像檔。 WPF 成像為上述每種圖像格式提供編碼器。  
  
 下列範例示範使用編碼器儲存新建立的點陣圖影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>在 WPF 中顯示影像  
 有幾種方法可以在 Windows 演示文稿基礎 （WPF） 應用程式中顯示圖像。 圖像可以使用<xref:System.Windows.Controls.Image>控制項顯示，使用 在視覺物件上繪製<xref:System.Windows.Media.ImageBrush>，或使用 進行繪製。 <xref:System.Windows.Media.ImageDrawing>  
  
### <a name="using-the-image-control"></a>使用影像控制項  
 <xref:System.Windows.Controls.Image>是框架元素和在應用程式中顯示圖像的主要方式。 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<xref:System.Windows.Controls.Image>中，可通過兩種方式使用;屬性語法或屬性語法。 下列範例顯示如何使用屬性 (Attribute) 語法和屬性 (Property) 標記語法呈現 200 像素寬的影像。 如需有關屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 許多示例使用<xref:System.Windows.Media.Imaging.BitmapImage>物件來引用影像檔。 <xref:System.Windows.Media.Imaging.BitmapImage>是專為載入<xref:System.Windows.Media.Imaging.BitmapSource>而[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]優化<xref:System.Windows.Controls.Image.Source%2A>的專用函數，是作為<xref:System.Windows.Controls.Image>控制項顯示圖像的簡便方法。  
  
 下列範例示範如何使用程式碼來轉譯寬度為 200 像素的影像。  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>實現介面<xref:System.ComponentModel.ISupportInitialize>以優化多個屬性的初始化。 只有在物件初始化期間，才會發生屬性變更。 調用<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>以發出初始化已經開始的信號，並<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>發出初始化已完成的信號。 初始化之後，所做的屬性變更都會被忽略。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>旋轉、轉換和裁剪影像  
 WPF 使使用者能夠<xref:System.Windows.Media.Imaging.BitmapImage>通過使用 屬性或使用 其他<xref:System.Windows.Media.Imaging.BitmapSource>物件（如<xref:System.Windows.Media.Imaging.CroppedBitmap>或<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>） 轉換圖像。 這些影像轉換作業可以縮放或旋轉影像、變更影像的像素格式，或裁剪影像。  
  
 使用<xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A>的屬性執行圖像旋轉<xref:System.Windows.Media.Imaging.BitmapImage>。 只能以 90 度遞增的角度旋轉。 在下列範例中，影像會旋轉 90 度。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 使用 將圖像轉換為其他像素格式（如灰度）後，將使用<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>。 在以下示例中，圖像將轉換為<xref:System.Windows.Media.PixelFormats.Gray4%2A>。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 要裁剪圖像，<xref:System.Windows.UIElement.Clip%2A>可以使用 或<xref:System.Windows.Controls.Image><xref:System.Windows.Media.Imaging.CroppedBitmap>可以使用 屬性。 通常，如果您只想顯示圖像的一部分，<xref:System.Windows.UIElement.Clip%2A>則應使用。 如果需要對裁剪的圖像進行編碼和保存，則應使用 。 <xref:System.Windows.Media.Imaging.CroppedBitmap> 在下面的示例中，使用 Clip 屬性使用<xref:System.Windows.Media.EllipseGeometry>裁剪圖像。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>縮放影像  
 屬性<xref:System.Windows.Controls.Image.Stretch%2A>控制圖像拉伸以填充其容器的方式。 屬性<xref:System.Windows.Controls.Image.Stretch%2A>接受以下值，由<xref:System.Windows.Media.Stretch>枚舉定義：  
  
- <xref:System.Windows.Media.Stretch.None>： 圖像不會拉伸以填充輸出區域。 如果影像大於輸出區域，會將影像繪製到輸出區域，並裁剪超過的部分。  
  
- <xref:System.Windows.Media.Stretch.Fill>： 縮放圖像以適合輸出區域。 因為影像的高度和寬度是分開縮放，所以可能不會維持影像的原始外觀比例。 也就是說，影像可能會變形以完全填滿輸出容器。  
  
- <xref:System.Windows.Media.Stretch.Uniform>： 縮放圖像，使其完全適合輸出區域。 會維持影像的外觀比例。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>： 縮放圖像，使其完全填充輸出區域，同時保持圖像的原始縱橫比。  
  
 下面的示例將每個可用的<xref:System.Windows.Media.Stretch>枚舉應用於 。 <xref:System.Windows.Controls.Image>  
  
 下圖顯示了示例中的輸出，並演示了應用於圖像時的不同<xref:System.Windows.Controls.Image.Stretch%2A>設置的影響。  
  
 ![不同的 TileBrush Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
不同的縮放設定  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>以影像繪製  
 圖像也可以通過使用 進行繪製顯示在應用程式中<xref:System.Windows.Media.Brush>。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件。 要使用圖像進行繪製，請使用<xref:System.Windows.Media.ImageBrush>。 是<xref:System.Windows.Media.ImageBrush>將其內容定義為<xref:System.Windows.Media.TileBrush>點陣圖圖像的類型。 顯示<xref:System.Windows.Media.ImageBrush>由其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性指定的單個圖像。 您可以控制影像縮放、對齊及並排的方式，以防止扭曲並且創造出圖樣和其他效果。 下圖顯示了可以使用 可以實現的一<xref:System.Windows.Media.ImageBrush>些效果。  
  
 ![ImageBrush 輸出範例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
影像筆刷可以填滿圖形、控制項、文字等等  
  
 下面的示例演示如何使用 圖像繪製按鈕的背景<xref:System.Windows.Media.ImageBrush>。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 有關<xref:System.Windows.Media.ImageBrush>圖像和繪製圖像的其他資訊，請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>影像中繼資料  
 某些影像檔包含描述檔案內容或特性的中繼資料。 例如，大部分數位相機建立的影像，會包含用來擷取影像之相機廠牌與型號的中繼資料。 每個圖像格式處理中繼資料的方式不同，但 WPF 映射提供了存儲和檢索每個受支援圖像格式的中繼資料的統一方法。  
  
 中繼資料的訪問通過<xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A><xref:System.Windows.Media.Imaging.BitmapSource>物件的屬性提供。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>返回包含<xref:System.Windows.Media.Imaging.BitmapMetadata>圖像包含的所有中繼資料的物件。 此資料可能位於單一的中繼資料結構描述，或不同結構描述的組合中。 WPF 成像支援以下圖像中繼資料架構：可交換影像檔 （Exif）、tEXt （PNG 文本資料）、影像檔目錄 （IFD）、國際新聞電信理事會 （IPTC） 和可擴展中繼資料平臺 （XMP）。  
  
 為了簡化<xref:System.Windows.Media.Imaging.BitmapMetadata>讀取中繼資料的過程，提供了幾個可以輕鬆訪問的命名屬性，如<xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>和<xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>。 <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A> 許多具名屬性也可以用於寫入中繼資料。 讀取中繼資料的其他支援是由中繼資料查詢讀取器提供。 該方法<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>用於通過提供字串查詢（如 *"/app1/exif/"）* 來檢索中繼資料查詢讀取器。 在下面的示例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>用於獲取存儲在 *"/文本/描述"* 位置的文本。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 若要寫入中繼資料，必須使用中繼資料查詢寫入器。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>獲取查詢編寫器並設置所需的值。 在下面的示例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>用於寫入存儲在 *"/文本/描述"* 位置的文本。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>轉碼器擴充性  
 WPF成像的核心特徵是新圖像編解碼器的可擴充性模型。 這些非託管介面使編解碼器開發人員能夠將編解碼器與 WPF 集成，以便 WPF 應用程式可以自動使用新的映射格式。  
  
 有關擴充性 API 的示例，請參閱[Win32 示例編解碼器](https://go.microsoft.com/fwlink/?LinkID=160052)。 此範例示範如何針對自訂影像格式建立解碼器和編碼器。  
  
> [!NOTE]
> 轉碼器必須經過數位簽署，系統才能辨識它。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 範例轉碼器 (英文)](https://go.microsoft.com/fwlink/?LinkID=160052)
