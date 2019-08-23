---
title: HOW TO：建立含陰影的文字
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960447"
---
# <a name="how-to-create-text-with-a-shadow"></a>作法：建立含陰影的文字
本節中的範例示範如何建立所顯示文字的陰影效果。  
  
## <a name="example"></a>範例  
 物件可讓您建立[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]物件的各種投影效果。 <xref:System.Windows.Media.Effects.DropShadowEffect> 下列範例示範套用至文字的延伸陰影效果。 在此情況下，陰影是柔邊陰影，表示陰影色彩模糊。  
  
 ![具有柔和度&#61; 0.25 的文字陰影](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 您可以藉由設定<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>屬性來控制陰影的寬度。 的值`4.0`表示陰影寬度為4個圖元。 您可以藉由修改<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性來控制陰影的柔和度或模糊。 的`0.0`值表示沒有模糊。 下列程式碼範例示範如何建立柔邊陰影。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> 這些陰影效果不會經過[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文字轉譯管線。 因此，使用這些效果時，會停用 ClearType。  
  
 下列範例示範套用至文字的實色延伸陰影效果。 在此情況下，陰影不會模糊。  
  
 ![以柔和度&#61;為0的文字陰影](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 您可以藉由將<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性設定為來`0.0`建立硬陰影, 這表示不會使用模糊。 您可以藉由修改<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性來控制陰影的方向。 將此屬性的方向值設定為與`0` `360`之間的度數。 下圖顯示<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性設定的方向值。  
  
 ![陰影的 DropShadow 程度設定](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 下列程式碼範例示範如何建立強烈陰影。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>使用模糊效果  
 <xref:System.Windows.Media.Effects.BlurBitmapEffect>可以用來建立可放在文字物件後方的類似陰影效果。 套用至文字的模糊點陣圖效果會讓文字所有方向都平均模糊。  
  
 下列範例示範套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 下列程式碼範例示範如何建立模糊效果。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>使用平移轉換  
 <xref:System.Windows.Media.TranslateTransform>可以用來建立可放在文字物件後方的類似陰影效果。  
  
 下列程式碼範例會使用<xref:System.Windows.Media.TranslateTransform>來位移文字。 在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。  
  
 ![使用 TranslateTransform 的文字陰影](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 下列程式碼範例示範如何建立陰影效果的轉換。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
