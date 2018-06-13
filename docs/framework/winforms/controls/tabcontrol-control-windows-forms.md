---
title: TabControl 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- TabControl control [Windows Forms]
- tab controls
- tab controls [Windows Forms], creating
- multipage dialog boxes
- dialog boxes [Windows Forms], creating multipage
- property pages [Windows Forms], creating
- tab dialog boxes
ms.assetid: 915091af-93ac-4d3d-8283-738dd2d21ea7
ms.openlocfilehash: 91a9930a3678e08fc0e46335f1eb95330bd171a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536757"
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="028e3-102">TabControl 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="028e3-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="028e3-103">Windows Form `TabControl` 顯示多個索引標籤，像是在筆記本中的分隔線或在檔案櫃中一組資料夾的標籤。</span><span class="sxs-lookup"><span data-stu-id="028e3-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="028e3-104">索引標籤可以包含圖片和其他控制項。</span><span class="sxs-lookup"><span data-stu-id="028e3-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="028e3-105">使用 `TabControl` 建立屬性頁。</span><span class="sxs-lookup"><span data-stu-id="028e3-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="028e3-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="028e3-106">In This Section</span></span>  
 [<span data-ttu-id="028e3-107">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="028e3-107">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="028e3-108">說明此控制項是什麼，並說明其重要功能與屬性。</span><span class="sxs-lookup"><span data-stu-id="028e3-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="028e3-109">操作說明：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="028e3-109">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="028e3-110">提供如何在索引標籤頁上顯示控制項的指引。</span><span class="sxs-lookup"><span data-stu-id="028e3-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="028e3-111">操作說明：使用 Windows Forms TabControl 加入和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="028e3-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="028e3-112">提供如何在設計工具或程式碼中新增和移除索引標籤的指引。</span><span class="sxs-lookup"><span data-stu-id="028e3-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="028e3-113">操作說明：變更 Windows Forms TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="028e3-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="028e3-114">提供如何調整會影響個別索引標籤外觀之屬性的指引。</span><span class="sxs-lookup"><span data-stu-id="028e3-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="028e3-115">操作說明：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="028e3-115">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 <span data-ttu-id="028e3-116">說明如何限制存取索引標籤頁，可能會根據使用者認證而限制。</span><span class="sxs-lookup"><span data-stu-id="028e3-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="028e3-117">另請參閱[如何： 加入和移除的索引標籤與使用 Windows Form TabControl 設計工具](http://msdn.microsoft.com/library/ms233654\(v=vs.110\))， [How to： 將控制項加入索引標籤頁面使用設計工具](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="028e3-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [How to: Add a Control to a Tab Page Using the Designer](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="028e3-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="028e3-118">Reference</span></span>  
 <span data-ttu-id="028e3-119"><xref:System.Windows.Forms.TabControl> 類別</span><span class="sxs-lookup"><span data-stu-id="028e3-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="028e3-120">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="028e3-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="028e3-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="028e3-121">Related Sections</span></span>  
 [<span data-ttu-id="028e3-122">Windows Forms 中的對話方塊</span><span class="sxs-lookup"><span data-stu-id="028e3-122">Dialog Boxes in Windows Forms</span></span>](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="028e3-123">提供通常會顯示索引標籤之對話方塊的工作清單。</span><span class="sxs-lookup"><span data-stu-id="028e3-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="028e3-124">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="028e3-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="028e3-125">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="028e3-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
