---
title: 逐步解說：在設計階段變更已裝載之 WPF 項目的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: 15cab9266af5840aa4b37a62b71bd5010b7a859a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741016"
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="cd093-102">逐步解說：在設計階段變更已裝載之 WPF 項目的屬性</span><span class="sxs-lookup"><span data-stu-id="cd093-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="cd093-103">本逐步解說示範如何變更 Windows Form 上裝載的 Windows Presentation Foundation (WPF) 控制項的屬性值。</span><span class="sxs-lookup"><span data-stu-id="cd093-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="cd093-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="cd093-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="cd093-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="cd093-105">Create the project.</span></span>  
  
-   <span data-ttu-id="cd093-106">建立 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="cd093-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="cd093-107">在 Windows Form 上裝載 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="cd093-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="cd093-108">使用 WPF Designer for Visual Studio 來變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="cd093-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd093-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="cd093-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cd093-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="cd093-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cd093-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="cd093-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cd093-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="cd093-112">Prerequisites</span></span>  
 <span data-ttu-id="cd093-113">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="cd093-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="cd093-114">.</span><span class="sxs-lookup"><span data-stu-id="cd093-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="cd093-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="cd093-115">Creating the Project</span></span>  
 <span data-ttu-id="cd093-116">第一個步驟是建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="cd093-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd093-117">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="cd093-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="cd093-118">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="cd093-118">To create the project</span></span>  
  
-   <span data-ttu-id="cd093-119">建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`WpfHost`。</span><span class="sxs-lookup"><span data-stu-id="cd093-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="cd093-120">建立 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="cd093-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="cd093-121">在將 WPF 控制項加入專案後，即可在表單上予以排列。</span><span class="sxs-lookup"><span data-stu-id="cd093-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="cd093-122">建立 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="cd093-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="cd093-123">將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="cd093-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="cd093-124">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="cd093-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="cd093-125">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="cd093-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="cd093-126">在 **屬性**視窗中，設定的值<xref:System.Windows.Controls.Control.Background%2A>屬性設`Blue`。</span><span class="sxs-lookup"><span data-stu-id="cd093-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="cd093-127">建置專案。</span><span class="sxs-lookup"><span data-stu-id="cd093-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="cd093-128">變更 WPF 控制項的屬性值</span><span class="sxs-lookup"><span data-stu-id="cd093-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="cd093-129"><xref:System.Windows.Forms.Integration.ElementHost> 智慧標籤可藉由使用 WPF 設計工具，輕鬆地變更裝載 WPF 內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd093-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="cd093-130">裝載 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="cd093-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="cd093-131">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="cd093-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="cd093-132">在**工具箱**，請在**WPF 使用者控制項**索引標籤上，按兩下`UserControl1`若要建立的執行個體`UserControl1`表單上。</span><span class="sxs-lookup"><span data-stu-id="cd093-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="cd093-133">`UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="cd093-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="cd093-134">在  **ElementHost 工作**智慧標籤面板中，選取**編輯裝載內容**。</span><span class="sxs-lookup"><span data-stu-id="cd093-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="cd093-135">UserControl1.xaml 檔案會在 WPF 設計工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="cd093-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="cd093-136">在 **屬性**視窗中，設定的值<xref:System.Windows.Controls.Control.Background%2A>屬性設`Red`。</span><span class="sxs-lookup"><span data-stu-id="cd093-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="cd093-137">重建專案。</span><span class="sxs-lookup"><span data-stu-id="cd093-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="cd093-138">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="cd093-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="cd093-139">`UserControl1` 的執行個體具有紅色背景。</span><span class="sxs-lookup"><span data-stu-id="cd093-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd093-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd093-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="cd093-141">操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="cd093-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="cd093-142">操作說明：在設計階段將控制項對齊表單邊緣</span><span class="sxs-lookup"><span data-stu-id="cd093-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="cd093-143">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="cd093-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="cd093-144">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="cd093-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="cd093-145">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="cd093-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="cd093-146">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="cd093-146">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
