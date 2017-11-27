---
title: "逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dce58776af84b1f4c733ddce2553e4b18b1b824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a><span data-ttu-id="89907-102">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="89907-102">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>
<span data-ttu-id="89907-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="89907-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="89907-104">**Windows Form 設計工具**可提供您許多版面配置工具完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="89907-104">The **Windows Forms Designer** gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="89907-105">三個最重要的是<xref:System.Windows.Forms.Control.Margin%2A>， <xref:System.Windows.Forms.Control.Padding%2A>，和<xref:System.Windows.Forms.Control.AutoSize%2A>都存在於所有 Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-105">Three of the most important are the <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, and <xref:System.Windows.Forms.Control.AutoSize%2A> properties, which are present on all Windows Forms controls.</span></span>  
  
 <span data-ttu-id="89907-106"><xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="89907-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="89907-107"><xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="89907-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="89907-108">下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="89907-109">![填補和邊界，適用於 Windows Form 控制項](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="89907-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="89907-110"><xref:System.Windows.Forms.Control.AutoSize%2A>屬性會告知自動調整本身大小到其內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-110">The <xref:System.Windows.Forms.Control.AutoSize%2A> property tells a control to automatically size itself to its contents.</span></span> <span data-ttu-id="89907-111">它不會調整大小必須小於其原始值本身<xref:System.Windows.Forms.Control.Size%2A>屬性，而且它會負責的值及其<xref:System.Windows.Forms.Control.Padding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-111">It will not resize itself to be smaller than the value of its original <xref:System.Windows.Forms.Control.Size%2A> property, and it will account for the value of its <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
 <span data-ttu-id="89907-112">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="89907-112">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="89907-113">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="89907-113">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="89907-114">設定您的控制項的邊界</span><span class="sxs-lookup"><span data-stu-id="89907-114">Setting Margins for Your Controls</span></span>  
  
-   <span data-ttu-id="89907-115">設定您的控制項的邊框距離</span><span class="sxs-lookup"><span data-stu-id="89907-115">Setting Padding for Your Controls</span></span>  
  
-   <span data-ttu-id="89907-116">自動調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="89907-116">Automatically Sizing Your Controls</span></span>  
  
 <span data-ttu-id="89907-117">完成後，您就會了解這些重要配置功能所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="89907-117">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89907-118">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="89907-118">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="89907-119">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="89907-119">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="89907-120">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="89907-120">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="89907-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="89907-121">Prerequisites</span></span>  
 <span data-ttu-id="89907-122">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="89907-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="89907-123">若要能夠建立及安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="89907-123">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="89907-124">建立專案</span><span class="sxs-lookup"><span data-stu-id="89907-124">Creating the Project</span></span>  
 <span data-ttu-id="89907-125">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="89907-125">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="89907-126">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="89907-126">To create the project</span></span>  
  
1.  <span data-ttu-id="89907-127">建立**Windows 應用程式**專案，稱為`LayoutExample`。</span><span class="sxs-lookup"><span data-stu-id="89907-127">Create a **Windows Application** project called `LayoutExample`.</span></span> <span data-ttu-id="89907-128">如需詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="89907-128">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) .</span></span>  
  
2.  <span data-ttu-id="89907-129">選取的表單中**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="89907-129">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="setting-margins-for-your-controls"></a><span data-ttu-id="89907-130">設定您的控制項的邊界</span><span class="sxs-lookup"><span data-stu-id="89907-130">Setting Margins for Your Controls</span></span>  
 <span data-ttu-id="89907-131">您可以設定您使用的控制項之間的預設距離<xref:System.Windows.Forms.Control.Margin%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-131">You can set the default distance between your controls using the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="89907-132">當您移動控制項接近另一個控制項，您會看到顯示兩個控制項的邊界的對齊線。</span><span class="sxs-lookup"><span data-stu-id="89907-132">When you move a control close enough to another control, you will see a snapline that shows the margins for the two controls.</span></span> <span data-ttu-id="89907-133">您要移動的控制項也將貼齊邊界所定義的距離。</span><span class="sxs-lookup"><span data-stu-id="89907-133">The control you are moving will also snap to the distance defined by the margins.</span></span>  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a><span data-ttu-id="89907-134">若要排列使用 Margin 屬性在表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="89907-134">To arrange controls on your form using the Margin property</span></span>  
  
1.  <span data-ttu-id="89907-135">拖放兩<xref:System.Windows.Forms.Button>控制從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-135">Drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="89907-136">選取其中一個<xref:System.Windows.Forms.Button>控制，並將其接近，直到幾乎碰觸。</span><span class="sxs-lookup"><span data-stu-id="89907-136">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span>  
  
     <span data-ttu-id="89907-137">觀察出現在它們之間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="89907-137">Observe the snapline that appears between them.</span></span> <span data-ttu-id="89907-138">這個距離為兩個控制項的總和<xref:System.Windows.Forms.Control.Margin%2A>值。</span><span class="sxs-lookup"><span data-stu-id="89907-138">This distance is the sum of the two controls' <xref:System.Windows.Forms.Control.Margin%2A> values.</span></span> <span data-ttu-id="89907-139">您要移動的控制項貼齊至這個距離。</span><span class="sxs-lookup"><span data-stu-id="89907-139">The control you are moving snaps to this distance.</span></span> <span data-ttu-id="89907-140">如需詳細資訊，請參閱[逐步解說： 在 Windows Form 使用對齊線排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="89907-140">For details, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
3.  <span data-ttu-id="89907-141">變更<xref:System.Windows.Forms.Control.Margin%2A>屬性的其中一個方法是展開控制項<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>到 20 的屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-141">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of one of the controls by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 20.</span></span>  
  
4.  <span data-ttu-id="89907-142">選取其中一個<xref:System.Windows.Forms.Button>控制，並將它移到靠近另。</span><span class="sxs-lookup"><span data-stu-id="89907-142">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other.</span></span>  
  
     <span data-ttu-id="89907-143">對齊線定義的邊界值總和較長，而且從其他控制項的控制項貼齊至較遠的距離。</span><span class="sxs-lookup"><span data-stu-id="89907-143">The snapline defining the sum of the margin values is longer and that the control snaps to a greater distance from the other control.</span></span>  
  
5.  <span data-ttu-id="89907-144">變更<xref:System.Windows.Forms.Control.Margin%2A>展開選取的控制項屬性<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.Top%2A>屬性設定為 5。</span><span class="sxs-lookup"><span data-stu-id="89907-144">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of the selected control by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.Top%2A> property to 5.</span></span>  
  
6.  <span data-ttu-id="89907-145">將其他控制項下方選取的控制項，並觀察對齊線是短。</span><span class="sxs-lookup"><span data-stu-id="89907-145">Move the selected control below the other control and observe that the snapline is shorter.</span></span> <span data-ttu-id="89907-146">將選取的控制項移到其他控制項的左邊，並觀察對齊線會保留在步驟 4 中觀察到的值。</span><span class="sxs-lookup"><span data-stu-id="89907-146">Move the selected control to the left of the other control and observe that the snapline retains the value observed in step 4.</span></span>  
  
7.  <span data-ttu-id="89907-147">您可以設定每個層面<xref:System.Windows.Forms.Control.Margin%2A>屬性， <xref:System.Windows.Forms.Padding.Left%2A>， <xref:System.Windows.Forms.Padding.Top%2A>， <xref:System.Windows.Forms.Padding.Right%2A>， <xref:System.Windows.Forms.Padding.Bottom%2A>、 到不同的值，或者您可以將它們設定為相同的值與所有<xref:System.Windows.Forms.Padding.All%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-147">You can set each of the aspects of the <xref:System.Windows.Forms.Control.Margin%2A> property, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, to different values, or you can set them all to the same value with the <xref:System.Windows.Forms.Padding.All%2A> property.</span></span>  
  
## <a name="setting-padding-for-your-controls"></a><span data-ttu-id="89907-148">設定您的控制項的邊框距離</span><span class="sxs-lookup"><span data-stu-id="89907-148">Setting Padding for Your Controls</span></span>  
 <span data-ttu-id="89907-149">若要達成精確的版面配置所需的應用程式，您的控制項通常會包含子控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-149">To achieve the precise layout required for your application, your controls will often contain child controls.</span></span> <span data-ttu-id="89907-150">當您想要指定子控制項的框線的接近度，以父控制項的框線時，使用父控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性搭配子控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-150">When you want to specify the proximity of the child control's border to the parent control's border, use the parent control's <xref:System.Windows.Forms.Control.Padding%2A> property in conjunction with the child control's <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="89907-151"><xref:System.Windows.Forms.Control.Padding%2A>屬性也用來控制 「 相近的控制項的內容 (例如，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性) 至其框線。</span><span class="sxs-lookup"><span data-stu-id="89907-151">The <xref:System.Windows.Forms.Control.Padding%2A> property is also used to control the proximity of a control's content (for example, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property) to its borders.</span></span>  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a><span data-ttu-id="89907-152">若要排列使用邊框距離表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="89907-152">To arrange controls on your form using padding</span></span>  
  
1.  <span data-ttu-id="89907-153">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-153">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="89907-154">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="89907-154">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="89907-155">變更<xref:System.Windows.Forms.Control.Padding%2A>屬性展開<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性設定為 5。</span><span class="sxs-lookup"><span data-stu-id="89907-155">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 5.</span></span>  
  
     <span data-ttu-id="89907-156">控制項會展開騰出空間給新的邊框距離。</span><span class="sxs-lookup"><span data-stu-id="89907-156">The control expands to provide room for the new padding.</span></span>  
  
4.  <span data-ttu-id="89907-157">拖曳<xref:System.Windows.Forms.GroupBox>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-157">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="89907-158">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**到<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-158">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="89907-159">位置<xref:System.Windows.Forms.Button>控制排清的右下角是<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-159">Position the <xref:System.Windows.Forms.Button> control so it is flush with the lower-right corner of the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
     <span data-ttu-id="89907-160">觀察顯示為的對齊線<xref:System.Windows.Forms.Button>控制方法的下和右框線的<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-160">Observe the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="89907-161">這些對齊線對應至<xref:System.Windows.Forms.Control.Margin%2A>屬性<xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="89907-161">These snaplines correspond to the <xref:System.Windows.Forms.Control.Margin%2A> property of the <xref:System.Windows.Forms.Button>.</span></span>  
  
5.  <span data-ttu-id="89907-162">變更<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性展開<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>到 20 的屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-162">Change the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 20.</span></span>  
  
6.  <span data-ttu-id="89907-163">選取<xref:System.Windows.Forms.Button>內控制<xref:System.Windows.Forms.GroupBox>控制，並將其移向的中央<xref:System.Windows.Forms.GroupBox>。</span><span class="sxs-lookup"><span data-stu-id="89907-163">Select the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and move it toward the center of the <xref:System.Windows.Forms.GroupBox>.</span></span>  
  
     <span data-ttu-id="89907-164">從的框線對齊線會出現在較遠的距離<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-164">The snaplines appear at a greater distance from the borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="89907-165">是的總和。 這個距離<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性和<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-165">This distance is the sum of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property and the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
## <a name="automatically-sizing-your-controls"></a><span data-ttu-id="89907-166">自動調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="89907-166">Automatically Sizing Your Controls</span></span>  
 <span data-ttu-id="89907-167">在某些應用程式中，控制項的大小不會相同執行階段是在設計階段。</span><span class="sxs-lookup"><span data-stu-id="89907-167">In some applications, the size of a control will not be the same at run time as it was at design time.</span></span> <span data-ttu-id="89907-168">文字<xref:System.Windows.Forms.Button>控制項，例如，可能會從資料庫中，並將無法事先知道它的長度。</span><span class="sxs-lookup"><span data-stu-id="89907-168">The text of a <xref:System.Windows.Forms.Button> control, for example, may be taken from a database, and its length will not be known in advance.</span></span>  
  
 <span data-ttu-id="89907-169">當<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設定為`true`，控制項將其內容調整本身。</span><span class="sxs-lookup"><span data-stu-id="89907-169">When the <xref:System.Windows.Forms.Control.AutoSize%2A> property is set to `true`, the control will size itself to its content.</span></span> <span data-ttu-id="89907-170">如需詳細資訊，請參閱[AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="89907-170">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a><span data-ttu-id="89907-171">若要排列使用 AutoSize 屬性在表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="89907-171">To arrange controls on your form using the AutoSize property</span></span>  
  
1.  <span data-ttu-id="89907-172">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-172">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="89907-173">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="89907-173">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="89907-174">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性為"**此按鈕會有長字串的文字屬性**。 」</span><span class="sxs-lookup"><span data-stu-id="89907-174">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property**."</span></span>  
  
     <span data-ttu-id="89907-175">當您認可變更，<xref:System.Windows.Forms.Button>控制項自動調整大小以配合新的文字。</span><span class="sxs-lookup"><span data-stu-id="89907-175">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself to fit the new text.</span></span>  
  
4.  <span data-ttu-id="89907-176">拖曳其他<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-176">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
5.  <span data-ttu-id="89907-177">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性為"**此按鈕會有長字串的文字屬性。**"</span><span class="sxs-lookup"><span data-stu-id="89907-177">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>  
  
     <span data-ttu-id="89907-178">當您認可變更，<xref:System.Windows.Forms.Button>控制項調整本身，都不大小和文字由控制項的右邊緣裁剪。</span><span class="sxs-lookup"><span data-stu-id="89907-178">When you commit the change, the <xref:System.Windows.Forms.Button> control does not resize itself, and the text is clipped by the right edge of the control.</span></span>  
  
6.  <span data-ttu-id="89907-179">變更<xref:System.Windows.Forms.Control.Padding%2A>屬性展開<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性設定為 5。</span><span class="sxs-lookup"><span data-stu-id="89907-179">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 5.</span></span>  
  
     <span data-ttu-id="89907-180">在控制項的內部文字會遭到裁剪，四個邊。</span><span class="sxs-lookup"><span data-stu-id="89907-180">The text in the control's interior is clipped on all four sides.</span></span>  
  
7.  <span data-ttu-id="89907-181">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="89907-181">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="89907-182"><xref:System.Windows.Forms.Button>控制項調整大小，以包含整個字串。</span><span class="sxs-lookup"><span data-stu-id="89907-182">The <xref:System.Windows.Forms.Button> control resizes itself to encompass the entire string.</span></span> <span data-ttu-id="89907-183">此外，填補已加入該文字周圍，造成<xref:System.Windows.Forms.Button>控制項中所有的四個方向擴展。</span><span class="sxs-lookup"><span data-stu-id="89907-183">Also, padding has been added around the text, causing the <xref:System.Windows.Forms.Button> control to expand in all four directions.</span></span>  
  
8.  <span data-ttu-id="89907-184">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-184">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="89907-185">將它放置在表單的右下角附近。</span><span class="sxs-lookup"><span data-stu-id="89907-185">Position it near the lower-right corner of the form.</span></span>  
  
9. <span data-ttu-id="89907-186">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="89907-186">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
10. <span data-ttu-id="89907-187">設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性<xref:System.Windows.Forms.AnchorStyles.Right>， <xref:System.Windows.Forms.AnchorStyles.Bottom>。</span><span class="sxs-lookup"><span data-stu-id="89907-187">Set the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.</span></span>  
  
11. <span data-ttu-id="89907-188">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性為"**此按鈕會有長字串的文字屬性。**"</span><span class="sxs-lookup"><span data-stu-id="89907-188">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>  
  
     <span data-ttu-id="89907-189">當您認可變更，<xref:System.Windows.Forms.Button>控制項會調整本身大小方。</span><span class="sxs-lookup"><span data-stu-id="89907-189">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself toward the left.</span></span> <span data-ttu-id="89907-190">一般情況下，自動調整大小會增加相反方向中的控制項大小其<xref:System.Windows.Forms.Control.Anchor%2A>屬性設定。</span><span class="sxs-lookup"><span data-stu-id="89907-190">In general, automatic sizing will increase the size of a control in the direction opposite its <xref:System.Windows.Forms.Control.Anchor%2A> property setting.</span></span>  
  
## <a name="autosize-and-autosizemode-properties"></a><span data-ttu-id="89907-191">AutoSize 和 AutoSizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="89907-191">AutoSize and AutoSizeMode Properties</span></span>  
 <span data-ttu-id="89907-192">有些控制項支援`AutoSizeMode`屬性，可讓您進一步控制控制項的自動調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="89907-192">Some controls support the `AutoSizeMode` property, which gives you more fine-grained control over the automatic sizing behavior of a control.</span></span>  
  
#### <a name="to-use-the-autosizemode-property"></a><span data-ttu-id="89907-193">若要使用的 AutoSizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="89907-193">To use the AutoSizeMode property</span></span>  
  
1.  <span data-ttu-id="89907-194">拖曳<xref:System.Windows.Forms.Panel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="89907-194">Drag a <xref:System.Windows.Forms.Panel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="89907-195">值設定<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="89907-195">Set the value of the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="89907-196">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**到<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-196">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
4.  <span data-ttu-id="89907-197">位置<xref:System.Windows.Forms.Button>控制項的右下角附近<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-197">Place the <xref:System.Windows.Forms.Button> control near the lower-right corner of the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
5.  <span data-ttu-id="89907-198">選取<xref:System.Windows.Forms.Panel>控制和抓取右下方的調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="89907-198">Select the <xref:System.Windows.Forms.Panel> control and grab the lower-right sizing handle.</span></span> <span data-ttu-id="89907-199">調整大小<xref:System.Windows.Forms.Panel>放大及縮小控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-199">Resize the <xref:System.Windows.Forms.Panel> control to be larger and smaller.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="89907-200">您也可以自由調整<xref:System.Windows.Forms.Panel>控制項，但是您無法將其大小小於位置<xref:System.Windows.Forms.Button>控制項的右下角。</span><span class="sxs-lookup"><span data-stu-id="89907-200">You can freely resize the <xref:System.Windows.Forms.Panel> control, but you cannot size it smaller than the position of the <xref:System.Windows.Forms.Button> control's lower-right corner.</span></span> <span data-ttu-id="89907-201">此行為的預設值所指定`AutoSizeMode`屬性，這是<xref:System.Windows.Forms.AutoSizeMode.GrowOnly>。</span><span class="sxs-lookup"><span data-stu-id="89907-201">This behavior is specified by the default value of the `AutoSizeMode` property, which is <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.</span></span>  
  
6.  <span data-ttu-id="89907-202">值設定<xref:System.Windows.Forms.Panel>控制項的`AutoSizeMode`屬性<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>。</span><span class="sxs-lookup"><span data-stu-id="89907-202">Set the value of the <xref:System.Windows.Forms.Panel> control's `AutoSizeMode` property to <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.</span></span>  
  
     <span data-ttu-id="89907-203"><xref:System.Windows.Forms.Panel>括住調整控制項大小<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-203">The <xref:System.Windows.Forms.Panel> control sizes itself to surround the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="89907-204">您無法調整大小<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-204">You cannot resize the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
7.  <span data-ttu-id="89907-205">拖曳<xref:System.Windows.Forms.Button>控制項左上角<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-205">Drag the <xref:System.Windows.Forms.Button> control toward the upper-left corner of the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
     <span data-ttu-id="89907-206"><xref:System.Windows.Forms.Panel>控制項會調整大小以<xref:System.Windows.Forms.Button>控制項的新位置。</span><span class="sxs-lookup"><span data-stu-id="89907-206">The <xref:System.Windows.Forms.Panel> control resizes to the <xref:System.Windows.Forms.Button> control's new position.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="89907-207">後續步驟</span><span class="sxs-lookup"><span data-stu-id="89907-207">Next Steps</span></span>  
 <span data-ttu-id="89907-208">還有許多其他版面配置功能，用來排列 Windows Form 應用程式中的控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-208">There are many other layout features for arranging controls in your Windows Forms applications.</span></span> <span data-ttu-id="89907-209">以下是一些您可能會嘗試的組合：</span><span class="sxs-lookup"><span data-stu-id="89907-209">Here are some combinations you might try:</span></span>  
  
-   <span data-ttu-id="89907-210">建立表單使用<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-210">Build a form using a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="89907-211">如需詳細資訊，請參閱[逐步解說： 在 Windows Form 使用 TableLayoutPanel 排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="89907-211">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span> <span data-ttu-id="89907-212">變更的值再試一次<xref:System.Windows.Forms.TableLayoutPanel>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性，並將<xref:System.Windows.Forms.Control.Margin%2A>屬性在其子控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-212">Try changing the values of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.Control.Padding%2A> property, as well as the <xref:System.Windows.Forms.Control.Margin%2A> property on its child controls.</span></span>  
  
-   <span data-ttu-id="89907-213">請嘗試在相同的實驗使用<xref:System.Windows.Forms.FlowLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-213">Try the same experiment using a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="89907-214">如需詳細資訊，請參閱[逐步解說： 在 Windows Form 使用 FlowLayoutPanel 排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="89907-214">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).</span></span>  
  
-   <span data-ttu-id="89907-215">實驗中的子控制項的停駐<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="89907-215">Experiment with docking child controls in a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="89907-216"><xref:System.Windows.Forms.Control.Padding%2A>屬性是的較通用實現<xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>屬性，而且可以滿足您自己，這種方法是將子控制項放置<xref:System.Windows.Forms.Panel>控制項並設定子控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="89907-216">The <xref:System.Windows.Forms.Control.Padding%2A> property is a more general realization of the <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> property, and you can satisfy yourself that this is the case by putting a child control in a <xref:System.Windows.Forms.Panel> control and setting the child control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="89907-217">設定<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Control.Padding%2A>各種值，注意效果的屬性。</span><span class="sxs-lookup"><span data-stu-id="89907-217">Set the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.Padding%2A> property to various values and note the effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89907-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89907-218">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [<span data-ttu-id="89907-219">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="89907-219">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="89907-220">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="89907-220">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="89907-221">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="89907-221">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="89907-222">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="89907-222">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
