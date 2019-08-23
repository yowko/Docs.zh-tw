---
title: 作法：使用 DockPanel 元素分割空間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960191"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="e80cb-102">作法：使用 DockPanel 元素分割空間</span><span class="sxs-lookup"><span data-stu-id="e80cb-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="e80cb-103">下列範例會<xref:System.Windows.Controls.DockPanel>使用元素來[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]建立簡單的架構。</span><span class="sxs-lookup"><span data-stu-id="e80cb-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="e80cb-104">分割<xref:System.Windows.Controls.DockPanel>區的可用空間可供其子項目使用。</span><span class="sxs-lookup"><span data-stu-id="e80cb-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e80cb-105">範例</span><span class="sxs-lookup"><span data-stu-id="e80cb-105">Example</span></span>  
 <span data-ttu-id="e80cb-106">這個範例會使用<xref:System.Windows.Controls.DockPanel.Dock%2A>屬性 (也就是附加屬性), 將兩個<xref:System.Windows.Controls.Border>完全相同的<xref:System.Windows.Controls.Dock.Top>元素固定在分割空間的上。</span><span class="sxs-lookup"><span data-stu-id="e80cb-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="e80cb-107">第三<xref:System.Windows.Controls.Border>個元素停駐<xref:System.Windows.Controls.Dock.Left>于, 其寬度設定為200圖元。</span><span class="sxs-lookup"><span data-stu-id="e80cb-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="e80cb-108">第四<xref:System.Windows.Controls.Border>個<xref:System.Windows.Controls.Dock.Bottom>停駐在螢幕的上。</span><span class="sxs-lookup"><span data-stu-id="e80cb-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="e80cb-109">最後一個<xref:System.Windows.Controls.Border>元素會自動填滿剩餘的空間。</span><span class="sxs-lookup"><span data-stu-id="e80cb-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> <span data-ttu-id="e80cb-110">根據預設, <xref:System.Windows.Controls.DockPanel>元素的最後一個子系會填滿剩餘的未配置空間。</span><span class="sxs-lookup"><span data-stu-id="e80cb-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="e80cb-111">如果您不想要有此行為，請設定 `LastChildFill="False"`。</span><span class="sxs-lookup"><span data-stu-id="e80cb-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="e80cb-112">編譯後的應用程式會產生一個看起來如下的新 UI。</span><span class="sxs-lookup"><span data-stu-id="e80cb-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="e80cb-113">![典型的 DockPanel 案例。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="e80cb-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80cb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e80cb-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="e80cb-115">面板概觀</span><span class="sxs-lookup"><span data-stu-id="e80cb-115">Panels Overview</span></span>](panels-overview.md)
