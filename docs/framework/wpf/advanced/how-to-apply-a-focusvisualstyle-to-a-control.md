---
title: 如何：對控制項套用 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459815"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>如何：對控制項套用 FocusVisualStyle
這個範例會示範如何使用 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性，在資源中建立焦點視覺化樣式，並將樣式套用至控制項。  
  
## <a name="example"></a>範例  
 下列範例定義的樣式會建立額外的控制群組合，只有在該控制項是 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]的鍵盤焦點時才適用。 這是藉由定義具有 <xref:System.Windows.Controls.ControlTemplate>的樣式來完成，然後在設定 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性時將該樣式參考為資源。  
  
 類似框線的外部矩形會放在矩形區域之外。 除非另有修改，否則樣式的大小會使用套用焦點視覺化樣式之矩形控制項的 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 和 <xref:System.Windows.FrameworkElement.ActualWidth%2A>。 這個範例會設定 <xref:System.Windows.FrameworkElement.Margin%2A> 的負值，讓框線在焦點的控制項之外稍微出現。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 會加到任何來自明確樣式或主題樣式的控制項範本樣式;控制項的主要樣式仍然可以使用 <xref:System.Windows.Controls.ControlTemplate> 來建立，並將該樣式設定為 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。  
  
 焦點視覺化樣式應在主題或 UI 中一致地使用，而不是針對每個可設定焦點的元素使用不同的視覺效果樣式。 如需詳細資訊，請參閱將[焦點放在控制項中的樣式，以及 FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [設定控制項中焦點的樣式和 FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
