---
title: 如何：建立 ListView 的自訂檢視模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243215"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="c0374-102">如何:為清單檢視建立自訂檢視模式</span><span class="sxs-lookup"><span data-stu-id="c0374-102">How to: Create a custom view mode for a ListView</span></span>

<span data-ttu-id="c0374-103">此示例演示如何為<xref:System.Windows.Controls.ListView.View%2A><xref:System.Windows.Controls.ListView>控制項創建自定義模式。</span><span class="sxs-lookup"><span data-stu-id="c0374-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0374-104">範例</span><span class="sxs-lookup"><span data-stu-id="c0374-104">Example</span></span>  
 <span data-ttu-id="c0374-105">在為<xref:System.Windows.Controls.ListView>控制項創建自訂<xref:System.Windows.Controls.ViewBase>檢視時,必須使用該類。</span><span class="sxs-lookup"><span data-stu-id="c0374-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="c0374-106">下面的範例顯示從類別的稱為`PlainView`檢視模式<xref:System.Windows.Controls.ViewBase>。</span><span class="sxs-lookup"><span data-stu-id="c0374-106">The following example shows a view mode called `PlainView` that's derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="c0374-107">要將樣式應用於自訂檢視,請使用類別<xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="c0374-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="c0374-108">下面的範例為`PlainView`檢視模式定義<xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="c0374-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="c0374-109">在前面的範例中,此樣式設置為為<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>`PlainView`定義的屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c0374-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that's defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="c0374-110">要在自訂檢視模式下定義資料的佈局,請定義物件<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="c0374-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="c0374-111">下面的範例定義可用於在<xref:System.Windows.DataTemplate>`PlainView`檢視模式下顯示資料的 。</span><span class="sxs-lookup"><span data-stu-id="c0374-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="c0374-112">下面的範例展示如何<xref:System.Windows.ResourceKey>`PlainView`為使用上一個範例中定義<xref:System.Windows.DataTemplate>的檢視模式定義 。</span><span class="sxs-lookup"><span data-stu-id="c0374-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="c0374-113">如果將<xref:System.Windows.Controls.ListView>屬性設置為資源鍵<xref:System.Windows.Controls.ListView.View%2A>, 則控件可以使用自定義檢視。</span><span class="sxs-lookup"><span data-stu-id="c0374-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="c0374-114">下面的範例展示如何`PlainView`指定為的檢視模式<xref:System.Windows.Controls.ListView>。</span><span class="sxs-lookup"><span data-stu-id="c0374-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="c0374-115">有關完整範例,請參閱[具有多個檢視的清單檢視 (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp)或[具有多個視圖的清單檢視(可視基本檢視)。](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)</span><span class="sxs-lookup"><span data-stu-id="c0374-115">For the complete sample, see [ListView with Multiple Views (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0374-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0374-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="c0374-117">如何主題</span><span class="sxs-lookup"><span data-stu-id="c0374-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="c0374-118">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="c0374-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="c0374-119">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="c0374-119">GridView Overview</span></span>](gridview-overview.md)
