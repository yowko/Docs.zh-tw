---
title: 如何：使用含階層式 XML 資料的主從式模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733422"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="8a764-102">如何：使用含階層式 XML 資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="8a764-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="8a764-103">這個範例示範如何使用 XML 資料來執行主版詳細案例。</span><span class="sxs-lookup"><span data-stu-id="8a764-103">This example shows how to implement the master-detail scenario with XML data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a764-104">範例</span><span class="sxs-lookup"><span data-stu-id="8a764-104">Example</span></span>  
 <span data-ttu-id="8a764-105">這個範例是[使用具有階層式資料的主版詳細模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)中所討論之範例的 XML 資料版本。</span><span class="sxs-lookup"><span data-stu-id="8a764-105">This example is the XML data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="8a764-106">在此範例中，資料來自 `League.xml`的檔案。</span><span class="sxs-lookup"><span data-stu-id="8a764-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="8a764-107">請注意第三個 <xref:System.Windows.Controls.ListBox> 控制項如何藉由系結至其 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性來追蹤第二個 <xref:System.Windows.Controls.ListBox> 中的選取範圍變更。</span><span class="sxs-lookup"><span data-stu-id="8a764-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="8a764-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a764-108">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="8a764-109">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="8a764-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
