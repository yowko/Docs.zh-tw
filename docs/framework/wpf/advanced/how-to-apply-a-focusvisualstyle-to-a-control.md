---
title: HOW TO：對控制項套用 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: c4b379d3c57b6d0ae29952c23a35d7cc2cdf7f96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366591"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>HOW TO：對控制項套用 FocusVisualStyle
此範例將示範如何在資源建立焦點視覺化樣式，並套用樣式至控制項，使用<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。  
  
## <a name="example"></a>範例  
 下列範例會定義建立複合僅適用於該控制項鍵盤的焦點時的其他控制項的樣式[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 這可以藉由定義的樣式<xref:System.Windows.Controls.ControlTemplate>，然後設定時，該樣式參考做為資源<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。  
  
 類似於框線外部矩形被位於外部的矩形區域。 調整大小樣式的修改，除非使用<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>套用焦點視覺化樣式的位置的矩形控制項。 此範例會設定為負數值<xref:System.Windows.FrameworkElement.Margin%2A>使稍微顯示取得焦點的控制項外框線。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>會附加至任何隨附的控制項範本樣式從明確樣式或佈景主題樣式控制項的主要樣式可以仍會建立使用<xref:System.Windows.Controls.ControlTemplate>並將該樣式設定為<xref:System.Windows.FrameworkElement.Style%2A>屬性。  
  
 焦點視覺化樣式應該一致地使用佈景主題或 UI，而不是使用每個可設定焦點的項目，另一種。 如需詳細資訊，請參閱 <<c0> [ 控制項和 FocusVisualStyle 中焦點的樣式](styling-for-focus-in-controls-and-focusvisualstyle.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [樣式設定和範本化](../controls/styling-and-templating.md)
- [設定控制項中焦點的樣式和 FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
