---
title: 如何：讓資料可於 XAML 中繫結
description: 探索您可以根據應用程式在 Windows Presentation Foundation （WPF）中的需求，讓資料可供使用的各種方式。
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620790"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>如何：讓資料可於 XAML 中繫結
本主題討論您可以根據 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 應用程式的需求，在中將資料提供給系結的各種方式。  
  
## <a name="example"></a>範例  
 如果您有想要系結的 common language runtime （CLR）物件 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，您可以將物件定義為可供系結使用的方式之一，就是將它定義為資源並提供 `x:Key` 。 在下列範例中，您的 `Person` 物件具有名為的字串屬性 `PersonName` 。 在 `Person` 名為的命名空間中，會定義物件（在反白顯示的行中，包含 `<src>` 元素） `SDKSample` 。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 接著，您可以將 <xref:System.Windows.Controls.TextBlock> 控制項系結至中的物件 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，如包含專案的反白顯示程式程式碼所 `<TextBlock>` 示。
  
 或者，您可以使用 <xref:System.Windows.Data.ObjectDataProvider> 類別，如下列範例所示：  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 您可以用相同方式定義系結，如包含專案的反白顯示行所 `<TextBlock>` 示。  
  
 在此特定範例中，結果相同：您有 <xref:System.Windows.Controls.TextBlock> 具有文字內容的 `Joe` 。 不過，類別會提供功能，例如能夠系結 <xref:System.Windows.Data.ObjectDataProvider> 至方法的結果。 <xref:System.Windows.Data.ObjectDataProvider>如果您需要它所提供的功能，您可以選擇使用類別。  
  
 不過，如果您要系結至已建立的物件，您需要 `DataContext` 在程式碼中設定，如下列範例所示。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要使用類別來存取 XML 資料以進行系結 <xref:System.Windows.Data.XmlDataProvider> ，請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 xml 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 若要使用類別來存取 XML 資料以進行系結 <xref:System.Windows.Data.ObjectDataProvider> ，請參閱系結[至 Xml 查詢結果的 XDocument、SYSTEM.XML.LINQ.XELEMENT> 或 LINQ](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 如需您可以指定所系結之資料的許多方法的詳細資訊，請參閱指定系結[來源](how-to-specify-the-binding-source.md)。 如需您可以系結至哪些類型的資料，或如何實作為系結的通用語言執行平臺（CLR）物件的相關資訊，請參閱系結[來源總覽](binding-sources-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [操作說明主題](data-binding-how-to-topics.md)
