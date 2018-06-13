---
title: 如何：停用加入和刪除 DataRepeater 項目 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590794"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="9a14a-102">如何：停用加入和刪除 DataRepeater 項目 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="9a14a-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="9a14a-103">根據預設，使用者可以新增或刪除的項目<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="9a14a-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="9a14a-104">使用者可以按 CTRL + N 加入新項目時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>焦點或按一下**AddNewItem**按鈕<xref:System.Windows.Forms.BindingNavigator>控制項。</span><span class="sxs-lookup"><span data-stu-id="9a14a-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="9a14a-105">使用者可以藉由按下刪除的項目刪除時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>焦點或按一下**DeleteItem**按鈕<xref:System.Windows.Forms.BindingNavigator>控制項。</span><span class="sxs-lookup"><span data-stu-id="9a14a-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="9a14a-106">新增及/或刪除在設計階段或執行階段，您可以停用。</span><span class="sxs-lookup"><span data-stu-id="9a14a-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="9a14a-107">若要停用加入和刪除在設計階段</span><span class="sxs-lookup"><span data-stu-id="9a14a-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="9a14a-108">在 Windows Form 設計工具中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="9a14a-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9a14a-109">您必須選取控制項的較低的區段。</span><span class="sxs-lookup"><span data-stu-id="9a14a-109">You must select the lower section of the control.</span></span> <span data-ttu-id="9a14a-110">如果您選取項目範本 > 一節，將會顯示一組不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a14a-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="9a14a-111">在 [屬性] 視窗中，設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="9a14a-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="9a14a-112">設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="9a14a-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="9a14a-113">在 Windows Form 設計工具中，選取 <xref:System.Windows.Forms.BindingNavigator>控制項，然後再按一下**AddNewItem**按鈕 （在其上的加號按鈕）。</span><span class="sxs-lookup"><span data-stu-id="9a14a-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="9a14a-114">在 [屬性] 視窗中，設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="9a14a-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="9a14a-115">在 Windows Form 設計工具中，選取 <xref:System.Windows.Forms.BindingNavigator>控制項，然後再按一下**DeleteItem**按鈕 （具有紅色 X 上的按鈕）。</span><span class="sxs-lookup"><span data-stu-id="9a14a-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="9a14a-116">在 [屬性] 視窗中，設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="9a14a-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="9a14a-117">在元件匣中，選取<xref:System.Windows.Forms.BindingSource>的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>繫結。</span><span class="sxs-lookup"><span data-stu-id="9a14a-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="9a14a-118">在 [屬性] 視窗中，設定<xref:System.Windows.Forms.BindingSource.AllowNew%2A>屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="9a14a-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="9a14a-119">在 [Windows Form 設計工具中，按兩下**DeleteItem** ] 按鈕以開啟程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="9a14a-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="9a14a-120">在 [事件] 下拉式清單中，選取`BindingNavigatorDeleteItem_EnabledChanged`事件。</span><span class="sxs-lookup"><span data-stu-id="9a14a-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="9a14a-121">將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="9a14a-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="9a14a-122">這是必要步驟，因為每次目前資料錄變更時， <xref:System.Windows.Forms.BindingSource> 都會啟用 [DeleteItem]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a14a-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="9a14a-123">若要停用加入和刪除執行階段</span><span class="sxs-lookup"><span data-stu-id="9a14a-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="9a14a-124">在 [Windows Form 設計工具] 中，按兩下表單開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="9a14a-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="9a14a-125">將下列程式碼加入 `Form_Load` 事件：</span><span class="sxs-lookup"><span data-stu-id="9a14a-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="9a14a-126">將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="9a14a-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="9a14a-127">這是必要步驟，因為每次目前資料錄變更時， <xref:System.Windows.Forms.BindingSource> 都會啟用 [DeleteItem]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a14a-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a14a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a14a-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="9a14a-129">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="9a14a-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="9a14a-130"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="9a14a-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
