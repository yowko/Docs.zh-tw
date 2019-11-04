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
ms.openlocfilehash: 2bfd9809a6ad487a7e706366dc6bce8fe951c940
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459756"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>如何：讓資料可於 XAML 中繫結
本主題討論您可以根據應用程式的需求，讓資料可在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中進行系結的各種方式。  
  
## <a name="example"></a>範例  
 如果您有想要系結至 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的 common language runtime （CLR）物件，則可讓物件進行系結的方法之一，就是將它定義為資源並提供 `x:Key`。 在下列範例中，您有一個 `Person` 物件，其中具有名為 `PersonName`的字串屬性。 `Person` 物件（在反白顯示的行中，包含 `<src>` 元素）定義于名為 `SDKSample`的命名空間中。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 接著，您可以將 <xref:System.Windows.Controls.TextBlock> 控制項系結至 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中的物件，如同包含 `<TextBlock>` 元素的反白顯示行所示。 
  
 或者，您可以使用 <xref:System.Windows.Data.ObjectDataProvider> 類別，如下列範例所示：  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 您可以用相同的方式定義系結，如同包含 `<TextBlock>` 元素的反白顯示行所示。  
  
 在此特定範例中，結果相同：您有 <xref:System.Windows.Controls.TextBlock>，其中包含文字內容 `Joe`。 不過，<xref:System.Windows.Data.ObjectDataProvider> 類別提供的功能，例如能夠系結至方法的結果。 如果您需要所提供的功能，您可以選擇使用 <xref:System.Windows.Data.ObjectDataProvider> 類別。  
  
 不過，如果您要系結至已建立的物件，您需要在程式碼中設定 `DataContext`，如下列範例所示。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要使用 <xref:System.Windows.Data.XmlDataProvider> 類別來存取 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料以進行系結，請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 XML 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 若要使用 <xref:System.Windows.Data.ObjectDataProvider> 類別來存取 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料以進行系結，請參閱系結[至 XML 查詢結果的 XDocument、system.xml.linq.xelement> 或 LINQ](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 如需您可以指定所系結之資料的許多方法的詳細資訊，請參閱指定系結[來源](how-to-specify-the-binding-source.md)。 如需您可以系結至哪些類型的資料，或如何實作為系結的通用語言執行平臺（CLR）物件的相關資訊，請參閱系結[來源總覽](binding-sources-overview.md)。  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
