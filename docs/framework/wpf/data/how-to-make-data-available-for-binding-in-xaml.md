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
ms.openlocfilehash: 09a6fca48c06efca6f06b9e0617de9095197bd17
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070795"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="8c762-102">如何：讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="8c762-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="8c762-103">本主題討論您可以讓資料可用於繫結中的各種方式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，取決於您的應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="8c762-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c762-104">範例</span><span class="sxs-lookup"><span data-stu-id="8c762-104">Example</span></span>  
 <span data-ttu-id="8c762-105">如果您有[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]您想要從繫結至的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您可以讓物件可以繫結是定義為資源，並為它提供一種方式`x:Key`。</span><span class="sxs-lookup"><span data-stu-id="8c762-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="8c762-106">在下列範例中，您必須`Person`物件具有名為字串屬性`PersonName`。</span><span class="sxs-lookup"><span data-stu-id="8c762-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="8c762-107">`Person`物件 (顯示反白顯示的列中包含`<src>`項目) 中命名空間中定義`SDKSample`。</span><span class="sxs-lookup"><span data-stu-id="8c762-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="8c762-108">您接著可以繫結<xref:System.Windows.Controls.TextBlock>控制項中的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，如反白顯示列包含`<TextBlock>`項目顯示。</span><span class="sxs-lookup"><span data-stu-id="8c762-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="8c762-109">或者，您可以使用<xref:System.Windows.Data.ObjectDataProvider>類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8c762-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="8c762-110">定義繫結一樣，強調顯示的行會包含`<TextBlock>`項目顯示。</span><span class="sxs-lookup"><span data-stu-id="8c762-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="8c762-111">在這個範例中，結果會是相同： 您必須<xref:System.Windows.Controls.TextBlock>使用的文字內容`Joe`。</span><span class="sxs-lookup"><span data-stu-id="8c762-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="8c762-112">不過，<xref:System.Windows.Data.ObjectDataProvider>類別提供的功能，例如能夠繫結至方法的結果。</span><span class="sxs-lookup"><span data-stu-id="8c762-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="8c762-113">您可以選擇使用<xref:System.Windows.Data.ObjectDataProvider>類別，如果您需要它所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="8c762-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="8c762-114">不過，如果您要繫結已經存在的物件，您需要設定`DataContext`在程式碼，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8c762-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="8c762-115">若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]繫結使用的資料<xref:System.Windows.Data.XmlDataProvider>類別，請參閱[XMLDataProvider 和 XPath 查詢，繫結至 XML 資料使用](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="8c762-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="8c762-116">若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]繫結使用的資料<xref:System.Windows.Data.ObjectDataProvider>類別，請參閱[for XML 查詢結果繫結至 XDocument、 XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。</span><span class="sxs-lookup"><span data-stu-id="8c762-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="8c762-117">如需您可以指定您要繫結資料的多種資訊，請參閱[指定的繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)。</span><span class="sxs-lookup"><span data-stu-id="8c762-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="8c762-118">如需您可以結合的資料類型至或如何實作您自己[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件的繫結，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8c762-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c762-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c762-119">See Also</span></span>  
 [<span data-ttu-id="8c762-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="8c762-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="8c762-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="8c762-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
