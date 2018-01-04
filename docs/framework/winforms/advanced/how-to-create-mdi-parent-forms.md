---
title: "如何：建立 MDI 父表單"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0147bc0777fdf3168ab0bc36ced0943571187d3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="ec437-102">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="ec437-102">How to: Create MDI Parent Forms</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="ec437-103">本主題使用 <xref:System.Windows.Forms.MainMenu> 控制項，該控制項已被 <xref:System.Windows.Forms.MenuStrip> 控制項取代。</span><span class="sxs-lookup"><span data-stu-id="ec437-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="ec437-104">您可以選擇保留 <xref:System.Windows.Forms.MainMenu> 控制項，以提供回溯相容性並供未來使用。</span><span class="sxs-lookup"><span data-stu-id="ec437-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span>  <span data-ttu-id="ec437-105">如需建立 MDI 父表單的使用<xref:System.Windows.Forms.MenuStrip>，請參閱[How to： 使用 MenuStrip 建立 MDI 視窗清單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="ec437-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>  
  
 <span data-ttu-id="ec437-106">MDI 父表單是多重文件介面 (MDI) 應用程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="ec437-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="ec437-107">這個表單包含 MDI 子視窗，也就是使用者與 MDI 應用程式互動所在的子視窗。</span><span class="sxs-lookup"><span data-stu-id="ec437-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="ec437-108">您可以透過 Windows Form 設計工具及程式設計方式，輕鬆建立 MDI 父表單。</span><span class="sxs-lookup"><span data-stu-id="ec437-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="ec437-109">在設計階段建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="ec437-109">To create an MDI parent form at design time</span></span>  
  
1.  <span data-ttu-id="ec437-110">建立 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="ec437-110">Create a Windows Application project.</span></span>  
  
2.  <span data-ttu-id="ec437-111">在**屬性**視窗中，將<xref:System.Windows.Forms.Form.IsMdiContainer%2A>屬性**true**。</span><span class="sxs-lookup"><span data-stu-id="ec437-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>  
  
     <span data-ttu-id="ec437-112">如此即可將表單指定為子視窗的 MDI 容器。</span><span class="sxs-lookup"><span data-stu-id="ec437-112">This designates the form as an MDI container for child windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec437-113">當您設定 [屬性] 視窗中的屬性時，也可以視需要將 `WindowState` 屬性設定為 **Maximized**，這是因為當父表單最大化時，最容易操作 MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="ec437-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="ec437-114">此外，請注意 MDI 父表單的邊緣會採用系統色彩 (在 Windows 系統控制台中設定)，而不是採用您使用 <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> 屬性所設定的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="ec437-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>  
  
3.  <span data-ttu-id="ec437-115">從 [工具箱] 中，將 **MenuStrip** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="ec437-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="ec437-116">建立一個最上層功能表項目，並將 **Text** 屬性設定為 **&File**，其中包含子功能表項目 **&New** 和 **&Close**。</span><span class="sxs-lookup"><span data-stu-id="ec437-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="ec437-117">另外再建立一個名為 **&Window** 的最上層功能表項目。</span><span class="sxs-lookup"><span data-stu-id="ec437-117">Also create a top-level menu item called **&Window**.</span></span>  
  
     <span data-ttu-id="ec437-118">第一個功能表會在執行階段建立及隱藏功能表項目，第二個功能表則會追蹤開啟的 MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="ec437-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="ec437-119">此時，您已經建立 MDI 父視窗。</span><span class="sxs-lookup"><span data-stu-id="ec437-119">At this point, you have created an MDI parent window.</span></span>  
  
4.  <span data-ttu-id="ec437-120">按 **F5** 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec437-120">Press **F5** to run the application.</span></span> <span data-ttu-id="ec437-121">如需建立在 MDI 父表單內操作之 MDI 子視窗的資訊，請參閱[如何：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="ec437-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec437-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec437-122">See Also</span></span>  
 [<span data-ttu-id="ec437-123">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="ec437-123">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="ec437-124">操作說明：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="ec437-124">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="ec437-125">操作說明：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="ec437-125">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="ec437-126">操作說明：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="ec437-126">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="ec437-127">操作說明：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="ec437-127">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
