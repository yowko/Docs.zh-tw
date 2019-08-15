---
title: HOW TO：將現有控制項重新指派至不同的父代
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039793"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="660c6-102">HOW TO：將現有控制項重新指派至不同的父代</span><span class="sxs-lookup"><span data-stu-id="660c6-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="660c6-103">您可以將表單上現有的控制項指派給新的容器控制項。</span><span class="sxs-lookup"><span data-stu-id="660c6-103">You can assign controls that exist on your form to a new container control.</span></span>

## <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="660c6-104">將現有控制項重新指派至不同的父代</span><span class="sxs-lookup"><span data-stu-id="660c6-104">To reassign existing controls to a different parent</span></span>

1. <span data-ttu-id="660c6-105">從 [工具箱] <xref:System.Windows.Forms.Button>**將三個** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="660c6-105">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>

     <span data-ttu-id="660c6-106">將它們放在相鄰的位置，但不要對齊。</span><span class="sxs-lookup"><span data-stu-id="660c6-106">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="660c6-107">按一下 [工具箱]的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="660c6-107">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>

     <span data-ttu-id="660c6-108">請勿將圖示拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="660c6-108">Do not drag the icon onto the form.</span></span>

3. <span data-ttu-id="660c6-109">將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。</span><span class="sxs-lookup"><span data-stu-id="660c6-109">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

     <span data-ttu-id="660c6-110">指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="660c6-110">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="660c6-111">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="660c6-111">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="660c6-112">拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。</span><span class="sxs-lookup"><span data-stu-id="660c6-112">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="660c6-113">繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。</span><span class="sxs-lookup"><span data-stu-id="660c6-113">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="660c6-114">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="660c6-114">Release the mouse button.</span></span>

     <span data-ttu-id="660c6-115">三個 <xref:System.Windows.Forms.Button> 控制項現在都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="660c6-115">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="660c6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="660c6-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="660c6-117">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="660c6-117">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="660c6-118">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="660c6-118">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="660c6-119">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="660c6-119">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
