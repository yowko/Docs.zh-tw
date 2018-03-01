---
title: "如何：將樹狀檢視繫結至未知深度的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be21ecb75420b6499e5b95d5f4d93a5f079f9646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a><span data-ttu-id="cd13f-102">如何：將樹狀檢視繫結至未知深度的資料</span><span class="sxs-lookup"><span data-stu-id="cd13f-102">How to: Bind a TreeView to Data That Has an Indeterminable Depth</span></span>
<span data-ttu-id="cd13f-103">有時當您想要繫結<xref:System.Windows.Controls.TreeView>深度不知道資料來源。</span><span class="sxs-lookup"><span data-stu-id="cd13f-103">There might be times when you want to bind a <xref:System.Windows.Controls.TreeView> to a data source whose depth is not known.</span></span>  <span data-ttu-id="cd13f-104">發生這個問題的資料是遞迴的本質，例如檔案系統，其中的資料夾可以包含資料夾或公司的組織結構，其中員工的直屬員工的其他員工。</span><span class="sxs-lookup"><span data-stu-id="cd13f-104">This can occur when the data is recursive in nature, such as a file system, where folders can contain folders, or a company's organizational structure, where employees have other employees as direct reports.</span></span>  
  
 <span data-ttu-id="cd13f-105">資料來源必須具有階層式物件模型。</span><span class="sxs-lookup"><span data-stu-id="cd13f-105">The data source must have a hierarchical object model.</span></span> <span data-ttu-id="cd13f-106">例如，`Employee`類別可能包含員工的直屬員工的員工物件的集合。</span><span class="sxs-lookup"><span data-stu-id="cd13f-106">For example, an `Employee` class might contain a collection of Employee objects that are the direct reports of an employee.</span></span> <span data-ttu-id="cd13f-107">如果資料以不是階層式的方式表示，您必須建置資料的階層式表示法。</span><span class="sxs-lookup"><span data-stu-id="cd13f-107">If the data is represented in a way that is not hierarchical, you must build a hierarchical representation of the data.</span></span>  
  
 <span data-ttu-id="cd13f-108">當您將<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType>屬性，而且當<xref:System.Windows.Controls.ItemsControl>產生<xref:System.Windows.Controls.ItemsControl>每個子項目，則子系<xref:System.Windows.Controls.ItemsControl>會使用相同<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>做為父系。</span><span class="sxs-lookup"><span data-stu-id="cd13f-108">When you set the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> property and if the <xref:System.Windows.Controls.ItemsControl> generates an <xref:System.Windows.Controls.ItemsControl> for each child item, then the child <xref:System.Windows.Controls.ItemsControl> uses the same <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> as the parent.</span></span> <span data-ttu-id="cd13f-109">例如，如果您設定<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>資料繫結上的屬性<xref:System.Windows.Controls.TreeView>，每個<xref:System.Windows.Controls.TreeViewItem>也就是產生的使用<xref:System.Windows.DataTemplate>，已指派給<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="cd13f-109">For example, if you set the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property on a data-bound <xref:System.Windows.Controls.TreeView>, each <xref:System.Windows.Controls.TreeViewItem> that is generated uses the <xref:System.Windows.DataTemplate> that was assigned to the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property of the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="cd13f-110"><xref:System.Windows.HierarchicalDataTemplate>可讓您指定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.TreeViewItem>，或任何<xref:System.Windows.Controls.HeaderedItemsControl>，資料範本。</span><span class="sxs-lookup"><span data-stu-id="cd13f-110">The <xref:System.Windows.HierarchicalDataTemplate> enables you to specify the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for a <xref:System.Windows.Controls.TreeViewItem>, or any <xref:System.Windows.Controls.HeaderedItemsControl>, on the data template.</span></span> <span data-ttu-id="cd13f-111">當您將<xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType>屬性的值時使用<xref:System.Windows.HierarchicalDataTemplate>套用。</span><span class="sxs-lookup"><span data-stu-id="cd13f-111">When you set the <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> property, that value is used when the <xref:System.Windows.HierarchicalDataTemplate> is applied.</span></span> <span data-ttu-id="cd13f-112">使用<xref:System.Windows.HierarchicalDataTemplate>，您可以以遞迴方式組<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>每個<xref:System.Windows.Controls.TreeViewItem>中<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="cd13f-112">By using a <xref:System.Windows.HierarchicalDataTemplate>, you can recursively set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for each <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd13f-113">範例</span><span class="sxs-lookup"><span data-stu-id="cd13f-113">Example</span></span>  
 <span data-ttu-id="cd13f-114">下列範例示範如何將繫結<xref:System.Windows.Controls.TreeView>階層式資料和使用<xref:System.Windows.HierarchicalDataTemplate>指定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>每個<xref:System.Windows.Controls.TreeViewItem>。</span><span class="sxs-lookup"><span data-stu-id="cd13f-114">The following example demonstrates how to bind a <xref:System.Windows.Controls.TreeView> to hierarchical data and use a <xref:System.Windows.HierarchicalDataTemplate> to specify the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for each <xref:System.Windows.Controls.TreeViewItem>.</span></span>  <span data-ttu-id="cd13f-115"><xref:System.Windows.Controls.TreeView>繫結至 XML 資料表示公司的員工。</span><span class="sxs-lookup"><span data-stu-id="cd13f-115">The <xref:System.Windows.Controls.TreeView> binds to XML data that represents the employees in a company.</span></span>  <span data-ttu-id="cd13f-116">每個`Employee`元素可包含其他`Employee`表示人員報告對項目。</span><span class="sxs-lookup"><span data-stu-id="cd13f-116">Each `Employee` element can contain other `Employee` elements to indicate who reports to whom.</span></span> <span data-ttu-id="cd13f-117">因為資料是遞迴，<xref:System.Windows.HierarchicalDataTemplate>可以套用至每個層級。</span><span class="sxs-lookup"><span data-stu-id="cd13f-117">Because the data is recursive, the <xref:System.Windows.HierarchicalDataTemplate> can be applied to each level.</span></span>  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cd13f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd13f-118">See Also</span></span>  
 [<span data-ttu-id="cd13f-119">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="cd13f-119">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="cd13f-120">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="cd13f-120">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
