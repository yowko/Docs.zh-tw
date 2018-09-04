---
title: 如何：繼承自 UserControl 類別
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5a826b9fc68bebfa32049a38899ddffaacd25607
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563704"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="6a02a-102">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="6a02a-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="6a02a-103">若要結合一或多個 Windows Forms 控制項的功能與自訂程式碼，您可以建立「使用者控制項」。</span><span class="sxs-lookup"><span data-stu-id="6a02a-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="6a02a-104">使用者控制項可結合快速控制項開發、標準 Windows Forms 控制項功能，以及自訂屬性和方法的各種用途。</span><span class="sxs-lookup"><span data-stu-id="6a02a-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="6a02a-105">當您開始建立使用者控制項時，您會看到吸引人的設計工具，您可以在其上放置標準 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="6a02a-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="6a02a-106">這些控制項會保留其所有固有功能，以及標準控制項的外觀和行為 (外觀及操作)。</span><span class="sxs-lookup"><span data-stu-id="6a02a-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="6a02a-107">不過，這些控制項一旦內建於使用者控制項，您就無法再透過程式碼使用它們。</span><span class="sxs-lookup"><span data-stu-id="6a02a-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="6a02a-108">使用者控制項會進行自己的繪製，也會處理與控制項相關聯的所有基本功能。</span><span class="sxs-lookup"><span data-stu-id="6a02a-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a02a-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="6a02a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6a02a-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="6a02a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6a02a-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="6a02a-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-user-control"></a><span data-ttu-id="6a02a-112">建立使用者控制項</span><span class="sxs-lookup"><span data-stu-id="6a02a-112">To create a user control</span></span>  
  
1.  <span data-ttu-id="6a02a-113">建立新的 [Windows 控制項程式庫] 專案。</span><span class="sxs-lookup"><span data-stu-id="6a02a-113">Create a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="6a02a-114">使用空白使用者控制項來建立新專案。</span><span class="sxs-lookup"><span data-stu-id="6a02a-114">A new project is created with a blank user control.</span></span>  
  
2.  <span data-ttu-id="6a02a-115">將控制項從 [工具箱] 的 [Windows Forms] 索引標籤拖曳到您的設計工具。</span><span class="sxs-lookup"><span data-stu-id="6a02a-115">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>  
  
3.  <span data-ttu-id="6a02a-116">這些控制項的放置和設計方式應該依照您希望它們出現於最終使用者控制項的方式。</span><span class="sxs-lookup"><span data-stu-id="6a02a-116">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="6a02a-117">如果您想要讓開發人員存取組成控制項，您必須將它們宣告為公用，或選擇性地公開組成控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a02a-117">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="6a02a-118">如需詳細資訊，請參閱[如何：公開組成控制項的屬性](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="6a02a-118">For details, see [How to: Expose Properties of Constituent Controls](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span></span>  
  
4.  <span data-ttu-id="6a02a-119">實作您的控制項將併入的任何自訂方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="6a02a-119">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
5.  <span data-ttu-id="6a02a-120">按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="6a02a-120">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="6a02a-121">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="6a02a-121">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a02a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a02a-122">See Also</span></span>  
 [<span data-ttu-id="6a02a-123">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="6a02a-123">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="6a02a-124">操作說明：繼承自 Control 類別</span><span class="sxs-lookup"><span data-stu-id="6a02a-124">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="6a02a-125">操作說明：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="6a02a-125">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="6a02a-126">操作說明：撰寫 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="6a02a-126">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="6a02a-127">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="6a02a-127">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="6a02a-128">操作說明：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="6a02a-128">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
