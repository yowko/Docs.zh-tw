---
title: HOW TO：繫結至列舉
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: db7b02a961c148bbdc31b05e7c71ea5b5d301c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586562"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="0eb56-102">HOW TO：繫結至列舉</span><span class="sxs-lookup"><span data-stu-id="0eb56-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="0eb56-103">此範例示範如何將繫結至繫結至列舉型別的 GetValues 方法來列舉型別。</span><span class="sxs-lookup"><span data-stu-id="0eb56-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eb56-104">範例</span><span class="sxs-lookup"><span data-stu-id="0eb56-104">Example</span></span>  
 <span data-ttu-id="0eb56-105">在下列範例中，<xref:System.Windows.Controls.ListBox>顯示的清單<xref:System.Windows.HorizontalAlignment>透過資料繫結的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0eb56-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="0eb56-106"><xref:System.Windows.Controls.ListBox>而<xref:System.Windows.Controls.Button>，您可以變更繫結<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性值<xref:System.Windows.Controls.Button>選取中的值<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="0eb56-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="0eb56-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eb56-107">See also</span></span>
- [<span data-ttu-id="0eb56-108">繫結至方法</span><span class="sxs-lookup"><span data-stu-id="0eb56-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)
- [<span data-ttu-id="0eb56-109">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="0eb56-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="0eb56-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="0eb56-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
