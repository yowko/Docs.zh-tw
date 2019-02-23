---
title: HOW TO：繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 67d81c02ca7a207a48190a3bf09b6ab5dbec17de
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746399"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="78991-102">HOW TO：繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ</span><span class="sxs-lookup"><span data-stu-id="78991-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="78991-103">此範例示範如何繫結至 XML 資料<xref:System.Windows.Controls.ItemsControl>使用<xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="78991-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78991-104">範例</span><span class="sxs-lookup"><span data-stu-id="78991-104">Example</span></span>  
 <span data-ttu-id="78991-105">下列 XAML 程式碼定義<xref:System.Windows.Controls.ItemsControl>，並包含類型之資料的資料範本`Planet`在`http://planetsNS`XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="78991-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="78991-106">佔用命名空間的 XML 資料類型必須將命名空間放在大括號中，而如果它出現在 XAML 標記延伸可能出現的位置，則必須在命名空間前面加上大括號逸出序列。</span><span class="sxs-lookup"><span data-stu-id="78991-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="78991-107">此程式碼會繫結至動態屬性都對應於<xref:System.Xml.Linq.XContainer.Element%2A>並<xref:System.Xml.Linq.XElement.Attribute%2A>方法<xref:System.Xml.Linq.XElement>類別。</span><span class="sxs-lookup"><span data-stu-id="78991-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="78991-108">動態屬性可以讓 XAML 繫結至共用方法名稱的動態屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="78991-109">若要深入了解，請參閱 [LINQ to XML 動態屬性](/visualstudio/designers/linq-to-xml-dynamic-properties)。</span><span class="sxs-lookup"><span data-stu-id="78991-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="78991-110">請注意，XML 的預設命名空間宣告不適用於屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="78991-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="78991-111">下列 C# 程式碼會呼叫<xref:System.Xml.Linq.XDocument.Load%2A>並將堆疊面板資料內容設定為具名項目的所有子元素`SolarSystemPlanets`在`http://planetsNS`XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="78991-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="78991-112">XML 資料可以儲存為 XAML 資源使用<xref:System.Windows.Data.ObjectDataProvider>。</span><span class="sxs-lookup"><span data-stu-id="78991-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="78991-113">如需完整範例，請參閱 < [L2DBForm.xaml 來源程式碼](/visualstudio/designers/l2dbform-xaml-source-code)。</span><span class="sxs-lookup"><span data-stu-id="78991-113">For a complete example, see  [L2DBForm.xaml source code](/visualstudio/designers/l2dbform-xaml-source-code).</span></span> <span data-ttu-id="78991-114">下列範例顯示程式碼如何將資料內容設定為物件資源。</span><span class="sxs-lookup"><span data-stu-id="78991-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="78991-115">動態屬性都對應至<xref:System.Xml.Linq.XContainer.Element%2A>和<xref:System.Xml.Linq.XElement.Attribute%2A>提供 XAML 中的彈性。</span><span class="sxs-lookup"><span data-stu-id="78991-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="78991-116">您的程式碼也可以繫結至 LINQ for XML 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="78991-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="78991-117">此範例會繫結至依照元素值排序的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="78991-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="78991-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78991-118">See also</span></span>
- [<span data-ttu-id="78991-119">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="78991-119">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [<span data-ttu-id="78991-120">WPF 資料繫結與 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="78991-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [<span data-ttu-id="78991-121">使用 LINQ to XML 的 WPF 資料繫結範例</span><span class="sxs-lookup"><span data-stu-id="78991-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [<span data-ttu-id="78991-122">LINQ to XML 動態屬性</span><span class="sxs-lookup"><span data-stu-id="78991-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
