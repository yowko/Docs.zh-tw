---
title: HOW TO：在 TableLayoutPanel 控制項中對齊和縮放控制項
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210369"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="acd95-102">HOW TO：在 TableLayoutPanel 控制項中對齊和縮放控制項</span><span class="sxs-lookup"><span data-stu-id="acd95-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>

<span data-ttu-id="acd95-103">您可以對齊和縮放控制項<xref:System.Windows.Forms.TableLayoutPanel>具有<xref:System.Windows.Forms.Control.Anchor%2A>和<xref:System.Windows.Forms.Control.Dock%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="acd95-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>

## <a name="align-and-stretch-a-control"></a><span data-ttu-id="acd95-104">對齊和縮放控制項</span><span class="sxs-lookup"><span data-stu-id="acd95-104">Align and stretch a control</span></span>

1. <span data-ttu-id="acd95-105">在 Visual Studio 中，拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acd95-105">In Visual Studio, drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="acd95-106">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的左上方儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="acd95-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="acd95-107"><xref:System.Windows.Forms.Button>控制項在儲存格中置中對齊。</span><span class="sxs-lookup"><span data-stu-id="acd95-107">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>

3. <span data-ttu-id="acd95-108">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Left,Right`。</span><span class="sxs-lookup"><span data-stu-id="acd95-108">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="acd95-109"><xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合儲存格的寬度。</span><span class="sxs-lookup"><span data-stu-id="acd95-109">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>

4. <span data-ttu-id="acd95-110">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Top,Bottom`。</span><span class="sxs-lookup"><span data-stu-id="acd95-110">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="acd95-111"><xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合資料格的高度。</span><span class="sxs-lookup"><span data-stu-id="acd95-111">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>

5. <span data-ttu-id="acd95-112">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="acd95-112">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="acd95-113"><xref:System.Windows.Forms.Button>展開以填滿儲存格的控制項。</span><span class="sxs-lookup"><span data-stu-id="acd95-113">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>

6. <span data-ttu-id="acd95-114">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.None>。</span><span class="sxs-lookup"><span data-stu-id="acd95-114">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="acd95-115"><xref:System.Windows.Forms.Button>控制項傳回至其原始大小，並將移至儲存格的左上角。</span><span class="sxs-lookup"><span data-stu-id="acd95-115">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="acd95-116">**Windows Form 設計工具**已設定<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Top, Left`。</span><span class="sxs-lookup"><span data-stu-id="acd95-116">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>

7. <span data-ttu-id="acd95-117">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Bottom,Right`。</span><span class="sxs-lookup"><span data-stu-id="acd95-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="acd95-118"><xref:System.Windows.Forms.Button>控制項移到儲存格右下角。</span><span class="sxs-lookup"><span data-stu-id="acd95-118">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>

8. <span data-ttu-id="acd95-119">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設<xref:System.Windows.Forms.AnchorStyles.None>。</span><span class="sxs-lookup"><span data-stu-id="acd95-119">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="acd95-120"><xref:System.Windows.Forms.Button>控制項移到儲存格的中央。</span><span class="sxs-lookup"><span data-stu-id="acd95-120">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>

## <a name="see-also"></a><span data-ttu-id="acd95-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd95-121">See also</span></span>

- [<span data-ttu-id="acd95-122">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="acd95-122">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
