---
title: 操作說明：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: f075d646539de5d68e1c9c75d9664451125e9919
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733559"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a><span data-ttu-id="248e1-102">操作說明：使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="248e1-102">How to: Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>
<span data-ttu-id="248e1-103">這個範例示範如何使用 <xref:System.Windows.Data.XmlDataProvider>系結至 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="248e1-103">This example shows how to bind to XML data using an <xref:System.Windows.Data.XmlDataProvider>.</span></span>  
  
 <span data-ttu-id="248e1-104">有了 <xref:System.Windows.Data.XmlDataProvider>，可以透過應用程式中的資料系結存取的基礎資料，可以是任何 XML 節點的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="248e1-104">With an <xref:System.Windows.Data.XmlDataProvider>, the underlying data that can be accessed through data binding in your application can be any tree of XML nodes.</span></span> <span data-ttu-id="248e1-105">換句話說，<xref:System.Windows.Data.XmlDataProvider> 提供一個便利的方式，可以使用任何 XML 節點的樹狀結構做為系結來源。</span><span class="sxs-lookup"><span data-stu-id="248e1-105">In other words, an <xref:System.Windows.Data.XmlDataProvider> provides a convenient way to use any tree of XML nodes as a binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="248e1-106">範例</span><span class="sxs-lookup"><span data-stu-id="248e1-106">Example</span></span>  
 <span data-ttu-id="248e1-107">在下列範例中，資料會直接內嵌為 <xref:System.Windows.FrameworkElement.Resources%2A> 區段中的 XML*資料島*。</span><span class="sxs-lookup"><span data-stu-id="248e1-107">In the following example, the data is embedded directly as an XML *data island* within the <xref:System.Windows.FrameworkElement.Resources%2A> section.</span></span> <span data-ttu-id="248e1-108">XML 資料島必須包裝在 `<x:XData>` 標籤中，而且一律具有單一根節點，在此範例中為*清查*。</span><span class="sxs-lookup"><span data-stu-id="248e1-108">An XML data island must be wrapped in `<x:XData>` tags and always have a single root node, which is *Inventory* in this example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="248e1-109">XML 資料的根節點具有**xmlns**屬性，可將 xml 命名空間設定為空字串。</span><span class="sxs-lookup"><span data-stu-id="248e1-109">The root node of the XML data has an **xmlns** attribute that sets the XML namespace to an empty string.</span></span> <span data-ttu-id="248e1-110">這是將 XPath 查詢套用至內嵌於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面內之資料島的需求。</span><span class="sxs-lookup"><span data-stu-id="248e1-110">This is a requirement for applying XPath queries to a data island that is inline within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="248e1-111">在此內嵌案例中，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，因此資料島會繼承 <xref:System.Windows> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="248e1-111">In this inline case, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], and thus the data island, inherits the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="248e1-112">因此，您必須將命名空間設為空白，讓 XPath 查詢不受 <xref:System.Windows> 命名空間的限定，這會 misdirect 查詢。</span><span class="sxs-lookup"><span data-stu-id="248e1-112">Because of this, you need to set the namespace blank to keep XPath queries from being qualified by the <xref:System.Windows> namespace, which would misdirect the queries.</span></span>  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="248e1-113">如此範例所示，若要在屬性語法中建立相同的繫結宣告，您必須正確地逸出特殊字元。</span><span class="sxs-lookup"><span data-stu-id="248e1-113">As shown in this example, to create the same binding declaration in attribute syntax you must escape the special characters properly.</span></span> <span data-ttu-id="248e1-114">如需詳細資訊，請參閱 [XML 字元實體和 XAML](../../xaml-services/xml-character-entities-and-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="248e1-114">For more information, see [XML Character Entities and XAML](../../xaml-services/xml-character-entities-and-xaml.md).</span></span>  
  
 <span data-ttu-id="248e1-115">執行此範例時，<xref:System.Windows.Controls.ListBox> 將會顯示下列專案。</span><span class="sxs-lookup"><span data-stu-id="248e1-115">The <xref:System.Windows.Controls.ListBox> will show the following items when this example is run.</span></span> <span data-ttu-id="248e1-116">這些是 *Books* 底下之所有元素的 *Title*，其有一個 *Stock* 值為 *out*，或有一個 *Number* 值為 3 或大於等於 8 。</span><span class="sxs-lookup"><span data-stu-id="248e1-116">These are the *Title*s of all of the elements under *Books* with either a *Stock* value of "*out*" or a *Number* value of 3 or greater than or equals to 8.</span></span> <span data-ttu-id="248e1-117">請注意，因為 <xref:System.Windows.Data.XmlDataProvider> 上設定的 <xref:System.Windows.Data.XmlDataProvider.XPath%2A> 值指出只應公開*書籍*元素（基本上是設定篩選器），所以不會傳回任何*CD*專案。</span><span class="sxs-lookup"><span data-stu-id="248e1-117">Notice that no *CD* items are returned because the <xref:System.Windows.Data.XmlDataProvider.XPath%2A> value set on the <xref:System.Windows.Data.XmlDataProvider> indicates that only the *Books* elements should be exposed (essentially setting a filter).</span></span>  
  
 ![XPath 範例的螢幕擷取畫面，其中顯示四本書的標題。](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 <span data-ttu-id="248e1-119">在此範例中，會顯示書名，因為 <xref:System.Windows.DataTemplate> 中 <xref:System.Windows.Controls.TextBlock> 系結的 <xref:System.Windows.Data.Binding.XPath%2A> 設定為「*標題*」。</span><span class="sxs-lookup"><span data-stu-id="248e1-119">In this example, the book titles are displayed because the <xref:System.Windows.Data.Binding.XPath%2A> of the <xref:System.Windows.Controls.TextBlock> binding in the <xref:System.Windows.DataTemplate> is set to "*Title*".</span></span> <span data-ttu-id="248e1-120">如果您想要顯示內容的值（例如*ISBN*），您可以將該 <xref:System.Windows.Data.Binding.XPath%2A> 值設定為 "`@ISBN`"。</span><span class="sxs-lookup"><span data-stu-id="248e1-120">If you want to display the value of an attribute, such as the *ISBN*, you would set that <xref:System.Windows.Data.Binding.XPath%2A> value to "`@ISBN`".</span></span>  
  
 <span data-ttu-id="248e1-121">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的 **XPath** 屬性是由 XmlNode.SelectNodes 方法處理。</span><span class="sxs-lookup"><span data-stu-id="248e1-121">The **XPath** properties in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are handled by the XmlNode.SelectNodes method.</span></span> <span data-ttu-id="248e1-122">您可以修改 **XPath** 查詢，以取得不同的結果。</span><span class="sxs-lookup"><span data-stu-id="248e1-122">You can modify the **XPath** queries to get different results.</span></span> <span data-ttu-id="248e1-123">以下是上一個範例中系結 <xref:System.Windows.Controls.ListBox> 上 <xref:System.Windows.Data.Binding.XPath%2A> 查詢的一些範例：</span><span class="sxs-lookup"><span data-stu-id="248e1-123">Here are some examples for the <xref:System.Windows.Data.Binding.XPath%2A> query on the bound <xref:System.Windows.Controls.ListBox> from the previous example:</span></span>  
  
- <span data-ttu-id="248e1-124">`XPath="Book[1]"` 會傳回第一個書籍元素 ("XML in Action")。</span><span class="sxs-lookup"><span data-stu-id="248e1-124">`XPath="Book[1]"` will return the first book element ("XML in Action").</span></span> <span data-ttu-id="248e1-125">請注意，**XPath** 索引以 1 為起始，而非 0。</span><span class="sxs-lookup"><span data-stu-id="248e1-125">Note that **XPath** indexes are based on 1, not 0.</span></span>  
  
- <span data-ttu-id="248e1-126">`XPath="Book[@*]"` 會傳回所有具有屬性的書籍元素。</span><span class="sxs-lookup"><span data-stu-id="248e1-126">`XPath="Book[@*]"` will return all book elements with any attributes.</span></span>  
  
- <span data-ttu-id="248e1-127">`XPath="Book[last()-1]"` 會傳回第二個至最後一個書籍元素 ("Introducing Microsoft .NET")。</span><span class="sxs-lookup"><span data-stu-id="248e1-127">`XPath="Book[last()-1]"` will return the second to last book element ("Introducing Microsoft .NET").</span></span>  
  
- <span data-ttu-id="248e1-128">`XPath="*[position()>3]"` 會傳回除前 3 個以外的所有書籍元素。</span><span class="sxs-lookup"><span data-stu-id="248e1-128">`XPath="*[position()>3]"` will return all of the book elements except for the first 3.</span></span>  
  
 <span data-ttu-id="248e1-129">當您執行**XPath**查詢時，它會傳回 <xref:System.Xml.XmlNode> 或 XmlNodes 清單。</span><span class="sxs-lookup"><span data-stu-id="248e1-129">When you run an **XPath** query, it returns an <xref:System.Xml.XmlNode> or a list of XmlNodes.</span></span> <span data-ttu-id="248e1-130"><xref:System.Xml.XmlNode> 是 common language runtime （CLR）物件，這表示您可以使用 <xref:System.Windows.Data.Binding.Path%2A> 屬性來系結至 common language runtime （CLR）屬性。</span><span class="sxs-lookup"><span data-stu-id="248e1-130"><xref:System.Xml.XmlNode> is a common language runtime (CLR) object, which means you can use the <xref:System.Windows.Data.Binding.Path%2A> property to bind to the common language runtime (CLR) properties.</span></span> <span data-ttu-id="248e1-131">再看一次上一個範例。</span><span class="sxs-lookup"><span data-stu-id="248e1-131">Consider the previous example again.</span></span> <span data-ttu-id="248e1-132">如果範例的其餘部分維持不變，而您將 <xref:System.Windows.Controls.TextBlock> 系結變更為下列，您會在 <xref:System.Windows.Controls.ListBox>中看到傳回之 XmlNodes 的名稱。</span><span class="sxs-lookup"><span data-stu-id="248e1-132">If the rest of the example stays the same and you change the <xref:System.Windows.Controls.TextBlock> binding to the following, you will see the names of the returned XmlNodes in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="248e1-133">在這個案例中，所有傳回的節點名稱都將為 *Book*。</span><span class="sxs-lookup"><span data-stu-id="248e1-133">In this case, the name of all the returned nodes is "*Book*".</span></span>  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 <span data-ttu-id="248e1-134">在某些應用程式中，將 XML 內嵌為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面來源內的資料島可能很不方便，因為在編譯時期，資料的確切內容必須是已知的。</span><span class="sxs-lookup"><span data-stu-id="248e1-134">In some applications, embedding the XML as a data island within the source of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page can be inconvenient because the exact content of the data must be known at compile time.</span></span> <span data-ttu-id="248e1-135">因此，也支援從外部 XML 檔案取得資料，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="248e1-135">Therefore, obtaining the data from an external XML file is also supported, as in the following example:</span></span>  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 <span data-ttu-id="248e1-136">如果 XML 資料位於遠端 XML 檔案中，您可以將適當的 URL 指派給 <xref:System.Windows.Data.XmlDataProvider.Source%2A> 屬性，藉以定義資料的存取權，如下所示：</span><span class="sxs-lookup"><span data-stu-id="248e1-136">If the XML data resides in a remote XML file, you would define access to the data by assigning an appropriate URL to the <xref:System.Windows.Data.XmlDataProvider.Source%2A> attribute as follows:</span></span>  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="248e1-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="248e1-137">See also</span></span>

- <xref:System.Windows.Data.ObjectDataProvider>
- [<span data-ttu-id="248e1-138">繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ</span><span class="sxs-lookup"><span data-stu-id="248e1-138">Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [<span data-ttu-id="248e1-139">使用含階層式 XML 資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="248e1-139">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="248e1-140">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="248e1-140">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="248e1-141">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="248e1-141">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="248e1-142">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="248e1-142">How-to Topics</span></span>](data-binding-how-to-topics.md)
