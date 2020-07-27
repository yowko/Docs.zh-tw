---
title: 如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
description: 瞭解如何使用 SelectedValue 和 SelectedValuePath 屬性，為 Windows Presentation Foundation TreeView 的 SelectedItem 指定值。
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
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166276"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="fcc78-103">如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem</span><span class="sxs-lookup"><span data-stu-id="fcc78-103">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="fcc78-104">這個範例會示範如何使用 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 和 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性來指定 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 的值 <xref:System.Windows.Controls.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-104">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcc78-105">範例</span><span class="sxs-lookup"><span data-stu-id="fcc78-105">Example</span></span>  
 <span data-ttu-id="fcc78-106"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性提供一種方法，可為 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 中的指定 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-106">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="fcc78-107"><xref:System.Windows.Controls.TreeView.SelectedItem%2A>表示集合中的物件 <xref:System.Windows.Controls.ItemsControl.Items%2A> ，而則會 <xref:System.Windows.Controls.TreeView> 顯示所選取專案的單一屬性值。</span><span class="sxs-lookup"><span data-stu-id="fcc78-107">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="fcc78-108"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性會指定用來判斷屬性值的屬性路徑 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-108">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="fcc78-109">本主題中的範例將說明此概念。</span><span class="sxs-lookup"><span data-stu-id="fcc78-109">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="fcc78-110">下列範例 <xref:System.Windows.Data.XmlDataProvider> 會顯示包含員工資訊的。</span><span class="sxs-lookup"><span data-stu-id="fcc78-110">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="fcc78-111">下列範例 <xref:System.Windows.HierarchicalDataTemplate> 會定義，其會顯示的 `EmployeeName` 和 `EmployeeWorkDay` `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-111">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="fcc78-112">請注意， <xref:System.Windows.HierarchicalDataTemplate> 不會將指定 `EmployeeNumber` 為範本的一部分。</span><span class="sxs-lookup"><span data-stu-id="fcc78-112">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="fcc78-113">下列範例 <xref:System.Windows.Controls.TreeView> 會顯示，其使用先前定義的 <xref:System.Windows.HierarchicalDataTemplate> ，並將 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 屬性設定為 `EmployeeNumber` 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-113">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="fcc78-114">當您選取 `EmployeeName` 中的時 <xref:System.Windows.Controls.TreeView> ， <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 屬性會傳回對應于 `EmployeeInfo` 所選取的資料項目 `EmployeeName` 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-114">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="fcc78-115">不過，由於 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 這個的 <xref:System.Windows.Controls.TreeView> 是設定為 `EmployeeNumber` ，因此 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 會設定為 `EmployeeNumber` 。</span><span class="sxs-lookup"><span data-stu-id="fcc78-115">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="fcc78-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcc78-116">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="fcc78-117">TreeView 概觀</span><span class="sxs-lookup"><span data-stu-id="fcc78-117">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="fcc78-118">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="fcc78-118">How-to Topics</span></span>](treeview-how-to-topics.md)
