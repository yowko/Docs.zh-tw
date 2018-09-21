---
title: 如何：讓資料可於 XAML 中繫結
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 09a6fca48c06efca6f06b9e0617de9095197bd17
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525028"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>如何：讓資料可於 XAML 中繫結
本主題討論您可以讓資料可用於繫結中的各種方式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，取決於您的應用程式的需求。  
  
## <a name="example"></a>範例  
 如果您有[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]您想要從繫結至的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您可以讓物件可以繫結是定義為資源，並為它提供一種方式`x:Key`。 在下列範例中，您必須`Person`物件具有名為字串屬性`PersonName`。 `Person`物件 (顯示反白顯示的列中包含`<src>`項目) 中命名空間中定義`SDKSample`。  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 您接著可以繫結<xref:System.Windows.Controls.TextBlock>控制項中的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，如反白顯示列包含`<TextBlock>`項目顯示。 
  
 或者，您可以使用<xref:System.Windows.Data.ObjectDataProvider>類別，如下列範例所示：  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 定義繫結一樣，強調顯示的行會包含`<TextBlock>`項目顯示。  
  
 在這個範例中，結果會是相同： 您必須<xref:System.Windows.Controls.TextBlock>使用的文字內容`Joe`。 不過，<xref:System.Windows.Data.ObjectDataProvider>類別提供的功能，例如能夠繫結至方法的結果。 您可以選擇使用<xref:System.Windows.Data.ObjectDataProvider>類別，如果您需要它所提供的功能。  
  
 不過，如果您要繫結已經存在的物件，您需要設定`DataContext`在程式碼，如下列範例所示。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]繫結使用的資料<xref:System.Windows.Data.XmlDataProvider>類別，請參閱[XMLDataProvider 和 XPath 查詢，繫結至 XML 資料使用](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]繫結使用的資料<xref:System.Windows.Data.ObjectDataProvider>類別，請參閱[for XML 查詢結果繫結至 XDocument、 XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 如需您可以指定您要繫結資料的多種資訊，請參閱[指定的繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)。 如需您可以結合的資料類型至或如何實作您自己[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件的繫結，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
