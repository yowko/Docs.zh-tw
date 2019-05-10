---
title: HOW TO：使用設計工具設定 Windows Forms 面板的背景
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211634"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="0c410-102">HOW TO：設定使用設計工具的 Windows Form 面板的背景</span><span class="sxs-lookup"><span data-stu-id="0c410-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="0c410-103">Windows Form<xref:System.Windows.Forms.Panel>控制項可以顯示的背景色彩和背景影像。</span><span class="sxs-lookup"><span data-stu-id="0c410-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="0c410-104"><xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含在窗格中，例如標籤和選項按鈕控制項的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="0c410-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="0c410-105">如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未設定屬性，<xref:System.Windows.Forms.Control.BackColor%2A>選取項目將會填滿所有面板。</span><span class="sxs-lookup"><span data-stu-id="0c410-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="0c410-106">如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性設定，將控制項台中包含後面顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="0c410-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="0c410-107">下列程序需要**Windows 應用程式**專案，其表單包含<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="0c410-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="0c410-108">如需有關如何設定這類專案在 Visual Studio 中的資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="0c410-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="0c410-109">在 Windows Form 設計工具設定背景</span><span class="sxs-lookup"><span data-stu-id="0c410-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="0c410-110">在 Visual Studio 中開啟專案，然後選取<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="0c410-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="0c410-111">在 **屬性**視窗中，按一下旁邊的箭號按鈕<xref:System.Windows.Forms.Control.BackColor%2A>屬性以顯示具有三個索引標籤的視窗。</span><span class="sxs-lookup"><span data-stu-id="0c410-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="0c410-112">選取 **自訂**索引標籤，顯示色的調色盤。</span><span class="sxs-lookup"><span data-stu-id="0c410-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="0c410-113">選取  **Web**或是**系統**tab 鍵移至顯示的預先定義的色彩名稱清單，然後再選取色彩。</span><span class="sxs-lookup"><span data-stu-id="0c410-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="0c410-114">在 **屬性**視窗中，按一下旁邊的箭號按鈕<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0c410-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="0c410-115">在 **開啟**對話方塊方塊中，選取您想要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="0c410-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c410-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c410-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="0c410-117">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="0c410-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="0c410-118">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0c410-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="0c410-119">如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="0c410-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
