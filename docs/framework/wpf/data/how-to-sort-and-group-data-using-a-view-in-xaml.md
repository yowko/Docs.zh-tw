---
title: 如何：使用 XAML 排序和分組資料
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460122"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>如何：使用 XAML 排序和分組資料
這個範例示範如何在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中建立資料集合的視圖。 Views 允許群組、排序、篩選和目前專案的概念等功能。  
  
## <a name="example"></a>範例  
 在下列範例中，名為「*位置*」的靜態資源會定義為「*位置*」物件的集合，其中每個「*位置*」物件都是由「城市」名稱和「州」（city）組成。 前置詞*src*會對應至定義資料來源*位置*所在的命名空間。 首碼*scm*會對應到 `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` 和*dat*對應以 `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`。  
  
 下列範例會建立依城市名稱排序並依州/省分組之資料集合的視圖。  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 然後，此視圖可以是系結來源，如下列範例所示：  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 若為系結至 <xref:System.Windows.Data.XmlDataProvider> 資源中定義的 XML 資料，請在 XML 名稱前面加上 @ 符號。  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.CollectionViewSource>
- [取得資料集合的預設檢視](how-to-get-the-default-view-of-a-data-collection.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
