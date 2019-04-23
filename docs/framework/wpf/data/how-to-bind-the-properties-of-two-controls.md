---
title: HOW TO：繫結兩個控制項的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 0dd7b817b632758cfca8b5c45d88e333510485f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222056"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="9ba62-102">HOW TO：繫結兩個控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="9ba62-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="9ba62-103">此範例示範如何具現化控制項屬性繫結至另一個使用<xref:System.Windows.Data.Binding.ElementName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9ba62-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ba62-104">範例</span><span class="sxs-lookup"><span data-stu-id="9ba62-104">Example</span></span>  
 <span data-ttu-id="9ba62-105">下列範例示範如何繫結<xref:System.Windows.Controls.Panel.Background%2A>的屬性<xref:System.Windows.Controls.Canvas>至<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>。<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="9ba62-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="9ba62-106">屬性<xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="9ba62-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="9ba62-107">此範例轉譯後會如同以下所示︰</span><span class="sxs-lookup"><span data-stu-id="9ba62-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="9ba62-108">![具有綠色背景的畫布](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="9ba62-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="9ba62-109">**附註**繫結目標屬性 (在此範例中，<xref:System.Windows.Controls.Panel.Background%2A>屬性) 必須是相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9ba62-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="9ba62-110">如需詳細資訊，請參閱 [資料繫結概觀](data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9ba62-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba62-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ba62-111">See also</span></span>

- [<span data-ttu-id="9ba62-112">指定繫結來源</span><span class="sxs-lookup"><span data-stu-id="9ba62-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="9ba62-113">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="9ba62-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
