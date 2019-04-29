---
title: HOW TO：使用範本為使用 GridView 的 ListView 設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 1caa652c4a2a3a7d0a8d40fe703df7a3e8038c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699119"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="f40fc-102">HOW TO：使用範本為使用 GridView 的 ListView 設定樣式</span><span class="sxs-lookup"><span data-stu-id="f40fc-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="f40fc-103">此範例示範如何使用<xref:System.Windows.DataTemplate>並<xref:System.Windows.Style>物件，以指定的外觀<xref:System.Windows.Controls.ListView>使用的控制項<xref:System.Windows.Controls.GridView>檢視模式。</span><span class="sxs-lookup"><span data-stu-id="f40fc-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f40fc-104">範例</span><span class="sxs-lookup"><span data-stu-id="f40fc-104">Example</span></span>  
 <span data-ttu-id="f40fc-105">下列範例所示<xref:System.Windows.Style>並<xref:System.Windows.DataTemplate>物件的自訂資料行標題的外觀<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="f40fc-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="f40fc-106">下列範例示範如何使用這些<xref:System.Windows.Style>並<xref:System.Windows.DataTemplate>設定為<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>並<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>的屬性<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="f40fc-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="f40fc-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性會定義資料行儲存格的內容。</span><span class="sxs-lookup"><span data-stu-id="f40fc-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="f40fc-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>並<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>只有兩種數個屬性，您可以使用自訂資料行的標頭外觀<xref:System.Windows.Controls.GridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f40fc-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="f40fc-109">如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](gridview-column-header-styles-and-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f40fc-109">For more information, see [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="f40fc-110">下列範例示範如何定義<xref:System.Windows.DataTemplate>的自訂中的資料格的外觀<xref:System.Windows.Controls.GridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="f40fc-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="f40fc-111">下列範例示範如何使用這<xref:System.Windows.DataTemplate>定義的內容<xref:System.Windows.Controls.GridViewColumn>資料格。</span><span class="sxs-lookup"><span data-stu-id="f40fc-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="f40fc-112">而不是使用此範本<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性顯示在上一個<xref:System.Windows.Controls.GridViewColumn>範例。</span><span class="sxs-lookup"><span data-stu-id="f40fc-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="f40fc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f40fc-113">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="f40fc-114">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="f40fc-114">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="f40fc-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="f40fc-115">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="f40fc-116">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="f40fc-116">ListView Overview</span></span>](listview-overview.md)
