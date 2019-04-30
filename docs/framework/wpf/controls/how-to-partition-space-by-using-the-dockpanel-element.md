---
title: HOW TO：使用 DockPanel 元素分割空間
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
ms.openlocfilehash: ab51270644bf370944ebc933c765b40c528681c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052179"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="67531-102">HOW TO：使用 DockPanel 元素分割空間</span><span class="sxs-lookup"><span data-stu-id="67531-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="67531-103">下列範例會建立簡易[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]framework 使用<xref:System.Windows.Controls.DockPanel>項目。</span><span class="sxs-lookup"><span data-stu-id="67531-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="67531-104"><xref:System.Windows.Controls.DockPanel>分割可用空間，其子項目。</span><span class="sxs-lookup"><span data-stu-id="67531-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67531-105">範例</span><span class="sxs-lookup"><span data-stu-id="67531-105">Example</span></span>  
 <span data-ttu-id="67531-106">這個範例會使用<xref:System.Windows.Controls.DockPanel.Dock%2A>屬性，這是附加的屬性，將相同的兩個停駐<xref:System.Windows.Controls.Border>項目<xref:System.Windows.Controls.Dock.Top>的資料分割的空間。</span><span class="sxs-lookup"><span data-stu-id="67531-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="67531-107">第三個<xref:System.Windows.Controls.Border>元素會固定至<xref:System.Windows.Controls.Dock.Left>，使用其寬度設定為 200 像素。</span><span class="sxs-lookup"><span data-stu-id="67531-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="67531-108">第四個<xref:System.Windows.Controls.Border>停駐於<xref:System.Windows.Controls.Dock.Bottom>的畫面。</span><span class="sxs-lookup"><span data-stu-id="67531-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="67531-109">最後一個<xref:System.Windows.Controls.Border>項目會自動填滿剩餘的空間。</span><span class="sxs-lookup"><span data-stu-id="67531-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="67531-110">根據預設，最後一個子系<xref:System.Windows.Controls.DockPanel>項目填滿剩餘的未配置空間。</span><span class="sxs-lookup"><span data-stu-id="67531-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="67531-111">如果您不想要有此行為，請設定 `LastChildFill="False"`。</span><span class="sxs-lookup"><span data-stu-id="67531-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="67531-112">編譯後的應用程式會產生一個看起來如下的新 UI。</span><span class="sxs-lookup"><span data-stu-id="67531-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="67531-113">![典型的 DockPanel 案例。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="67531-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67531-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67531-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="67531-115">面板概觀</span><span class="sxs-lookup"><span data-stu-id="67531-115">Panels Overview</span></span>](panels-overview.md)
