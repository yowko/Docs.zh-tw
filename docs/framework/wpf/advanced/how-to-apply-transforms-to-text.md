---
title: HOW TO：對文字套用轉換
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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956476"
---
# <a name="how-to-apply-transforms-to-text"></a>作法：對文字套用轉換
轉換可以變更應用程式中文字的顯示。 下列範例會使用不同類型的轉譯轉換來影響<xref:System.Windows.Controls.TextBlock>控制項中的文字顯示。  
  
## <a name="example"></a>範例  
 下列範例示範二維 x-y 平面的指定點所旋轉的文字。  
  
 ![使用 RotateTransform 旋轉的文字](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 下列程式碼範例會使用<xref:System.Windows.Media.RotateTransform>來旋轉文字。 90 <xref:System.Windows.Media.RotateTransform.Angle%2A>的值會順時針旋轉元素90度。  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。  
  
 ![使用 ScaleTransform 縮放的文字](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 下列程式碼範例會使用<xref:System.Windows.Media.ScaleTransform>來根據原始大小調整文字。  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> 縮放文字與增加文字字型大小不同。 字型大小會彼此獨立計算，以提供不同大小的最佳解析度。 在另一方面，縮放的文字會保留原始大小文字的比例。  
  
 下列範例示範沿著 X 軸傾斜的文字。  
  
 ![使用 SkewTransform 傾斜的文字](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 下列程式碼範例會使用<xref:System.Windows.Media.SkewTransform>來扭曲文字。 扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。 在此範例中，這兩個文字字串會沿著 X 座標扭曲 -30° 和 30°。  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 下列範例顯示沿著 X 和 Y 軸平移或移動的文字。  
  
 ![使用 TranslateTransform 的文字位移](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 下列程式碼範例會使用<xref:System.Windows.Media.TranslateTransform>來位移文字。 在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>提供了一組豐富的功能, 可用來提供陰影效果。 如需詳細資訊, 請參閱[使用陰影建立文字](how-to-create-text-with-a-shadow.md)。  
  
## <a name="see-also"></a>另請參閱

- [對文字套用動畫](how-to-apply-animations-to-text.md)
