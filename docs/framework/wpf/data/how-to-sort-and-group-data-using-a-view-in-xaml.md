---
title: HOW TO：使用 XAML 中的檢視排序和分組資料
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
ms.openlocfilehash: ca4439b574264ebebfda745f0765f750099bc95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144517"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>HOW TO：使用 XAML 中的檢視排序和分組資料
此範例示範如何建立資料集合中的檢視[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 檢視允許的分組、 排序、 篩選、 功能和目前的項目的概念。  
  
## <a name="example"></a>範例  
 在下列範例中，靜態資源的名稱*放置*做為集合定義*位置*物件，其中每一個*位置*物件組成的縣 （市） 名稱，狀態。 前置詞*src*對應至命名空間位置的資料來源*上的芳鄰*定義。 前置詞*scm*對應至`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`並*dat*對應至`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`。  
  
 下列範例會建立依城市名稱排序和依狀態分組的資料集合的檢視。  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 檢視即可繫結來源，如下列範例所示：  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 XML 資料中定義的繫結<xref:System.Windows.Data.XmlDataProvider>資源，與 XML 名稱前面加上 @ 符號。  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.CollectionViewSource>
- [取得資料集合的預設檢視](how-to-get-the-default-view-of-a-data-collection.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
