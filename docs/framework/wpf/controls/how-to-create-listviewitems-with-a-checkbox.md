---
title: HOW TO：使用 CheckBox 建立 ListViewItems
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 1ed623495529609c83c0ced68bfc1696c29d4570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682238"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="9734f-102">HOW TO：使用 CheckBox 建立 ListViewItems</span><span class="sxs-lookup"><span data-stu-id="9734f-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="9734f-103">此範例示範如何顯示的資料行<xref:System.Windows.Controls.CheckBox>中的控制項<xref:System.Windows.Controls.ListView>使用的控制項<xref:System.Windows.Controls.GridView>。</span><span class="sxs-lookup"><span data-stu-id="9734f-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9734f-104">範例</span><span class="sxs-lookup"><span data-stu-id="9734f-104">Example</span></span>  
 <span data-ttu-id="9734f-105">若要建立包含的資料行<xref:System.Windows.Controls.CheckBox>中的控制項<xref:System.Windows.Controls.ListView>，建立<xref:System.Windows.DataTemplate>包含<xref:System.Windows.Controls.CheckBox>。</span><span class="sxs-lookup"><span data-stu-id="9734f-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="9734f-106">然後設定<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>的<xref:System.Windows.Controls.GridViewColumn>至<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="9734f-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="9734f-107">下列範例所示<xref:System.Windows.DataTemplate>，其中包含<xref:System.Windows.Controls.CheckBox>。</span><span class="sxs-lookup"><span data-stu-id="9734f-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="9734f-108">此範例會將繫結<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>屬性<xref:System.Windows.Controls.CheckBox>要<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>屬性值為<xref:System.Windows.Controls.ListViewItem>包含它。</span><span class="sxs-lookup"><span data-stu-id="9734f-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="9734f-109">因此，當<xref:System.Windows.Controls.ListViewItem>，其中包含<xref:System.Windows.Controls.CheckBox>已選取，<xref:System.Windows.Controls.CheckBox>已核取。</span><span class="sxs-lookup"><span data-stu-id="9734f-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="9734f-110">下列範例示範如何建立的資料行<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="9734f-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="9734f-111">若要將資料行，範例會設定<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>的屬性<xref:System.Windows.Controls.GridViewColumn>至<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="9734f-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="9734f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9734f-112">See also</span></span>
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="9734f-113">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="9734f-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
- [<span data-ttu-id="9734f-114">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="9734f-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [<span data-ttu-id="9734f-115">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="9734f-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
