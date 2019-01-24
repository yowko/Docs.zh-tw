---
title: HOW TO：對齊和縮放 TableLayoutPanel 控制項中的控制項
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 91464108a6ac4600c14a06b4a7dcea200d7f0254
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535927"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="45527-102">HOW TO：對齊和縮放 TableLayoutPanel 控制項中的控制項</span><span class="sxs-lookup"><span data-stu-id="45527-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="45527-103">您可以對齊和縮放控制項<xref:System.Windows.Forms.TableLayoutPanel>具有<xref:System.Windows.Forms.Control.Anchor%2A>和<xref:System.Windows.Forms.Control.Dock%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="45527-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45527-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="45527-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="45527-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="45527-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="45527-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="45527-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="45527-107">若要對齊和縮放控制項</span><span class="sxs-lookup"><span data-stu-id="45527-107">To align and stretch a control</span></span>  
  
1.  <span data-ttu-id="45527-108">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="45527-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="45527-109">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的左上方儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="45527-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="45527-110"><xref:System.Windows.Forms.Button>控制項在儲存格中置中對齊。</span><span class="sxs-lookup"><span data-stu-id="45527-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3.  <span data-ttu-id="45527-111">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Left,Right`。</span><span class="sxs-lookup"><span data-stu-id="45527-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="45527-112"><xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合儲存格的寬度。</span><span class="sxs-lookup"><span data-stu-id="45527-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4.  <span data-ttu-id="45527-113">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Top,Bottom`。</span><span class="sxs-lookup"><span data-stu-id="45527-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="45527-114"><xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合資料格的高度。</span><span class="sxs-lookup"><span data-stu-id="45527-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5.  <span data-ttu-id="45527-115">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="45527-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="45527-116"><xref:System.Windows.Forms.Button>展開以填滿儲存格的控制項。</span><span class="sxs-lookup"><span data-stu-id="45527-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6.  <span data-ttu-id="45527-117">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.None>。</span><span class="sxs-lookup"><span data-stu-id="45527-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="45527-118"><xref:System.Windows.Forms.Button>控制項傳回至其原始大小，並將移至儲存格的左上角。</span><span class="sxs-lookup"><span data-stu-id="45527-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="45527-119">**Windows Form 設計工具**已設定<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Top, Left`。</span><span class="sxs-lookup"><span data-stu-id="45527-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7.  <span data-ttu-id="45527-120">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Bottom,Right`。</span><span class="sxs-lookup"><span data-stu-id="45527-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="45527-121"><xref:System.Windows.Forms.Button>控制項移到儲存格右下角。</span><span class="sxs-lookup"><span data-stu-id="45527-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8.  <span data-ttu-id="45527-122">設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設<xref:System.Windows.Forms.AnchorStyles.None>。</span><span class="sxs-lookup"><span data-stu-id="45527-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="45527-123"><xref:System.Windows.Forms.Button>控制項移到儲存格的中央。</span><span class="sxs-lookup"><span data-stu-id="45527-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45527-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45527-124">See also</span></span>
- [<span data-ttu-id="45527-125">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="45527-125">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
