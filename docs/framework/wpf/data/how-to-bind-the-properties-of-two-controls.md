---
title: 操作說明：繫結兩個控制項的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459176"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="f773d-102">操作說明：繫結兩個控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="f773d-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="f773d-103">這個範例會示範如何使用 <xref:System.Windows.Data.Binding.ElementName%2A> 屬性，將一個具現化控制項的屬性系結至另一個實例的屬性。</span><span class="sxs-lookup"><span data-stu-id="f773d-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f773d-104">範例</span><span class="sxs-lookup"><span data-stu-id="f773d-104">Example</span></span>  
 <span data-ttu-id="f773d-105">下列範例顯示如何將 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Panel.Background%2A> 屬性系結至 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>。<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="f773d-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="f773d-106"><xref:System.Windows.Controls.ComboBox>的屬性：</span><span class="sxs-lookup"><span data-stu-id="f773d-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="f773d-107">此範例轉譯後會如同以下所示︰</span><span class="sxs-lookup"><span data-stu-id="f773d-107">When this example is rendered it looks like the following:</span></span>  
  
![螢幕擷取畫面：顯示已選取綠色值和綠色方形的下拉式方塊。](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="f773d-109">系結目標屬性（在此範例中為 <xref:System.Windows.Controls.Panel.Background%2A> 屬性）必須是相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="f773d-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="f773d-110">如需詳細資訊，請參閱 [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f773d-110">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f773d-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="f773d-111">See also</span></span>

- [<span data-ttu-id="f773d-112">指定繫結來源</span><span class="sxs-lookup"><span data-stu-id="f773d-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="f773d-113">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="f773d-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
