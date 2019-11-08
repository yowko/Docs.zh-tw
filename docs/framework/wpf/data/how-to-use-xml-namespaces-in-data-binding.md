---
title: 操作說明：在資料繫結中使用 XML 命名空間
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740583"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="c4fbf-102">操作說明：在資料繫結中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="c4fbf-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="c4fbf-103">範例</span><span class="sxs-lookup"><span data-stu-id="c4fbf-103">Example</span></span>
 <span data-ttu-id="c4fbf-104">這個範例示範如何處理 XML 系結來源中指定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4fbf-104">This example shows how to handle namespaces specified in your XML binding source.</span></span>

 <span data-ttu-id="c4fbf-105">如果您的 XML 資料具有下列 XML 命名空間定義：</span><span class="sxs-lookup"><span data-stu-id="c4fbf-105">If your XML data has the following XML namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="c4fbf-106">您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping> 元素，將命名空間對應至 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c4fbf-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="c4fbf-107">然後，您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 來參考 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4fbf-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the XML namespace.</span></span> <span data-ttu-id="c4fbf-108">此範例中的 <xref:System.Windows.Controls.ListBox> 會顯示每個*專案*的*標題*和*dc： date* 。</span><span class="sxs-lookup"><span data-stu-id="c4fbf-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="c4fbf-109">請注意，您指定的 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 不一定要與 XML 來源中使用的相同。如果 XML 來源中的前置詞變更，則您的對應仍可運作。</span><span class="sxs-lookup"><span data-stu-id="c4fbf-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the XML source; if the prefix changes in the XML source your mapping still works.</span></span>

 <span data-ttu-id="c4fbf-110">在此特定範例中，XML 資料來自 web 服務，但 <xref:System.Windows.Data.XmlNamespaceMapping> 元素也適用于內嵌檔案中的內嵌 XML 或 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="c4fbf-110">In this particular example, the XML data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline XML or XML data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4fbf-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4fbf-111">See also</span></span>

- [<span data-ttu-id="c4fbf-112">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c4fbf-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="c4fbf-113">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="c4fbf-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c4fbf-114">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="c4fbf-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
