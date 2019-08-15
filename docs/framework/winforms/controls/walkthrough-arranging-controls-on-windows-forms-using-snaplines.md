---
title: 逐步解說：使用對齊線排列 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 3ce6c250fadbb56b341d5e8dec3a9cb9d28940fe
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040261"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a><span data-ttu-id="acad3-102">逐步解說：使用對齊線排列 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-102">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>
<span data-ttu-id="acad3-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="acad3-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="acad3-104">Windows Form 設計工具提供您許多版面組態工具來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="acad3-104">The Windows Forms Designer gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="acad3-105">其中一個最重要的就是<xref:System.Windows.Forms.Design.Behavior.SnapLine>此功能。</span><span class="sxs-lookup"><span data-stu-id="acad3-105">One of the most important is the <xref:System.Windows.Forms.Design.Behavior.SnapLine> feature.</span></span>

 <span data-ttu-id="acad3-106">對齊線可讓您精確地顯示控制項與其他控制項的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-106">Snaplines show you precisely where to line up controls with other controls.</span></span> <span data-ttu-id="acad3-107">它們也會顯示控制項之間的邊界建議距離, 如 Windows 使用者介面指導方針所指定。</span><span class="sxs-lookup"><span data-stu-id="acad3-107">They also show you the recommended distances for margins between controls, as specified by the Windows User Interface Guidelines.</span></span> <span data-ttu-id="acad3-108">如需詳細資訊, 請參閱[使用者介面設計和開發](https://go.microsoft.com/FWLink/?LinkId=83878)。</span><span class="sxs-lookup"><span data-stu-id="acad3-108">For details, see [User Interface Design and Development](https://go.microsoft.com/FWLink/?LinkId=83878).</span></span>

 <span data-ttu-id="acad3-109">對齊線可讓您輕鬆對齊控制項, 以提供清晰、專業的外觀和行為 (外觀與風格)。</span><span class="sxs-lookup"><span data-stu-id="acad3-109">Snaplines make it easy to align your controls, for crisp, professional appearance and behavior (look and feel).</span></span>

 <span data-ttu-id="acad3-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="acad3-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="acad3-111">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="acad3-111">Creating a Windows Forms project</span></span>

- <span data-ttu-id="acad3-112">使用對齊線對齊控制項並調整其間距</span><span class="sxs-lookup"><span data-stu-id="acad3-112">Spacing and Aligning Controls Using Snaplines</span></span>

- <span data-ttu-id="acad3-113">對齊表單和容器邊界</span><span class="sxs-lookup"><span data-stu-id="acad3-113">Aligning to Form and Container Margins</span></span>

- <span data-ttu-id="acad3-114">對齊群組控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-114">Aligning to Grouped Controls</span></span>

- <span data-ttu-id="acad3-115">使用對齊線來放置控制項, 方法是大綱其大小</span><span class="sxs-lookup"><span data-stu-id="acad3-115">Using Snaplines to Place a Control by Outlining Its Size</span></span>

- <span data-ttu-id="acad3-116">從工具箱拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-116">Using Snaplines When Dragging a Control from the Toolbox</span></span>

- <span data-ttu-id="acad3-117">使用對齊線調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="acad3-117">Resizing Controls Using Snaplines</span></span>

- <span data-ttu-id="acad3-118">將標籤對齊控制項的文字</span><span class="sxs-lookup"><span data-stu-id="acad3-118">Aligning a Label to a Control's Text</span></span>

- <span data-ttu-id="acad3-119">使用對齊線與鍵盤導覽</span><span class="sxs-lookup"><span data-stu-id="acad3-119">Using Snaplines with Keyboard Navigation</span></span>

- <span data-ttu-id="acad3-120">對齊線和版面配置面板</span><span class="sxs-lookup"><span data-stu-id="acad3-120">Snaplines and Layout Panels</span></span>

- <span data-ttu-id="acad3-121">停用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-121">Disabling Snaplines</span></span>

 <span data-ttu-id="acad3-122">當您完成時, 您將瞭解對齊線功能所扮演的版面配置角色。</span><span class="sxs-lookup"><span data-stu-id="acad3-122">When you are finished, you will have an understanding of the layout role played by the snaplines feature.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="acad3-123">建立專案</span><span class="sxs-lookup"><span data-stu-id="acad3-123">Creating the Project</span></span>
 <span data-ttu-id="acad3-124">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-124">The first step is to create the project and set up the form.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="acad3-125">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="acad3-125">To create the project</span></span>

1. <span data-ttu-id="acad3-126">建立名為 "SnaplineExample" 的 Windows 應用程式專案 (  > [檔案] [**新增** > **專案** > ] [**視覺C#效果**] 或 [ **Visual Basic**  > **傳統]** 桌面 >  **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="acad3-126">Create a Windows-based application project called "SnaplineExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="acad3-127">在表單設計工具中選取表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-127">Select the form in the Forms Designer.</span></span>

## <a name="spacing-and-aligning-controls-using-snaplines"></a><span data-ttu-id="acad3-128">使用對齊線對齊控制項並調整其間距</span><span class="sxs-lookup"><span data-stu-id="acad3-128">Spacing and Aligning Controls Using Snaplines</span></span>
 <span data-ttu-id="acad3-129">對齊線可讓您以精確且直覺的方式對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-129">Snaplines give you an accurate and intuitive way to align controls on your form.</span></span> <span data-ttu-id="acad3-130">當您將選取的控制項或控制項移到靠近另一個控制項或一組控制項的位置附近時, 就會顯示它們。</span><span class="sxs-lookup"><span data-stu-id="acad3-130">They appear when you are moving a selected control or controls near a position that would align with another control or set of controls.</span></span> <span data-ttu-id="acad3-131">當您將它移到其他控制項之後, 您的選擇就會「貼齊」到建議的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-131">Your selection will "snap" to the suggested position as you move it past the other controls.</span></span>

### <a name="to-arrange-controls-using-snaplines"></a><span data-ttu-id="acad3-132">使用對齊線排列控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-132">To arrange controls using snaplines</span></span>

1. <span data-ttu-id="acad3-133">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-133">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="acad3-134"><xref:System.Windows.Forms.Button>將控制項移到表單的右下角。</span><span class="sxs-lookup"><span data-stu-id="acad3-134">Move the <xref:System.Windows.Forms.Button> control to the lower-right corner of the form.</span></span> <span data-ttu-id="acad3-135">請注意, 顯示為<xref:System.Windows.Forms.Button>控制項的對齊線會接近表單的底部和右側框線。</span><span class="sxs-lookup"><span data-stu-id="acad3-135">Note the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the form.</span></span> <span data-ttu-id="acad3-136">這些對齊線會顯示控制項框線與表單之間的建議距離。</span><span class="sxs-lookup"><span data-stu-id="acad3-136">These snaplines display the recommended distance between the borders of the control and the form.</span></span>

3. <span data-ttu-id="acad3-137"><xref:System.Windows.Forms.Button>將控制項移到表單的框線周圍, 並注意對齊線的顯示位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-137">Move the <xref:System.Windows.Forms.Button> control around the borders of the form and note where the snaplines appear.</span></span> <span data-ttu-id="acad3-138">當您完成時, 請將<xref:System.Windows.Forms.Button>控制項移到表單的中央附近。</span><span class="sxs-lookup"><span data-stu-id="acad3-138">When you are finished, move the <xref:System.Windows.Forms.Button> control near the center of the form.</span></span>

4. <span data-ttu-id="acad3-139">將另<xref:System.Windows.Forms.Button>一個控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="acad3-139">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="acad3-140">移動第二<xref:System.Windows.Forms.Button>個控制項, 直到接近第一個控制項的層級。</span><span class="sxs-lookup"><span data-stu-id="acad3-140">Move the second <xref:System.Windows.Forms.Button> control until it is nearly level with the first.</span></span> <span data-ttu-id="acad3-141">請注意這兩個按鈕的文字基線上所顯示的對齊線, 並請注意, 您要移動的控制項會貼齊至與其他控制項完全層級的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-141">Note the snapline that appears at the text baseline of both buttons, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>

6. <span data-ttu-id="acad3-142">移動第二<xref:System.Windows.Forms.Button>個控制項, 直到它位於第一個控制項的正上方。</span><span class="sxs-lookup"><span data-stu-id="acad3-142">Move the second <xref:System.Windows.Forms.Button> control until it is positioned directly above the first.</span></span> <span data-ttu-id="acad3-143">請注意出現在兩個按鈕左右邊緣的對齊線, 並請注意, 您要移動的控制項會對齊與其他控制項完全一致的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-143">Note the snaplines that appear along the left and right edges of both buttons, and note that the control you are moving snaps to a position that is exactly aligned with the other control.</span></span>

7. <span data-ttu-id="acad3-144">選取其中一個<xref:System.Windows.Forms.Button>控制項, 然後將其移至另一個, 直到幾乎觸及為止。</span><span class="sxs-lookup"><span data-stu-id="acad3-144">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span> <span data-ttu-id="acad3-145">請記下出現在其間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-145">Note the snapline that appears between them.</span></span> <span data-ttu-id="acad3-146">這個距離是控制項框線之間的建議距離。</span><span class="sxs-lookup"><span data-stu-id="acad3-146">This distance is the recommended distance between the borders of the controls.</span></span> <span data-ttu-id="acad3-147">另請注意, 您要移動的控制項會貼齊此位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-147">Also note that the control you are moving snaps to this position.</span></span>

8. <span data-ttu-id="acad3-148">將兩<xref:System.Windows.Forms.Panel>個控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="acad3-148">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto your form.</span></span>

9. <span data-ttu-id="acad3-149">將其中一個<xref:System.Windows.Forms.Panel>控制項移到接近第一個的層級。</span><span class="sxs-lookup"><span data-stu-id="acad3-149">Move one of the <xref:System.Windows.Forms.Panel> controls until it is nearly level with the first.</span></span> <span data-ttu-id="acad3-150">請注意顯示在這兩個控制項上下邊緣的對齊線, 並請注意, 您要移動的控制項會貼齊至與其他控制項完全層級的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-150">Note the snaplines that appear along the top and bottom edges of both controls, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>

## <a name="aligning-to-form-and-container-margins"></a><span data-ttu-id="acad3-151">對齊表單和容器邊界</span><span class="sxs-lookup"><span data-stu-id="acad3-151">Aligning to Form and Container Margins</span></span>
 <span data-ttu-id="acad3-152">對齊線可協助您以一致的方式讓控制項對齊表單和容器邊界。</span><span class="sxs-lookup"><span data-stu-id="acad3-152">Snaplines help you to align your controls to form and container margins in a consistent manner.</span></span>

### <a name="to-align-controls-to-form-and-container-margins"></a><span data-ttu-id="acad3-153">將控制項對齊表單和容器邊界</span><span class="sxs-lookup"><span data-stu-id="acad3-153">To align controls to form and container margins</span></span>

1. <span data-ttu-id="acad3-154">選取其中一個<xref:System.Windows.Forms.Button>控制項, 然後將它移到靠近表單的右框線, 直到對齊線出現為止。</span><span class="sxs-lookup"><span data-stu-id="acad3-154">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="acad3-155">對齊線與右框線的距離是控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性與表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性值的總和。</span><span class="sxs-lookup"><span data-stu-id="acad3-155">The snapline's distance from the right border is the sum of the control's <xref:System.Windows.Forms.Control.Margin%2A> property and the form's <xref:System.Windows.Forms.Control.Padding%2A> property values.</span></span>

> [!NOTE]
>  <span data-ttu-id="acad3-156">如果表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性設定為 0, 0, 0, 0, 則 Windows Form 設計工具會提供陰影<xref:System.Windows.Forms.Control.Padding%2A>值9、9、9、9的格式。</span><span class="sxs-lookup"><span data-stu-id="acad3-156">If the form's <xref:System.Windows.Forms.Control.Padding%2A> property is set to 0,0,0,0, the Windows Forms Designer gives the form a shadowed <xref:System.Windows.Forms.Control.Padding%2A> value of 9,9,9,9.</span></span> <span data-ttu-id="acad3-157">若要覆寫此行為, 請指派0、0、0、0以外的值。</span><span class="sxs-lookup"><span data-stu-id="acad3-157">To override this behavior, assign a value other than 0,0,0,0.</span></span>

1. <span data-ttu-id="acad3-158">藉由展開 [**屬性**] 視窗<xref:System.Windows.Forms.Control.Margin%2A>中的<xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A>專案, 並將屬性設定為 0, 來變更<xref:System.Windows.Forms.Button>控制項的屬性值。</span><span class="sxs-lookup"><span data-stu-id="acad3-158">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 0.</span></span> <span data-ttu-id="acad3-159">如需詳細資訊[, 請參閱逐步解說:配置具有填補、邊界和 AutoSize 屬性](windows-forms-controls-padding-autosize.md)的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-159">For details, see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>

2. <span data-ttu-id="acad3-160"><xref:System.Windows.Forms.Button>將控制項移到靠近表單的右框線, 直到對齊線出現為止。</span><span class="sxs-lookup"><span data-stu-id="acad3-160">Move the <xref:System.Windows.Forms.Button> control close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="acad3-161">此距離現在是由表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性值提供。</span><span class="sxs-lookup"><span data-stu-id="acad3-161">This distance is now given by the value of the form's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>

3. <span data-ttu-id="acad3-162">從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-162">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="acad3-163">在 [**屬性**] 視窗<xref:System.Windows.Forms.GroupBox>中展開<xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A>專案, 並將屬性設定為10,以變更控制項的屬性值。<xref:System.Windows.Forms.Padding.All%2A></span><span class="sxs-lookup"><span data-stu-id="acad3-163">Change the value of the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 10.</span></span>

5. <span data-ttu-id="acad3-164">將控制項從 [ <xref:System.Windows.Forms.GroupBox>工具箱] 拖曳至控制項。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-164">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>

6. <span data-ttu-id="acad3-165">將控制項移至靠近<xref:System.Windows.Forms.GroupBox>控制項的右框線, 直到對齊線出現為止。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-165">Move the <xref:System.Windows.Forms.Button> control close to the right border of the <xref:System.Windows.Forms.GroupBox> control until a snapline appears.</span></span> <span data-ttu-id="acad3-166">移動<xref:System.Windows.Forms.Button> 控制項<xref:System.Windows.Forms.GroupBox>內的控制項, 並注意對齊線的顯示位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-166">Move the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and note where the snaplines appear.</span></span>

## <a name="aligning-to-grouped-controls"></a><span data-ttu-id="acad3-167">對齊群組控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-167">Aligning to Grouped Controls</span></span>
 <span data-ttu-id="acad3-168">您可以使用對齊線來對齊群組控制項以及控制項內的<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-168">You can use snaplines to align grouped controls as well as controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span>

### <a name="to-align-to-grouped-controls"></a><span data-ttu-id="acad3-169">對齊群組控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-169">To align to grouped controls</span></span>

1. <span data-ttu-id="acad3-170">選取表單上的兩個控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-170">Select two of the controls on your form.</span></span> <span data-ttu-id="acad3-171">移動選取範圍, 並記下您的選取範圍與其他控制項之間出現的對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-171">Move the selection around and note the snaplines that appear between your selection and the other controls.</span></span>

2. <span data-ttu-id="acad3-172">從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-172">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>

3. <span data-ttu-id="acad3-173">將控制項從 [ <xref:System.Windows.Forms.GroupBox>工具箱] 拖曳至控制項。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-173">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>

4. <span data-ttu-id="acad3-174">選取其中一個<xref:System.Windows.Forms.Button>控制項, 然後將它移到<xref:System.Windows.Forms.GroupBox>控制項周圍。</span><span class="sxs-lookup"><span data-stu-id="acad3-174">Select one of the <xref:System.Windows.Forms.Button> controls and move it around the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="acad3-175">請注意顯示在<xref:System.Windows.Forms.GroupBox>控制項邊緣的對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-175">Note the snaplines that appear at the edges of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="acad3-176">也請注意出現在控制項所包含<xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.GroupBox>之控制項邊緣的對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-176">Also note the snaplines that appear at the edges of the <xref:System.Windows.Forms.Button> control that is contained by the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="acad3-177">屬於容器控制項子系的控制項也支援對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-177">Controls that are children of a container control also support snaplines.</span></span>

## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="acad3-178">使用對齊線來放置控制項, 方法是大綱其大小</span><span class="sxs-lookup"><span data-stu-id="acad3-178">Using Snaplines to Place a Control by Outlining Its Size</span></span>
 <span data-ttu-id="acad3-179">當您第一次將控制項放在表單上時, 對齊線可協助您對齊它們。</span><span class="sxs-lookup"><span data-stu-id="acad3-179">Snaplines help you align controls when you first place them on a form.</span></span>

### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="acad3-180">若要使用對齊線來放置控制項, 請藉由大綱其大小</span><span class="sxs-lookup"><span data-stu-id="acad3-180">To use snaplines to place a control by outlining its size</span></span>

1. <span data-ttu-id="acad3-181">按一下 [工具箱]的 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="acad3-181">In the **Toolbox**, click the <xref:System.Windows.Forms.Button> control icon.</span></span> <span data-ttu-id="acad3-182">請勿拖曳到表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-182">Do not drag it onto the form.</span></span>

2. <span data-ttu-id="acad3-183">將滑鼠指標移到表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="acad3-183">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="acad3-184">請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="acad3-184">Note that the pointer changes to a crosshair with the <xref:System.Windows.Forms.Button> control icon attached.</span></span> <span data-ttu-id="acad3-185">另請注意, 顯示的對齊線會建議<xref:System.Windows.Forms.Button>控制項的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-185">Also note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span>

3. <span data-ttu-id="acad3-186">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="acad3-186">Click and hold the mouse button.</span></span>

4. <span data-ttu-id="acad3-187">將滑鼠指標拖曳至表單的周圍。</span><span class="sxs-lookup"><span data-stu-id="acad3-187">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="acad3-188">請注意, 會繪製外框, 表示控制項的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="acad3-188">Note that an outline is drawn, indicating the position and the size of the control.</span></span>

5. <span data-ttu-id="acad3-189">拖曳指標, 直到它與表單上的另一個控制項對齊。</span><span class="sxs-lookup"><span data-stu-id="acad3-189">Drag the pointer until it aligns with another control on the form.</span></span> <span data-ttu-id="acad3-190">請注意, 對齊線會出現以指出對齊方式。</span><span class="sxs-lookup"><span data-stu-id="acad3-190">Note that a snapline appears to indicate alignment.</span></span>

6. <span data-ttu-id="acad3-191">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="acad3-191">Release the mouse button.</span></span> <span data-ttu-id="acad3-192">控制項會建立在外框所指示的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="acad3-192">The control is created at the position and size indicated by the outline.</span></span>

## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="acad3-193">從工具箱拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-193">Using Snaplines When Dragging a Control from the Toolbox</span></span>
 <span data-ttu-id="acad3-194">當您從 [**工具箱**] 將控制項拖曳至表單上時, 對齊線可協助您對齊控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-194">Snaplines help you align controls when you drag them from the **Toolbox** onto your form.</span></span>

### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="acad3-195">從工具箱拖曳控制項時使用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-195">To use snaplines when dragging a control from the Toolbox</span></span>

1. <span data-ttu-id="acad3-196">將控制項從 [工具箱] 拖曳至表單上, 但不要放開滑鼠按鍵。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-196">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form, but do not release the mouse button.</span></span>

2. <span data-ttu-id="acad3-197">將滑鼠指標移到表單的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="acad3-197">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="acad3-198">請注意, 指標會變更以指出將建立新<xref:System.Windows.Forms.Button>控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-198">Note that the pointer changes to indicate the position at which the new <xref:System.Windows.Forms.Button> control will be created.</span></span>

3. <span data-ttu-id="acad3-199">將滑鼠指標拖曳至表單的周圍。</span><span class="sxs-lookup"><span data-stu-id="acad3-199">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="acad3-200">請注意, 顯示的對齊線會建議<xref:System.Windows.Forms.Button>控制項的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-200">Note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="acad3-201">尋找與其他控制項對齊的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-201">Find a position that is aligned with other controls.</span></span>

4. <span data-ttu-id="acad3-202">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="acad3-202">Release the mouse button.</span></span> <span data-ttu-id="acad3-203">會在對齊線所指示的位置建立控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-203">The control is created at the position indicated by the snaplines.</span></span>

## <a name="resizing-controls-using-snaplines"></a><span data-ttu-id="acad3-204">使用對齊線調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="acad3-204">Resizing Controls Using Snaplines</span></span>
 <span data-ttu-id="acad3-205">對齊線可協助您在調整控制項大小時將其對齊。</span><span class="sxs-lookup"><span data-stu-id="acad3-205">Snaplines help you align controls as you resize them.</span></span>

### <a name="to-resize-a-control-using-snaplines"></a><span data-ttu-id="acad3-206">使用對齊線調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="acad3-206">To resize a control using snaplines</span></span>

1. <span data-ttu-id="acad3-207">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-207">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="acad3-208">藉由抓取其中一個角落調整大小控點和拖曳來調整控制項大小。<xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-208">Resize the <xref:System.Windows.Forms.Button> control by grabbing one of the corner sizing handles and dragging.</span></span> <span data-ttu-id="acad3-209">如需詳細資訊，請參閱[如何：調整 Windows Forms](how-to-resize-controls-on-windows-forms.md)上的控制項大小。</span><span class="sxs-lookup"><span data-stu-id="acad3-209">For details, see [How to: Resize Controls on Windows Forms](how-to-resize-controls-on-windows-forms.md).</span></span>

3. <span data-ttu-id="acad3-210">拖曳調整大小控點, 直到<xref:System.Windows.Forms.Button>其中一個控制項的框線與另一個控制項對齊為止。</span><span class="sxs-lookup"><span data-stu-id="acad3-210">Drag the sizing handle until one of the <xref:System.Windows.Forms.Button> control's borders is aligned with another control.</span></span> <span data-ttu-id="acad3-211">請注意, 對齊線隨即出現。</span><span class="sxs-lookup"><span data-stu-id="acad3-211">Note that a snapline appears.</span></span> <span data-ttu-id="acad3-212">另請注意, 調整大小控點會貼齊對齊線所指示的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-212">Also note that the sizing handle snaps to the position indicated by the snapline.</span></span>

4. <span data-ttu-id="acad3-213">以不同<xref:System.Windows.Forms.Button>的方向調整控制項的大小, 並將調整大小控點對齊不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-213">Resize the <xref:System.Windows.Forms.Button> control in different directions and align the sizing handle to different controls.</span></span> <span data-ttu-id="acad3-214">請注意對齊線如何顯示在各種方向, 以表示對齊方式。</span><span class="sxs-lookup"><span data-stu-id="acad3-214">Note how the snaplines appear in various orientations to indicate alignment.</span></span>

## <a name="aligning-a-label-to-a-controls-text"></a><span data-ttu-id="acad3-215">將標籤對齊控制項的文字</span><span class="sxs-lookup"><span data-stu-id="acad3-215">Aligning a Label to a Control's Text</span></span>
 <span data-ttu-id="acad3-216">有些控制項提供對齊線, 讓其他控制項對齊顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="acad3-216">Some controls offer a snapline for aligning other controls to displayed text.</span></span>

### <a name="to-align-a-label-to-a-controls-text"></a><span data-ttu-id="acad3-217">將標籤對齊控制項的文字</span><span class="sxs-lookup"><span data-stu-id="acad3-217">To align a label to a control's text</span></span>

1. <span data-ttu-id="acad3-218">從 [工具箱] <xref:System.Windows.Forms.TextBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-218">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="acad3-219">當您將<xref:System.Windows.Forms.TextBox>控制項拖放到表單上時, 請按一下智慧標籤圖像, 然後選取 [**將文字設定為 textBox1** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="acad3-219">When you drop the <xref:System.Windows.Forms.TextBox> control onto the form, click the smart-tag glyph and select the **Set text to textBox1** option.</span></span> <span data-ttu-id="acad3-220">如需詳細資訊[, 請參閱逐步解說:使用 Windows Forms 控制項](performing-common-tasks-using-smart-tags-on-wf-controls.md)上的智慧標籤執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="acad3-220">For details, see [Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md).</span></span>

2. <span data-ttu-id="acad3-221">從 [工具箱] <xref:System.Windows.Forms.Label>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-221">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto your form.</span></span>

3. <span data-ttu-id="acad3-222">變更 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="acad3-222">Change the value of the <xref:System.Windows.Forms.Label> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="acad3-223">請注意, 控制項的框線會調整以符合顯示文字。</span><span class="sxs-lookup"><span data-stu-id="acad3-223">Note that the control's borders are adjusted to fit the display text.</span></span>

4. <span data-ttu-id="acad3-224">將控制項移至<xref:System.Windows.Forms.TextBox>控制項的左側, 使其與<xref:System.Windows.Forms.TextBox>控制項的下邊緣對齊。 <xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="acad3-224">Move the <xref:System.Windows.Forms.Label> control to the left of the <xref:System.Windows.Forms.TextBox> control, so it is aligned with the bottom edge of the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="acad3-225">請注意沿著兩個控制項的下邊緣顯示的對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-225">Note the snapline that appears along the bottom edges of the two controls.</span></span>

5. <span data-ttu-id="acad3-226">將控制項稍微向上移動, <xref:System.Windows.Forms.Label>直到文字與<xref:System.Windows.Forms.TextBox>文字對齊為止。 <xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="acad3-226">Move the <xref:System.Windows.Forms.Label> control slightly upward, until the <xref:System.Windows.Forms.Label> text and the <xref:System.Windows.Forms.TextBox> text are aligned.</span></span> <span data-ttu-id="acad3-227">請注意出現的不同樣式對齊線, 表示兩個控制項的文字欄位何時對齊。</span><span class="sxs-lookup"><span data-stu-id="acad3-227">Note the differently styled snapline that appears, indicating when the text fields of both controls are aligned.</span></span>

## <a name="using-snaplines-with-keyboard-navigation"></a><span data-ttu-id="acad3-228">使用對齊線與鍵盤導覽</span><span class="sxs-lookup"><span data-stu-id="acad3-228">Using Snaplines with Keyboard Navigation</span></span>
 <span data-ttu-id="acad3-229">當您使用鍵盤的方向鍵排列控制項時, 對齊線可協助您對齊控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-229">Snaplines help you align controls when you are arranging them using the keyboard's arrow keys.</span></span>

### <a name="to-use-snaplines-with-keyboard-navigation"></a><span data-ttu-id="acad3-230">搭配鍵盤導覽使用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-230">To use snaplines with keyboard navigation</span></span>

1. <span data-ttu-id="acad3-231">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-231">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="acad3-232">將它放在表單的左上角。</span><span class="sxs-lookup"><span data-stu-id="acad3-232">Place it in the upper-left corner of the form.</span></span>

2. <span data-ttu-id="acad3-233">按 CTRL + 向下鍵。</span><span class="sxs-lookup"><span data-stu-id="acad3-233">Press CTRL+DOWN ARROW.</span></span> <span data-ttu-id="acad3-234">請注意, 控制項會向下移動到第一個可用的水準對齊位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-234">Note that the control moves down the form to the first available horizontal alignment position.</span></span>

3. <span data-ttu-id="acad3-235">按 CTRL + 向下鍵, 直到控制項到達表單的底部為止。</span><span class="sxs-lookup"><span data-stu-id="acad3-235">Press CTRL+DOWN ARROW until the control reaches the bottom of the form.</span></span> <span data-ttu-id="acad3-236">請注意它在表單向下移動時所佔用的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-236">Note the positions it occupies as it moves down the form.</span></span>

4. <span data-ttu-id="acad3-237">按 CTRL + 向右鍵。</span><span class="sxs-lookup"><span data-stu-id="acad3-237">Press CTRL+RIGHT ARROW.</span></span> <span data-ttu-id="acad3-238">請注意, 控制項會在表單上移動到第一個可用的垂直對齊位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-238">Note that the control moves across the form to the first available vertical alignment position.</span></span>

5. <span data-ttu-id="acad3-239">按 CTRL + 向右鍵, 直到控制項到達表單的側邊為止。</span><span class="sxs-lookup"><span data-stu-id="acad3-239">Press CTRL+RIGHT ARROW until the control reaches the side of the form.</span></span> <span data-ttu-id="acad3-240">請注意它在表單上移動時所佔用的位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-240">Note the positions it occupies as it moves across the form.</span></span>

6. <span data-ttu-id="acad3-241">使用方向鍵的組合來移動表單周圍的控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-241">Move the control around the form with a combination of arrow keys.</span></span> <span data-ttu-id="acad3-242">請注意控制項所佔用的位置以及伴隨的對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-242">Note the positions the control occupies and the snaplines that accompany them.</span></span>

7. <span data-ttu-id="acad3-243">按 SHIFT + 任何方向鍵, 以一個<xref:System.Windows.Forms.Button>圖元的增量來調整控制項大小。</span><span class="sxs-lookup"><span data-stu-id="acad3-243">Press SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control by increments of one pixel.</span></span>

8. <span data-ttu-id="acad3-244">按 CTRL + SHIFT + 任何方向鍵, 以調整<xref:System.Windows.Forms.Button>控制項的對齊方式遞增。</span><span class="sxs-lookup"><span data-stu-id="acad3-244">Press CTRL+SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control in snapline increments.</span></span>

## <a name="snaplines-and-layout-panels"></a><span data-ttu-id="acad3-245">對齊線和版面配置面板</span><span class="sxs-lookup"><span data-stu-id="acad3-245">Snaplines and Layout Panels</span></span>
 <span data-ttu-id="acad3-246">對齊線會在版面配置面板內停用。</span><span class="sxs-lookup"><span data-stu-id="acad3-246">Snaplines are disabled within layout panels.</span></span>

### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="acad3-247">選擇性停用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-247">To selectively disable snaplines</span></span>

1. <span data-ttu-id="acad3-248">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="acad3-248">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="acad3-249">在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="acad3-249">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox**.</span></span> <span data-ttu-id="acad3-250">請注意, <xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個儲存格會顯示新的按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-250">Note that a new button control appears in the <xref:System.Windows.Forms.TableLayoutPanel> control's first cell.</span></span>

3. <span data-ttu-id="acad3-251">在 [**工具箱**] 中按兩下控制項圖示,再按兩次。<xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-251">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox** twice more.</span></span> <span data-ttu-id="acad3-252">這會在<xref:System.Windows.Forms.TableLayoutPanel>控制項中留下一個空白儲存格。</span><span class="sxs-lookup"><span data-stu-id="acad3-252">This leaves one empty cell in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="acad3-253">將控制項從 [**工具箱**] 拖曳至<xref:System.Windows.Forms.TableLayoutPanel>控制項的空白儲存格。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-253">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the empty cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="acad3-254">請注意, 不會顯示對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-254">Note that no snaplines appear.</span></span>

5. <span data-ttu-id="acad3-255">將控制項拖曳到控制項外<xref:System.Windows.Forms.TableLayoutPanel> , 並將其移到<xref:System.Windows.Forms.TableLayoutPanel>控制項周圍。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-255">Drag the <xref:System.Windows.Forms.Button> control out of the <xref:System.Windows.Forms.TableLayoutPanel> control and move it around the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="acad3-256">請注意, 對齊線會再次出現。</span><span class="sxs-lookup"><span data-stu-id="acad3-256">Note that snaplines appear again.</span></span>

## <a name="disabling-snaplines"></a><span data-ttu-id="acad3-257">停用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-257">Disabling Snaplines</span></span>
 <span data-ttu-id="acad3-258">預設會開啟對齊線。</span><span class="sxs-lookup"><span data-stu-id="acad3-258">Snaplines are turned on by default.</span></span> <span data-ttu-id="acad3-259">您可以選擇性地停用對齊線, 也可以在設計環境中將它停用。</span><span class="sxs-lookup"><span data-stu-id="acad3-259">You can disable snaplines selectively, or you can disable them in the design environment.</span></span>

### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="acad3-260">選擇性停用對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-260">To selectively disable snaplines</span></span>

- <span data-ttu-id="acad3-261">按 ALT 鍵, 並在表單周圍移動控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-261">Press the ALT key and while moving a control around the form.</span></span>

     <span data-ttu-id="acad3-262">請注意, 不會顯示對齊線, 而且控制項不會貼齊任何可能的對齊位置。</span><span class="sxs-lookup"><span data-stu-id="acad3-262">Note that no snaplines appear and the control does not snap to any potential alignment positions.</span></span>

### <a name="to-disable-snaplines-in-the-design-environment"></a><span data-ttu-id="acad3-263">停用設計環境中的對齊線</span><span class="sxs-lookup"><span data-stu-id="acad3-263">To disable snaplines in the design environment</span></span>

1. <span data-ttu-id="acad3-264">從 [**工具**] 功能表中, 開啟 [**選項**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="acad3-264">From the **Tools** menu, open the **Options** dialog box.</span></span> <span data-ttu-id="acad3-265">開啟 [Windows Form 設計工具] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="acad3-265">Open the Windows Forms Designer dialog box.</span></span> <span data-ttu-id="acad3-266">如需詳細資訊, 請參閱[[一般]、[Windows Form 設計工具]、[選項] 對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="acad3-266">For details, see [General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).</span></span>

2. <span data-ttu-id="acad3-267">選取 [**一般**] 節點。</span><span class="sxs-lookup"><span data-stu-id="acad3-267">Select the **General** node.</span></span> <span data-ttu-id="acad3-268">在 [**版面配置模式]** 區段中, 將選取專案從**對齊線**變更為**對齊**。</span><span class="sxs-lookup"><span data-stu-id="acad3-268">In the **Layout Mode** section, change the selection from **SnapLines** to **SnapToGrid**.</span></span>

3. <span data-ttu-id="acad3-269">按一下 [確定] 以套用設定。</span><span class="sxs-lookup"><span data-stu-id="acad3-269">Click OK to apply the setting.</span></span>

4. <span data-ttu-id="acad3-270">選取表單上的控制項, 並將它移到其他控制項的周圍。</span><span class="sxs-lookup"><span data-stu-id="acad3-270">Select a control on your form and move it around the other controls.</span></span> <span data-ttu-id="acad3-271">請注意, 對齊線不會出現。</span><span class="sxs-lookup"><span data-stu-id="acad3-271">Note that snaplines do not appear.</span></span>

## <a name="next-steps"></a><span data-ttu-id="acad3-272">後續步驟</span><span class="sxs-lookup"><span data-stu-id="acad3-272">Next Steps</span></span>
 <span data-ttu-id="acad3-273">對齊線提供直覺的方式來對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-273">Snaplines offer an intuitive means of aligning controls on your form.</span></span> <span data-ttu-id="acad3-274">進一步的探索建議包括：</span><span class="sxs-lookup"><span data-stu-id="acad3-274">Suggestions for more exploration include:</span></span>

- <span data-ttu-id="acad3-275">嘗試在另<xref:System.Windows.Forms.GroupBox>一個<xref:System.Windows.Forms.GroupBox>控制項內嵌套控制項。</span><span class="sxs-lookup"><span data-stu-id="acad3-275">Try nesting a <xref:System.Windows.Forms.GroupBox> control within another <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="acad3-276">將控制項放在子<xref:System.Windows.Forms.GroupBox>控制項內, 另一個在父<xref:System.Windows.Forms.GroupBox>控制項內。 <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="acad3-276">Place a <xref:System.Windows.Forms.Button> control within the child <xref:System.Windows.Forms.GroupBox> control, and another within the parent <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="acad3-277">移動周圍<xref:System.Windows.Forms.Button>的控制項, 以查看對齊線如何跨容器界限。</span><span class="sxs-lookup"><span data-stu-id="acad3-277">Move the <xref:System.Windows.Forms.Button> controls around to see how the snaplines cross container boundaries.</span></span>

- <span data-ttu-id="acad3-278">建立<xref:System.Windows.Forms.TextBox>控制項的資料行, 以及<xref:System.Windows.Forms.Label>控制項的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="acad3-278">Create a column of <xref:System.Windows.Forms.TextBox> controls and a corresponding column of <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="acad3-279">將<xref:System.Windows.Forms.Label> `true`控制項的屬性值設定為。 <xref:System.Windows.Forms.Control.AutoSize%2A></span><span class="sxs-lookup"><span data-stu-id="acad3-279">Set the value of the <xref:System.Windows.Forms.Label> controls' <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="acad3-280">使用對齊線移動<xref:System.Windows.Forms.Label>控制項, 使其顯示的文字與<xref:System.Windows.Forms.TextBox>控制項中的文字對齊。</span><span class="sxs-lookup"><span data-stu-id="acad3-280">Use snaplines to move the <xref:System.Windows.Forms.Label> controls so their displayed text is aligned with the text in the <xref:System.Windows.Forms.TextBox> controls.</span></span>

 <span data-ttu-id="acad3-281">如需 Windows 使用者介面設計的相關資訊, 請參閱《 *Microsoft Windows 使用者經驗》, 使用者介面開發人員和設計人員的官方指導方針*, WA:Microsoft 請按1999。</span><span class="sxs-lookup"><span data-stu-id="acad3-281">For information about Windows user interface design, see the book *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, WA: Microsoft Press, 1999.</span></span> <span data-ttu-id="acad3-282">(USBN:0-7356-0566-1)。</span><span class="sxs-lookup"><span data-stu-id="acad3-282">(USBN: 0-7356-0566-1).</span></span>

## <a name="see-also"></a><span data-ttu-id="acad3-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acad3-283">See also</span></span>

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [<span data-ttu-id="acad3-284">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-284">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="acad3-285">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-285">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="acad3-286">逐步解說：配置具有填補、邊界和 AutoSize 屬性的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-286">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
- [<span data-ttu-id="acad3-287">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="acad3-287">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
