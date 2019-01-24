---
title: HOW TO：使用含階層式 XML 資料的主從式模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 4beb2377fa9740e5103df0a82cfda9bd5f6f4769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550061"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="91402-102">HOW TO：使用含階層式 XML 資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="91402-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="91402-103">此範例示範如何實作主從式案例[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料。</span><span class="sxs-lookup"><span data-stu-id="91402-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91402-104">範例</span><span class="sxs-lookup"><span data-stu-id="91402-104">Example</span></span>  
 <span data-ttu-id="91402-105">此範例中是[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]中所討論的範例資料版本[使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="91402-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="91402-106">在此範例中的資料是從檔案`League.xml`。</span><span class="sxs-lookup"><span data-stu-id="91402-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="91402-107">請注意如何第三個<xref:System.Windows.Controls.ListBox>控制項中第二個追蹤選取範圍變更<xref:System.Windows.Controls.ListBox>繫結至其<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="91402-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="91402-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91402-108">See also</span></span>
- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="91402-109">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="91402-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
