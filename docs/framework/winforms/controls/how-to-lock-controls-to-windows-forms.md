---
title: HOW TO：鎖定 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f6dd079331c6c1883839efe5c6cb127044380fd2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987471"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="04bb5-102">作法：鎖定控制項以 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04bb5-102">How to: Lock controls to Windows Forms</span></span>

<span data-ttu-id="04bb5-103">當您設計 Windows 應用程式的使用者介面 (UI) 時, 可以在控制項正確定位之後鎖定它們, 以便在設定其他屬性時不會不慎移動或調整其大小。</span><span class="sxs-lookup"><span data-stu-id="04bb5-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

<span data-ttu-id="04bb5-104">此外, 您可以一次鎖定和解除鎖定表單上的所有控制項, 這對於具有許多控制項的表單很有説明, 或者您也可以解除鎖定個別控制項。</span><span class="sxs-lookup"><span data-stu-id="04bb5-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="04bb5-105">當您將所有控制項放在表單上時, 請將它們全部鎖定, 以避免發生錯誤的移動。</span><span class="sxs-lookup"><span data-stu-id="04bb5-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="04bb5-106">若要鎖定控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-106">To lock a control</span></span>

<span data-ttu-id="04bb5-107">在 Visual Studio 的 [**屬性**] 視窗中, 選取 [已**鎖定**] 屬性, 然後選取 [ **true**]。</span><span class="sxs-lookup"><span data-stu-id="04bb5-107">In the **Properties** window of Visual Studio, select the **Locked** property and then select **true**.</span></span> <span data-ttu-id="04bb5-108">(按兩下名稱即可切換屬性設定)。</span><span class="sxs-lookup"><span data-stu-id="04bb5-108">(Double-clicking the name toggles the property setting.)</span></span>

<span data-ttu-id="04bb5-109">或者, 以滑鼠右鍵按一下控制項, 然後選擇 [**鎖定控制項**]。</span><span class="sxs-lookup"><span data-stu-id="04bb5-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="04bb5-110">鎖定控制項可避免將它們拖曳至設計介面上的新大小或位置。</span><span class="sxs-lookup"><span data-stu-id="04bb5-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="04bb5-111">不過, 您仍然可以透過 [**屬性**] 視窗或在程式碼中變更控制項的大小或位置。</span><span class="sxs-lookup"><span data-stu-id="04bb5-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="04bb5-112">鎖定表單上的所有控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-112">To lock all the controls on a form</span></span>

<span data-ttu-id="04bb5-113">從 [**格式**] 功能表選擇 [**鎖定控制項**]。</span><span class="sxs-lookup"><span data-stu-id="04bb5-113">From the **Format** menu, choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="04bb5-114">此命令也會鎖定表單的大小, 因為表單是控制項。</span><span class="sxs-lookup"><span data-stu-id="04bb5-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="04bb5-115">解除鎖定表單上所有鎖定的控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-115">To unlock all locked controls on a form</span></span>

<span data-ttu-id="04bb5-116">從 [**格式**] 功能表選擇 [**鎖定控制項**]。</span><span class="sxs-lookup"><span data-stu-id="04bb5-116">From the **Format** menu, choose **Lock Controls**.</span></span>

<span data-ttu-id="04bb5-117">表單上先前鎖定的所有控制項現在都會解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="04bb5-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="04bb5-118">個別解除鎖定鎖定的控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-118">To unlock locked controls individually</span></span>

<span data-ttu-id="04bb5-119">在 [**屬性**] 視窗中, 選取 [已**鎖定**] 屬性, 然後選取 [ **false**]。</span><span class="sxs-lookup"><span data-stu-id="04bb5-119">In the **Properties** window, select the **Locked** property and then select **false**.</span></span> <span data-ttu-id="04bb5-120">(按兩下名稱即可切換屬性設定)。</span><span class="sxs-lookup"><span data-stu-id="04bb5-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="04bb5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04bb5-121">See also</span></span>

- [<span data-ttu-id="04bb5-122">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="04bb5-123">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="04bb5-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="04bb5-124">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="04bb5-125">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="04bb5-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
