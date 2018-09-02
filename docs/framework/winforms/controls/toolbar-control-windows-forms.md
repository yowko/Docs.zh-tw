---
title: ToolBar 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 8162dfc898f7965d65de918d2a5b1f7afbfdf9b2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400845"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="144d0-102">ToolBar 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="144d0-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="144d0-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 `ToolBar` 控制項並加入其他功能，不過您也可以選擇保留 `ToolBar` 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="144d0-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="144d0-104">Windows Form `ToolBar` 控制項在表單中，是當做顯示下拉式功能表其中一列的控制列和啟動命令的點陣圖按鈕使用。</span><span class="sxs-lookup"><span data-stu-id="144d0-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="144d0-105">因此，按一下工具列按鈕相當於選擇功能表命令。</span><span class="sxs-lookup"><span data-stu-id="144d0-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="144d0-106">您可將這些按鈕設定成和按鈕、下拉式功能表或分隔符號一樣顯示和運作。</span><span class="sxs-lookup"><span data-stu-id="144d0-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="144d0-107">一般而言，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。</span><span class="sxs-lookup"><span data-stu-id="144d0-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="144d0-108">`ToolBar` 控制項的 <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> 屬性會將 <xref:System.Windows.Forms.ContextMenu> 類別的執行個體當做參考。</span><span class="sxs-lookup"><span data-stu-id="144d0-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="144d0-109">請仔細考慮在應用程式中實作工具列上這類按鈕時所傳遞的參考，因為這個屬性會接受任何繼承自 <xref:System.Windows.Forms.Menu> 類別的物件。</span><span class="sxs-lookup"><span data-stu-id="144d0-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="144d0-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="144d0-110">In This Section</span></span>  
 [<span data-ttu-id="144d0-111">工具列控制項概觀</span><span class="sxs-lookup"><span data-stu-id="144d0-111">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="144d0-112">介紹 `ToolBar` 控制項的一般概念，讓您能夠設計自訂工具列以供使用者利用。</span><span class="sxs-lookup"><span data-stu-id="144d0-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="144d0-113">操作說明：將按鈕新增至工具列控制項</span><span class="sxs-lookup"><span data-stu-id="144d0-113">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="144d0-114">描述如何將按鈕加入 `ToolBar` 控制項。</span><span class="sxs-lookup"><span data-stu-id="144d0-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="144d0-115">操作說明：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="144d0-115">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="144d0-116">描述如何在 `ToolBar` 控制項的按鈕內顯示圖示。</span><span class="sxs-lookup"><span data-stu-id="144d0-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="144d0-117">操作說明：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="144d0-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="144d0-118">指示如何撰寫程式碼，來解譯使用者在 `ToolBar` 控制項中按的是哪一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="144d0-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="144d0-119">另請參閱[如何： 定義工具列按鈕使用設計工具的圖示](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md)，[如何： 將按鈕加入工具列控制項使用設計工具](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="144d0-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="144d0-120">參考資料</span><span class="sxs-lookup"><span data-stu-id="144d0-120">Reference</span></span>  
 <span data-ttu-id="144d0-121"><xref:System.Windows.Forms.ToolBar> 類別</span><span class="sxs-lookup"><span data-stu-id="144d0-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="144d0-122">提供這個類別及其成員的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="144d0-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="144d0-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="144d0-123">Related Sections</span></span>  
 [<span data-ttu-id="144d0-124">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="144d0-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="144d0-125">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="144d0-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="144d0-126">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="144d0-126">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 <span data-ttu-id="144d0-127">描述可以在 Windows Forms 應用程式中裝載功能表、控制項和使用者控制項的工具列。</span><span class="sxs-lookup"><span data-stu-id="144d0-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
