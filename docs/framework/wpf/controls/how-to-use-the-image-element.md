---
title: HOW TO：使用 Image 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958318"
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="95e76-102">作法：使用 Image 元素</span><span class="sxs-lookup"><span data-stu-id="95e76-102">How to: Use the Image Element</span></span>
<span data-ttu-id="95e76-103">這個範例示範如何使用<xref:System.Windows.Controls.Image>專案, 在應用程式中包含影像。</span><span class="sxs-lookup"><span data-stu-id="95e76-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95e76-104">範例</span><span class="sxs-lookup"><span data-stu-id="95e76-104">Example</span></span>  
 <span data-ttu-id="95e76-105">下列範例示範如何轉譯寬度為 200 像素的影像。</span><span class="sxs-lookup"><span data-stu-id="95e76-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="95e76-106">在這個 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例中，同時使用了屬性語法和屬性標記語法來定義影像。</span><span class="sxs-lookup"><span data-stu-id="95e76-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="95e76-107">如需屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="95e76-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="95e76-108"><xref:System.Windows.Media.Imaging.BitmapImage>是用來定義影像的來源資料, 並已針對屬性標記語法範例明確定義。</span><span class="sxs-lookup"><span data-stu-id="95e76-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="95e76-109">此外, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.Controls.Image>的會設定為與的相同寬度<xref:System.Windows.FrameworkElement.Width%2A>。 <xref:System.Windows.Media.Imaging.BitmapImage></span><span class="sxs-lookup"><span data-stu-id="95e76-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="95e76-110">這麼做是為了確保僅使用最少量的記憶體來轉譯影像。</span><span class="sxs-lookup"><span data-stu-id="95e76-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95e76-111">一般來說, 如果您想要指定轉譯影像的大小, 請只<xref:System.Windows.FrameworkElement.Width%2A>指定<xref:System.Windows.FrameworkElement.Height%2A>或, 而非兩者。</span><span class="sxs-lookup"><span data-stu-id="95e76-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="95e76-112">如果您只指定其中一項，便可維持影像的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="95e76-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="95e76-113">否則，影像可能會意外地自動縮放或變形。</span><span class="sxs-lookup"><span data-stu-id="95e76-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="95e76-114">若要控制影像的延展行為, 請使用<xref:System.Windows.Controls.Image.Stretch%2A>和<xref:System.Windows.Controls.Image.StretchDirection%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="95e76-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95e76-115">當您使用<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>來指定影像的大小時, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>您也應該將或<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A>設為相同的個別大小。</span><span class="sxs-lookup"><span data-stu-id="95e76-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="95e76-116"><xref:System.Windows.Controls.Image.Stretch%2A>屬性會決定如何延展影像來源, 以填滿影像元素。</span><span class="sxs-lookup"><span data-stu-id="95e76-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="95e76-117">如需詳細資訊，請參閱 <xref:System.Windows.Media.Stretch> 列舉。</span><span class="sxs-lookup"><span data-stu-id="95e76-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="95e76-118">範例</span><span class="sxs-lookup"><span data-stu-id="95e76-118">Example</span></span>  
 <span data-ttu-id="95e76-119">下列範例示範如何使用程式碼呈現 200 像素寬的影像。</span><span class="sxs-lookup"><span data-stu-id="95e76-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95e76-120">設定<xref:System.Windows.Media.Imaging.BitmapImage>屬性必須<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>在和<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>區塊中完成。</span><span class="sxs-lookup"><span data-stu-id="95e76-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="95e76-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e76-121">See also</span></span>

- [<span data-ttu-id="95e76-122">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="95e76-122">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
