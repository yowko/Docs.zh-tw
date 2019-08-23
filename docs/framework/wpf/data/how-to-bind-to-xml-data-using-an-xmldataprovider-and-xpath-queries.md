---
title: HOW TO：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 4833e024fcd352094a2163f11df8572aa4c241f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944640"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>HOW TO：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
這個範例會示範如何[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] <xref:System.Windows.Data.XmlDataProvider>使用系結至資料。  
  
 使用, 可以透過應用程式中的資料系結存取的基礎資料, 可以是任何節點的[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]樹狀結構。 <xref:System.Windows.Data.XmlDataProvider> 換句話說, <xref:System.Windows.Data.XmlDataProvider>會提供一個便利的方式, 使用任何[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]節點樹狀結構做為系結來源。  
  
## <a name="example"></a>範例  
 在下列範例中, 資料會直接內嵌為[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.FrameworkElement.Resources%2A>區段內的*資料島*。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料島必須包裝在 `<x:XData>` 標記中，並一律具有單一根節點，在此範例中為 *Inventory*。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料的根節點具有一個 **xmlns** 屬性，會將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間設為空白字串。 這是將 XPath 查詢套用至內嵌於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面內之資料島的需求。 在此內嵌案例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中,、和因此資料島會<xref:System.Windows>繼承命名空間。 因此, 您必須將命名空間設為空白, 讓 XPath 查詢不受<xref:System.Windows>命名空間的限定, 這會 misdirect 查詢。  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 如此範例所示，若要在屬性語法中建立相同的繫結宣告，您必須正確地逸出特殊字元。 如需詳細資訊，請參閱 [XML 字元實體和 XAML](../../xaml-services/xml-character-entities-and-xaml.md)。  
  
 執行<xref:System.Windows.Controls.ListBox>此範例時, 將會顯示下列專案。 這些是 *Books* 底下之所有元素的 *Title*，其有一個 *Stock* 值為 *out*，或有一個 *Number* 值為 3 或大於等於 8 。 請注意,在上設定的<xref:System.Windows.Data.XmlDataProvider.XPath%2A> <xref:System.Windows.Data.XmlDataProvider>值表示只會公開*書籍*元素 (基本上是設定篩選器), 因此不會傳回任何 CD 專案。  
  
 ![XPath 範例的螢幕擷取畫面, 其中顯示四本書的標題。](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 在此範例中, 會顯示書名<xref:System.Windows.Data.Binding.XPath%2A> , 因為<xref:System.Windows.Controls.TextBlock>中<xref:System.Windows.DataTemplate>系結的已設定為 "*Title*"。 如果您想要顯示內容的值 (例如*ISBN*), 您可以將該值設<xref:System.Windows.Data.Binding.XPath%2A>為 "`@ISBN`"。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的 **XPath** 屬性是由 XmlNode.SelectNodes 方法處理。 您可以修改 **XPath** 查詢，以取得不同的結果。 以下是上一個範例系<xref:System.Windows.Data.Binding.XPath%2A>結上<xref:System.Windows.Controls.ListBox>的查詢範例:  
  
- `XPath="Book[1]"` 會傳回第一個書籍元素 ("XML in Action")。 請注意，**XPath** 索引以 1 為起始，而非 0。  
  
- `XPath="Book[@*]"` 會傳回所有具有屬性的書籍元素。  
  
- `XPath="Book[last()-1]"` 會傳回第二個至最後一個書籍元素 ("Introducing Microsoft .NET")。  
  
- `XPath="*[position()>3]"` 會傳回除前 3 個以外的所有書籍元素。  
  
 當您執行**XPath**查詢時, 它會<xref:System.Xml.XmlNode>傳回或 XmlNodes 清單。 <xref:System.Xml.XmlNode>是 common language runtime (clr) 物件, 這表示您可以使用<xref:System.Windows.Data.Binding.Path%2A>屬性系結至 common language runtime (clr) 屬性。 再看一次上一個範例。 如果範例的其餘部分維持不變, 而您將系<xref:System.Windows.Controls.TextBlock>結變更為下列, 您會<xref:System.Windows.Controls.ListBox>在中看到傳回之 XmlNodes 的名稱。 在這個案例中，所有傳回的節點名稱都將為 *Book*。  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 在某些應用程式中，因為在編譯時即須取得資料的確切內容，所以可能不便在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面的來源內將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 內嵌為資料島。 因此，您也可以從外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案取得資料，如下列範例所示：  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 如果資料位於遠端[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]檔案中, 您可以藉由<xref:System.Windows.Data.XmlDataProvider.Source%2A>指派適當[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]的給屬性來定義對資料的存取, 如下所示: [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.ObjectDataProvider>
- [繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [使用含階層式 XML 資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [繫結來源概觀](binding-sources-overview.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
