---
title: "操作說明：繫結兩個控制項的屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e79b1f9f00e8c76f94bf4386a284607f526624a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="0e1cc-102">操作說明：繫結兩個控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="0e1cc-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="0e1cc-103">這個範例示範如何將一個具現化的控制項屬性繫結至另一個使用<xref:System.Windows.Data.Binding.ElementName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0e1cc-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e1cc-104">範例</span><span class="sxs-lookup"><span data-stu-id="0e1cc-104">Example</span></span>  
 <span data-ttu-id="0e1cc-105">下列範例示範如何將繫結<xref:System.Windows.Controls.Panel.Background%2A>屬性<xref:System.Windows.Controls.Canvas>至<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>。<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="0e1cc-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="0e1cc-106">此範例轉譯後會如同以下所示︰</span><span class="sxs-lookup"><span data-stu-id="0e1cc-106">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="0e1cc-107">![具有綠色背景的畫布](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="0e1cc-107">![A canvas with a green background](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="0e1cc-108">**請注意**繫結目標屬性 (在此範例中，<xref:System.Windows.Controls.Panel.Background%2A>屬性) 必須是相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="0e1cc-108">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="0e1cc-109">如需詳細資訊，請參閱 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0e1cc-109">For more information, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1cc-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e1cc-110">See Also</span></span>  
 [<span data-ttu-id="0e1cc-111">指定繫結來源</span><span class="sxs-lookup"><span data-stu-id="0e1cc-111">Specify the Binding Source</span></span>](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [<span data-ttu-id="0e1cc-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="0e1cc-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
