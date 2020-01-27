---
title: 使用設計工具的群組控制項與面板控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745648"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="5d4ae-102">如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="5d4ae-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="5d4ae-103">Windows Forms <xref:System.Windows.Forms.Panel> 控制項用來分組其他控制項。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="5d4ae-104">群組控制項的原因有三個。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-104">There are three reasons to group controls.</span></span> <span data-ttu-id="5d4ae-105">其中一個是明確使用者介面的相關表單元素的視覺化群組;另一個是以程式設計方式分組，例如選項按鈕，最後一個是在設計階段將控制項移動為一個單位。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="5d4ae-106">若要建立控制項群組</span><span class="sxs-lookup"><span data-stu-id="5d4ae-106">To create a group of controls</span></span>

1. <span data-ttu-id="5d4ae-107">將 [<xref:System.Windows.Forms.Panel>] 控制項從 [工具箱] 的 [ **Windows Forms** ] 索引標籤拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="5d4ae-108">將其他控制項新增至面板，並在面板內繪製每個控制項。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="5d4ae-109">如果您有想要放在面板中的現有控制項，您可以選取所有控制項、將其剪下至剪貼簿、選取 <xref:System.Windows.Forms.Panel> 控制項，然後將其貼到面板中。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="5d4ae-110">您也可以將它們拖曳至面板。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="5d4ae-111">選擇性如果您想要將框線新增至面板，請設定其 [<xref:System.Windows.Forms.BorderStyle>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="5d4ae-112">有三個選擇： [<xref:System.Windows.Forms.BorderStyle.Fixed3D>]、[<xref:System.Windows.Forms.BorderStyle.FixedSingle>] 和 [<xref:System.Windows.Forms.BorderStyle.None>]。</span><span class="sxs-lookup"><span data-stu-id="5d4ae-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d4ae-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d4ae-113">See also</span></span>

- [<span data-ttu-id="5d4ae-114">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="5d4ae-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="5d4ae-115">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="5d4ae-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="5d4ae-116">操作說明：設定面板背景</span><span class="sxs-lookup"><span data-stu-id="5d4ae-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
