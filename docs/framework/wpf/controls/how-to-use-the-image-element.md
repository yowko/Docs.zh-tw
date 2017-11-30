---
title: "操作說明：使用 Image 元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75177c8aae8964ebdc50ae94b2f3a6372991e2c6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="307d7-102">操作說明：使用 Image 元素</span><span class="sxs-lookup"><span data-stu-id="307d7-102">How to: Use the Image Element</span></span>
<span data-ttu-id="307d7-103">這個範例示範如何使用應用程式中包含影像<xref:System.Windows.Controls.Image>項目。</span><span class="sxs-lookup"><span data-stu-id="307d7-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="307d7-104">範例</span><span class="sxs-lookup"><span data-stu-id="307d7-104">Example</span></span>  
 <span data-ttu-id="307d7-105">下列範例示範如何轉譯寬度為 200 像素的影像。</span><span class="sxs-lookup"><span data-stu-id="307d7-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="307d7-106">在這個 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例中，同時使用了屬性語法和屬性標記語法來定義影像。</span><span class="sxs-lookup"><span data-stu-id="307d7-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="307d7-107">如需屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="307d7-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="307d7-108">A<xref:System.Windows.Media.Imaging.BitmapImage>用來定義影像的來源資料，而且已明確定義屬性標記的語法範例。</span><span class="sxs-lookup"><span data-stu-id="307d7-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="307d7-109">此外，<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>的<xref:System.Windows.Media.Imaging.BitmapImage>設為相同的寬度為<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Controls.Image>。</span><span class="sxs-lookup"><span data-stu-id="307d7-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="307d7-110">這麼做是為了確保僅使用最少量的記憶體來轉譯影像。</span><span class="sxs-lookup"><span data-stu-id="307d7-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="307d7-111">一般情況下，如果您想要指定呈現影像的大小，只指定<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>但非兩者。</span><span class="sxs-lookup"><span data-stu-id="307d7-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="307d7-112">如果您只指定其中一項，便可維持影像的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="307d7-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="307d7-113">否則，影像可能會意外地自動縮放或變形。</span><span class="sxs-lookup"><span data-stu-id="307d7-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="307d7-114">若要控制影像的縮放行為，請使用<xref:System.Windows.Controls.Image.Stretch%2A>和<xref:System.Windows.Controls.Image.StretchDirection%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="307d7-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="307d7-115">當您指定的映像大小為<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>，您也應該設定 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>或<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A>以相同的個別大小。</span><span class="sxs-lookup"><span data-stu-id="307d7-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="307d7-116"><xref:System.Windows.Controls.Image.Stretch%2A>屬性會決定影像來源如何自動縮放以填滿影像項目。</span><span class="sxs-lookup"><span data-stu-id="307d7-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="307d7-117">如需詳細資訊，請參閱 <xref:System.Windows.Media.Stretch> 列舉。</span><span class="sxs-lookup"><span data-stu-id="307d7-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="307d7-118">範例</span><span class="sxs-lookup"><span data-stu-id="307d7-118">Example</span></span>  
 <span data-ttu-id="307d7-119">下列範例示範如何使用程式碼呈現 200 像素寬的影像。</span><span class="sxs-lookup"><span data-stu-id="307d7-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="307d7-120">設定<xref:System.Windows.Media.Imaging.BitmapImage>屬性必須完成內<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>和<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>區塊。</span><span class="sxs-lookup"><span data-stu-id="307d7-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="307d7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="307d7-121">See Also</span></span>  
 [<span data-ttu-id="307d7-122">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="307d7-122">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
