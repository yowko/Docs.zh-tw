---
title: 操作說明：在資料繫結中使用 XML 命名空間
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 483b59bb7cea25617c832b96690f742b8b64b3e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556896"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="5f806-102">操作說明：在資料繫結中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="5f806-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="5f806-103">範例</span><span class="sxs-lookup"><span data-stu-id="5f806-103">Example</span></span>  
 <span data-ttu-id="5f806-104">這個範例顯示如何處理 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 繫結來源中指定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5f806-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>  
  
 <span data-ttu-id="5f806-105">如果您的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料具有下列 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間定義：</span><span class="sxs-lookup"><span data-stu-id="5f806-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 <span data-ttu-id="5f806-106">您可以使用<xref:System.Windows.Data.XmlNamespaceMapping>命名空間對應至的項目<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5f806-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="5f806-107">然後您可以使用<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>指[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間。</span><span class="sxs-lookup"><span data-stu-id="5f806-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="5f806-108"><xref:System.Windows.Controls.ListBox>在此範例會顯示*標題*和*dc:date*每個*項目*。</span><span class="sxs-lookup"><span data-stu-id="5f806-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 <span data-ttu-id="5f806-109">請注意，<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>您指定不需要符合用於[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]來源; 如果前置詞中變更[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]來源對應仍能運作。</span><span class="sxs-lookup"><span data-stu-id="5f806-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>  
  
 <span data-ttu-id="5f806-110">在此特定範例中，[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料來自 web 服務，但<xref:System.Windows.Data.XmlNamespaceMapping>項目也會搭配內嵌[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]或[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]內嵌檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="5f806-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f806-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f806-111">See Also</span></span>  
 [<span data-ttu-id="5f806-112">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5f806-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="5f806-113">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="5f806-113">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5f806-114">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="5f806-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
