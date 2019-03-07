---
title: HOW TO：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 80be1460906100072e6263c967c213df7968c705
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492058"
---
# <a name="how-to-define-and-reference-a-resource"></a>HOW TO：定義和參考資源

此範例示範如何定義資源，並在使用中的屬性中參考此[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。

## <a name="example"></a>範例

下列範例會定義兩種資源類型：<xref:System.Windows.Media.SolidColorBrush>資源，以及數個<xref:System.Windows.Style>資源。 <xref:System.Windows.Media.SolidColorBrush> Resource`MyBrush`用來提供數個屬性的值，每個需要<xref:System.Windows.Media.Brush>輸入值。 <xref:System.Windows.Style>資源`PageBackground`，`TitleText`和`Label`每個目標的特定控制項類型。 樣式各種不同的屬性上設定的目標控制項，當該樣式資源資源索引鍵所參考，並將用來設定<xref:System.Windows.FrameworkElement.Style%2A>屬性中定義的數個特定的控制項項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。

Setter 內屬性的其中一個筆記`Label`樣式也會參考`MyBrush`稍早定義的資源。 這是常用的技巧，但請務必記住，資源會被剖析，並輸入的資源字典中的順序，就會提供。 如果您使用，字典中找到的順序也要求資源[StaticResource 標記延伸](staticresource-markup-extension.md)參考從另一個資源內。 請確定您參考的任何資源稍早定義於其中然後要求該資源的資源集合內。 如果有必要，您可以解決的資源參考的嚴格的建立順序使用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)相反地，參考在執行階段的資源，但您應該要注意，此 DynamicResource技術會影響效能。 如需詳細資訊，請參閱 < [XAML 資源](xaml-resources.md)。

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>另請參閱

- [XAML 資源](xaml-resources.md)
- [樣式設定和範本化](../controls/styling-and-templating.md)
