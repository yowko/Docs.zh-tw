---
title: 如何：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646516"
---
# <a name="how-to-define-and-reference-a-resource"></a>如何：定義和參考資源

此範例簡報如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中的屬性定義資源並引用它。

## <a name="example"></a>範例

下面的範例定義了兩種類型的資源:一種<xref:System.Windows.Media.SolidColorBrush>資源和<xref:System.Windows.Style>多個資源。 該<xref:System.Windows.Media.SolidColorBrush>資源`MyBrush`用於提供每個屬性的值,每個屬性都採用<xref:System.Windows.Media.Brush>類型值。 資源和<xref:System.Windows.Style>`PageBackground``TitleText`每個目標為特定的控制`Label`項類型。 當資源鍵引用該樣式資源並用於設置<xref:System.Windows.FrameworkElement.Style%2A>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中 定義的多個特定控制項元素的屬性時,樣式在目標控制項上設置各種不同的屬性。

請注意,`Label`樣式的 setter 中的一個屬性也引用`MyBrush`前面定義的 資源。 這是一種常見的技術,但請務必記住,資源按給定順序解析並輸入到資源字典中。 如果使用[靜態資源標記擴展](staticresource-markup-extension.md)從其他資源中引用資源,則字典中找到的順序也會請求資源。 確保引用的任何資源在資源集合中定義的任何資源都早於請求該資源的位置。 如有必要,可以使用[動態資源標記擴展](dynamicresource-markup-extension.md)在運行時引用資源,從而繞過資源引用的嚴格創建順序,但您應該知道此動態資源技術具有性能後果。 有關詳細資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>另請參閱

- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
