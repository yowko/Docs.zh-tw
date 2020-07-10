---
title: 如何：建立 MDI 父表單
description: 瞭解如何以程式設計方式建立 MDI 父表單，以及如何使用 Windows Form 設計工具。
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174701"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="0d616-103">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="0d616-103">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d616-104">本主題使用 <xref:System.Windows.Forms.MainMenu> 控制項，該控制項已被 <xref:System.Windows.Forms.MenuStrip> 控制項取代。</span><span class="sxs-lookup"><span data-stu-id="0d616-104">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="0d616-105">您可以選擇保留 <xref:System.Windows.Forms.MainMenu> 控制項，以提供回溯相容性並供未來使用。</span><span class="sxs-lookup"><span data-stu-id="0d616-105">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="0d616-106">如需使用建立 MDI 父表單的詳細資訊 <xref:System.Windows.Forms.MenuStrip> ，請參閱[如何：使用 MENUSTRIP 建立 Mdi 視窗清單](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="0d616-106">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="0d616-107">MDI 父表單是多重文件介面 (MDI) 應用程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="0d616-107">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="0d616-108">這個表單包含 MDI 子視窗，也就是使用者與 MDI 應用程式互動所在的子視窗。</span><span class="sxs-lookup"><span data-stu-id="0d616-108">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="0d616-109">您可以透過 Windows Form 設計工具及程式設計方式，輕鬆建立 MDI 父表單。</span><span class="sxs-lookup"><span data-stu-id="0d616-109">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="0d616-110">在設計階段建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="0d616-110">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="0d616-111">在 Visual Studio 中建立 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="0d616-111">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="0d616-112">在 [**屬性**] 視窗中，將 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 [ **true**]。</span><span class="sxs-lookup"><span data-stu-id="0d616-112">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="0d616-113">如此即可將表單指定為子視窗的 MDI 容器。</span><span class="sxs-lookup"><span data-stu-id="0d616-113">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0d616-114">當您設定 [屬性]\*\*\*\* 視窗中的屬性時，也可以視需要將 `WindowState` 屬性設定為 **Maximized**，這是因為當父表單最大化時，最容易操作 MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="0d616-114">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="0d616-115">此外，請注意 MDI 父表單的邊緣會採用系統色彩 (在 Windows 系統控制台中設定)，而不是採用您使用 <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> 屬性所設定的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="0d616-115">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="0d616-116">從 [工具箱]\*\*\*\* 中，將 **MenuStrip** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="0d616-116">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="0d616-117">建立一個最上層功能表項目，並將 **Text** 屬性設定為 **&File**，其中包含子功能表項目 **&New** 和 **&Close**。</span><span class="sxs-lookup"><span data-stu-id="0d616-117">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="0d616-118">另外再建立一個名為 **&Window** 的最上層功能表項目。</span><span class="sxs-lookup"><span data-stu-id="0d616-118">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="0d616-119">第一個功能表會在執行階段建立及隱藏功能表項目，第二個功能表則會追蹤開啟的 MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="0d616-119">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="0d616-120">此時，您已經建立 MDI 父視窗。</span><span class="sxs-lookup"><span data-stu-id="0d616-120">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="0d616-121">按**F5**執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d616-121">Press **F5** to run the application.</span></span> <span data-ttu-id="0d616-122">如需建立在 MDI 父表單內操作之 MDI 子視窗的資訊，請參閱[如何：建立 MDI 子表單](how-to-create-mdi-child-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="0d616-122">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d616-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d616-123">See also</span></span>

- [<span data-ttu-id="0d616-124">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="0d616-124">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="0d616-125">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="0d616-125">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="0d616-126">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="0d616-126">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="0d616-127">如何：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="0d616-127">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="0d616-128">如何：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="0d616-128">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
