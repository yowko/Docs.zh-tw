---
title: 如何：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460169"
---
# <a name="how-to-define-and-reference-a-resource"></a>如何：定義和參考資源

這個範例示範如何使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中的屬性，定義資源並加以參考。

## <a name="example"></a>範例

下列範例會定義兩種資源類型： <xref:System.Windows.Media.SolidColorBrush> 資源和數個 <xref:System.Windows.Style> 資源。 <xref:System.Windows.Media.SolidColorBrush> 資源 `MyBrush` 是用來提供數個屬性的值，每個都採用 <xref:System.Windows.Media.Brush> 的類型值。 <xref:System.Windows.Style> 資源 `PageBackground`、`TitleText` 和 `Label` 各以特定控制項類型為目標。 樣式會在目標控制項上設定各種不同的屬性，而資源索引鍵會參考該樣式資源，並且用來設定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中定義之數個特定控制項專案的 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。

請注意，`Label` 樣式的 setter 中，其中一個屬性也會參考先前定義的 `MyBrush` 資源。 這是常見的技巧，但請務必記住，資源會依照其指定的順序，進行剖析和輸入至資源字典。 如果您使用[StaticResource 標記延伸](staticresource-markup-extension.md)從另一個資源中參考，則也會依字典中找到的順序要求資源。 請確定您參考的任何資源都是在資源集合中稍早定義，而不是要求該資源的位置。 如有需要，您可以使用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)，改為在執行時間參考資源，以解決資源參考的嚴格建立順序，但請注意，此 DynamicResource 技術具有效能後果. 如需詳細資訊，請參閱[XAML 資源](xaml-resources.md)。

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>請參閱

- [XAML 資源](xaml-resources.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
