---
title: SplitContainer 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: d860763e935c88619e3355661038757d00247dfd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963581"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="332cc-102">SplitContainer 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="332cc-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="332cc-103">Windows Form `SplitContainer` 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。</span><span class="sxs-lookup"><span data-stu-id="332cc-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="332cc-104">將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。</span><span class="sxs-lookup"><span data-stu-id="332cc-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="332cc-105">在 [**工具箱**] 中, 這個控制項<xref:System.Windows.Forms.Splitter>會取代舊版 Visual Studio 中的控制項。</span><span class="sxs-lookup"><span data-stu-id="332cc-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="332cc-106">`SplitContainer` 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。</span><span class="sxs-lookup"><span data-stu-id="332cc-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="332cc-107">.NET Framework 中仍會包含 <xref:System.Windows.Forms.Splitter> 類別，以與現有的應用程式相容，但強烈建議您在新專案中使用 `SplitContainer` 控制項。</span><span class="sxs-lookup"><span data-stu-id="332cc-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="332cc-108">`SplitContainer` 控制項可讓您建立複雜的使用者介面；通常，在某個面板中選取的項目會決定在另一個面板中所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="332cc-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="332cc-109">這種排列方式可有效地顯示及瀏覽資訊。</span><span class="sxs-lookup"><span data-stu-id="332cc-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="332cc-110">擁有兩個面板可讓您彙總區域中的資訊，而分隔列 (或「分隔器」) 可讓使用者輕鬆調整面板的大小。</span><span class="sxs-lookup"><span data-stu-id="332cc-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="332cc-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="332cc-111">In This Section</span></span>  
 [<span data-ttu-id="332cc-112">SplitContainer 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="332cc-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="332cc-113">介紹 `SplitContainer` 控制項，並描述常用的屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="332cc-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="332cc-114">如何：定義分割視窗中的調整大小和位置行為</span><span class="sxs-lookup"><span data-stu-id="332cc-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="332cc-115">描述如何在 `SplitContainer` 控制項中控制分隔器。</span><span class="sxs-lookup"><span data-stu-id="332cc-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="332cc-116">如何：水準分割視窗</span><span class="sxs-lookup"><span data-stu-id="332cc-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="332cc-117">描述如何在 `SplitContainer` 控制項中控制分隔器的方向。</span><span class="sxs-lookup"><span data-stu-id="332cc-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="332cc-118">如何：建立具有 Windows Forms 的多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="332cc-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="332cc-119">建立與 Microsoft Outlook 中所用類似的多窗格使用者介面。</span><span class="sxs-lookup"><span data-stu-id="332cc-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="332cc-120">另請[參閱如何:使用設計](how-to-split-a-window-horizontally-using-the-designer.md)工具水準分割視窗, [如何:在 windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md)上建立 windows Explorer 樣式的介面, [how to:使用設計](create-a-multipane-user-interface-with-wf-using-the-designer.md)工具建立具有 Windows Forms 的多窗格使用者介面。</span><span class="sxs-lookup"><span data-stu-id="332cc-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="332cc-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="332cc-121">Reference</span></span>  
 <span data-ttu-id="332cc-122"><xref:System.Windows.Forms.SplitContainer> 類別</span><span class="sxs-lookup"><span data-stu-id="332cc-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="332cc-123">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="332cc-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="332cc-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="332cc-124">Related Sections</span></span>  
 [<span data-ttu-id="332cc-125">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="332cc-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="332cc-126">提供專為搭配 Windows Form 使用所設計之控制項的相關主題連結。</span><span class="sxs-lookup"><span data-stu-id="332cc-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="332cc-127">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="332cc-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="332cc-128">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="332cc-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
