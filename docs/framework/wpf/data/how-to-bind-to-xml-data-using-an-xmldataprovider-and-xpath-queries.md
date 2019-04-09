---
title: HOW TO：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: f6cd09279cf23d3273e7a4083950a5f42714c8bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097222"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>HOW TO：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
此範例示範如何將繫結至[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]資料使用<xref:System.Windows.Data.XmlDataProvider>。  
  
 具有<xref:System.Windows.Data.XmlDataProvider>，則基礎，您可以透過在您的應用程式中的資料繫結的資料可以是任何樹狀目錄中的[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]節點。 亦即<xref:System.Windows.Data.XmlDataProvider>提供便利的方式，若要使用的任一樹狀[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]做為繫結來源的節點。  
  
## <a name="example"></a>範例  
 在下列範例中，會將資料內嵌直接當做[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]*資料島*內<xref:System.Windows.FrameworkElement.Resources%2A>一節。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料島必須包裝在 `<x:XData>` 標記中，並一律具有單一根節點，在此範例中為 *Inventory*。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料的根節點具有一個 **xmlns** 屬性，會將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間設為空白字串。 這是將 XPath 查詢套用至內嵌於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面內之資料島的需求。 在此內嵌案例中， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，因此會繼承資料島，<xref:System.Windows>命名空間。 基於這個原因，您需要設定的命名空間空白可繼續使用 XPath 查詢從限定<xref:System.Windows>命名空間，而錯用查詢。  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 如此範例所示，若要在屬性語法中建立相同的繫結宣告，您必須正確地逸出特殊字元。 如需詳細資訊，請參閱 [XML 字元實體和 XAML](../../xaml-services/xml-character-entities-and-xaml.md)。  
  
 <xref:System.Windows.Controls.ListBox>時執行此範例會顯示下列項目。 這些是 *Books* 底下之所有元素的 *Title*，其有一個 *Stock* 值為 *out*，或有一個 *Number* 值為 3 或大於等於 8 。 請注意，沒有*CD*會傳回項目，因為<xref:System.Windows.Data.XmlDataProvider.XPath%2A>值組<xref:System.Windows.Data.XmlDataProvider>僅表示*書籍*項目應該公開 （基本上設定篩選條件）。  
  
 ![XPath 範例](./media/xpathexample.PNG "XPathExample")  
  
 在此範例中，因為，會顯示書籍標題<xref:System.Windows.Data.Binding.XPath%2A>的<xref:System.Windows.Controls.TextBlock>中的繫結<xref:System.Windows.DataTemplate>設定為 「*標題*"。 如果您想要顯示的屬性 (attribute) 值，例如*ISBN*，則您會設定<xref:System.Windows.Data.Binding.XPath%2A>值"`@ISBN`」。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的 **XPath** 屬性是由 XmlNode.SelectNodes 方法處理。 您可以修改 **XPath** 查詢，以取得不同的結果。 以下是一些範例，如<xref:System.Windows.Data.Binding.XPath%2A>查詢繫結<xref:System.Windows.Controls.ListBox>前一個範例：  
  
-   `XPath="Book[1]"` 會傳回第一個書籍元素 ("XML in Action")。 請注意，**XPath** 索引以 1 為起始，而非 0。  
  
-   `XPath="Book[@*]"` 會傳回具有任何屬性的所有 book 項目。  
  
-   `XPath="Book[last()-1]"` 會傳回第二個到最後一個書籍元素 ("Introducing Microsoft.NET")。  
  
-   `XPath="*[position()>3]"` 會傳回所有 book 項目，除了第一個 3。  
  
 當您執行**XPath**查詢，它會傳回<xref:System.Xml.XmlNode>或 XmlNodes 的清單。 <xref:System.Xml.XmlNode> 已[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件，這表示您可以使用<xref:System.Windows.Data.Binding.Path%2A>屬性繫結至[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]屬性。 再看一次上一個範例。 如果此範例的其餘部分維持不變，而且您變更<xref:System.Windows.Controls.TextBlock>繫結至下列，您會看到在所傳回之 Xmlnode 的名稱<xref:System.Windows.Controls.ListBox>。 在這個案例中，所有傳回的節點名稱都將為 *Book*。  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 在某些應用程式中，因為在編譯時即須取得資料的確切內容，所以可能不便在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面的來源內將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 內嵌為資料島。 因此，您也可以從外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案取得資料，如下列範例所示：  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 如果[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]的資料位於遠端[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]檔案中，您會定義存取資料，指派適當[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]到<xref:System.Windows.Data.XmlDataProvider.Source%2A>屬性，如下所示：  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.ObjectDataProvider>
- [繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [使用含階層式 XML 資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [繫結來源概觀](binding-sources-overview.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW TO 主題](data-binding-how-to-topics.md)
