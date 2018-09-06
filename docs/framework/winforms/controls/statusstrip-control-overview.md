---
title: StatusStrip 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: e40373dd05e59325cdb6c2272d5749f3828b0755
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864559"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="1e3f5-102">StatusStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1e3f5-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="1e3f5-103"><xref:System.Windows.Forms.StatusStrip> 控制項會顯示 <xref:System.Windows.Forms.Form> 上正在檢視之物件或該物件之元件的相關資訊，或顯示與該物件在您的應用程式中作業相關的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="1e3f5-104">一般而言，<xref:System.Windows.Forms.StatusStrip> 控制項是由 <xref:System.Windows.Forms.ToolStripStatusLabel> 物件所組成，其中每個物件會顯示文字和 (或) 圖示。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="1e3f5-105"><xref:System.Windows.Forms.StatusStrip> 也可以包含 <xref:System.Windows.Forms.ToolStripDropDownButton>、<xref:System.Windows.Forms.ToolStripSplitButton> 和 <xref:System.Windows.Forms.ToolStripProgressBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="1e3f5-106">預設 <xref:System.Windows.Forms.StatusStrip> 沒有面板。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="1e3f5-107">若要將面板加入 <xref:System.Windows.Forms.StatusStrip>，請使用 <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1e3f5-108">在 Visual Studio 中，已針對處理 <xref:System.Windows.Forms.StatusStrip> 項目和常用命令提供廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="1e3f5-109">另請參閱[StatusStrip 項目集合編輯器](https://msdn.microsoft.com/library/ms233631\(v=vs.110\))， [StatusStrip 工作對話方塊](https://msdn.microsoft.com/library/ms233642\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-109">Also see [StatusStrip Items Collection Editor](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="1e3f5-110">雖然 <xref:System.Windows.Forms.StatusStrip> 會取代及擴充舊版的 <xref:System.Windows.Forms.StatusBar> 控制項，但是您也可以選擇保留 <xref:System.Windows.Forms.StatusBar>，以提供回溯相容性及供未來使用。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="1e3f5-111">重要的 StatusStrip 成員</span><span class="sxs-lookup"><span data-stu-id="1e3f5-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="1e3f5-112">名稱</span><span class="sxs-lookup"><span data-stu-id="1e3f5-112">Name</span></span>|<span data-ttu-id="1e3f5-113">描述</span><span class="sxs-lookup"><span data-stu-id="1e3f5-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="1e3f5-114">取得或設定值，表示 <xref:System.Windows.Forms.StatusStrip> 是否支援溢位功能。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="1e3f5-115">取得或設定值，表示 <xref:System.Windows.Forms.StatusStrip> 是否會在其 <xref:System.Windows.Forms.ToolStripContainer> 中的兩端之間自動縮放。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="1e3f5-116">重要的 StatusStrip 附屬類別</span><span class="sxs-lookup"><span data-stu-id="1e3f5-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="1e3f5-117">名稱</span><span class="sxs-lookup"><span data-stu-id="1e3f5-117">Name</span></span>|<span data-ttu-id="1e3f5-118">描述</span><span class="sxs-lookup"><span data-stu-id="1e3f5-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="1e3f5-119">代表 <xref:System.Windows.Forms.StatusStrip> 控制項中的面板。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="1e3f5-120">顯示關聯的 <xref:System.Windows.Forms.ToolStripDropDown>，使用者可從中選取單一項目。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="1e3f5-121">代表由兩個部分組成的控制項，其中一部分是標準按鈕，另一部分是下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="1e3f5-122">顯示處理序的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="1e3f5-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e3f5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e3f5-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
