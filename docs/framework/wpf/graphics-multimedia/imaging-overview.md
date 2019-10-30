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
ms.openlocfilehash: 7c0168d5ca8b1d3bda709f934e454b2603d37b71
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039873"
---
# <a name="imaging-overview"></a>影像處理概觀
本主題提供 Microsoft Windows Presentation Foundation 映射元件的簡介。 WPF 影像處理可讓開發人員顯示、轉換和格式化影像。  

## <a name="wpf-imaging-component"></a>WPF 影像處理元件  
 WPF 映射提供 Microsoft Windows 內映射功能的大幅增強功能。 影像處理功能（例如顯示點陣圖或在通用控制項上使用影像）先前依賴 Microsoft Windows 圖形裝置介面（GDI）或 Microsoft Windows GDI + 程式庫。 這些 API 提供基準影像處理功能，但缺少支援編解碼器擴充性和高精確度影像支援等功能。 WPF 影像處理的設計是要克服 GDI 和 GDI + 的缺點，並提供一組新的 API，在您的應用程式內顯示及使用影像。  
  
 有兩種方式可存取 WPF 影像處理 API （受控元件和非受控元件）。 Unmanaged 元件提供下列功能。  
  
- 新的或專屬影像格式的擴充性模型。  
  
- 改善原生映射格式的效能和安全性，包括點陣圖（BMP）、聯合 Photographics 專家群組（JPEG）、可移植網狀圖形（PNG）、標記的影像檔案格式（TIFF）、Microsoft Windows Media 相片、圖形交換格式（GIF）、和圖示（.ico）。  
  
- 高位元深度影像資料最多可保留每色頻 8 位元 (每像素 32 位元)。  
  
- 非破壞性的影像縮放、裁剪及旋轉。  
  
- 簡化的色彩管理。  
  
- 支援檔案內、專屬中繼資料。  
  
- Managed 元件會利用 Unmanaged 基礎結構來提供影像與其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 功能 (例如 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、動畫和圖形) 的緊密整合。 Managed 元件也受益于 Windows Presentation Foundation （WPF）影像處理編解碼器擴充性模型，可讓您在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中自動識別新的影像格式。  
  
 大部分的 managed WPF 影像處理 API 都位於 <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> 命名空間中，不過有幾個重要的類型（例如 <xref:System.Windows.Media.ImageBrush> 和 <xref:System.Windows.Media.ImageDrawing> 位於 <xref:System.Windows.Media?displayProperty=nameWithType> 命名空間中，而 <xref:System.Windows.Controls.Image> 位於 <xref:System.Windows.Controls?displayProperty=nameWithType> 命名空間中。  
  
 本主題提供 Managed 元件的詳細資訊。 如需非受控 API 的詳細資訊，請參閱[非受控 WPF 影像處理元件](/windows/desktop/wic/-wic-lh)檔。  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF 影像格式  

 轉碼器可以用來將特定媒體格式解碼或編碼。 WPF 影像處理包含 BMP、JPEG、PNG、TIFF、Windows Media 相片、GIF 和圖示影像格式的編解碼器。 每個轉碼器都可以讓應用程式解碼和編碼各自的影像格式 (但 ICON 在編碼部分是例外)。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> 是用於解碼和編碼影像的重要類別。 這是 WPF 影像處理管線的基本建立區塊，代表特定大小和解析度的一組固定圖元。 <xref:System.Windows.Media.Imaging.BitmapSource> 可以是多個框架影像的個別框架，也可以是在 <xref:System.Windows.Media.Imaging.BitmapSource>上執行之轉換的結果。 這是許多主要類別的父系，用於 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 影像處理，例如 <xref:System.Windows.Media.Imaging.BitmapFrame>。  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame> 可用來儲存影像格式的實際點陣圖資料。 許多影像格式僅支援單一 <xref:System.Windows.Media.Imaging.BitmapFrame>，雖然 GIF 和 TIFF 之類的格式支援每個影像有多個畫面格。 畫面格會由解碼器作為輸入資料並傳遞至編碼器以建立影像檔。  
  
 下列範例示範如何從 <xref:System.Windows.Media.Imaging.BitmapSource> 建立 <xref:System.Windows.Media.Imaging.BitmapFrame>，然後新增至 TIFF 影像。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>影像格式解碼  
 影像解碼是指將影像格式變成系統可用之影像資料的轉譯作業。 接著可使用影像資料來顯示、處理，或編碼成不同格式。 選取的解碼器是根據影像格式而定。 除非指定特定的解碼器，否則會自動選取轉碼器。 [在 WPF 中顯示影像](#_displayingimages)一節中的範例示範自動解碼。 使用未受管理的 WPF 映射介面開發並向系統註冊的自訂格式解碼器，會自動參與解碼器選取專案。 這可讓自訂格式自動在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中顯示。  
  
 下列範例示範如何使用點陣圖解碼器來解碼 BMP 格式影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>影像格式編碼  
 影像編碼是指將影像資料變成特定影像格式的轉換作業。 接著可使用已編碼的影像資料建立新的影像檔。 WPF 影像處理會針對上述的每個影像格式提供編碼器。  
  
 下列範例示範使用編碼器儲存新建立的點陣圖影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>在 WPF 中顯示影像  
 有數種方式可以在 Windows Presentation Foundation （WPF）應用程式中顯示影像。 影像可以使用 <xref:System.Windows.Controls.Image> 控制項來顯示、使用 <xref:System.Windows.Media.ImageBrush>繪製在視覺效果上，或是使用 <xref:System.Windows.Media.ImageDrawing>繪製。  
  
### <a name="using-the-image-control"></a>使用影像控制項  
 <xref:System.Windows.Controls.Image> 是一個架構元素，以及在應用程式中顯示影像的主要方式。 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，可以透過兩種方式來使用 <xref:System.Windows.Controls.Image>：屬性語法或屬性語法。 下列範例顯示如何使用屬性 (Attribute) 語法和屬性 (Property) 標記語法呈現 200 像素寬的影像。 如需屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 許多範例都使用 <xref:System.Windows.Media.Imaging.BitmapImage> 物件來參考影像檔案。 <xref:System.Windows.Media.Imaging.BitmapImage> 是專為 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 載入而優化的特製化 <xref:System.Windows.Media.Imaging.BitmapSource>，這是將影像顯示為 <xref:System.Windows.Controls.Image> 控制項 <xref:System.Windows.Controls.Image.Source%2A> 的簡單方式。  
  
 下列範例示範如何使用程式碼呈現 200 像素寬的影像。  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage> 會執行 <xref:System.ComponentModel.ISupportInitialize> 介面，以優化多個屬性的初始化。 只有在物件初始化期間，才會發生屬性變更。 呼叫 <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> 以通知初始化已開始，並 <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> 以表示初始化已完成。 初始化之後，所做的屬性變更都會被忽略。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>旋轉、轉換和裁剪影像  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓使用者使用 <xref:System.Windows.Media.Imaging.BitmapImage> 的屬性，或使用 <xref:System.Windows.Media.Imaging.CroppedBitmap> 或 <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>之類的其他 <xref:System.Windows.Media.Imaging.BitmapSource> 物件來轉換影像。 這些影像轉換作業可以縮放或旋轉影像、變更影像的像素格式，或裁剪影像。  
  
 影像旋轉是使用 <xref:System.Windows.Media.Imaging.BitmapImage>的 <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> 屬性來執行。 只能以 90 度遞增的角度旋轉。 在下列範例中，影像會旋轉 90 度。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 將影像轉換成不同的像素格式（例如灰階）會使用 <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>來完成。 在下列範例中，會將影像轉換成 <xref:System.Windows.Media.PixelFormats.Gray4%2A>。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 若要裁剪影像，可以使用 <xref:System.Windows.Controls.Image> 或 <xref:System.Windows.Media.Imaging.CroppedBitmap> 的 <xref:System.Windows.UIElement.Clip%2A> 屬性。 一般來說，如果您只想要顯示影像的一部分，就應該使用 <xref:System.Windows.UIElement.Clip%2A>。 如果您需要編碼並儲存裁剪的影像，就應該使用 <xref:System.Windows.Media.Imaging.CroppedBitmap>。 在下列範例中，會使用 <xref:System.Windows.Media.EllipseGeometry>的剪輯屬性來裁剪影像。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>縮放影像  
 [<xref:System.Windows.Controls.Image.Stretch%2A>] 屬性會控制如何延展影像以填滿其容器。 <xref:System.Windows.Controls.Image.Stretch%2A> 屬性會接受由 <xref:System.Windows.Media.Stretch> 列舉所定義的下列值：  
  
- <xref:System.Windows.Media.Stretch.None>：影像不會伸展以填滿輸出區域。 如果影像大於輸出區域，會將影像繪製到輸出區域，並裁剪超過的部分。  
  
- <xref:System.Windows.Media.Stretch.Fill>：影像會縮放以符合輸出區域。 因為影像的高度和寬度是分開縮放，所以可能不會維持影像的原始外觀比例。 也就是說，影像可能會變形以完全填滿輸出容器。  
  
- <xref:System.Windows.Media.Stretch.Uniform>：影像會進行縮放，使其完全符合輸出區域的範圍。 會維持影像的外觀比例。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>：縮放影像，使其完全填滿輸出區域，同時保留影像的原始外觀比例。  
  
 下列範例會將每個可用的 <xref:System.Windows.Media.Stretch> 列舉套用至 <xref:System.Windows.Controls.Image>。  
  
 下圖顯示範例的輸出，並示範套用至影像時，不同 <xref:System.Windows.Controls.Image.Stretch%2A> 設定的影響。  
  
 ![不同的 TileBrush 縮放設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
不同的縮放設定  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>以影像繪製  
 您也可以使用 <xref:System.Windows.Media.Brush>繪製，以在應用程式中顯示影像。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件。 若要繪製影像，請使用 <xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.ImageBrush> 是將其內容定義為點陣圖影像的 <xref:System.Windows.Media.TileBrush> 類型。 <xref:System.Windows.Media.ImageBrush> 會顯示由其 <xref:System.Windows.Media.ImageBrush.ImageSource%2A> 屬性指定的單一影像。 您可以控制影像縮放、對齊及並排的方式，以防止扭曲並且創造出圖樣和其他效果。 下圖顯示 <xref:System.Windows.Media.ImageBrush>可以達到的一些效果。  
  
 ![ImageBrush 輸出範例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
影像筆刷可以填滿圖形、控制項、文字等等  
  
 下列範例示範如何使用 <xref:System.Windows.Media.ImageBrush>，以影像繪製按鈕的背景。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 如需 <xref:System.Windows.Media.ImageBrush> 和繪製影像的詳細資訊[，請參閱使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>影像中繼資料  
 某些影像檔包含描述檔案內容或特性的中繼資料。 例如，大部分數位相機建立的影像，會包含用來擷取影像之相機廠牌與型號的中繼資料。 每一種影像格式會以不同的方式處理中繼資料，但 WPF 映射會提供統一的方式來儲存和抓取每個支援影像格式的中繼資料。  
  
 中繼資料的存取是透過 <xref:System.Windows.Media.Imaging.BitmapSource> 物件的 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 屬性來提供。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 會傳回 <xref:System.Windows.Media.Imaging.BitmapMetadata> 物件，其中包含影像所包含的所有中繼資料。 此資料可能位於單一的中繼資料結構描述，或不同結構描述的組合中。 WPF 影像處理支援下列影像中繼資料架構：交換影像檔案（Exif）、文字（PNG 文字資料）、影像檔案目錄（IFD）、國際按電信委員會（IPTC）和 [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]。  
  
 為了簡化讀取中繼資料的程式，<xref:System.Windows.Media.Imaging.BitmapMetadata> 提供了數個可輕易存取的命名屬性，例如 <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>、<xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>和 <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>。 許多具名屬性也可以用於寫入中繼資料。 讀取中繼資料的其他支援是由中繼資料查詢讀取器提供。 <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> 方法是藉由提供字串查詢（例如 *"/app1/exif/"* ），用來抓取中繼資料查詢讀取器。 在下列範例中，會使用 <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> 來取得儲存在 *"/Text/Description"* 位置的文字。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 若要寫入中繼資料，必須使用中繼資料查詢寫入器。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> 取得查詢寫入器，並設定所需的值。 在下列範例中，會使用 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> 來寫入儲存在 *"/Text/Description"* 位置的文字。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>轉碼器擴充性  
 WPF 影像處理的核心功能是新影像編解碼器的擴充性模型。 這些 Unmanaged 介面可讓轉碼器開發人員整合轉碼器與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，以便 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式可以自動使用新的影像格式。  
  
 如需擴充性 API 的範例，請參閱[Win32 範例編解碼器](https://go.microsoft.com/fwlink/?LinkID=160052)。 此範例示範如何針對自訂影像格式建立解碼器和編碼器。  
  
> [!NOTE]
> 轉碼器必須經過數位簽署，系統才能辨識它。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 範例轉碼器 (英文)](https://go.microsoft.com/fwlink/?LinkID=160052)
