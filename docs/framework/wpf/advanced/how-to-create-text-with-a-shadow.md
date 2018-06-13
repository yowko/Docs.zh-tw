---
title: 如何：建立含陰影的文字
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 1b7740284afcda6eab41fb68be3b4a2f032cc77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544754"
---
# <a name="how-to-create-text-with-a-shadow"></a>如何：建立含陰影的文字
本節中的範例示範如何建立所顯示文字的陰影效果。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Effects.DropShadowEffect>物件可讓您建立各種下拉式陰影效果[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]物件。 下列範例示範套用至文字的延伸陰影效果。 在此情況下，陰影是柔邊陰影，表示陰影色彩模糊。  
  
 ![文字陰影濃淡&#61;0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
含柔邊陰影的文字範例  
  
 您可以設定來控制陰影寬度<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>屬性。 值為`4.0`表示陰影寬度 4 像素。 您可以控制柔和度，或藉由修改陰影模糊<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性。 值為`0.0`表示沒有模糊。 下列程式碼範例示範如何建立柔邊陰影。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  這些陰影效果不會通過[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文字轉譯管線。 因此，使用這些效果時，會停用 ClearType。  
  
 下列範例示範套用至文字的實色延伸陰影效果。 在此情況下，陰影不會模糊。  
  
 ![文字陰影濃淡&#61;0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")  
含強烈陰影的文字範例  
  
 您可以設定來建立硬陰影<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性`0.0`，這表示使用沒有模糊。 您可以藉由修改控制陰影方向<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性。 這個屬性的方向的值設定到某個程度之間`0`和`360`。 下圖顯示的方向值<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性設定。  
  
 ![陰影的 DropShadow 程度設定](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
DropShadow 方向圖  
  
 下列程式碼範例示範如何建立強烈陰影。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>使用模糊效果  
 A<xref:System.Windows.Media.Effects.BlurBitmapEffect>可用來建立類似陰影的效果，可放置文字物件後面。 套用至文字的模糊點陣圖效果會讓文字所有方向都平均模糊。  
  
 下列範例示範套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
含模糊效果的文字範例  
  
 下列程式碼範例示範如何建立模糊效果。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>使用平移轉換  
 A<xref:System.Windows.Media.TranslateTransform>可用來建立類似陰影的效果，可放置文字物件後面。  
  
 下列程式碼範例使用<xref:System.Windows.Media.TranslateTransform>位移文字。 在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。  
  
 ![使用 translatetransform 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")  
使用陰影效果轉換的文字範例  
  
 下列程式碼範例示範如何建立陰影效果的轉換。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
