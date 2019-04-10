---
title: HOW TO：使用 SelectedValue、SelectedValuePath 和 SelectedItem
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169698"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="4ecc8-102">HOW TO：使用 SelectedValue、SelectedValuePath 和 SelectedItem</span><span class="sxs-lookup"><span data-stu-id="4ecc8-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="4ecc8-103">此範例示範如何使用<xref:System.Windows.Controls.TreeView.SelectedValue%2A>並<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性，以指定的值<xref:System.Windows.Controls.TreeView.SelectedItem%2A>的<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ecc8-104">範例</span><span class="sxs-lookup"><span data-stu-id="4ecc8-104">Example</span></span>  
 <span data-ttu-id="4ecc8-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會提供方法來指定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>for<xref:System.Windows.Controls.TreeView.SelectedItem%2A>在<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="4ecc8-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A>表示中的物件<xref:System.Windows.Controls.ItemsControl.Items%2A>集合和<xref:System.Windows.Controls.TreeView>顯示選取項目的單一屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="4ecc8-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會指定用來判斷的值屬性的路徑<xref:System.Windows.Controls.TreeView.SelectedValue%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="4ecc8-108">本主題中的範例將說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="4ecc8-109">下列範例所示<xref:System.Windows.Data.XmlDataProvider>包含員工資訊。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="4ecc8-110">下列範例會定義<xref:System.Windows.HierarchicalDataTemplate>會顯示`EmployeeName`並`EmployeeWorkDay`的`Employee`。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="4ecc8-111">請注意，<xref:System.Windows.HierarchicalDataTemplate>未指定`EmployeeNumber`為範本的一部分。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="4ecc8-112">下列範例所示<xref:System.Windows.Controls.TreeView>使用先前定義<xref:System.Windows.HierarchicalDataTemplate>，並可設定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>屬性設`EmployeeNumber`。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="4ecc8-113">當您選取`EmployeeName`中<xref:System.Windows.Controls.TreeView>，則<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性會傳回`EmployeeInfo`對應至所選的資料項目`EmployeeName`。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="4ecc8-114">不過，因為<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>這個<xref:System.Windows.Controls.TreeView>設為`EmployeeNumber`，則<xref:System.Windows.Controls.TreeView.SelectedValue%2A>設定為`EmployeeNumber`。</span><span class="sxs-lookup"><span data-stu-id="4ecc8-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="4ecc8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ecc8-115">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="4ecc8-116">TreeView 概觀</span><span class="sxs-lookup"><span data-stu-id="4ecc8-116">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="4ecc8-117">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="4ecc8-117">How-to Topics</span></span>](treeview-how-to-topics.md)
