---
title: HOW TO：調整 Windows Forms 的控制項大小
ms.date: 03/30/2017
f1_keywords:
- Size.Height
- Size.Width
helpviewer_keywords:
- controls [Windows Forms], resizing
- size [Windows Forms], controls
- Windows Forms controls, size
ms.assetid: d2dba441-a8c0-4705-b8e8-2e5d86d6e7ec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e659bf02ea079afc10561e1d83f7ab7cef29a2e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987055"
---
# <a name="how-to-resize-controls-on-windows-forms"></a><span data-ttu-id="e99dc-102">作法：調整 Windows Forms 上控制項的大小</span><span class="sxs-lookup"><span data-stu-id="e99dc-102">How to: Resize controls on Windows Forms</span></span>

<span data-ttu-id="e99dc-103">您可以調整個別控制項的大小, 也可以調整相同或不同種類 (例如<xref:System.Windows.Forms.Button>和<xref:System.Windows.Forms.GroupBox>控制項) 的多個控制項大小。</span><span class="sxs-lookup"><span data-stu-id="e99dc-103">You can resize individual controls, and you can resize multiple controls of the same or different kind, such as <xref:System.Windows.Forms.Button> and <xref:System.Windows.Forms.GroupBox> controls.</span></span>

## <a name="to-resize-a-control"></a><span data-ttu-id="e99dc-104">調整控制項的大小</span><span class="sxs-lookup"><span data-stu-id="e99dc-104">To resize a control</span></span>

<span data-ttu-id="e99dc-105">在 Visual Studio 中, 選取要調整大小的控制項, 然後拖曳其中一個八個大小控點。</span><span class="sxs-lookup"><span data-stu-id="e99dc-105">In Visual Studio, select the control to be resized and drag one of the eight sizing handles.</span></span>

> [!NOTE]
> <span data-ttu-id="e99dc-106">選取控制項, 然後在按住**Shift**鍵時按**箭頭**鍵, 一次調整控制項的一個圖元。</span><span class="sxs-lookup"><span data-stu-id="e99dc-106">Select the control and press the **arrow** keys while holding down the **Shift** key to resize the control one pixel at a time.</span></span> <span data-ttu-id="e99dc-107">按**向下**鍵或**向右鍵**, 同時按住**Shift**和**Ctrl**鍵, 以大幅增加控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="e99dc-107">Press the **down arrow** or **right arrow** keys while holding down the **Shift** and **Ctrl** keys to resize the control in large increments.</span></span>

## <a name="to-resize-multiple-controls-on-a-form"></a><span data-ttu-id="e99dc-108">調整表單上的多個控制項大小</span><span class="sxs-lookup"><span data-stu-id="e99dc-108">To resize multiple controls on a form</span></span>

1. <span data-ttu-id="e99dc-109">在 Visual Studio 中, 按住**Ctrl**或**Shift**鍵, 然後選取您想要調整大小的控制項。</span><span class="sxs-lookup"><span data-stu-id="e99dc-109">In Visual Studio, hold down the **Ctrl** or **Shift** key and select the controls you want to resize.</span></span> <span data-ttu-id="e99dc-110">您選取的第一個控制項的大小會用於其他控制項。</span><span class="sxs-lookup"><span data-stu-id="e99dc-110">The size of the first control you select is used for the other controls.</span></span>

2. <span data-ttu-id="e99dc-111">在 [**格式**] 功能表上, 選擇 [**設成相同大小**], 然後選取四個選項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="e99dc-111">On the **Format** menu, choose **Make Same Size**, and select one of the four options.</span></span> <span data-ttu-id="e99dc-112">前三個命令會變更控制項的維度, 以符合第一個選取的控制項。</span><span class="sxs-lookup"><span data-stu-id="e99dc-112">The first three commands change the dimensions of the controls to match the first-selected control.</span></span>

## <a name="see-also"></a><span data-ttu-id="e99dc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e99dc-113">See also</span></span>

- [<span data-ttu-id="e99dc-114">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e99dc-114">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e99dc-115">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="e99dc-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="e99dc-116">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="e99dc-116">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="e99dc-117">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e99dc-117">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="e99dc-118">[如何：使用設計工具調整 Windows Forms 大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e99dc-118">[How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))</span></span>
