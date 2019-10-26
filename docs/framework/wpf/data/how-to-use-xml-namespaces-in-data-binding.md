---
title: 操作說明：在資料繫結中使用 XML 命名空間
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919660"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="9c7b3-102">操作說明：在資料繫結中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="9c7b3-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="9c7b3-103">範例</span><span class="sxs-lookup"><span data-stu-id="9c7b3-103">Example</span></span>
 <span data-ttu-id="9c7b3-104">這個範例顯示如何處理 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 繫結來源中指定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9c7b3-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>

 <span data-ttu-id="9c7b3-105">如果您的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料具有下列 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間定義：</span><span class="sxs-lookup"><span data-stu-id="9c7b3-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="9c7b3-106">您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping> 元素，將命名空間對應至 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9c7b3-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="9c7b3-107">然後，您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 來參考 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9c7b3-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="9c7b3-108">此範例中的 <xref:System.Windows.Controls.ListBox> 會顯示每個*專案*的*標題*和*dc： date* 。</span><span class="sxs-lookup"><span data-stu-id="9c7b3-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="9c7b3-109">請注意，您指定的 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 不一定要符合 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 來源中所使用的值;如果 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 來源中的前置詞變更，則您的對應仍可運作。</span><span class="sxs-lookup"><span data-stu-id="9c7b3-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>

 <span data-ttu-id="9c7b3-110">在此特定範例中，[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料來自 web 服務，但 <xref:System.Windows.Data.XmlNamespaceMapping> 元素也適用于內嵌 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 或內嵌檔案中的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料。</span><span class="sxs-lookup"><span data-stu-id="9c7b3-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c7b3-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="9c7b3-111">See also</span></span>

- [<span data-ttu-id="9c7b3-112">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="9c7b3-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="9c7b3-113">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="9c7b3-113">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9c7b3-114">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="9c7b3-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
