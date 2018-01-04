---
title: "如何：讓資料可於 XAML 中繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c342f0d635a9220a88a2af79c76e2c1580dee2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="1034e-102">如何：讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="1034e-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="1034e-103">本主題討論您可以將資料繫結中的不同方式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，視您的應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="1034e-103">This topic discusses the different ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1034e-104">範例</span><span class="sxs-lookup"><span data-stu-id="1034e-104">Example</span></span>  
 <span data-ttu-id="1034e-105">如果您有[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件您想要從繫結到[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以將物件提供的繫結是定義為資源，並提供給它的其中一種方式`x:Key`。</span><span class="sxs-lookup"><span data-stu-id="1034e-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="1034e-106">在下列範例中，您必須`Person`物件具有名為字串屬性`PersonName`。</span><span class="sxs-lookup"><span data-stu-id="1034e-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="1034e-107">`Person`物件定義在命名空間稱為`SDKSample`。</span><span class="sxs-lookup"><span data-stu-id="1034e-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="1034e-108">您可以再繫結中的物件至[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1034e-108">You can then bind to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as shown in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="1034e-109">或者，您可以使用<xref:System.Windows.Data.ObjectDataProvider>類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1034e-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 <span data-ttu-id="1034e-110">定義繫結相同的方式：</span><span class="sxs-lookup"><span data-stu-id="1034e-110">You define the binding the same way:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="1034e-111">在這個範例中，結果都相同： 您有<xref:System.Windows.Controls.TextBlock>以文字內容`Joe`。</span><span class="sxs-lookup"><span data-stu-id="1034e-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="1034e-112">不過，<xref:System.Windows.Data.ObjectDataProvider>類別提供的功能，例如可以繫結至方法的結果。</span><span class="sxs-lookup"><span data-stu-id="1034e-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="1034e-113">您可以選擇使用<xref:System.Windows.Data.ObjectDataProvider>類別，如果您需要它所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="1034e-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="1034e-114">不過，如果您要繫結至已建立的物件，您需要設定`DataContext`在程式碼，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1034e-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="1034e-115">若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料繫結使用<xref:System.Windows.Data.XmlDataProvider>類別，請參閱[XMLDataProvider 和 XPath 查詢來使用 XML 資料繫結](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="1034e-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="1034e-116">若要存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料繫結使用<xref:System.Windows.Data.ObjectDataProvider>類別，請參閱[for XML 查詢結果繫結至 XDocument、 XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。</span><span class="sxs-lookup"><span data-stu-id="1034e-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="1034e-117">如需不同的方式。 您可以指定您要繫結的資料，請參閱[指定繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)。</span><span class="sxs-lookup"><span data-stu-id="1034e-117">For information about the different ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="1034e-118">如需哪些資料型別可以繫結或如何實作您自己[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件繫結，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1034e-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1034e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1034e-119">See Also</span></span>  
 [<span data-ttu-id="1034e-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="1034e-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1034e-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="1034e-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
