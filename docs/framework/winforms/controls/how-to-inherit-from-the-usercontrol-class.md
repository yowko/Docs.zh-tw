---
title: HOW TO：繼承 UserControl 類別
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 77233517203989f188a2b3ddf436656bc8da82a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966560"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="cd6ef-102">HOW TO：繼承 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="cd6ef-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="cd6ef-103">若要結合一或多個 Windows Forms 控制項的功能與自訂程式碼，您可以建立「使用者控制項」。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="cd6ef-104">使用者控制項可結合快速控制項開發、標準 Windows Forms 控制項功能，以及自訂屬性和方法的各種用途。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="cd6ef-105">當您開始建立使用者控制項時，您會看到吸引人的設計工具，您可以在其上放置標準 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="cd6ef-106">這些控制項會保留其所有固有功能，以及標準控制項的外觀和行為 (外觀及操作)。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="cd6ef-107">不過，這些控制項一旦內建於使用者控制項，您就無法再透過程式碼使用它們。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="cd6ef-108">使用者控制項會進行自己的繪製，也會處理與控制項相關聯的所有基本功能。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="cd6ef-109">建立使用者控制項</span><span class="sxs-lookup"><span data-stu-id="cd6ef-109">To create a user control</span></span>

1. <span data-ttu-id="cd6ef-110">建立新的 [Windows 控制項程式庫] 專案。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-110">Create a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="cd6ef-111">使用空白使用者控制項來建立新專案。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="cd6ef-112">將控制項從 [工具箱] 的 [Windows Forms] 索引標籤拖曳到您的設計工具。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="cd6ef-113">這些控制項的放置和設計方式應該依照您希望它們出現於最終使用者控制項的方式。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="cd6ef-114">如果您想要讓開發人員存取組成控制項，您必須將它們宣告為公用，或選擇性地公開組成控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="cd6ef-115">如需詳細資訊，請參閱[如何：公開組成控制項](how-to-expose-properties-of-constituent-controls.md)的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="cd6ef-116">實作您的控制項將併入的任何自訂方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="cd6ef-117">按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-117">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="cd6ef-118">如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="cd6ef-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd6ef-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd6ef-119">See also</span></span>

- [<span data-ttu-id="cd6ef-120">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="cd6ef-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="cd6ef-121">如何：繼承自控制項類別</span><span class="sxs-lookup"><span data-stu-id="cd6ef-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="cd6ef-122">如何：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="cd6ef-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="cd6ef-123">如何：Windows Forms 的作者控制項</span><span class="sxs-lookup"><span data-stu-id="cd6ef-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="cd6ef-124">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="cd6ef-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="cd6ef-125">如何：測試 UserControl 的執行時間行為</span><span class="sxs-lookup"><span data-stu-id="cd6ef-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
