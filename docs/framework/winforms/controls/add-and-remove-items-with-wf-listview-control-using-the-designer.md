---
title: HOW TO：使用設計工具以 Windows Forms ListView 控制項新增和移除項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 37660061140e38661a27f8f750604ae2609ac57c
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882285"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="19afc-102">作法：使用設計工具以 Windows Forms ListView 控制項新增和移除項目</span><span class="sxs-lookup"><span data-stu-id="19afc-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="19afc-103">加入 Windows Form 中的項目中的程序<xref:System.Windows.Forms.ListView>控制主要包含指定的項目，並將屬性指派給它。</span><span class="sxs-lookup"><span data-stu-id="19afc-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="19afc-104">隨時都可以新增或移除清單項目。</span><span class="sxs-lookup"><span data-stu-id="19afc-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="19afc-105">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="19afc-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="19afc-106">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="19afc-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19afc-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="19afc-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="19afc-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="19afc-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="19afc-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="19afc-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="19afc-110">若要新增或移除項目使用設計工具</span><span class="sxs-lookup"><span data-stu-id="19afc-110">To add or remove items using the designer</span></span>  
  
1. <span data-ttu-id="19afc-111">選取 <xref:System.Windows.Forms.ListView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="19afc-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="19afc-112">在 [**屬性**] 視窗中，按一下**省略符號**(![。 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 按鈕旁<xref:System.Windows.Forms.ListView.Items%2A>屬性.</span><span class="sxs-lookup"><span data-stu-id="19afc-112">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="19afc-113">**ListViewItem 集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="19afc-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3. <span data-ttu-id="19afc-114">若要加入的項目，按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19afc-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="19afc-115">您可以再設定屬性的新的項目，例如<xref:System.Windows.Forms.ListView.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="19afc-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4. <span data-ttu-id="19afc-116">若要移除的項目，請選取它，然後按一下**移除** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19afc-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19afc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19afc-117">See also</span></span>

- [<span data-ttu-id="19afc-118">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="19afc-118">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="19afc-119">如何：資料行加入 Windows Form ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="19afc-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="19afc-120">如何：使用 Windows Forms ListView 控制項的資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="19afc-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="19afc-121">如何：Windows Form ListView 控制項中顯示的圖示</span><span class="sxs-lookup"><span data-stu-id="19afc-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="19afc-122">如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="19afc-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="19afc-123">如何：在 Windows Form ListView 控制項中的群組項目</span><span class="sxs-lookup"><span data-stu-id="19afc-123">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
