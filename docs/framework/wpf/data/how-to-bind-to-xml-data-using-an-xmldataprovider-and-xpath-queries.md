---
title: "如何：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "繫結, 使用 XmlDataProvider 查詢繫結至 XML 資料"
  - "資料繫結, 使用 XmlDataProvider 查詢繫結至 XML 資料"
  - "XmlDataProvider, 繫結至 XML 資料"
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
這個範例顯示如何使用 <xref:System.Windows.Data.XmlDataProvider> 繫結至 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 資料。  
  
 透過 <xref:System.Windows.Data.XmlDataProvider>，任何 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 節點樹狀目錄皆可做為在應用程式中經由資料繫結進行存取的基礎資料。  換句話說，<xref:System.Windows.Data.XmlDataProvider> 提供了便利的方式來將任何 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 節點樹狀目錄做為[繫結來源](GTMT)。  
  
## 範例  
 下列範例會將資料直接內嵌為 <xref:System.Windows.FrameworkElement.Resources%2A> 區段內的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *資料島*。  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料島必須包裝在 `<x:XData>` 標記中，且一律具有單一根節點，在這個範例中為 *Inventory*。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料的根節點具有 **xmlns** 屬性 \(Attribute\)，可以將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間設為空字串。  將 XPath 查詢套用至 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面內的內嵌 \(Inline\) 資料島時，必須使用這個屬性。  在這個內嵌案例中，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] \(包括資料島\) 會繼承 <xref:System.Windows> 命名空間。  因此，您必須將命名空間設為空白，使 XPath 查詢不會套用 <xref:System.Windows> 命名空間，以免錯用查詢。  
  
 [!code-xml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 如這個範例所示，若要以屬性語法建立相同的宣告，您必須適當逸出特定字元。  如需詳細資訊，請參閱 [XML 字元實體和 XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)。  
  
 這個範例執行時，<xref:System.Windows.Controls.ListBox> 會顯示下列項目，  這些是 *Books* 下 *Stock* 值為 "*out*" 或是 *Number* 值為 3 或大於等於 8 的所有項目的 *Title*。  請注意，不會傳回任何 *CD* 項目 \(Item\)，因為 <xref:System.Windows.Data.XmlDataProvider> 上設定的 <xref:System.Windows.Data.XmlDataProvider.XPath%2A> 值僅表示應該公開 *Books* 項目 \(Element\) \(基本上是設定篩選\)。  
  
 ![XPath 範例](../../../../docs/framework/wpf/data/media/xpathexample.png "XPathExample")  
  
 在這個範例中，因為 <xref:System.Windows.DataTemplate> 中之 <xref:System.Windows.Controls.TextBlock> 繫結的 <xref:System.Windows.Data.Binding.XPath%2A> 設為 *Title*，所以會顯示書籍標題。  若要顯示屬性 \(Attribute\) 的值 \(如 *ISBN*\)，則應該將 <xref:System.Windows.Data.Binding.XPath%2A> 值設為 "`@ISBN`"。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的 **XPath** 屬性 \(Property\) 會以 XmlNode.SelectNodes 方法處理。  您可以修改 **XPath** 查詢，以取得不同的結果。  下列幾個範例說明上一個範例中已繫結的 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Data.Binding.XPath%2A> 查詢：  
  
-   `XPath="Book[1]"` 會傳回第一個書籍項目 \("XML in Action"\)。  請注意，**XPath** 索引以 1 為起始，而非 0。  
  
-   `XPath="Book[@*]"` 會傳回所有具有屬性 \(Attribute\) 的書籍項目。  
  
-   `XPath="Book[last()-1]"` 會傳回第二個至最後一個書籍項目 \("Introducing Microsoft .NET"\)。  
  
-   `XPath="*[position()>3]"` 會傳回除前三個以外的所有書籍項目。  
  
 當您執行 **XPath** 查詢時，會傳回 <xref:System.Xml.XmlNode> 或 XmlNodes 的清單。  <xref:System.Xml.XmlNode> 是 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件，這表示您可以使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性繫結至 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性。  請再次考量上一個範例。  如果您將 <xref:System.Windows.Controls.TextBlock> 繫結變更為下列項目，而範例其餘部分保持不變，您將在 <xref:System.Windows.Controls.ListBox> 中看見所傳回之 XmlNode 的名稱。  在這個案例中，所有傳回的節點名稱都將為 *Book*。  
  
 [!code-xml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 在某些應用程式中，因為在進行編譯時即須取得資料的確切內容，所以可能不便在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面的來源內將 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 內嵌為資料島。  因此，您也可以從外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案取得資料，如下列範例所示：  
  
 [!code-xml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 如果 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料位於遠端 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案中，您就必須指派適當的 [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 給 <xref:System.Windows.Data.XmlDataProvider.Source%2A> 屬性 \(Attribute\) 以定義資料存取，如下所示：  
  
```  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## 請參閱  
 <xref:System.Windows.Data.ObjectDataProvider>   
 [繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)   
 [使用含階層式 XML 資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)   
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)