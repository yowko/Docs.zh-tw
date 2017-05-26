---
title: "影像處理概觀 | Microsoft Docs"
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
  - "轉換影像"
  - "裁剪影像"
  - "解碼影像格式"
  - "顯示影像"
  - "編碼影像格式"
  - "影像格式解碼"
  - "影像格式編碼"
  - "影像中繼資料"
  - "影像, 關於影像處理"
  - "影像處理 API"
  - "中繼資料, 影像"
  - "以影像繪製"
  - "旋轉影像"
  - "自動縮放影像"
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# 影像處理概觀
本主題提供 [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)] 的簡介。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]讓開發人員可以顯示、轉換及格式化影像。  
  
   
  
<a name="_wpfImaging"></a>   
## WPF 影像處理元件  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]提供 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 內重要的影像處理增強功能。  之前的影像處理功能 \(例如顯示點陣圖或在通用控制項上使用影像\) 要依賴 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 或 [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] 程式庫運作。  這些 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 提供基準的影像處理功能，但是缺少一些功能，例如支援轉碼器擴充性和高精確度影像支援。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]的設計在於克服 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 和 [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] 的缺點，並提供一組新的 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 以在應用程式內顯示及使用影像。  
  
 有兩種方法可以存取 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]，也就是 Managed 元件和 Unmanaged 元件。  Unmanaged 元件會提供下列功能。  
  
-   新的或專屬影像格式的擴充性模型。  
  
-   [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)]、[!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]、[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]、[!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]、[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]、[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] 及圖示 \(.ico\) 等原生影像格式的改善效能及安全性。  
  
-   高位元深度影像資料最多可保留每色頻 8 位元 \(每一像素 32 位元\)。  
  
-   非解構性的影像縮放、裁剪及旋轉。  
  
-   簡化的色彩管理。  
  
-   支援檔案中、專屬中繼資料 \(Metadata\)。  
  
-   Managed 元件會利用 Unmanaged 基礎結構提供影像與其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 功能 \(例如[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、動畫及圖形\) 的緊密整合。  Managed 元件還受益於 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 影像處理轉碼器擴充性模型，該模型會自動辨識 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中的新影像格式。  
  
 大多數 Managed [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 都位於 <xref:System.Windows.Media.Imaging?displayProperty=fullName> 命名空間，不過有幾項重要型別例外，例如 <xref:System.Windows.Media.ImageBrush> 和 <xref:System.Windows.Media.ImageDrawing> 位於 <xref:System.Windows.Media?displayProperty=fullName> 命名空間，而 <xref:System.Windows.Controls.Image> 位於 <xref:System.Windows.Controls?displayProperty=fullName> 命名空間。  
  
 本主題提供 Managed 元件的詳細資訊。  如需 Unmanaged [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 的詳細資訊，請參閱 [Unmanaged WPF 影像處理元件](_wic_lh)文件。  
  
<a name="_imageformats"></a>   
## WPF 影像格式  
 轉碼器可用來解碼或編碼特定媒體格式。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]包含 [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]、[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]、[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]、[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]、[!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] 及 ICON 影像格式的轉碼器。  每個轉碼器都可以讓應用程式解碼和編碼各自的影像格式 \(但 ICON 在編碼部分是例外\)。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> 是重要的類別，用在影像的解碼和編碼。  它是 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]管線的基本建置組塊，代表在特定大小和解析度下的單一固定像素集。  <xref:System.Windows.Media.Imaging.BitmapSource> 可以是多畫面格影像中的個別畫面格，或者是對 <xref:System.Windows.Media.Imaging.BitmapSource> 執行轉換的結果。  它是許多 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 影像處理 \(例如 <xref:System.Windows.Media.Imaging.BitmapFrame>\) 中使用之主要類別的父代 \(Parent\)。  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame> 可以用來儲存影像格式的實際點陣圖資料。  許多影像格式只支援單一 <xref:System.Windows.Media.Imaging.BitmapFrame>，而例如 [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] 和 [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] 的格式則支援每個影像有多畫面格。  畫面格會由解碼器做為輸入資料並傳送至編碼器以建立影像檔。  
  
 下列範例示範 <xref:System.Windows.Media.Imaging.BitmapFrame> 如何從 <xref:System.Windows.Media.Imaging.BitmapSource> 建立，然後加入至 [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] 影像。  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### 影像格式解碼  
 影像解碼是指將影像格式變成系統可用之影像資料的轉譯作業。  然後就可以使用影像資料來顯示、處理或編碼為不同格式。  選擇的解碼器視影像格式而定。  除非指定特定的解碼器，否則轉碼器選擇作業是自動的。  [在 WPF 中顯示影像](#_displayingimages)一節中的範例會示範自動解碼。  使用 Unmanaged [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]介面開發的以及自動向系統註冊的自訂格式解碼器，會參與解碼器選擇作業。  這可以讓自訂格式自動在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中顯示。  
  
 下列範例示範使用點陣圖解碼器將 [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 格式影像解碼。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### 影像格式編碼  
 影像編碼是指將影像資料變成特定影像格式的轉譯作業。  然後就可以使用編碼的影像資料建立新的影像檔。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]會為上述每一種影像格式提供編碼器。  
  
 下列範例示範使用編碼器儲存新建立的點陣圖影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## 在 WPF 中顯示影像  
 有幾種方法可以在 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式中顯示影像。  顯示影像的方法有使用 <xref:System.Windows.Controls.Image> 控制項顯示影像，使用 <xref:System.Windows.Media.ImageBrush> 在視覺物件上繪製影像，或使用 <xref:System.Windows.Media.ImageDrawing> 繪製影像。  
  
### 使用影像控制項  
 <xref:System.Windows.Controls.Image> 是一項架構項目，也是在應用程式中顯示影像的主要方法。  在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，有兩種方法可以使用 <xref:System.Windows.Controls.Image>，也就是屬性 \(Attribute\) 語法和屬性 \(Property\) 語法。  下列範例顯示如何使用屬性 \(Attribute\) 語法和屬性 \(Property\) 標記語法呈現 200 像素寬的影像。  如需屬性 \(Attribute\) 語法和屬性 \(Property\) 語法的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 其中許多範例是使用 <xref:System.Windows.Media.Imaging.BitmapImage> 物件參考影像檔。  <xref:System.Windows.Media.Imaging.BitmapImage> 是一種特製的 <xref:System.Windows.Media.Imaging.BitmapSource>，已針對載入[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 最佳化，並且是將影像顯示為 <xref:System.Windows.Controls.Image> 控制項的 <xref:System.Windows.Controls.Image.Source%2A> 的一個簡單方法。  
  
 下列範例顯示如何使用程式碼呈現 200 像素寬的影像。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> 會實作 <xref:System.ComponentModel.ISupportInitialize> 介面以最佳化多個屬性的初始化作業。  屬性變更只會在物件初始化期間發生。  呼叫 <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> 表示初始化已經開始，呼叫 <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> 則表示初始化已經完成。  初始化之後所做的屬性變更會被忽略。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### 旋轉、轉換及裁剪影像  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 讓使用者可以透過下列兩種方式轉換影像：使用 <xref:System.Windows.Media.Imaging.BitmapImage> 的屬性，以及使用其他 <xref:System.Windows.Media.Imaging.BitmapSource> 物件，例如 <xref:System.Windows.Media.Imaging.CroppedBitmap> 或 <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>。  這些影像轉換作業可以縮放或旋轉影像、變更影像的像素格式，或裁剪影像。  
  
 影像旋轉作業是使用 <xref:System.Windows.Media.Imaging.BitmapImage> 的 <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> 屬性執行。  只能以 90 度遞增的角度旋轉。  在下列範例中，影像會旋轉 90 度。  
  
 [!code-xml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 將影像轉換為不同的像素格式，例如使用 <xref:System.Windows.Media.Imaging.FormatConvertedBitmap> 轉換成灰階。  在下列範例中，影像會轉換為 <xref:System.Windows.Media.PixelFormats.Gray4%2A>。  
  
 [!code-xml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 若要裁剪影像，可以使用 <xref:System.Windows.Controls.Image> 或 <xref:System.Windows.Media.Imaging.CroppedBitmap> 的 <xref:System.Windows.UIElement.Clip%2A> 屬性。  通常，如果您只要顯示影像的某一部分，應該使用 <xref:System.Windows.UIElement.Clip%2A>。  如果您需要編碼並且儲存裁剪的影像，應該使用 <xref:System.Windows.Media.Imaging.CroppedBitmap>。  在下列範例中，會使用 Clip 屬性 \(利用 <xref:System.Windows.Media.EllipseGeometry>\) 裁剪影像。  
  
 [!code-xml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### 自動縮放影像  
 <xref:System.Windows.Controls.Image.Stretch%2A> 屬性控制影像如何自動縮放以填滿容器。  <xref:System.Windows.Controls.Image.Stretch%2A> 屬性接受下列值 \(由 <xref:System.Windows.Media.Stretch> 列舉型別定義\)：  
  
-   <xref:System.Windows.Media.Stretch>：影像不會自動縮放以填滿輸出區域。  如果影像大於輸出區域，會將影像繪製至輸出區域，並裁剪超過的部分。  
  
-   <xref:System.Windows.Media.Stretch>：影像會隨縮放以符合輸出區域的大小。  因為影像的高度和寬度是分開縮放的，所以可能不會保留影像的原始外觀比例 \(Aspect Ratio\)。  也就是說，影像可能會扭曲以完全填滿輸出容器。  
  
-   <xref:System.Windows.Media.Stretch>：影像會縮放以完全符合輸出區域的大小。  會保留影像的外觀比例。  
  
-   <xref:System.Windows.Media.Stretch>：影像會縮放以完全填滿輸出區域，並同時保留影像的原始外觀比例。  
  
 下列範例會將每個可用的 <xref:System.Windows.Media.Stretch> 列舉型別套用至 <xref:System.Windows.Controls.Image>。  
  
 下圖顯示這個範例的輸出，並且示範不同 <xref:System.Windows.Controls.Image.Stretch%2A> 設定套用至影像時的影響。  
  
 ![不同的 TileBrush Stretch 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.png "img\_mmgraphics\_stretchenum")  
不同自動縮放設定  
  
 [!code-xml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### 以影像繪製  
 影像也可以藉由以 <xref:System.Windows.Media.Brush> 在應用程式中繪製來顯示。  筆刷可以讓您以任何項目 \(從簡單、單純的色彩到複雜的圖樣和影像集\) 繪製 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件。  若要以影像繪製，請使用 <xref:System.Windows.Media.ImageBrush>。  <xref:System.Windows.Media.ImageBrush> 是一種 <xref:System.Windows.Media.TileBrush>，可將其內容定義為點陣圖影像。  <xref:System.Windows.Media.ImageBrush> 會顯示以其 <xref:System.Windows.Media.ImageBrush.ImageSource%2A> 屬性所指定的單一影像。  您可以控制影像自動縮放、對齊及並排的方式，以防止扭曲並且創造出圖樣和其他效果。  下圖顯示可以使用 <xref:System.Windows.Media.ImageBrush> 達成的部分效果。  
  
 ![ImageBrush 輸出範例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.png "wcpsdk\_mmgraphics\_imagebrushexamples")  
影像筆刷可以填滿圖案、控制項、文字等等  
  
 下列範例示範如何使用 <xref:System.Windows.Media.ImageBrush> 以影像繪製按鈕背景。  
  
 [!code-xml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 如需 <xref:System.Windows.Media.ImageBrush> 和繪製影像的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="_metadata"></a>   
## 影像中繼資料  
 有些影像檔包含中繼資料 來描述檔案的內容或特性。  例如，大多數數位相機建立的影像中會包含關於捕捉影像時所使用的相機品牌和型號的中繼資料。  雖然每個影像格式處理中繼資料的方式各有不同，但是 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]可以替所有支援的影像格式提供統一的中繼資料儲存及擷取方法。  
  
 中繼資料的存取是透過 <xref:System.Windows.Media.Imaging.BitmapSource> 物件的 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 屬性提供。  <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 會傳回 <xref:System.Windows.Media.Imaging.BitmapMetadata> 物件，其中包括影像內含的所有中繼資料。  這項資料可能位於單一中繼資料結構描述或不同結構描述的組合中。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]支援下列影像中繼資料結構描述：[!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)]、tEXt \(PNG 文字資料\)、[!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)]、[!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)] 和 [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]。  
  
 為了簡化讀取中繼資料的程序，<xref:System.Windows.Media.Imaging.BitmapMetadata> 提供數個可以輕易存取的具名屬性，例如 <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>、<xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A> 和 <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>。  許多具名屬性可以用於寫入中繼資料。  讀取中繼資料的其他支援是由中繼資料查詢讀取器提供。  <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> 方法可以擷取中繼資料查詢讀取器，方法是提供 *"\/app1\/exif\/"* 之類的字串查詢。  在下列範例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> 可以取得儲存在 *"\/Text\/Description"* 位置中的文字。  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 若要撰寫中繼資料，可使用中繼資料查詢寫入器。  <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> 會取得查詢寫入器並設定需要的值。  在下列範例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> 可以寫入儲存在 *"\/Text\/Description"* 位置中的文字。  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## 轉碼器擴充性  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]的核心功能是新影像轉碼器的擴充性模型。  這些 Unmanaged 介面可以讓轉碼器開發人員整合轉碼器與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，使得 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式可以自動使用新的影像格式。  
  
 如需擴充性 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 的範例，請參閱 [Win32 範例轉碼器](http://go.microsoft.com/fwlink/?LinkID=160052) \(英文\)。  這個範例示範如何針對自訂影像格式建立解碼器和編碼器。  
  
> [!NOTE]
>  轉碼器必須有數位簽章，系統才能加以辨識。  
  
## 請參閱  
 <xref:System.Windows.Media.Imaging.BitmapSource>   
 <xref:System.Windows.Media.Imaging.BitmapImage>   
 <xref:System.Windows.Controls.Image>   
 <xref:System.Windows.Media.Imaging.BitmapMetadata>   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Win32 範例轉碼器](http://go.microsoft.com/fwlink/?LinkID=160052)