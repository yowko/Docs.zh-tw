---
title: 作法：讓資料可於 XAML 中繫結
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401488"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="9106c-102">作法：讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="9106c-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="9106c-103">本主題討論您可以根據應用程式的需求, 在中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]將資料提供給系結的各種方式。</span><span class="sxs-lookup"><span data-stu-id="9106c-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9106c-104">範例</span><span class="sxs-lookup"><span data-stu-id="9106c-104">Example</span></span>  
 <span data-ttu-id="9106c-105">如果您有想要[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]系結的 common language runtime (CLR) 物件, 您可以將物件定義為可供系結使用的方式之一, 就是將它定義為資源並提供。 `x:Key`</span><span class="sxs-lookup"><span data-stu-id="9106c-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="9106c-106">在下列範例中, 您的`Person`物件具有名為`PersonName`的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="9106c-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="9106c-107">在名`<src>` `Person` 為的命名空間中,會定義物件(在反白顯示`SDKSample`的行中, 包含元素)。</span><span class="sxs-lookup"><span data-stu-id="9106c-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="9106c-108">接著<xref:System.Windows.Controls.TextBlock> , 您可以將控制項系結至中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的物件, 如包含`<TextBlock>`專案的反白顯示程式程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9106c-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="9106c-109">或者, 您可以使用<xref:System.Windows.Data.ObjectDataProvider>類別, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="9106c-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="9106c-110">您可以用相同方式定義系結, 如包含`<TextBlock>`專案的反白顯示行所示。</span><span class="sxs-lookup"><span data-stu-id="9106c-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="9106c-111">在此特定範例中, 結果相同: 您有<xref:System.Windows.Controls.TextBlock>具有文字內容`Joe`的。</span><span class="sxs-lookup"><span data-stu-id="9106c-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="9106c-112">不過, <xref:System.Windows.Data.ObjectDataProvider>類別會提供功能, 例如能夠系結至方法的結果。</span><span class="sxs-lookup"><span data-stu-id="9106c-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="9106c-113">如果您需要它所提供<xref:System.Windows.Data.ObjectDataProvider>的功能, 您可以選擇使用類別。</span><span class="sxs-lookup"><span data-stu-id="9106c-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="9106c-114">不過, 如果您要系結至已建立的物件, 您需要`DataContext`在程式碼中設定, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9106c-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="9106c-115">若要[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.Data.XmlDataProvider>使用類別存取資料以進行系結, 請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 XML 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9106c-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="9106c-116">若要[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.Data.ObjectDataProvider>使用類別存取要系結的資料, 請參閱系結[至 XDocument、system.xml.linq.xelement> 或 LINQ for XML 查詢結果](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。</span><span class="sxs-lookup"><span data-stu-id="9106c-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="9106c-117">如需您可以指定所系結之資料的許多方法的詳細資訊, 請參閱指定系結[來源](how-to-specify-the-binding-source.md)。</span><span class="sxs-lookup"><span data-stu-id="9106c-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="9106c-118">如需您可以系結至哪些類型的資料, 或如何實作為系結的通用語言執行平臺 (CLR) 物件的相關資訊, 請參閱系結[來源總覽](binding-sources-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9106c-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9106c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9106c-119">See also</span></span>

- [<span data-ttu-id="9106c-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="9106c-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9106c-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="9106c-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
