---
title: 使用設計工具設定面板的背景
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731928"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="bd785-102">如何：使用設計工具設定 Windows Forms 面板的背景</span><span class="sxs-lookup"><span data-stu-id="bd785-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="bd785-103">Windows Forms <xref:System.Windows.Forms.Panel> 控制項可以同時顯示背景色彩和背景影像。</span><span class="sxs-lookup"><span data-stu-id="bd785-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="bd785-104"><xref:System.Windows.Forms.Control.BackColor%2A> 屬性會設定面板中所包含控制項的背景色彩，例如標籤和選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="bd785-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="bd785-105">如果未設定 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性，<xref:System.Windows.Forms.Control.BackColor%2A> 選取專案就會填滿所有的面板。</span><span class="sxs-lookup"><span data-stu-id="bd785-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="bd785-106">如果已設定 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性，影像就會顯示在面板所包含的控制項後方。</span><span class="sxs-lookup"><span data-stu-id="bd785-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="bd785-107">下列程式需要具有包含 <xref:System.Windows.Forms.Panel> 控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="bd785-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="bd785-108">如需如何在 Visual Studio 中設定這類專案的詳細資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="bd785-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="bd785-109">設定 Windows Form 設計工具中的背景</span><span class="sxs-lookup"><span data-stu-id="bd785-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="bd785-110">在 Visual Studio 中開啟專案，然後選取 [<xref:System.Windows.Forms.Panel>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="bd785-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="bd785-111">在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.BackColor%2A>] 屬性旁的箭號按鈕，以顯示具有三個索引標籤的視窗。</span><span class="sxs-lookup"><span data-stu-id="bd785-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="bd785-112">選取 [**自訂**] 索引標籤以顯示色彩的調色板。</span><span class="sxs-lookup"><span data-stu-id="bd785-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="bd785-113">選取 [ **Web** ] 或 [**系統**] 索引標籤，以顯示色彩的預先定義名稱清單，然後選取色彩。</span><span class="sxs-lookup"><span data-stu-id="bd785-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="bd785-114">在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性旁的箭號按鈕。</span><span class="sxs-lookup"><span data-stu-id="bd785-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="bd785-115">在 [**開啟**] 對話方塊中，選取您要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="bd785-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd785-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd785-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="bd785-117">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="bd785-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="bd785-118">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="bd785-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="bd785-119">操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="bd785-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
