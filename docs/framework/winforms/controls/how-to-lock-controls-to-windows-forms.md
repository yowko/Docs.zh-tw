---
title: 如何：鎖定 Windows Form 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: 8de22ae6667446620867f3c15aac3c4af65582bf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511134"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="6d09d-102">如何：鎖定 Windows Form 的控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="6d09d-103">當您設計您的 Windows 應用程式的使用者介面 (UI) 時，您可以在之後放置的位置正確，因此，您不小心移動或調整其大小設定其他屬性時，鎖定控制項。</span><span class="sxs-lookup"><span data-stu-id="6d09d-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="6d09d-104">此外，您可以鎖定及解除鎖定所有表單上的控制項，也就是很有幫助具有許多控制項的表單，或您可以解除鎖定個別控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="6d09d-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="6d09d-105">一旦您已經置身在表單上放置所有控制項，可鎖定這些項目全都放在預防錯誤移動的位置。</span><span class="sxs-lookup"><span data-stu-id="6d09d-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d09d-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="6d09d-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6d09d-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="6d09d-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6d09d-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="6d09d-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="6d09d-109">若要鎖定控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="6d09d-110">在 [**屬性**] 視窗中，按一下**鎖定**屬性，並選取`true`。</span><span class="sxs-lookup"><span data-stu-id="6d09d-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="6d09d-111">（按兩下名稱切換屬性設定）。</span><span class="sxs-lookup"><span data-stu-id="6d09d-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="6d09d-112">或者，以滑鼠右鍵按一下控制項，然後選擇**鎖定控制項**。</span><span class="sxs-lookup"><span data-stu-id="6d09d-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d09d-113">鎖定控制項可防止它們被拖曳至新的大小或位置，在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="6d09d-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="6d09d-114">不過，您仍然可以變更的大小或位置的控制項，藉由**屬性**視窗或在程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d09d-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="6d09d-115">若要鎖定在表單上的所有控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="6d09d-116">從**格式**功能表上，選擇**鎖定控制項**。</span><span class="sxs-lookup"><span data-stu-id="6d09d-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d09d-117">由於表單是控制項，此命令會鎖定，表單的大小。</span><span class="sxs-lookup"><span data-stu-id="6d09d-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="6d09d-118">若要解除鎖定表單上的所有鎖定的控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="6d09d-119">從**格式**功能表上，選擇**鎖定控制項**。</span><span class="sxs-lookup"><span data-stu-id="6d09d-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="6d09d-120">在表單上的所有先前鎖定的控制項現在已解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="6d09d-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="6d09d-121">若要個別解除鎖定鎖定的控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="6d09d-122">在 [**屬性**] 視窗中，按一下**鎖定**屬性，並選取`false`。</span><span class="sxs-lookup"><span data-stu-id="6d09d-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="6d09d-123">（按兩下名稱切換屬性設定）。</span><span class="sxs-lookup"><span data-stu-id="6d09d-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d09d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d09d-124">See Also</span></span>  
 [<span data-ttu-id="6d09d-125">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="6d09d-126">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-126">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="6d09d-127">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="6d09d-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="6d09d-128">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="6d09d-129">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="6d09d-129">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
