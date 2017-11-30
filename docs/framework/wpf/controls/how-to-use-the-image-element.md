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
# <a name="how-to-use-the-image-element"></a>操作說明：使用 Image 元素
這個範例示範如何使用應用程式中包含影像<xref:System.Windows.Controls.Image>項目。  
  
## <a name="example"></a>範例  
 下列範例示範如何轉譯寬度為 200 像素的影像。 在這個 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例中，同時使用了屬性語法和屬性標記語法來定義影像。 如需屬性 (Attribute) 語法和屬性 (Property) 語法的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。 A<xref:System.Windows.Media.Imaging.BitmapImage>用來定義影像的來源資料，而且已明確定義屬性標記的語法範例。 此外，<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>的<xref:System.Windows.Media.Imaging.BitmapImage>設為相同的寬度為<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Controls.Image>。 這麼做是為了確保僅使用最少量的記憶體來轉譯影像。  
  
> [!NOTE]
>  一般情況下，如果您想要指定呈現影像的大小，只指定<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>但非兩者。 如果您只指定其中一項，便可維持影像的外觀比例。 否則，影像可能會意外地自動縮放或變形。 若要控制影像的縮放行為，請使用<xref:System.Windows.Controls.Image.Stretch%2A>和<xref:System.Windows.Controls.Image.StretchDirection%2A>屬性。  
  
> [!NOTE]
>  當您指定的映像大小為<xref:System.Windows.FrameworkElement.Width%2A>或<xref:System.Windows.FrameworkElement.Height%2A>，您也應該設定 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>或<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A>以相同的個別大小。  
  
 <xref:System.Windows.Controls.Image.Stretch%2A>屬性會決定影像來源如何自動縮放以填滿影像項目。 如需詳細資訊，請參閱 <xref:System.Windows.Media.Stretch> 列舉。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用程式碼呈現 200 像素寬的影像。  
  
> [!NOTE]
>  設定<xref:System.Windows.Media.Imaging.BitmapImage>屬性必須完成內<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>和<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>區塊。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>另請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
