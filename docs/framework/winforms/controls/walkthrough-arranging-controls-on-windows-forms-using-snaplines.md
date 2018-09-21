---
title: 逐步解說：使用對齊線排列 Windows Form 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 170b79f03515ab371f7013c267b28ba85dafd0f5
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525759"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a><span data-ttu-id="96870-102">逐步解說：使用對齊線排列 Windows Form 上的控制項</span><span class="sxs-lookup"><span data-stu-id="96870-102">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>
<span data-ttu-id="96870-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="96870-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="96870-104">Windows Form 設計工具會提供您許多版面配置工具，來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="96870-104">The Windows Forms Designer gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="96870-105">其中一個最重要的是<xref:System.Windows.Forms.Design.Behavior.SnapLine>功能。</span><span class="sxs-lookup"><span data-stu-id="96870-105">One of the most important is the <xref:System.Windows.Forms.Design.Behavior.SnapLine> feature.</span></span>  
  
 <span data-ttu-id="96870-106">對齊線所顯示的精確對齊控制項與其他控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-106">Snaplines show you precisely where to line up controls with other controls.</span></span> <span data-ttu-id="96870-107">也會顯示您的 Windows 使用者介面指導方針所指定的控制項之間的邊界的建議的距離。</span><span class="sxs-lookup"><span data-stu-id="96870-107">They also show you the recommended distances for margins between controls, as specified by the Windows User Interface Guidelines.</span></span> <span data-ttu-id="96870-108">如需詳細資訊，請參閱 <<c0> [ 使用者介面設計和開發](https://go.microsoft.com/FWLink/?LinkId=83878)。</span><span class="sxs-lookup"><span data-stu-id="96870-108">For details, see [User Interface Design and Development](https://go.microsoft.com/FWLink/?LinkId=83878).</span></span>  
  
 <span data-ttu-id="96870-109">對齊線讓您輕鬆對齊控制項，以產生簡潔、 專業外觀和行為 （外觀及操作）。</span><span class="sxs-lookup"><span data-stu-id="96870-109">Snaplines make it easy to align your controls, for crisp, professional appearance and behavior (look and feel).</span></span>  
  
 <span data-ttu-id="96870-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="96870-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="96870-111">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="96870-111">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="96870-112">間距，以及對齊這些控制項使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-112">Spacing and Aligning Controls Using Snaplines</span></span>  
  
-   <span data-ttu-id="96870-113">對齊表單及容器的邊界</span><span class="sxs-lookup"><span data-stu-id="96870-113">Aligning to Form and Container Margins</span></span>  
  
-   <span data-ttu-id="96870-114">群組的控制項對齊</span><span class="sxs-lookup"><span data-stu-id="96870-114">Aligning to Grouped Controls</span></span>  
  
-   <span data-ttu-id="96870-115">使用對齊線來放置控制項框大小</span><span class="sxs-lookup"><span data-stu-id="96870-115">Using Snaplines to Place a Control by Outlining Its Size</span></span>  
  
-   <span data-ttu-id="96870-116">從 [工具箱] 拖曳控制項時，使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-116">Using Snaplines When Dragging a Control from the Toolbox</span></span>  
  
-   <span data-ttu-id="96870-117">使用對齊線的控制項調整大小</span><span class="sxs-lookup"><span data-stu-id="96870-117">Resizing Controls Using Snaplines</span></span>  
  
-   <span data-ttu-id="96870-118">對齊控制項的文字標籤</span><span class="sxs-lookup"><span data-stu-id="96870-118">Aligning a Label to a Control's Text</span></span>  
  
-   <span data-ttu-id="96870-119">使用對齊線，使用鍵盤巡覽</span><span class="sxs-lookup"><span data-stu-id="96870-119">Using Snaplines with Keyboard Navigation</span></span>  
  
-   <span data-ttu-id="96870-120">對齊線和版面配置面板</span><span class="sxs-lookup"><span data-stu-id="96870-120">Snaplines and Layout Panels</span></span>  
  
-   <span data-ttu-id="96870-121">停用的對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-121">Disabling Snaplines</span></span>  
  
 <span data-ttu-id="96870-122">當您完成時，您將了解的版面配置功能所扮演角色對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-122">When you are finished, you will have an understanding of the layout role played by the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96870-123">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="96870-123">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="96870-124">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="96870-124">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="96870-125">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="96870-125">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="96870-126">建立專案</span><span class="sxs-lookup"><span data-stu-id="96870-126">Creating the Project</span></span>  
 <span data-ttu-id="96870-127">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="96870-127">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="96870-128">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="96870-128">To create the project</span></span>  
  
1.  <span data-ttu-id="96870-129">建立以 Windows 為基礎的應用程式專案，稱為 「 SnaplineExample"(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="96870-129">Create a Windows-based application project called "SnaplineExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="96870-130">在 表單設計工具中選取的表單。</span><span class="sxs-lookup"><span data-stu-id="96870-130">Select the form in the Forms Designer.</span></span>  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a><span data-ttu-id="96870-131">間距，以及對齊這些控制項使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-131">Spacing and Aligning Controls Using Snaplines</span></span>  
 <span data-ttu-id="96870-132">對齊線可讓您精確且直覺的方法，來調整您的表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-132">Snaplines give you an accurate and intuitive way to align controls on your form.</span></span> <span data-ttu-id="96870-133">當您要移動選取的控制項附近的位置時，會配合其他控制項或一組控制項便會出現。</span><span class="sxs-lookup"><span data-stu-id="96870-133">They appear when you are moving a selected control or controls near a position that would align with another control or set of controls.</span></span> <span data-ttu-id="96870-134">您的選擇會 「 貼齊 」 建議的位置，您將它移過去的其他控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-134">Your selection will "snap" to the suggested position as you move it past the other controls.</span></span>  
  
#### <a name="to-arrange-controls-using-snaplines"></a><span data-ttu-id="96870-135">使用對齊線排列控制項</span><span class="sxs-lookup"><span data-stu-id="96870-135">To arrange controls using snaplines</span></span>  
  
1.  <span data-ttu-id="96870-136">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-136">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="96870-137">移動<xref:System.Windows.Forms.Button>表單的右下角的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-137">Move the <xref:System.Windows.Forms.Button> control to the lower-right corner of the form.</span></span> <span data-ttu-id="96870-138">請注意，會顯示對齊線<xref:System.Windows.Forms.Button>控制方法的下框線和右框線的表單。</span><span class="sxs-lookup"><span data-stu-id="96870-138">Note the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the form.</span></span> <span data-ttu-id="96870-139">這些對齊線會顯示控制項的框線和表單的建議的距離。</span><span class="sxs-lookup"><span data-stu-id="96870-139">These snaplines display the recommended distance between the borders of the control and the form.</span></span>  
  
3.  <span data-ttu-id="96870-140">移動<xref:System.Windows.Forms.Button>控制項四周框線之表單和對齊線的出現位置的附註。</span><span class="sxs-lookup"><span data-stu-id="96870-140">Move the <xref:System.Windows.Forms.Button> control around the borders of the form and note where the snaplines appear.</span></span> <span data-ttu-id="96870-141">當您完成時，移動<xref:System.Windows.Forms.Button>表單中央附近的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-141">When you are finished, move the <xref:System.Windows.Forms.Button> control near the center of the form.</span></span>  
  
4.  <span data-ttu-id="96870-142">將另一個<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-142">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
5.  <span data-ttu-id="96870-143">將第二個<xref:System.Windows.Forms.Button>控制為止幾乎層級的第一個。</span><span class="sxs-lookup"><span data-stu-id="96870-143">Move the second <xref:System.Windows.Forms.Button> control until it is nearly level with the first.</span></span> <span data-ttu-id="96870-144">請注意會出現在這兩個按鈕的文字基準線對齊線，並請注意，您要移動的控制項會貼齊至完全與另一個控制項的層級的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-144">Note the snapline that appears at the text baseline of both buttons, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>  
  
6.  <span data-ttu-id="96870-145">將第二個<xref:System.Windows.Forms.Button>控制，直到將其置於第一個的正上方。</span><span class="sxs-lookup"><span data-stu-id="96870-145">Move the second <xref:System.Windows.Forms.Button> control until it is positioned directly above the first.</span></span> <span data-ttu-id="96870-146">請注意對齊線出現在這兩個按鈕、 左和右邊緣，並請注意，控制項就移動的貼齊至完全配合其他控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-146">Note the snaplines that appear along the left and right edges of both buttons, and note that the control you are moving snaps to a position that is exactly aligned with the other control.</span></span>  
  
7.  <span data-ttu-id="96870-147">選取其中一個<xref:System.Windows.Forms.Button>控制，並移動接近另一個，直到幾乎碰觸。</span><span class="sxs-lookup"><span data-stu-id="96870-147">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span> <span data-ttu-id="96870-148">請注意，出現在它們之間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-148">Note the snapline that appears between them.</span></span> <span data-ttu-id="96870-149">這個距離很控制項的框線之間的建議的距離。</span><span class="sxs-lookup"><span data-stu-id="96870-149">This distance is the recommended distance between the borders of the controls.</span></span> <span data-ttu-id="96870-150">也請注意，您要移動的控制項會貼齊至這個位置。</span><span class="sxs-lookup"><span data-stu-id="96870-150">Also note that the control you are moving snaps to this position.</span></span>  
  
8.  <span data-ttu-id="96870-151">將兩個<xref:System.Windows.Forms.Panel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-151">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto your form.</span></span>  
  
9. <span data-ttu-id="96870-152">移動其中一個<xref:System.Windows.Forms.Panel>控制項，直到它是第一個幾乎層級為止。</span><span class="sxs-lookup"><span data-stu-id="96870-152">Move one of the <xref:System.Windows.Forms.Panel> controls until it is nearly level with the first.</span></span> <span data-ttu-id="96870-153">請注意對齊線出現在兩個控制項中，頂端和底部邊緣，並請注意，您要移動的控制項會貼齊至完全與另一個控制項的層級的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-153">Note the snaplines that appear along the top and bottom edges of both controls, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>  
  
## <a name="aligning-to-form-and-container-margins"></a><span data-ttu-id="96870-154">對齊表單及容器的邊界</span><span class="sxs-lookup"><span data-stu-id="96870-154">Aligning to Form and Container Margins</span></span>  
 <span data-ttu-id="96870-155">對齊線可協助您對齊表單和容器的邊界控制項以一致的方式。</span><span class="sxs-lookup"><span data-stu-id="96870-155">Snaplines help you to align your controls to form and container margins in a consistent manner.</span></span>  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a><span data-ttu-id="96870-156">若要對齊控制項加入表單和容器的邊界</span><span class="sxs-lookup"><span data-stu-id="96870-156">To align controls to form and container margins</span></span>  
  
1.  <span data-ttu-id="96870-157">選取其中一個<xref:System.Windows.Forms.Button>控制，並將它移靠近右框線的表單中，直到對齊線出現。</span><span class="sxs-lookup"><span data-stu-id="96870-157">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="96870-158">右框線的對齊線的距離是控制項的總和<xref:System.Windows.Forms.Control.Margin%2A>屬性和表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性值。</span><span class="sxs-lookup"><span data-stu-id="96870-158">The snapline's distance from the right border is the sum of the control's <xref:System.Windows.Forms.Control.Margin%2A> property and the form's <xref:System.Windows.Forms.Control.Padding%2A> property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96870-159">如果表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性設定為 0,0,0,0、 Windows Form 設計工具，可讓表單遮蔽<xref:System.Windows.Forms.Control.Padding%2A>9,9,9,9 的值。</span><span class="sxs-lookup"><span data-stu-id="96870-159">If the form's <xref:System.Windows.Forms.Control.Padding%2A> property is set to 0,0,0,0, the Windows Forms Designer gives the form a shadowed <xref:System.Windows.Forms.Control.Padding%2A> value of 9,9,9,9.</span></span> <span data-ttu-id="96870-160">若要覆寫此行為，請指派 0,0,0,0 以外的值。</span><span class="sxs-lookup"><span data-stu-id="96870-160">To override this behavior, assign a value other than 0,0,0,0.</span></span>  
  
1.  <span data-ttu-id="96870-161">值變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性來擴充<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性設為 0。</span><span class="sxs-lookup"><span data-stu-id="96870-161">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 0.</span></span> <span data-ttu-id="96870-162">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 以配置出 Windows Form 控制項和邊框距離、 邊界和 AutoSize 屬性](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)。</span><span class="sxs-lookup"><span data-stu-id="96870-162">For details, see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).</span></span>  
  
2.  <span data-ttu-id="96870-163">移動<xref:System.Windows.Forms.Button>接近直到對齊線出現在表單的右框線的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-163">Move the <xref:System.Windows.Forms.Button> control close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="96870-164">這個距離現在指定表單的值來<xref:System.Windows.Forms.Control.Padding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="96870-164">This distance is now given by the value of the form's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
3.  <span data-ttu-id="96870-165">拖曳<xref:System.Windows.Forms.GroupBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-165">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="96870-166">值變更<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>展開屬性<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>為 10 的屬性。</span><span class="sxs-lookup"><span data-stu-id="96870-166">Change the value of the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 10.</span></span>  
  
5.  <span data-ttu-id="96870-167">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-167">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
6.  <span data-ttu-id="96870-168">移動<xref:System.Windows.Forms.Button>控制項的右框線接近<xref:System.Windows.Forms.GroupBox>控制項直到對齊線隨即出現。</span><span class="sxs-lookup"><span data-stu-id="96870-168">Move the <xref:System.Windows.Forms.Button> control close to the right border of the <xref:System.Windows.Forms.GroupBox> control until a snapline appears.</span></span> <span data-ttu-id="96870-169">移動<xref:System.Windows.Forms.Button>控制項中<xref:System.Windows.Forms.GroupBox>控制項和對齊線的出現位置的附註。</span><span class="sxs-lookup"><span data-stu-id="96870-169">Move the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and note where the snaplines appear.</span></span>  
  
## <a name="aligning-to-grouped-controls"></a><span data-ttu-id="96870-170">群組的控制項對齊</span><span class="sxs-lookup"><span data-stu-id="96870-170">Aligning to Grouped Controls</span></span>  
 <span data-ttu-id="96870-171">您可以使用對齊線來對齊控制項群組也可做為控制內<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-171">You can use snaplines to align grouped controls as well as controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
#### <a name="to-align-to-grouped-controls"></a><span data-ttu-id="96870-172">將群組的控制項對齊</span><span class="sxs-lookup"><span data-stu-id="96870-172">To align to grouped controls</span></span>  
  
1.  <span data-ttu-id="96870-173">選取您的表單上控制項的兩個。</span><span class="sxs-lookup"><span data-stu-id="96870-173">Select two of the controls on your form.</span></span> <span data-ttu-id="96870-174">移動選取項目，並注意會出現在您的選取項目和其他控制項之間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-174">Move the selection around and note the snaplines that appear between your selection and the other controls.</span></span>  
  
2.  <span data-ttu-id="96870-175">拖曳<xref:System.Windows.Forms.GroupBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-175">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>  
  
3.  <span data-ttu-id="96870-176">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-176">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
4.  <span data-ttu-id="96870-177">選取其中一個<xref:System.Windows.Forms.Button>控制項，並予以四處移動<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-177">Select one of the <xref:System.Windows.Forms.Button> controls and move it around the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="96870-178">請注意會出現在邊緣對齊線<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-178">Note the snaplines that appear at the edges of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="96870-179">也請注意會出現在邊緣對齊線<xref:System.Windows.Forms.Button>所包含的控制項<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-179">Also note the snaplines that appear at the edges of the <xref:System.Windows.Forms.Button> control that is contained by the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="96870-180">子系的容器控制項的控制項也支援對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-180">Controls that are children of a container control also support snaplines.</span></span>  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="96870-181">使用對齊線來放置控制項框大小</span><span class="sxs-lookup"><span data-stu-id="96870-181">Using Snaplines to Place a Control by Outlining Its Size</span></span>  
 <span data-ttu-id="96870-182">對齊線可協助您讓控制當您第一次將它們放在表單上。</span><span class="sxs-lookup"><span data-stu-id="96870-182">Snaplines help you align controls when you first place them on a form.</span></span>  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="96870-183">使用對齊線來放置控制項框大小</span><span class="sxs-lookup"><span data-stu-id="96870-183">To use snaplines to place a control by outlining its size</span></span>  
  
1.  <span data-ttu-id="96870-184">按一下 [工具箱] 的 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="96870-184">In the **Toolbox**, click the <xref:System.Windows.Forms.Button> control icon.</span></span> <span data-ttu-id="96870-185">請勿拖曳到表單。</span><span class="sxs-lookup"><span data-stu-id="96870-185">Do not drag it onto the form.</span></span>  
  
2.  <span data-ttu-id="96870-186">將滑鼠指標移至表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="96870-186">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="96870-187">請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="96870-187">Note that the pointer changes to a crosshair with the <xref:System.Windows.Forms.Button> control icon attached.</span></span> <span data-ttu-id="96870-188">也請注意對齊線來建議對齊的位置可<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-188">Also note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
3.  <span data-ttu-id="96870-189">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="96870-189">Click and hold the mouse button.</span></span>  
  
4.  <span data-ttu-id="96870-190">拖曳滑鼠指標圍繞表單。</span><span class="sxs-lookup"><span data-stu-id="96870-190">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="96870-191">請注意，已繪製外框，指出的位置和控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="96870-191">Note that an outline is drawn, indicating the position and the size of the control.</span></span>  
  
5.  <span data-ttu-id="96870-192">拖曳滑鼠指標，使其與另一個控制項在表單上對齊。</span><span class="sxs-lookup"><span data-stu-id="96870-192">Drag the pointer until it aligns with another control on the form.</span></span> <span data-ttu-id="96870-193">請注意，以指出對齊方式會出現 「 對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-193">Note that a snapline appears to indicate alignment.</span></span>  
  
6.  <span data-ttu-id="96870-194">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="96870-194">Release the mouse button.</span></span> <span data-ttu-id="96870-195">建立控制項的位置與由外框的大小。</span><span class="sxs-lookup"><span data-stu-id="96870-195">The control is created at the position and size indicated by the outline.</span></span>  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="96870-196">從 [工具箱] 拖曳控制項時，使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-196">Using Snaplines When Dragging a Control from the Toolbox</span></span>  
 <span data-ttu-id="96870-197">對齊線可協助您讓控制項時將它們從拖曳**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-197">Snaplines help you align controls when you drag them from the **Toolbox** onto your form.</span></span>  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="96870-198">若要從 [工具箱] 拖曳控制項時可以使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-198">To use snaplines when dragging a control from the Toolbox</span></span>  
  
1.  <span data-ttu-id="96870-199">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單，而不是釋放滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="96870-199">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form, but do not release the mouse button.</span></span>  
  
2.  <span data-ttu-id="96870-200">將滑鼠指標移至表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="96870-200">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="96870-201">請注意，指標會變更以指出之位置的新<xref:System.Windows.Forms.Button>會建立控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-201">Note that the pointer changes to indicate the position at which the new <xref:System.Windows.Forms.Button> control will be created.</span></span>  
  
3.  <span data-ttu-id="96870-202">拖曳滑鼠指標圍繞表單。</span><span class="sxs-lookup"><span data-stu-id="96870-202">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="96870-203">請注意對齊線來建議對齊的位置可<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-203">Note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="96870-204">尋找與其他控制項對齊的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-204">Find a position that is aligned with other controls.</span></span>  
  
4.  <span data-ttu-id="96870-205">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="96870-205">Release the mouse button.</span></span> <span data-ttu-id="96870-206">對齊線所指定的位置在建立控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-206">The control is created at the position indicated by the snaplines.</span></span>  
  
## <a name="resizing-controls-using-snaplines"></a><span data-ttu-id="96870-207">使用對齊線的控制項調整大小</span><span class="sxs-lookup"><span data-stu-id="96870-207">Resizing Controls Using Snaplines</span></span>  
 <span data-ttu-id="96870-208">對齊線可協助您對齊控制項，調整其大小。</span><span class="sxs-lookup"><span data-stu-id="96870-208">Snaplines help you align controls as you resize them.</span></span>  
  
#### <a name="to-resize-a-control-using-snaplines"></a><span data-ttu-id="96870-209">若要調整大小的控制項使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-209">To resize a control using snaplines</span></span>  
  
1.  <span data-ttu-id="96870-210">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-210">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="96870-211">調整大小<xref:System.Windows.Forms.Button>角調整大小控點，並拖曳抓取其中的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-211">Resize the <xref:System.Windows.Forms.Button> control by grabbing one of the corner sizing handles and dragging.</span></span> <span data-ttu-id="96870-212">如需詳細資訊，請參閱 <<c0> [ 如何： 調整 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="96870-212">For details, see [How to: Resize Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="96870-213">拖曳調整大小控點，直到其中一個<xref:System.Windows.Forms.Button>與另一個控制項對齊控制項的框線。</span><span class="sxs-lookup"><span data-stu-id="96870-213">Drag the sizing handle until one of the <xref:System.Windows.Forms.Button> control's borders is aligned with another control.</span></span> <span data-ttu-id="96870-214">請注意，對齊線隨即出現。</span><span class="sxs-lookup"><span data-stu-id="96870-214">Note that a snapline appears.</span></span> <span data-ttu-id="96870-215">也請注意，調整大小控點會貼齊至對齊線所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-215">Also note that the sizing handle snaps to the position indicated by the snapline.</span></span>  
  
4.  <span data-ttu-id="96870-216">調整大小<xref:System.Windows.Forms.Button>控制不同的方向，以及對齊的縮放控點，不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-216">Resize the <xref:System.Windows.Forms.Button> control in different directions and align the sizing handle to different controls.</span></span> <span data-ttu-id="96870-217">請注意如何對齊線出現在不同的方向，以指出對齊方式。</span><span class="sxs-lookup"><span data-stu-id="96870-217">Note how the snaplines appear in various orientations to indicate alignment.</span></span>  
  
## <a name="aligning-a-label-to-a-controls-text"></a><span data-ttu-id="96870-218">對齊控制項的文字標籤</span><span class="sxs-lookup"><span data-stu-id="96870-218">Aligning a Label to a Control's Text</span></span>  
 <span data-ttu-id="96870-219">某些控制項提供對齊其他控制項來顯示文字的對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-219">Some controls offer a snapline for aligning other controls to displayed text.</span></span>  
  
#### <a name="to-align-a-label-to-a-controls-text"></a><span data-ttu-id="96870-220">若要對齊控制項的文字標籤</span><span class="sxs-lookup"><span data-stu-id="96870-220">To align a label to a control's text</span></span>  
  
1.  <span data-ttu-id="96870-221">拖曳<xref:System.Windows.Forms.TextBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-221">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="96870-222">當您卸除<xref:System.Windows.Forms.TextBox>控制項拖曳至表單中，按一下智慧標籤圖像 （glyph），然後選取**將文字設定為 textBox1**選項。</span><span class="sxs-lookup"><span data-stu-id="96870-222">When you drop the <xref:System.Windows.Forms.TextBox> control onto the form, click the smart-tag glyph and select the **Set text to textBox1** option.</span></span> <span data-ttu-id="96870-223">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 執行常見工作使用智慧標籤在 Windows Form 控制項](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="96870-223">For details, see [Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).</span></span>  
  
2.  <span data-ttu-id="96870-224">拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-224">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto your form.</span></span>  
  
3.  <span data-ttu-id="96870-225">變更 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="96870-225">Change the value of the <xref:System.Windows.Forms.Label> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="96870-226">請注意控制項的框線會調整以符合顯示文字。</span><span class="sxs-lookup"><span data-stu-id="96870-226">Note that the control's borders are adjusted to fit the display text.</span></span>  
  
4.  <span data-ttu-id="96870-227">移動<xref:System.Windows.Forms.Label>控制項的左邊<xref:System.Windows.Forms.TextBox>控制項，以配合的下邊緣<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-227">Move the <xref:System.Windows.Forms.Label> control to the left of the <xref:System.Windows.Forms.TextBox> control, so it is aligned with the bottom edge of the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="96870-228">請注意會出現兩個控制項下邊緣對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-228">Note the snapline that appears along the bottom edges of the two controls.</span></span>  
  
5.  <span data-ttu-id="96870-229">移動<xref:System.Windows.Forms.Label>控制稍微向上，直到<xref:System.Windows.Forms.Label>文字和<xref:System.Windows.Forms.TextBox>對齊文字。</span><span class="sxs-lookup"><span data-stu-id="96870-229">Move the <xref:System.Windows.Forms.Label> control slightly upward, until the <xref:System.Windows.Forms.Label> text and the <xref:System.Windows.Forms.TextBox> text are aligned.</span></span> <span data-ttu-id="96870-230">請注意會出現，指出對齊兩個控制項的文字欄位時的不同樣式對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-230">Note the differently styled snapline that appears, indicating when the text fields of both controls are aligned.</span></span>  
  
## <a name="using-snaplines-with-keyboard-navigation"></a><span data-ttu-id="96870-231">使用對齊線，使用鍵盤巡覽</span><span class="sxs-lookup"><span data-stu-id="96870-231">Using Snaplines with Keyboard Navigation</span></span>  
 <span data-ttu-id="96870-232">對齊線可協助您讓控制項時，您會排列使用鍵盤方向鍵。</span><span class="sxs-lookup"><span data-stu-id="96870-232">Snaplines help you align controls when you are arranging them using the keyboard's arrow keys.</span></span>  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a><span data-ttu-id="96870-233">若要使用鍵盤瀏覽可以使用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-233">To use snaplines with keyboard navigation</span></span>  
  
1.  <span data-ttu-id="96870-234">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-234">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="96870-235">請將它放在表單的左上角。</span><span class="sxs-lookup"><span data-stu-id="96870-235">Place it in the upper-left corner of the form.</span></span>  
  
2.  <span data-ttu-id="96870-236">按下 CTRL + 向下箭號。</span><span class="sxs-lookup"><span data-stu-id="96870-236">Press CTRL+DOWN ARROW.</span></span> <span data-ttu-id="96870-237">請注意，控制項在表單下移至第一個可用的水平對齊位置。</span><span class="sxs-lookup"><span data-stu-id="96870-237">Note that the control moves down the form to the first available horizontal alignment position.</span></span>  
  
3.  <span data-ttu-id="96870-238">按下 CTRL + 向下箭號，直到控制到達表單底部。</span><span class="sxs-lookup"><span data-stu-id="96870-238">Press CTRL+DOWN ARROW until the control reaches the bottom of the form.</span></span> <span data-ttu-id="96870-239">請注意在表單下移動，它會佔用的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-239">Note the positions it occupies as it moves down the form.</span></span>  
  
4.  <span data-ttu-id="96870-240">按下 CTRL + 向右箭號。</span><span class="sxs-lookup"><span data-stu-id="96870-240">Press CTRL+RIGHT ARROW.</span></span> <span data-ttu-id="96870-241">請注意，控制項在表單上移至第一個可用的垂直對齊位置。</span><span class="sxs-lookup"><span data-stu-id="96870-241">Note that the control moves across the form to the first available vertical alignment position.</span></span>  
  
5.  <span data-ttu-id="96870-242">直到控制到達表單的側邊，請按 CTRL + 向右鍵。</span><span class="sxs-lookup"><span data-stu-id="96870-242">Press CTRL+RIGHT ARROW until the control reaches the side of the form.</span></span> <span data-ttu-id="96870-243">請注意它會佔用移動表單上的位置。</span><span class="sxs-lookup"><span data-stu-id="96870-243">Note the positions it occupies as it moves across the form.</span></span>  
  
6.  <span data-ttu-id="96870-244">移動周圍的表單控制項的組合鍵。</span><span class="sxs-lookup"><span data-stu-id="96870-244">Move the control around the form with a combination of arrow keys.</span></span> <span data-ttu-id="96870-245">請注意，控制項所佔的位置和對齊線，它們會隨附於。</span><span class="sxs-lookup"><span data-stu-id="96870-245">Note the positions the control occupies and the snaplines that accompany them.</span></span>  
  
7.  <span data-ttu-id="96870-246">請按 SHIFT + 任何方向鍵來調整大小<xref:System.Windows.Forms.Button>一個像素的增量的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-246">Press SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control by increments of one pixel.</span></span>  
  
8.  <span data-ttu-id="96870-247">按下 CTRL + SHIFT + 任何方向鍵來調整大小<xref:System.Windows.Forms.Button>對齊線為增量單位中的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-247">Press CTRL+SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control in snapline increments.</span></span>  
  
## <a name="snaplines-and-layout-panels"></a><span data-ttu-id="96870-248">對齊線和版面配置面板</span><span class="sxs-lookup"><span data-stu-id="96870-248">Snaplines and Layout Panels</span></span>  
 <span data-ttu-id="96870-249">對齊線版面配置面板內停用。</span><span class="sxs-lookup"><span data-stu-id="96870-249">Snaplines are disabled within layout panels.</span></span>  
  
#### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="96870-250">若要選擇性地停用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-250">To selectively disable snaplines</span></span>  
  
1.  <span data-ttu-id="96870-251">拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="96870-251">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="96870-252">在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="96870-252">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox**.</span></span> <span data-ttu-id="96870-253">請注意，新的按鈕控制項出現在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個資料格。</span><span class="sxs-lookup"><span data-stu-id="96870-253">Note that a new button control appears in the <xref:System.Windows.Forms.TableLayoutPanel> control's first cell.</span></span>  
  
3.  <span data-ttu-id="96870-254">按兩下<xref:System.Windows.Forms.Button>中的控制項圖示**工具箱**兩次。</span><span class="sxs-lookup"><span data-stu-id="96870-254">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox** twice more.</span></span> <span data-ttu-id="96870-255">這會保留一個空白儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-255">This leaves one empty cell in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="96870-256">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的空白儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-256">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the empty cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="96870-257">請注意，沒有對齊線隨即出現。</span><span class="sxs-lookup"><span data-stu-id="96870-257">Note that no snaplines appear.</span></span>  
  
5.  <span data-ttu-id="96870-258">拖曳<xref:System.Windows.Forms.Button>控制共<xref:System.Windows.Forms.TableLayoutPanel>控制項，並予以四處移動<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-258">Drag the <xref:System.Windows.Forms.Button> control out of the <xref:System.Windows.Forms.TableLayoutPanel> control and move it around the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="96870-259">請注意對齊線再度出現。</span><span class="sxs-lookup"><span data-stu-id="96870-259">Note that snaplines appear again.</span></span>  
  
## <a name="disabling-snaplines"></a><span data-ttu-id="96870-260">停用的對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-260">Disabling Snaplines</span></span>  
 <span data-ttu-id="96870-261">依預設會開啟對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-261">Snaplines are turned on by default.</span></span> <span data-ttu-id="96870-262">您可以選擇性地停用對齊線，或您可以在設計環境中停用它們。</span><span class="sxs-lookup"><span data-stu-id="96870-262">You can disable snaplines selectively, or you can disable them in the design environment.</span></span>  
  
#### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="96870-263">若要選擇性地停用對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-263">To selectively disable snaplines</span></span>  
  
-   <span data-ttu-id="96870-264">按 ALT 鍵並同時移動周圍的表單控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-264">Press the ALT key and while moving a control around the form.</span></span>  
  
     <span data-ttu-id="96870-265">請注意，沒有對齊線出現的控制項不會貼齊至任何潛在的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="96870-265">Note that no snaplines appear and the control does not snap to any potential alignment positions.</span></span>  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a><span data-ttu-id="96870-266">若要停用在設計環境中的對齊線</span><span class="sxs-lookup"><span data-stu-id="96870-266">To disable snaplines in the design environment</span></span>  
  
1.  <span data-ttu-id="96870-267">從**工具**功能表中，開啟**選項** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="96870-267">From the **Tools** menu, open the **Options** dialog box.</span></span> <span data-ttu-id="96870-268">開啟 [Windows Form 設計工具] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="96870-268">Open the Windows Forms Designer dialog box.</span></span> <span data-ttu-id="96870-269">如需詳細資訊，請參閱 <<c0> [ 一般]、 [Windows Form 設計工具、 [選項] 對話方塊中](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)。</span><span class="sxs-lookup"><span data-stu-id="96870-269">For details, see [General, Windows Forms Designer, Options Dialog Box](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span></span>  
  
2.  <span data-ttu-id="96870-270">選取 **一般**節點。</span><span class="sxs-lookup"><span data-stu-id="96870-270">Select the **General** node.</span></span> <span data-ttu-id="96870-271">在 **版面配置模式**區段中，變更選取範圍**對齊線**來**貼齊格線**。</span><span class="sxs-lookup"><span data-stu-id="96870-271">In the **Layout Mode** section, change the selection from **SnapLines** to **SnapToGrid**.</span></span>  
  
3.  <span data-ttu-id="96870-272">按一下 [確定] 以套用此設定。</span><span class="sxs-lookup"><span data-stu-id="96870-272">Click OK to apply the setting.</span></span>  
  
4.  <span data-ttu-id="96870-273">選取您的表單上控制項，並將它移至其他控制項周圍。</span><span class="sxs-lookup"><span data-stu-id="96870-273">Select a control on your form and move it around the other controls.</span></span> <span data-ttu-id="96870-274">請注意，不會顯示對齊線。</span><span class="sxs-lookup"><span data-stu-id="96870-274">Note that snaplines do not appear.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="96870-275">後續步驟</span><span class="sxs-lookup"><span data-stu-id="96870-275">Next Steps</span></span>  
 <span data-ttu-id="96870-276">對齊線提供易用的工具，來調整您的表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-276">Snaplines offer an intuitive means of aligning controls on your form.</span></span> <span data-ttu-id="96870-277">進一步的探索建議包括：</span><span class="sxs-lookup"><span data-stu-id="96870-277">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="96870-278">請嘗試巢狀<xref:System.Windows.Forms.GroupBox>在另一個控制項<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-278">Try nesting a <xref:System.Windows.Forms.GroupBox> control within another <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="96870-279">地方<xref:System.Windows.Forms.Button>內的子控制項<xref:System.Windows.Forms.GroupBox>控制項，以及另一個父代內<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-279">Place a <xref:System.Windows.Forms.Button> control within the child <xref:System.Windows.Forms.GroupBox> control, and another within the parent <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="96870-280">移動<xref:System.Windows.Forms.Button>大約是若要查看如何對齊線跨容器界限的控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-280">Move the <xref:System.Windows.Forms.Button> controls around to see how the snaplines cross container boundaries.</span></span>  
  
-   <span data-ttu-id="96870-281">建立的資料行<xref:System.Windows.Forms.TextBox>控制項和對應的資料行的<xref:System.Windows.Forms.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-281">Create a column of <xref:System.Windows.Forms.TextBox> controls and a corresponding column of <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="96870-282">設定的值<xref:System.Windows.Forms.Label>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="96870-282">Set the value of the <xref:System.Windows.Forms.Label> controls' <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="96870-283">使用對齊線來移動<xref:System.Windows.Forms.Label>控制項，其顯示的文字中的文字與對齊<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="96870-283">Use snaplines to move the <xref:System.Windows.Forms.Label> controls so their displayed text is aligned with the text in the <xref:System.Windows.Forms.TextBox> controls.</span></span>  
  
 <span data-ttu-id="96870-284">Windows 使用者介面設計的相關資訊，請參閱本書*Microsoft Windows 使用者經驗、 使用者介面開發人員和設計人員的正式方針*Redmond，WA: Microsoft Press，1999年。</span><span class="sxs-lookup"><span data-stu-id="96870-284">For information about Windows user interface design, see the book *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, WA: Microsoft Press, 1999.</span></span> <span data-ttu-id="96870-285">(USBN: 0-7356 0566年-1)。</span><span class="sxs-lookup"><span data-stu-id="96870-285">(USBN: 0-7356-0566-1).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96870-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96870-286">See Also</span></span>  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [<span data-ttu-id="96870-287">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="96870-287">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="96870-288">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="96870-288">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="96870-289">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="96870-289">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [<span data-ttu-id="96870-290">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="96870-290">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
