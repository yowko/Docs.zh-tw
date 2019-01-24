---
title: HOW TO：將 ListBox 繫結至資料
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 6d37cda057ea1e7ca6761363857a2647da37afee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650648"
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="fcd24-102">HOW TO：將 ListBox 繫結至資料</span><span class="sxs-lookup"><span data-stu-id="fcd24-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="fcd24-103">應用程式開發人員可以建立<xref:System.Windows.Controls.ListBox>不使用指定的每個內容控制項<xref:System.Windows.Controls.ListBoxItem>分開。</span><span class="sxs-lookup"><span data-stu-id="fcd24-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="fcd24-104">您可以使用資料繫結至資料繫結至個別的項目。</span><span class="sxs-lookup"><span data-stu-id="fcd24-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="fcd24-105">下列範例示範如何建立<xref:System.Windows.Controls.ListBox>填入<xref:System.Windows.Controls.ListBoxItem>藉由名為資料來源的資料繫結的項目*色彩*。</span><span class="sxs-lookup"><span data-stu-id="fcd24-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="fcd24-106">在此情況下不需要使用<xref:System.Windows.Controls.ListBoxItem>標記，以指定的每個項目內容。</span><span class="sxs-lookup"><span data-stu-id="fcd24-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcd24-107">範例</span><span class="sxs-lookup"><span data-stu-id="fcd24-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fcd24-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcd24-108">See also</span></span>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [<span data-ttu-id="fcd24-109">控制項</span><span class="sxs-lookup"><span data-stu-id="fcd24-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
