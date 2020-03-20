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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174182"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>如何：讓資料可於 XAML 中繫結
本主題討論各種方法，您可以根據應用程式的需求將資料可用於綁定[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
## <a name="example"></a>範例  
 如果您有一個公用語言運行時 （CLR） 物件，您希望綁定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]到 ，使物件可用於綁定的一種方法是將其定義為資源並給它一個`x:Key`。 在下面的示例中，您有一個`Person`具有字串屬性的物件， `PersonName` 物件`Person`（在顯示的突出顯示包含`<src>`元素的行中）在稱為`SDKSample`的命名空間中定義。  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 然後，<xref:System.Windows.Controls.TextBlock>可以將控制項綁定到 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的物件，如包含`<TextBlock>`元素的突出顯示行所示。
  
 或者，您可以使用類<xref:System.Windows.Data.ObjectDataProvider>，如以下示例所示：  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 定義綁定的方式與包含`<TextBlock>`元素的突出顯示行相同。  
  
 在此特定示例中，結果相同：您<xref:System.Windows.Controls.TextBlock>具有 與 文本內容`Joe`一起 。 但是，類<xref:System.Windows.Data.ObjectDataProvider>提供的功能，例如綁定到方法結果的功能。 如果需要提供的功能，<xref:System.Windows.Data.ObjectDataProvider>可以選擇使用該類。  
  
 但是，如果要綁定到已創建的物件，則需要設置`DataContext`in 代碼，如以下示例所示。  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 要使用<xref:System.Windows.Data.XmlDataProvider>類訪問 XML 資料以進行綁定，請參閱[使用 XMLData 提供程式和 XPath 查詢繫結到 XML 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。 要使用 類訪問用於綁定的<xref:System.Windows.Data.ObjectDataProvider>XML 資料，請參閱[綁定到 XDocument、XElement 或 LINQ 獲取 XML 查詢結果](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 有關指定綁定資料的許多方法的資訊，請參閱[指定綁定源](how-to-specify-the-binding-source.md)。 有關可以綁定到哪些類型的資料以及如何實現自己的通用語言運行時 （CLR） 物件進行綁定的資訊，請參閱[綁定源概述](binding-sources-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [如何使用主題](data-binding-how-to-topics.md)
