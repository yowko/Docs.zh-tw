---
title: 如何：建立 ListView 的自訂檢視模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: b8600a2e201fdbcb566e6a322e3ecdabbe1641ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551865"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="a973c-102">如何：建立 ListView 的自訂檢視模式</span><span class="sxs-lookup"><span data-stu-id="a973c-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="a973c-103">這個範例示範如何建立自訂<xref:System.Windows.Controls.ListView.View%2A>模式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="a973c-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a973c-104">範例</span><span class="sxs-lookup"><span data-stu-id="a973c-104">Example</span></span>  
 <span data-ttu-id="a973c-105">您必須使用<xref:System.Windows.Controls.ViewBase>類別時會建立的自訂檢視<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="a973c-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="a973c-106">下列範例示範呼叫的檢視模式`PlainView`，其衍生自<xref:System.Windows.Controls.ViewBase>類別。</span><span class="sxs-lookup"><span data-stu-id="a973c-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="a973c-107">若要將樣式套用至自訂的檢視，使用<xref:System.Windows.Style>類別。</span><span class="sxs-lookup"><span data-stu-id="a973c-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="a973c-108">下列範例會定義<xref:System.Windows.Style>如`PlainView`檢視模式。</span><span class="sxs-lookup"><span data-stu-id="a973c-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="a973c-109">在上一個範例中，設定此樣式的值為<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>屬性定義的`PlainView`。</span><span class="sxs-lookup"><span data-stu-id="a973c-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="a973c-110">若要在自訂檢視模式中定義的資料版面配置，定義<xref:System.Windows.DataTemplate>物件。</span><span class="sxs-lookup"><span data-stu-id="a973c-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="a973c-111">下列範例會定義<xref:System.Windows.DataTemplate>，可以用來顯示資料在`PlainView`檢視模式。</span><span class="sxs-lookup"><span data-stu-id="a973c-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="a973c-112">下列範例示範如何定義<xref:System.Windows.ResourceKey>如`PlainView`檢視模式中使用<xref:System.Windows.DataTemplate>前一個範例中定義的。</span><span class="sxs-lookup"><span data-stu-id="a973c-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="a973c-113">A<xref:System.Windows.Controls.ListView>控制項可以使用自訂的檢視，如果您設定<xref:System.Windows.Controls.ListView.View%2A>資源索引鍵的屬性。</span><span class="sxs-lookup"><span data-stu-id="a973c-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="a973c-114">下列範例示範如何指定`PlainView`作為檢視模式<xref:System.Windows.Controls.ListView>。</span><span class="sxs-lookup"><span data-stu-id="a973c-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="a973c-115">如需完整範例，請參閱[ListView 與多個檢視範例](http://go.microsoft.com/fwlink/?LinkID=160013)。</span><span class="sxs-lookup"><span data-stu-id="a973c-115">For the complete sample, see [ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a973c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a973c-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="a973c-117">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="a973c-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="a973c-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="a973c-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="a973c-119">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="a973c-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
