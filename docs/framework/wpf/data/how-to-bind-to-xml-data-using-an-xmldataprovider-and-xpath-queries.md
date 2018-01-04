---
title: "操作說明：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92037be2280eaa248951ff9bad82b7a1581a4fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>操作說明：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
這個範例示範如何將繫結至[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]資料使用<xref:System.Windows.Data.XmlDataProvider>。  
  
 與<xref:System.Windows.Data.XmlDataProvider>、 有基礎可以透過應用程式中的資料繫結來存取的資料可以是任何樹狀目錄中的[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]節點。 換句話說，<xref:System.Windows.Data.XmlDataProvider>提供便利的方式使用的任何樹[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]做為繫結來源的節點。  
  
## <a name="example"></a>範例  
 在下列範例中，則資料會做為內嵌[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]*資料島*內<xref:System.Windows.FrameworkElement.Resources%2A>> 一節。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料島必須包裝在 `<x:XData>` 標記中，並一律具有單一根節點，在此範例中為 *Inventory*。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料的根節點具有一個 **xmlns** 屬性，會將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間設為空白字串。 這是將 XPath 查詢套用至內嵌於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面內之資料島的需求。 在此內嵌情況下， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，而且資料島，因此繼承<xref:System.Windows>命名空間。 因此，您必須設定空白以防止 XPath 查詢所限定的命名空間<xref:System.Windows>會中的 「 查詢命名空間。  
  
 [!code-xaml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 如此範例所示，若要在屬性語法中建立相同的繫結宣告，您必須正確地逸出特殊字元。 如需詳細資訊，請參閱 [XML 字元實體和 XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)。  
  
 <xref:System.Windows.Controls.ListBox>時執行這個範例會顯示下列項目。 這些是 *Books* 底下之所有元素的 *Title*，其有一個 *Stock* 值為 *out*，或有一個 *Number* 值為 3 或大於等於 8 。 請注意，沒有*CD*會傳回項目，因為<xref:System.Windows.Data.XmlDataProvider.XPath%2A>值上的設定<xref:System.Windows.Data.XmlDataProvider>只表示*書籍*項目應該公開 （基本上設定篩選器）。  
  
 ![XPath 範例](../../../../docs/framework/wpf/data/media/xpathexample.PNG "XPathExample")  
  
 在此範例中，因為，會顯示書籍<xref:System.Windows.Data.Binding.XPath%2A>的<xref:System.Windows.Controls.TextBlock>中的繫結<xref:System.Windows.DataTemplate>設為"*標題*"。 如果您想要顯示屬性的值，例如*ISBN*，則您會設定<xref:System.Windows.Data.Binding.XPath%2A>值設定為"`@ISBN`"。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的 **XPath** 屬性是由 XmlNode.SelectNodes 方法處理。 您可以修改 **XPath** 查詢，以取得不同的結果。 以下是一些範例<xref:System.Windows.Data.Binding.XPath%2A>查詢繫結上<xref:System.Windows.Controls.ListBox>前一個範例：  
  
-   `XPath="Book[1]"` 會傳回第一個書籍元素 ("XML in Action")。 請注意，**XPath** 索引以 1 為起始，而非 0。  
  
-   `XPath="Book[@*]"` 會傳回所有具有屬性的書籍元素。  
  
-   `XPath="Book[last()-1]"` 會傳回第二個至最後一個書籍元素 ("Introducing Microsoft .NET")。  
  
-   `XPath="*[position()>3]"` 會傳回除前 3 個以外的所有書籍元素。  
  
 當您執行**XPath**查詢，它會傳回<xref:System.Xml.XmlNode>或 XmlNodes 的清單。 <xref:System.Xml.XmlNode>是[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件，這表示您可以使用<xref:System.Windows.Data.Binding.Path%2A>屬性要繫結至[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]屬性。 再看一次上一個範例。 如果此範例的其餘部分維持不變，而且您變更<xref:System.Windows.Controls.TextBlock>下列繫結，您會看到的名稱中傳回的 XmlNodes <xref:System.Windows.Controls.ListBox>。 在這個案例中，所有傳回的節點名稱都將為 *Book*。  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 在某些應用程式中，因為在編譯時即須取得資料的確切內容，所以可能不便在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面的來源內將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 內嵌為資料島。 因此，您也可以從外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案取得資料，如下列範例所示：  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 如果[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料位於遠端[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]檔案中，您會定義存取權限的資料藉由指派適當[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]至<xref:System.Windows.Data.XmlDataProvider.Source%2A>屬性，如下所示：  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Data.ObjectDataProvider>  
 [繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)  
 [使用含階層式 XML 資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
