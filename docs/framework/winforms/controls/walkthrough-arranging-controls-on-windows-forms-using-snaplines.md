---
title: 逐步解說：使用對齊線排列 Windows Form 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: f8e8122f82bc6a8c4fab17b8b73c07d08bab4d26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a><span data-ttu-id="a0101-102">逐步解說：使用對齊線排列 Windows Form 上的控制項</span><span class="sxs-lookup"><span data-stu-id="a0101-102">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>
<span data-ttu-id="a0101-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="a0101-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="a0101-104">Windows Form 設計工具提供您許多版面配置工具，可完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="a0101-104">The Windows Forms Designer gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="a0101-105">其中一個最重要的是<xref:System.Windows.Forms.Design.Behavior.SnapLine>功能。</span><span class="sxs-lookup"><span data-stu-id="a0101-105">One of the most important is the <xref:System.Windows.Forms.Design.Behavior.SnapLine> feature.</span></span>  
  
 <span data-ttu-id="a0101-106">對齊線所顯示的精確對齊控制項與其他控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-106">Snaplines show you precisely where to line up controls with other controls.</span></span> <span data-ttu-id="a0101-107">它們也會顯示您的 Windows 使用者介面指導方針所指定的控制項之間的邊界建議的距離。</span><span class="sxs-lookup"><span data-stu-id="a0101-107">They also show you the recommended distances for margins between controls, as specified by the Windows User Interface Guidelines.</span></span> <span data-ttu-id="a0101-108">如需詳細資訊，請參閱[使用者介面的設計和開發](http://go.microsoft.com/FWLink/?LinkId=83878)。</span><span class="sxs-lookup"><span data-stu-id="a0101-108">For details, see [User Interface Design and Development](http://go.microsoft.com/FWLink/?LinkId=83878).</span></span>  
  
 <span data-ttu-id="a0101-109">對齊線讓您輕鬆對齊控制項，以產生簡潔、 專業外觀和行為 （外觀及操作）。</span><span class="sxs-lookup"><span data-stu-id="a0101-109">Snaplines make it easy to align your controls, for crisp, professional appearance and behavior (look and feel).</span></span>  
  
 <span data-ttu-id="a0101-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="a0101-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a0101-111">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="a0101-111">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="a0101-112">間距和對齊控制項使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-112">Spacing and Aligning Controls Using Snaplines</span></span>  
  
-   <span data-ttu-id="a0101-113">對齊表單和容器的邊界</span><span class="sxs-lookup"><span data-stu-id="a0101-113">Aligning to Form and Container Margins</span></span>  
  
-   <span data-ttu-id="a0101-114">對齊控制項群組</span><span class="sxs-lookup"><span data-stu-id="a0101-114">Aligning to Grouped Controls</span></span>  
  
-   <span data-ttu-id="a0101-115">使用對齊線來放置控制項框大小</span><span class="sxs-lookup"><span data-stu-id="a0101-115">Using Snaplines to Place a Control by Outlining Its Size</span></span>  
  
-   <span data-ttu-id="a0101-116">從 [工具箱] 拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-116">Using Snaplines When Dragging a Control from the Toolbox</span></span>  
  
-   <span data-ttu-id="a0101-117">使用對齊線的控制項調整大小</span><span class="sxs-lookup"><span data-stu-id="a0101-117">Resizing Controls Using Snaplines</span></span>  
  
-   <span data-ttu-id="a0101-118">對齊控制項的文字標籤</span><span class="sxs-lookup"><span data-stu-id="a0101-118">Aligning a Label to a Control's Text</span></span>  
  
-   <span data-ttu-id="a0101-119">使用鍵盤瀏覽使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-119">Using Snaplines with Keyboard Navigation</span></span>  
  
-   <span data-ttu-id="a0101-120">對齊線和版面配置面板</span><span class="sxs-lookup"><span data-stu-id="a0101-120">Snaplines and Layout Panels</span></span>  
  
-   <span data-ttu-id="a0101-121">停用的對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-121">Disabling Snaplines</span></span>  
  
 <span data-ttu-id="a0101-122">當您完成時，您必須了解版面配置功能所扮演角色的對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-122">When you are finished, you will have an understanding of the layout role played by the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0101-123">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="a0101-123">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a0101-124">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="a0101-124">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a0101-125">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="a0101-125">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a0101-126">建立專案</span><span class="sxs-lookup"><span data-stu-id="a0101-126">Creating the Project</span></span>  
 <span data-ttu-id="a0101-127">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-127">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="a0101-128">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="a0101-128">To create the project</span></span>  
  
1.  <span data-ttu-id="a0101-129">建立 Windows 架構應用程式專案，稱為 「 SnaplineExample"。</span><span class="sxs-lookup"><span data-stu-id="a0101-129">Create a Windows-based application project called "SnaplineExample".</span></span> <span data-ttu-id="a0101-130">如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="a0101-130">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="a0101-131">在表單設計工具中選取的表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-131">Select the form in the Forms Designer.</span></span>  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a><span data-ttu-id="a0101-132">間距和對齊控制項使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-132">Spacing and Aligning Controls Using Snaplines</span></span>  
 <span data-ttu-id="a0101-133">對齊線可讓您精確且直覺式對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-133">Snaplines give you an accurate and intuitive way to align controls on your form.</span></span> <span data-ttu-id="a0101-134">當您要移動選取的控制項附近的位置時，對齊線與另一個控制項或一組控制項便會出現。</span><span class="sxs-lookup"><span data-stu-id="a0101-134">They appear when you are moving a selected control or controls near a position that would align with another control or set of controls.</span></span> <span data-ttu-id="a0101-135">您的選擇將 「 對齊 」 至建議的位置超出其他控制項時。</span><span class="sxs-lookup"><span data-stu-id="a0101-135">Your selection will "snap" to the suggested position as you move it past the other controls.</span></span>  
  
#### <a name="to-arrange-controls-using-snaplines"></a><span data-ttu-id="a0101-136">使用對齊線排列控制項</span><span class="sxs-lookup"><span data-stu-id="a0101-136">To arrange controls using snaplines</span></span>  
  
1.  <span data-ttu-id="a0101-137">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-137">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="a0101-138">移動<xref:System.Windows.Forms.Button>表單的右下角的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-138">Move the <xref:System.Windows.Forms.Button> control to the lower-right corner of the form.</span></span> <span data-ttu-id="a0101-139">請注意會顯示為的對齊線<xref:System.Windows.Forms.Button>控制方法的下和右框線的表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-139">Note the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the form.</span></span> <span data-ttu-id="a0101-140">這些對齊線顯示控制項的框線和表單的建議的距離。</span><span class="sxs-lookup"><span data-stu-id="a0101-140">These snaplines display the recommended distance between the borders of the control and the form.</span></span>  
  
3.  <span data-ttu-id="a0101-141">移動<xref:System.Windows.Forms.Button>控制項周圍的框線的表單，並注意對齊線出現的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-141">Move the <xref:System.Windows.Forms.Button> control around the borders of the form and note where the snaplines appear.</span></span> <span data-ttu-id="a0101-142">當您完成時，移動<xref:System.Windows.Forms.Button>表單的中央附近的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-142">When you are finished, move the <xref:System.Windows.Forms.Button> control near the center of the form.</span></span>  
  
4.  <span data-ttu-id="a0101-143">拖曳其他<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-143">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
5.  <span data-ttu-id="a0101-144">將第二個<xref:System.Windows.Forms.Button>控制直到幾乎層級的第一個。</span><span class="sxs-lookup"><span data-stu-id="a0101-144">Move the second <xref:System.Windows.Forms.Button> control until it is nearly level with the first.</span></span> <span data-ttu-id="a0101-145">請注意會出現在這兩個按鈕的文字基準線對齊線，請注意您要移動的控制項貼齊至是完全與其他控制項的層級的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-145">Note the snapline that appears at the text baseline of both buttons, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>  
  
6.  <span data-ttu-id="a0101-146">將第二個<xref:System.Windows.Forms.Button>控制直到將其置於上方的第一個。</span><span class="sxs-lookup"><span data-stu-id="a0101-146">Move the second <xref:System.Windows.Forms.Button> control until it is positioned directly above the first.</span></span> <span data-ttu-id="a0101-147">請注意的對齊線出現在這兩個按鈕，左和右邊緣，並請注意，控制項必須移動的貼齊至完全對齊其他控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-147">Note the snaplines that appear along the left and right edges of both buttons, and note that the control you are moving snaps to a position that is exactly aligned with the other control.</span></span>  
  
7.  <span data-ttu-id="a0101-148">選取其中一個<xref:System.Windows.Forms.Button>控制，並將其接近，直到幾乎碰觸。</span><span class="sxs-lookup"><span data-stu-id="a0101-148">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span> <span data-ttu-id="a0101-149">請注意，出現在它們之間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-149">Note the snapline that appears between them.</span></span> <span data-ttu-id="a0101-150">這個距離是控制項的框線之間的建議的距離。</span><span class="sxs-lookup"><span data-stu-id="a0101-150">This distance is the recommended distance between the borders of the controls.</span></span> <span data-ttu-id="a0101-151">也請注意，您要移動的控制項貼齊至這個位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-151">Also note that the control you are moving snaps to this position.</span></span>  
  
8.  <span data-ttu-id="a0101-152">拖放兩<xref:System.Windows.Forms.Panel>控制從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-152">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto your form.</span></span>  
  
9. <span data-ttu-id="a0101-153">將其中一個移<xref:System.Windows.Forms.Panel>直到幾乎層級的第一個控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-153">Move one of the <xref:System.Windows.Forms.Panel> controls until it is nearly level with the first.</span></span> <span data-ttu-id="a0101-154">請注意，出現在這兩個控制項的頂端和底端邊緣，並記下您要移動的控制項貼齊至是完全與其他控制項的層級位置的對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-154">Note the snaplines that appear along the top and bottom edges of both controls, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>  
  
## <a name="aligning-to-form-and-container-margins"></a><span data-ttu-id="a0101-155">對齊表單和容器的邊界</span><span class="sxs-lookup"><span data-stu-id="a0101-155">Aligning to Form and Container Margins</span></span>  
 <span data-ttu-id="a0101-156">對齊線可協助您對齊表單和容器的邊界控制項以一致的方式。</span><span class="sxs-lookup"><span data-stu-id="a0101-156">Snaplines help you to align your controls to form and container margins in a consistent manner.</span></span>  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a><span data-ttu-id="a0101-157">對齊控制項加入表單和容器的邊界</span><span class="sxs-lookup"><span data-stu-id="a0101-157">To align controls to form and container margins</span></span>  
  
1.  <span data-ttu-id="a0101-158">選取其中一個<xref:System.Windows.Forms.Button>控制，並將其移接近右框線的形式，直到對齊線出現。</span><span class="sxs-lookup"><span data-stu-id="a0101-158">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="a0101-159">右框線的對齊線的距離就是控制項的總和<xref:System.Windows.Forms.Control.Margin%2A>屬性和表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性值。</span><span class="sxs-lookup"><span data-stu-id="a0101-159">The snapline's distance from the right border is the sum of the control's <xref:System.Windows.Forms.Control.Margin%2A> property and the form's <xref:System.Windows.Forms.Control.Padding%2A> property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0101-160">如果表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性設為 0,0,0,0，加上陰影的 Windows Form 設計工具提供表單<xref:System.Windows.Forms.Control.Padding%2A>9,9,9,9 的值。</span><span class="sxs-lookup"><span data-stu-id="a0101-160">If the form's <xref:System.Windows.Forms.Control.Padding%2A> property is set to 0,0,0,0, the Windows Forms Designer gives the form a shadowed <xref:System.Windows.Forms.Control.Padding%2A> value of 9,9,9,9.</span></span> <span data-ttu-id="a0101-161">若要覆寫此行為，請指派 0,0,0,0 以外的值。</span><span class="sxs-lookup"><span data-stu-id="a0101-161">To override this behavior, assign a value other than 0,0,0,0.</span></span>  
  
1.  <span data-ttu-id="a0101-162">值變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性展開<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性設為 0。</span><span class="sxs-lookup"><span data-stu-id="a0101-162">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 0.</span></span> <span data-ttu-id="a0101-163">如需詳細資訊，請參閱[逐步解說： 用來配置 Windows Form 控制項的邊框距離、 邊界和 AutoSize 屬性](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)。</span><span class="sxs-lookup"><span data-stu-id="a0101-163">For details, see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).</span></span>  
  
2.  <span data-ttu-id="a0101-164">移動<xref:System.Windows.Forms.Button>接近右框線直到對齊線出現在表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-164">Move the <xref:System.Windows.Forms.Button> control close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="a0101-165">表單的值現在會提供這個距離<xref:System.Windows.Forms.Control.Padding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a0101-165">This distance is now given by the value of the form's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
3.  <span data-ttu-id="a0101-166">拖曳<xref:System.Windows.Forms.GroupBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-166">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="a0101-167">值變更<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性展開<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性為 10。</span><span class="sxs-lookup"><span data-stu-id="a0101-167">Change the value of the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 10.</span></span>  
  
5.  <span data-ttu-id="a0101-168">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**到<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-168">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
6.  <span data-ttu-id="a0101-169">移動<xref:System.Windows.Forms.Button>控制項的右框線接近<xref:System.Windows.Forms.GroupBox>控制直到對齊線出現。</span><span class="sxs-lookup"><span data-stu-id="a0101-169">Move the <xref:System.Windows.Forms.Button> control close to the right border of the <xref:System.Windows.Forms.GroupBox> control until a snapline appears.</span></span> <span data-ttu-id="a0101-170">移動<xref:System.Windows.Forms.Button>內控制<xref:System.Windows.Forms.GroupBox>控制項和附註的對齊線出現的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-170">Move the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and note where the snaplines appear.</span></span>  
  
## <a name="aligning-to-grouped-controls"></a><span data-ttu-id="a0101-171">對齊控制項群組</span><span class="sxs-lookup"><span data-stu-id="a0101-171">Aligning to Grouped Controls</span></span>  
 <span data-ttu-id="a0101-172">您可以使用對齊線來對齊控制項群組以及做為控制內<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-172">You can use snaplines to align grouped controls as well as controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
#### <a name="to-align-to-grouped-controls"></a><span data-ttu-id="a0101-173">對齊控制項群組</span><span class="sxs-lookup"><span data-stu-id="a0101-173">To align to grouped controls</span></span>  
  
1.  <span data-ttu-id="a0101-174">選取您的表單上控制項的兩個。</span><span class="sxs-lookup"><span data-stu-id="a0101-174">Select two of the controls on your form.</span></span> <span data-ttu-id="a0101-175">移動選取項目，並記下出現在您的選取項目和其他控制項之間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-175">Move the selection around and note the snaplines that appear between your selection and the other controls.</span></span>  
  
2.  <span data-ttu-id="a0101-176">拖曳<xref:System.Windows.Forms.GroupBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-176">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>  
  
3.  <span data-ttu-id="a0101-177">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**到<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-177">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
4.  <span data-ttu-id="a0101-178">選取其中一個<xref:System.Windows.Forms.Button>控制，並將之移<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-178">Select one of the <xref:System.Windows.Forms.Button> controls and move it around the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a0101-179">請注意會出現在邊緣對齊線<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-179">Note the snaplines that appear at the edges of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a0101-180">也請注意會出現在邊緣對齊線<xref:System.Windows.Forms.Button>所包含的控制項<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-180">Also note the snaplines that appear at the edges of the <xref:System.Windows.Forms.Button> control that is contained by the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a0101-181">容器控制項的子系的控制項也支援對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-181">Controls that are children of a container control also support snaplines.</span></span>  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="a0101-182">使用對齊線來放置控制項框大小</span><span class="sxs-lookup"><span data-stu-id="a0101-182">Using Snaplines to Place a Control by Outlining Its Size</span></span>  
 <span data-ttu-id="a0101-183">對齊線幫助您對齊控制當您第一次將它們放在表單上。</span><span class="sxs-lookup"><span data-stu-id="a0101-183">Snaplines help you align controls when you first place them on a form.</span></span>  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="a0101-184">使用對齊線來放置控制項框大小</span><span class="sxs-lookup"><span data-stu-id="a0101-184">To use snaplines to place a control by outlining its size</span></span>  
  
1.  <span data-ttu-id="a0101-185">按一下 [工具箱] 的 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="a0101-185">In the **Toolbox**, click the <xref:System.Windows.Forms.Button> control icon.</span></span> <span data-ttu-id="a0101-186">請勿拖曳到表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-186">Do not drag it onto the form.</span></span>  
  
2.  <span data-ttu-id="a0101-187">將滑鼠指標移至表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="a0101-187">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="a0101-188">請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="a0101-188">Note that the pointer changes to a crosshair with the <xref:System.Windows.Forms.Button> control icon attached.</span></span> <span data-ttu-id="a0101-189">也請注意對齊線來建議對齊的位置可<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-189">Also note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
3.  <span data-ttu-id="a0101-190">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="a0101-190">Click and hold the mouse button.</span></span>  
  
4.  <span data-ttu-id="a0101-191">拖曳滑鼠指標圍繞表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-191">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="a0101-192">請注意，已繪製外框，表示位置和控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="a0101-192">Note that an outline is drawn, indicating the position and the size of the control.</span></span>  
  
5.  <span data-ttu-id="a0101-193">拖曳滑鼠指標，使其與另一個控制項在表單上對齊。</span><span class="sxs-lookup"><span data-stu-id="a0101-193">Drag the pointer until it aligns with another control on the form.</span></span> <span data-ttu-id="a0101-194">請注意，會出現對齊線，表示對齊方式。</span><span class="sxs-lookup"><span data-stu-id="a0101-194">Note that a snapline appears to indicate alignment.</span></span>  
  
6.  <span data-ttu-id="a0101-195">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="a0101-195">Release the mouse button.</span></span> <span data-ttu-id="a0101-196">建立控制項的位置與大小以 外框。</span><span class="sxs-lookup"><span data-stu-id="a0101-196">The control is created at the position and size indicated by the outline.</span></span>  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="a0101-197">從 [工具箱] 拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-197">Using Snaplines When Dragging a Control from the Toolbox</span></span>  
 <span data-ttu-id="a0101-198">對齊線線可協助您對齊控制項拖曳它們從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-198">Snaplines help you align controls when you drag them from the **Toolbox** onto your form.</span></span>  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="a0101-199">若要從 [工具箱] 拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-199">To use snaplines when dragging a control from the Toolbox</span></span>  
  
1.  <span data-ttu-id="a0101-200">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單，但不要放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="a0101-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form, but do not release the mouse button.</span></span>  
  
2.  <span data-ttu-id="a0101-201">將滑鼠指標移至表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="a0101-201">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="a0101-202">請注意，指標會變成表示之位置的新<xref:System.Windows.Forms.Button>會建立控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-202">Note that the pointer changes to indicate the position at which the new <xref:System.Windows.Forms.Button> control will be created.</span></span>  
  
3.  <span data-ttu-id="a0101-203">拖曳滑鼠指標圍繞表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-203">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="a0101-204">請注意對齊線來建議對齊的位置可<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-204">Note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="a0101-205">找出與其他控制項對齊的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-205">Find a position that is aligned with other controls.</span></span>  
  
4.  <span data-ttu-id="a0101-206">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="a0101-206">Release the mouse button.</span></span> <span data-ttu-id="a0101-207">對齊線所指示之位置建立控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-207">The control is created at the position indicated by the snaplines.</span></span>  
  
## <a name="resizing-controls-using-snaplines"></a><span data-ttu-id="a0101-208">使用對齊線的控制項調整大小</span><span class="sxs-lookup"><span data-stu-id="a0101-208">Resizing Controls Using Snaplines</span></span>  
 <span data-ttu-id="a0101-209">對齊線可協助您對齊的控制項，調整其大小時。</span><span class="sxs-lookup"><span data-stu-id="a0101-209">Snaplines help you align controls as you resize them.</span></span>  
  
#### <a name="to-resize-a-control-using-snaplines"></a><span data-ttu-id="a0101-210">若要調整大小的控制項使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-210">To resize a control using snaplines</span></span>  
  
1.  <span data-ttu-id="a0101-211">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-211">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="a0101-212">調整大小<xref:System.Windows.Forms.Button>抓取其中一個調整大小控點，並拖曳邊角的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-212">Resize the <xref:System.Windows.Forms.Button> control by grabbing one of the corner sizing handles and dragging.</span></span> <span data-ttu-id="a0101-213">如需詳細資訊，請參閱[如何： 調整 Windows Form 上控制項](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a0101-213">For details, see [How to: Resize Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="a0101-214">拖曳調整大小控點，直到其中一個<xref:System.Windows.Forms.Button>控制項的框線對齊的另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-214">Drag the sizing handle until one of the <xref:System.Windows.Forms.Button> control's borders is aligned with another control.</span></span> <span data-ttu-id="a0101-215">請注意，會出現對齊。</span><span class="sxs-lookup"><span data-stu-id="a0101-215">Note that a snapline appears.</span></span> <span data-ttu-id="a0101-216">另外請注意，調整大小控點貼齊至對齊線所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-216">Also note that the sizing handle snaps to the position indicated by the snapline.</span></span>  
  
4.  <span data-ttu-id="a0101-217">調整大小<xref:System.Windows.Forms.Button>控制不同的方向並對齊到不同的控制項調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="a0101-217">Resize the <xref:System.Windows.Forms.Button> control in different directions and align the sizing handle to different controls.</span></span> <span data-ttu-id="a0101-218">請注意對齊線出現在不同的方向，以指示對齊的方式。</span><span class="sxs-lookup"><span data-stu-id="a0101-218">Note how the snaplines appear in various orientations to indicate alignment.</span></span>  
  
## <a name="aligning-a-label-to-a-controls-text"></a><span data-ttu-id="a0101-219">對齊控制項的文字標籤</span><span class="sxs-lookup"><span data-stu-id="a0101-219">Aligning a Label to a Control's Text</span></span>  
 <span data-ttu-id="a0101-220">某些控制項提供的對齊線來對齊其他控制項加入顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="a0101-220">Some controls offer a snapline for aligning other controls to displayed text.</span></span>  
  
#### <a name="to-align-a-label-to-a-controls-text"></a><span data-ttu-id="a0101-221">若要對齊的標籤控制項的文字</span><span class="sxs-lookup"><span data-stu-id="a0101-221">To align a label to a control's text</span></span>  
  
1.  <span data-ttu-id="a0101-222">拖曳<xref:System.Windows.Forms.TextBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-222">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="a0101-223">當您卸除<xref:System.Windows.Forms.TextBox>控制項拖曳至表單中，按一下智慧標籤圖像，然後選取**文字設 textBox1**選項。</span><span class="sxs-lookup"><span data-stu-id="a0101-223">When you drop the <xref:System.Windows.Forms.TextBox> control onto the form, click the smart-tag glyph and select the **Set text to textBox1** option.</span></span> <span data-ttu-id="a0101-224">如需詳細資訊，請參閱[逐步解說： 執行常見工作使用智慧標籤上的 Windows Form 控制項](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="a0101-224">For details, see [Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).</span></span>  
  
2.  <span data-ttu-id="a0101-225">拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-225">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto your form.</span></span>  
  
3.  <span data-ttu-id="a0101-226">變更 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a0101-226">Change the value of the <xref:System.Windows.Forms.Label> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="a0101-227">請注意控制項的框線會調整以符合顯示文字。</span><span class="sxs-lookup"><span data-stu-id="a0101-227">Note that the control's borders are adjusted to fit the display text.</span></span>  
  
4.  <span data-ttu-id="a0101-228">移動<xref:System.Windows.Forms.Label>控制項左邊<xref:System.Windows.Forms.TextBox>控制，讓它配合的下邊緣<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-228">Move the <xref:System.Windows.Forms.Label> control to the left of the <xref:System.Windows.Forms.TextBox> control, so it is aligned with the bottom edge of the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="a0101-229">請注意會出現兩個控制項下邊緣對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-229">Note the snapline that appears along the bottom edges of the two controls.</span></span>  
  
5.  <span data-ttu-id="a0101-230">移動<xref:System.Windows.Forms.Label>控制項稍微向上，直到<xref:System.Windows.Forms.Label>文字和<xref:System.Windows.Forms.TextBox>對齊文字。</span><span class="sxs-lookup"><span data-stu-id="a0101-230">Move the <xref:System.Windows.Forms.Label> control slightly upward, until the <xref:System.Windows.Forms.Label> text and the <xref:System.Windows.Forms.TextBox> text are aligned.</span></span> <span data-ttu-id="a0101-231">請注意會出現，指出對齊兩個控制項的文字欄位時的不同樣式對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-231">Note the differently styled snapline that appears, indicating when the text fields of both controls are aligned.</span></span>  
  
## <a name="using-snaplines-with-keyboard-navigation"></a><span data-ttu-id="a0101-232">使用鍵盤瀏覽使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-232">Using Snaplines with Keyboard Navigation</span></span>  
 <span data-ttu-id="a0101-233">對齊線幫助您對齊控制當您排列使用鍵盤的方向鍵。</span><span class="sxs-lookup"><span data-stu-id="a0101-233">Snaplines help you align controls when you are arranging them using the keyboard's arrow keys.</span></span>  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a><span data-ttu-id="a0101-234">若要使用鍵盤瀏覽可以使用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-234">To use snaplines with keyboard navigation</span></span>  
  
1.  <span data-ttu-id="a0101-235">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-235">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="a0101-236">請將它放在表單的左上角。</span><span class="sxs-lookup"><span data-stu-id="a0101-236">Place it in the upper-left corner of the form.</span></span>  
  
2.  <span data-ttu-id="a0101-237">按 CTRL + 向下箭號。</span><span class="sxs-lookup"><span data-stu-id="a0101-237">Press CTRL+DOWN ARROW.</span></span> <span data-ttu-id="a0101-238">請注意，控制項移到表單下方的第一個可用的水平對齊的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-238">Note that the control moves down the form to the first available horizontal alignment position.</span></span>  
  
3.  <span data-ttu-id="a0101-239">請按 CTRL + 向下箭號，直到控制項到達表單底部。</span><span class="sxs-lookup"><span data-stu-id="a0101-239">Press CTRL+DOWN ARROW until the control reaches the bottom of the form.</span></span> <span data-ttu-id="a0101-240">請注意佔有表單下方移動的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-240">Note the positions it occupies as it moves down the form.</span></span>  
  
4.  <span data-ttu-id="a0101-241">按 CTRL + 向右鍵。</span><span class="sxs-lookup"><span data-stu-id="a0101-241">Press CTRL+RIGHT ARROW.</span></span> <span data-ttu-id="a0101-242">請注意，控制項在表單中移動至第一個可用的垂直對齊位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-242">Note that the control moves across the form to the first available vertical alignment position.</span></span>  
  
5.  <span data-ttu-id="a0101-243">請按 CTRL + 向右箭號，直到控制項到達表單的側邊。</span><span class="sxs-lookup"><span data-stu-id="a0101-243">Press CTRL+RIGHT ARROW until the control reaches the side of the form.</span></span> <span data-ttu-id="a0101-244">請注意佔有移動在表單上的位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-244">Note the positions it occupies as it moves across the form.</span></span>  
  
6.  <span data-ttu-id="a0101-245">移動周圍表單控制項使用的箭頭按鍵組合。</span><span class="sxs-lookup"><span data-stu-id="a0101-245">Move the control around the form with a combination of arrow keys.</span></span> <span data-ttu-id="a0101-246">請注意，控制項所佔的位置和對齊線，其會隨附於。</span><span class="sxs-lookup"><span data-stu-id="a0101-246">Note the positions the control occupies and the snaplines that accompany them.</span></span>  
  
7.  <span data-ttu-id="a0101-247">按 SHIFT + 任何方向鍵調整<xref:System.Windows.Forms.Button>增加一個像素的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-247">Press SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control by increments of one pixel.</span></span>  
  
8.  <span data-ttu-id="a0101-248">按下 CTRL + SHIFT + 任何方向鍵調整<xref:System.Windows.Forms.Button>對齊線為增量來控制。</span><span class="sxs-lookup"><span data-stu-id="a0101-248">Press CTRL+SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control in snapline increments.</span></span>  
  
## <a name="snaplines-and-layout-panels"></a><span data-ttu-id="a0101-249">對齊線和版面配置面板</span><span class="sxs-lookup"><span data-stu-id="a0101-249">Snaplines and Layout Panels</span></span>  
 <span data-ttu-id="a0101-250">對齊線會在配置面板內停用。</span><span class="sxs-lookup"><span data-stu-id="a0101-250">Snaplines are disabled within layout panels.</span></span>  
  
#### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="a0101-251">若要選擇性地停用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-251">To selectively disable snaplines</span></span>  
  
1.  <span data-ttu-id="a0101-252">拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a0101-252">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="a0101-253">在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="a0101-253">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox**.</span></span> <span data-ttu-id="a0101-254">請注意，新的按鈕控制項出現在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個資料格。</span><span class="sxs-lookup"><span data-stu-id="a0101-254">Note that a new button control appears in the <xref:System.Windows.Forms.TableLayoutPanel> control's first cell.</span></span>  
  
3.  <span data-ttu-id="a0101-255">按兩下<xref:System.Windows.Forms.Button>中的控制項圖示**工具箱**兩次。</span><span class="sxs-lookup"><span data-stu-id="a0101-255">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox** twice more.</span></span> <span data-ttu-id="a0101-256">這會保留在一個空資料格<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-256">This leaves one empty cell in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="a0101-257">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的空白儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-257">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the empty cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="a0101-258">請注意，沒有對齊線隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a0101-258">Note that no snaplines appear.</span></span>  
  
5.  <span data-ttu-id="a0101-259">拖曳<xref:System.Windows.Forms.Button>超出控制<xref:System.Windows.Forms.TableLayoutPanel>控制，並將其移<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-259">Drag the <xref:System.Windows.Forms.Button> control out of the <xref:System.Windows.Forms.TableLayoutPanel> control and move it around the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="a0101-260">請注意對齊線出現一次。</span><span class="sxs-lookup"><span data-stu-id="a0101-260">Note that snaplines appear again.</span></span>  
  
## <a name="disabling-snaplines"></a><span data-ttu-id="a0101-261">停用的對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-261">Disabling Snaplines</span></span>  
 <span data-ttu-id="a0101-262">預設會開啟對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-262">Snaplines are turned on by default.</span></span> <span data-ttu-id="a0101-263">您可以選擇性地停用對齊線，或您可以在設計環境中停用它們。</span><span class="sxs-lookup"><span data-stu-id="a0101-263">You can disable snaplines selectively, or you can disable them in the design environment.</span></span>  
  
#### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="a0101-264">若要選擇性地停用對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-264">To selectively disable snaplines</span></span>  
  
-   <span data-ttu-id="a0101-265">按下 ALT 鍵並移動周圍表單的控制項時。</span><span class="sxs-lookup"><span data-stu-id="a0101-265">Press the ALT key and while moving a control around the form.</span></span>  
  
     <span data-ttu-id="a0101-266">請注意，任何對齊線出現控制項不會貼齊至任何可能的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="a0101-266">Note that no snaplines appear and the control does not snap to any potential alignment positions.</span></span>  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a><span data-ttu-id="a0101-267">若要停用在設計環境中的對齊線</span><span class="sxs-lookup"><span data-stu-id="a0101-267">To disable snaplines in the design environment</span></span>  
  
1.  <span data-ttu-id="a0101-268">從**工具**功能表中，開啟**選項** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a0101-268">From the **Tools** menu, open the **Options** dialog box.</span></span> <span data-ttu-id="a0101-269">開啟 [Windows Form 設計工具] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a0101-269">Open the Windows Forms Designer dialog box.</span></span> <span data-ttu-id="a0101-270">如需詳細資訊，請參閱[一般]、 [Windows Form 設計工具、 [選項] 對話方塊](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)。</span><span class="sxs-lookup"><span data-stu-id="a0101-270">For details, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span></span>  
  
2.  <span data-ttu-id="a0101-271">選取**一般**節點。</span><span class="sxs-lookup"><span data-stu-id="a0101-271">Select the **General** node.</span></span> <span data-ttu-id="a0101-272">在**版面配置模式**區段中，變更選取項目從**對齊線**至**SnapToGrid**。</span><span class="sxs-lookup"><span data-stu-id="a0101-272">In the **Layout Mode** section, change the selection from **SnapLines** to **SnapToGrid**.</span></span>  
  
3.  <span data-ttu-id="a0101-273">按一下 [確定] 以套用此設定。</span><span class="sxs-lookup"><span data-stu-id="a0101-273">Click OK to apply the setting.</span></span>  
  
4.  <span data-ttu-id="a0101-274">選取您的表單上控制項，並將它移至其他控制項周圍。</span><span class="sxs-lookup"><span data-stu-id="a0101-274">Select a control on your form and move it around the other controls.</span></span> <span data-ttu-id="a0101-275">請注意，不會顯示對齊線。</span><span class="sxs-lookup"><span data-stu-id="a0101-275">Note that snaplines do not appear.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a0101-276">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a0101-276">Next Steps</span></span>  
 <span data-ttu-id="a0101-277">對齊線可直覺的對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-277">Snaplines offer an intuitive means of aligning controls on your form.</span></span> <span data-ttu-id="a0101-278">進一步的探索建議包括：</span><span class="sxs-lookup"><span data-stu-id="a0101-278">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="a0101-279">請嘗試巢狀<xref:System.Windows.Forms.GroupBox>在另一個控制項<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-279">Try nesting a <xref:System.Windows.Forms.GroupBox> control within another <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a0101-280">位置<xref:System.Windows.Forms.Button>內的子控制項<xref:System.Windows.Forms.GroupBox>控制項，以及另一個父系內<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-280">Place a <xref:System.Windows.Forms.Button> control within the child <xref:System.Windows.Forms.GroupBox> control, and another within the parent <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a0101-281">移動<xref:System.Windows.Forms.Button>大約以查看如何對齊跨容器界限的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-281">Move the <xref:System.Windows.Forms.Button> controls around to see how the snaplines cross container boundaries.</span></span>  
  
-   <span data-ttu-id="a0101-282">建立的資料行<xref:System.Windows.Forms.TextBox>控制項和對應的資料行的<xref:System.Windows.Forms.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-282">Create a column of <xref:System.Windows.Forms.TextBox> controls and a corresponding column of <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="a0101-283">值設定<xref:System.Windows.Forms.Label>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="a0101-283">Set the value of the <xref:System.Windows.Forms.Label> controls' <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="a0101-284">使用對齊線來移動<xref:System.Windows.Forms.Label>控制項，其顯示的文字中的文字對齊<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a0101-284">Use snaplines to move the <xref:System.Windows.Forms.Label> controls so their displayed text is aligned with the text in the <xref:System.Windows.Forms.TextBox> controls.</span></span>  
  
 <span data-ttu-id="a0101-285">Windows 使用者介面設計的相關資訊，請參閱本書*Microsoft Windows 使用者經驗、 使用者介面的開發人員和設計工具的正式方針*Redmond，WA: Microsoft Press，1999年。</span><span class="sxs-lookup"><span data-stu-id="a0101-285">For information about Windows user interface design, see the book *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, WA: Microsoft Press, 1999.</span></span> <span data-ttu-id="a0101-286">(USBN: 0-7356-0566年-1)。</span><span class="sxs-lookup"><span data-stu-id="a0101-286">(USBN: 0-7356-0566-1).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0101-287">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0101-287">See Also</span></span>  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [<span data-ttu-id="a0101-288">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="a0101-288">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="a0101-289">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="a0101-289">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="a0101-290">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="a0101-290">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [<span data-ttu-id="a0101-291">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="a0101-291">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
