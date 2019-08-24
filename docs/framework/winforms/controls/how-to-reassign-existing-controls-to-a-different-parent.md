---
title: HOW TO：將現有控制項重新指派至不同的父代
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987038"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="bcd34-102">作法：將現有控制項重新指派至不同的父系</span><span class="sxs-lookup"><span data-stu-id="bcd34-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="bcd34-103">您可以將表單上現有的控制項指派給新的容器控制項。</span><span class="sxs-lookup"><span data-stu-id="bcd34-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="bcd34-104">在 Visual Studio 中, 從<xref:System.Windows.Forms.Button> [**工具箱**] 將三個控制項拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="bcd34-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="bcd34-105">將它們放在相鄰的位置，但不要對齊。</span><span class="sxs-lookup"><span data-stu-id="bcd34-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="bcd34-106">按一下 [工具箱]的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="bcd34-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="bcd34-107">(請勿將圖示拖曳到表單上。)</span><span class="sxs-lookup"><span data-stu-id="bcd34-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="bcd34-108">將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。</span><span class="sxs-lookup"><span data-stu-id="bcd34-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="bcd34-109">指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="bcd34-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="bcd34-110">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="bcd34-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="bcd34-111">拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。</span><span class="sxs-lookup"><span data-stu-id="bcd34-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="bcd34-112">繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。</span><span class="sxs-lookup"><span data-stu-id="bcd34-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="bcd34-113">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="bcd34-113">Release the mouse button.</span></span>

   <span data-ttu-id="bcd34-114">三個 <xref:System.Windows.Forms.Button> 控制項現在都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="bcd34-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcd34-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcd34-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="bcd34-116">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="bcd34-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="bcd34-117">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="bcd34-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
