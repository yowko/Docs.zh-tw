---
title: 如何：對文字套用轉換
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 531537013ab3bbfba278ca63e14155341eefc826
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-transforms-to-text"></a>如何：對文字套用轉換
轉換可以變更應用程式中文字的顯示。 下列範例會使用不同類型的呈現轉換來影響的文字顯示<xref:System.Windows.Controls.TextBlock>控制項。  
  
## <a name="example"></a>範例  
 下列範例示範二維 x-y 平面的指定點所旋轉的文字。  
  
 ![使用 rotatetransform 旋轉的文字](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
旋轉 90 度的文字範例  
  
 下列程式碼範例使用<xref:System.Windows.Media.RotateTransform>旋轉文字。 <xref:System.Windows.Media.RotateTransform.Angle%2A>值 90 旋轉元素順時針旋轉 90 度。  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。  
  
 ![使用 scaletransform 縮放的文字](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
縮放文字範例  
  
 下列程式碼範例使用<xref:System.Windows.Media.ScaleTransform>從其原始大小的小數位數文字。  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  縮放文字與增加文字字型大小不同。 字型大小會彼此獨立計算，以提供不同大小的最佳解析度。 在另一方面，縮放的文字會保留原始大小文字的比例。  
  
 下列範例示範沿著 X 軸傾斜的文字。  
  
 ![使用 skewtransform 傾斜的文字](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
扭曲文字範例  
  
 下列程式碼範例使用<xref:System.Windows.Media.SkewTransform>扭曲文字。 扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。 在此範例中，這兩個文字字串會沿著 X 座標扭曲 -30° 和 30°。  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 下列範例顯示沿著 X 和 Y 軸平移或移動的文字。  
  
 ![位移使用 translatetransform 的文字](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
平移文字範例  
  
 下列程式碼範例使用<xref:System.Windows.Media.TranslateTransform>位移文字。 在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>提供一組豐富的功能提供陰影效果。 如需詳細資訊，請參閱[建立文字陰影](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對文字套用動畫](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
