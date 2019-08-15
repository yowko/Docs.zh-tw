---
title: HOW TO：使用設計工具以 Windows Forms TabControl 新增和移除索引標籤
ms.date: 03/30/2017
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
ms.openlocfilehash: da9a9d40529a1902c58f67d6a8696d8906eb34c9
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040066"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="09590-102">作法：使用設計工具以 Windows Forms TabControl 新增和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="09590-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="09590-103">當您將<xref:System.Windows.Forms.TabControl>控制項放在表單上時, 預設會包含兩個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="09590-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="09590-104">您可以使用設計工具來新增或移除索引標籤。</span><span class="sxs-lookup"><span data-stu-id="09590-104">You can add or remove tabs using the designer.</span></span>

 <span data-ttu-id="09590-105">下列程式需要具有包含<xref:System.Windows.Forms.TabControl>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="09590-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="09590-106">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="09590-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="09590-107">若要使用設計工具加入或移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="09590-107">To add or remove a tab using the designer</span></span>

- <span data-ttu-id="09590-108">在控制項的智慧標籤上, 按一下 [**新增]** 索引標籤或 [移除索引標籤 **]**</span><span class="sxs-lookup"><span data-stu-id="09590-108">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>

     <span data-ttu-id="09590-109">-或-</span><span class="sxs-lookup"><span data-stu-id="09590-109">-or-</span></span>

     <span data-ttu-id="09590-110">在 [**屬性**] 視窗中<xref:System.Windows.Forms.TabControl.TabPages%2A> , 按一下屬性旁邊![的**省略號**按鈕 (... Visual Studio](./media/visual-studio-ellipsis-button.png)屬性視窗), 以開啟 [ **TabPage 集合編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="09590-110">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="09590-111">按一下 [**新增**] 或 [**移除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="09590-111">Click the **Add** or **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="09590-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09590-112">See also</span></span>

- [<span data-ttu-id="09590-113">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="09590-113">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="09590-114">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="09590-114">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="09590-115">如何：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="09590-115">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="09590-116">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="09590-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="09590-117">如何：變更 Windows Forms TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="09590-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
