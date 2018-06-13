---
title: 操作說明：使用 DockPanel 元素分割空間
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
ms.openlocfilehash: 6b10fbcd14236f9259dc5772e7f8763c1602d0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553880"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="d5a24-102">操作說明：使用 DockPanel 元素分割空間</span><span class="sxs-lookup"><span data-stu-id="d5a24-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="d5a24-103">下列範例會建立簡單[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]framework 使用<xref:System.Windows.Controls.DockPanel>項目。</span><span class="sxs-lookup"><span data-stu-id="d5a24-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="d5a24-104"><xref:System.Windows.Controls.DockPanel>分割可用空間其子項目。</span><span class="sxs-lookup"><span data-stu-id="d5a24-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a24-105">範例</span><span class="sxs-lookup"><span data-stu-id="d5a24-105">Example</span></span>  
 <span data-ttu-id="d5a24-106">這個範例會使用<xref:System.Windows.Controls.DockPanel.Dock%2A>屬性，這是附加的屬性，若要將相同的兩個停駐<xref:System.Windows.Controls.Border>位於項目<xref:System.Windows.Controls.Dock.Top>的分割區的空間。</span><span class="sxs-lookup"><span data-stu-id="d5a24-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="d5a24-107">第三個<xref:System.Windows.Controls.Border>元素停駐於<xref:System.Windows.Controls.Dock.Left>，使用其寬度設定為 200 像素為單位。</span><span class="sxs-lookup"><span data-stu-id="d5a24-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="d5a24-108">第四個<xref:System.Windows.Controls.Border>停駐於<xref:System.Windows.Controls.Dock.Bottom>的螢幕。</span><span class="sxs-lookup"><span data-stu-id="d5a24-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="d5a24-109">最後一個<xref:System.Windows.Controls.Border>項目自動填滿剩餘的空間。</span><span class="sxs-lookup"><span data-stu-id="d5a24-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="d5a24-110">根據預設，最後一個子系<xref:System.Windows.Controls.DockPanel>項目填滿剩餘未配置空間。</span><span class="sxs-lookup"><span data-stu-id="d5a24-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="d5a24-111">如果您不想要有此行為，請設定 `LastChildFill="False"`。</span><span class="sxs-lookup"><span data-stu-id="d5a24-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="d5a24-112">編譯後的應用程式會產生一個看起來如下的新 UI。</span><span class="sxs-lookup"><span data-stu-id="d5a24-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="d5a24-113">![典型的 DockPanel 案例。](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="d5a24-113">![A typical DockPanel scenario.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a24-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5a24-114">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="d5a24-115">面板概觀</span><span class="sxs-lookup"><span data-stu-id="d5a24-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
