---
title: 作法：讓資料可於 XAML 中繫結
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401488"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>作法：讓資料可於 XAML 中繫結
本主題討論您可以根據應用程式的需求, 在中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]將資料提供給系結的各種方式。  
  
## <a name="example"></a>範例  
 如果您有想要[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]系結的 common language runtime (CLR) 物件, 您可以將物件定義為可供系結使用的方式之一, 就是將它定義為資源並提供。 `x:Key` 在下列範例中, 您的`Person`物件具有名為`PersonName`的字串屬性。 在名`<src>` `Person` 為的命名空間中,會定義物件(在反白顯示`SDKSample`的行中, 包含元素)。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 接著<xref:System.Windows.Controls.TextBlock> , 您可以將控制項系結至中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的物件, 如包含`<TextBlock>`專案的反白顯示程式程式碼所示。 
  
 或者, 您可以使用<xref:System.Windows.Data.ObjectDataProvider>類別, 如下列範例所示:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 您可以用相同方式定義系結, 如包含`<TextBlock>`專案的反白顯示行所示。  
  
 在此特定範例中, 結果相同: 您有<xref:System.Windows.Controls.TextBlock>具有文字內容`Joe`的。 不過, <xref:System.Windows.Data.ObjectDataProvider>類別會提供功能, 例如能夠系結至方法的結果。 如果您需要它所提供<xref:System.Windows.Data.ObjectDataProvider>的功能, 您可以選擇使用類別。  
  
 不過, 如果您要系結至已建立的物件, 您需要`DataContext`在程式碼中設定, 如下列範例所示。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.Data.XmlDataProvider>使用類別存取資料以進行系結, 請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 XML 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 若要[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.Data.ObjectDataProvider>使用類別存取要系結的資料, 請參閱系結[至 XDocument、system.xml.linq.xelement> 或 LINQ for XML 查詢結果](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 如需您可以指定所系結之資料的許多方法的詳細資訊, 請參閱指定系結[來源](how-to-specify-the-binding-source.md)。 如需您可以系結至哪些類型的資料, 或如何實作為系結的通用語言執行平臺 (CLR) 物件的相關資訊, 請參閱系結[來源總覽](binding-sources-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
