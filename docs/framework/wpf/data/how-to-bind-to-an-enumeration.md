---
title: 如何：繫結至列舉
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454448"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="8fe90-102">如何：繫結至列舉</span><span class="sxs-lookup"><span data-stu-id="8fe90-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="8fe90-103">這個範例示範如何系結至列舉的 GetValues 方法，以系結至列舉。</span><span class="sxs-lookup"><span data-stu-id="8fe90-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fe90-104">範例</span><span class="sxs-lookup"><span data-stu-id="8fe90-104">Example</span></span>  
 <span data-ttu-id="8fe90-105">在下列範例中，<xref:System.Windows.Controls.ListBox> 會透過資料系結顯示 <xref:System.Windows.HorizontalAlignment> 列舉值的清單。</span><span class="sxs-lookup"><span data-stu-id="8fe90-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="8fe90-106"><xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.Button> 系結，讓您可以藉由選取 <xref:System.Windows.Controls.ListBox>中的值來變更 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="8fe90-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="8fe90-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fe90-107">See also</span></span>

- [<span data-ttu-id="8fe90-108">繫結至方法</span><span class="sxs-lookup"><span data-stu-id="8fe90-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="8fe90-109">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="8fe90-109">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8fe90-110">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="8fe90-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
