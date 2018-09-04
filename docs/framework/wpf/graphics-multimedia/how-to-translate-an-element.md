---
title: 操作說明：平移元素
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 04e1e8288bcccc4a310f05abff01fbdf160cdb11
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505904"
---
# <a name="how-to-translate-an-element"></a>操作說明：平移元素
此範例示範如何平移 （移動） 項目使用<xref:System.Windows.Media.TranslateTransform>。  
  
 <xref:System.Windows.Media.TranslateTransform>類別是特別適用於不支援絕對位置的面板內移動元素。 例如，藉由套用<xref:System.Windows.Media.TranslateTransform>要<xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性，您可以移動中的項目<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>。  
  
 使用<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>來指定，單位為像素元素沿著 x 軸移動。 使用<xref:System.Windows.Media.TranslateTransform.Y%2A>屬性來指定，單位為像素元素沿著 y 軸移動。 最後，套用<xref:System.Windows.Media.TranslateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>項目的屬性。  
  
 下列範例會使用<xref:System.Windows.Media.TranslateTransform>向下移元素 50 像素為右到 50 個像素。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
