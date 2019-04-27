---
title: HOW TO：建立 ListView 的自訂檢視模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: de11250a2e7529fba3b262e42b6714262738fa90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910906"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="6b128-102">HOW TO：建立 ListView 的自訂檢視模式</span><span class="sxs-lookup"><span data-stu-id="6b128-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="6b128-103">此範例示範如何建立自訂<xref:System.Windows.Controls.ListView.View%2A>模式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="6b128-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b128-104">範例</span><span class="sxs-lookup"><span data-stu-id="6b128-104">Example</span></span>  
 <span data-ttu-id="6b128-105">您必須使用<xref:System.Windows.Controls.ViewBase>類別，在您建立的自訂檢視<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="6b128-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="6b128-106">下列範例示範呼叫的檢視模式`PlainView`，其係衍生自<xref:System.Windows.Controls.ViewBase>類別。</span><span class="sxs-lookup"><span data-stu-id="6b128-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="6b128-107">若要將樣式套用至自訂的檢視，使用<xref:System.Windows.Style>類別。</span><span class="sxs-lookup"><span data-stu-id="6b128-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="6b128-108">下列範例會定義<xref:System.Windows.Style>針對`PlainView`檢視模式。</span><span class="sxs-lookup"><span data-stu-id="6b128-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="6b128-109">在上述範例中，這個樣式設定的值<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>屬性所定義`PlainView`。</span><span class="sxs-lookup"><span data-stu-id="6b128-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="6b128-110">若要定義的資料配置的自訂檢視模式中，定義<xref:System.Windows.DataTemplate>物件。</span><span class="sxs-lookup"><span data-stu-id="6b128-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="6b128-111">下列範例會定義<xref:System.Windows.DataTemplate>，可以用來顯示資料在`PlainView`檢視模式。</span><span class="sxs-lookup"><span data-stu-id="6b128-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="6b128-112">下列範例示範如何定義<xref:System.Windows.ResourceKey>for`PlainView`使用的檢視模式<xref:System.Windows.DataTemplate>在上述範例中定義。</span><span class="sxs-lookup"><span data-stu-id="6b128-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="6b128-113">A<xref:System.Windows.Controls.ListView>控制項可以使用自訂的檢視，如果您將設定<xref:System.Windows.Controls.ListView.View%2A>資源索引鍵的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b128-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="6b128-114">下列範例示範如何指定`PlainView`做為檢視模式的<xref:System.Windows.Controls.ListView>。</span><span class="sxs-lookup"><span data-stu-id="6b128-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="6b128-115">如需完整的範例，請參閱[具有多個檢視的 ListView (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp)或[與多個 Views(Visual Basic) ListView](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)。</span><span class="sxs-lookup"><span data-stu-id="6b128-115">For the complete sample, see [ListView with Multiple Views(C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b128-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b128-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="6b128-117">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="6b128-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="6b128-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="6b128-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="6b128-119">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="6b128-119">GridView Overview</span></span>](gridview-overview.md)
