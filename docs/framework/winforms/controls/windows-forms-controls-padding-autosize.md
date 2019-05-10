---
title: 逐步解說：使用邊框間距、邊界和自動調整屬性配置 Windows Forms 控制項
ms.date: 03/30/2017
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
ms.openlocfilehash: 997db37369e52a024b53254117291a1e31555487
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211340"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a><span data-ttu-id="59010-102">逐步解說：使用邊框間距、邊界和自動調整屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="59010-102">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>

<span data-ttu-id="59010-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="59010-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="59010-104">**Windows Form 設計工具**Visual Studio 中提供您許多版面配置工具，來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="59010-104">The **Windows Forms Designer** in Visual Studio gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="59010-105">三個最重要的是<xref:System.Windows.Forms.Control.Margin%2A>， <xref:System.Windows.Forms.Control.Padding%2A>，和<xref:System.Windows.Forms.Control.AutoSize%2A>都存在於所有 Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-105">Three of the most important are the <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, and <xref:System.Windows.Forms.Control.AutoSize%2A> properties, which are present on all Windows Forms controls.</span></span>

 <span data-ttu-id="59010-106"><xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="59010-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>

 <span data-ttu-id="59010-107"><xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="59010-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>

 <span data-ttu-id="59010-108">下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>

 <span data-ttu-id="59010-109">![邊框距離及邊界 Windows Forms 控制項](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="59010-109">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>

 <span data-ttu-id="59010-110"><xref:System.Windows.Forms.Control.AutoSize%2A>屬性會告知自動本身自行調整大小，其內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-110">The <xref:System.Windows.Forms.Control.AutoSize%2A> property tells a control to automatically size itself to its contents.</span></span> <span data-ttu-id="59010-111">它不會調整大小必須小於其原始值本身<xref:System.Windows.Forms.Control.Size%2A>屬性，然後它會負責處理的值及其<xref:System.Windows.Forms.Control.Padding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-111">It will not resize itself to be smaller than the value of its original <xref:System.Windows.Forms.Control.Size%2A> property, and it will account for the value of its <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>

 <span data-ttu-id="59010-112">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="59010-112">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="59010-113">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="59010-113">Creating a Windows Forms project</span></span>

- <span data-ttu-id="59010-114">設定您的控制項的邊界</span><span class="sxs-lookup"><span data-stu-id="59010-114">Setting Margins for Your Controls</span></span>

- <span data-ttu-id="59010-115">設定您的控制項的邊框距離</span><span class="sxs-lookup"><span data-stu-id="59010-115">Setting Padding for Your Controls</span></span>

- <span data-ttu-id="59010-116">自動調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="59010-116">Automatically Sizing Your Controls</span></span>

 <span data-ttu-id="59010-117">完成後，您就會了解這些重要配置功能所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="59010-117">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59010-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="59010-118">Prerequisites</span></span>

<span data-ttu-id="59010-119">您將需要 Visual Studio 來完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="59010-119">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="59010-120">建立專案</span><span class="sxs-lookup"><span data-stu-id="59010-120">Create the project</span></span>

1. <span data-ttu-id="59010-121">在 Visual Studio 中建立**Windows 應用程式**專案，稱為`LayoutExample`。</span><span class="sxs-lookup"><span data-stu-id="59010-121">In Visual Studio, create a **Windows Application** project called `LayoutExample`.</span></span> <span data-ttu-id="59010-122">如需詳細資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)。</span><span class="sxs-lookup"><span data-stu-id="59010-122">For more information, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .</span></span>

2. <span data-ttu-id="59010-123">選取中的表單**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="59010-123">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="setting-margins-for-your-controls"></a><span data-ttu-id="59010-124">設定您的控制項的邊界</span><span class="sxs-lookup"><span data-stu-id="59010-124">Setting Margins for Your Controls</span></span>

<span data-ttu-id="59010-125">您可以將預設的距離設定為您使用的控制項<xref:System.Windows.Forms.Control.Margin%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-125">You can set the default distance between your controls using the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="59010-126">當您移動控制項時接近另一個控制項，您會看到顯示兩個控制項的邊界的對齊線。</span><span class="sxs-lookup"><span data-stu-id="59010-126">When you move a control close enough to another control, you will see a snapline that shows the margins for the two controls.</span></span> <span data-ttu-id="59010-127">您要移動的控制項也會貼齊邊界所定義的距離。</span><span class="sxs-lookup"><span data-stu-id="59010-127">The control you are moving will also snap to the distance defined by the margins.</span></span>

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a><span data-ttu-id="59010-128">您使用 Margin 屬性的表單上的控制項排列</span><span class="sxs-lookup"><span data-stu-id="59010-128">Arrange controls on your form using the Margin property</span></span>

1. <span data-ttu-id="59010-129">將兩個<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-129">Drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="59010-130">選取其中一個<xref:System.Windows.Forms.Button>控制，並移動接近另一個，直到幾乎碰觸。</span><span class="sxs-lookup"><span data-stu-id="59010-130">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span>

     <span data-ttu-id="59010-131">觀察出現在它們之間的對齊線。</span><span class="sxs-lookup"><span data-stu-id="59010-131">Observe the snapline that appears between them.</span></span> <span data-ttu-id="59010-132">這個距離很的兩個控制項的總和<xref:System.Windows.Forms.Control.Margin%2A>值。</span><span class="sxs-lookup"><span data-stu-id="59010-132">This distance is the sum of the two controls' <xref:System.Windows.Forms.Control.Margin%2A> values.</span></span> <span data-ttu-id="59010-133">您要移動的控制項會貼齊至這個距離。</span><span class="sxs-lookup"><span data-stu-id="59010-133">The control you are moving snaps to this distance.</span></span> <span data-ttu-id="59010-134">如需詳細資訊，請參閱[逐步解說：排列控制項，在 Windows Form 使用對齊線](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="59010-134">For details, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

3. <span data-ttu-id="59010-135">變更<xref:System.Windows.Forms.Control.Margin%2A>屬性的其中一個方法是展開的控制項<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性** 視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性為 20。</span><span class="sxs-lookup"><span data-stu-id="59010-135">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of one of the controls by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 20.</span></span>

4. <span data-ttu-id="59010-136">選取其中一個<xref:System.Windows.Forms.Button>控制，並將它移到靠近其他。</span><span class="sxs-lookup"><span data-stu-id="59010-136">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other.</span></span>

     <span data-ttu-id="59010-137">對齊線定義邊界值的總和較長，而且從另一個控制項的控制項會貼齊至較大的距離。</span><span class="sxs-lookup"><span data-stu-id="59010-137">The snapline defining the sum of the margin values is longer and that the control snaps to a greater distance from the other control.</span></span>

5. <span data-ttu-id="59010-138">變更<xref:System.Windows.Forms.Control.Margin%2A>藉由展開選取之控制項的屬性<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性** 視窗和設定<xref:System.Windows.Forms.Padding.Top%2A>為 5 的屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-138">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of the selected control by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.Top%2A> property to 5.</span></span>

6. <span data-ttu-id="59010-139">將其他控制項下方選取的控制項，並觀察對齊線是較短。</span><span class="sxs-lookup"><span data-stu-id="59010-139">Move the selected control below the other control and observe that the snapline is shorter.</span></span> <span data-ttu-id="59010-140">將選取的控制項移至其他控制項的左邊，並觀察對齊線會保留在步驟 4 中觀察到的值。</span><span class="sxs-lookup"><span data-stu-id="59010-140">Move the selected control to the left of the other control and observe that the snapline retains the value observed in step 4.</span></span>

7. <span data-ttu-id="59010-141">您可以設定每個層面<xref:System.Windows.Forms.Control.Margin%2A>屬性， <xref:System.Windows.Forms.Padding.Left%2A>， <xref:System.Windows.Forms.Padding.Top%2A>， <xref:System.Windows.Forms.Padding.Right%2A>， <xref:System.Windows.Forms.Padding.Bottom%2A>，以不同的值，或者您可以將它們設定為相同的值與所有<xref:System.Windows.Forms.Padding.All%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-141">You can set each of the aspects of the <xref:System.Windows.Forms.Control.Margin%2A> property, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, to different values, or you can set them all to the same value with the <xref:System.Windows.Forms.Padding.All%2A> property.</span></span>

## <a name="setting-padding-for-your-controls"></a><span data-ttu-id="59010-142">設定您的控制項的邊框距離</span><span class="sxs-lookup"><span data-stu-id="59010-142">Setting Padding for Your Controls</span></span>

<span data-ttu-id="59010-143">若要達成精確應用程式所需的版面配置，您的控制項通常會包含子控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-143">To achieve the precise layout required for your application, your controls will often contain child controls.</span></span> <span data-ttu-id="59010-144">當您想要指定子控制項的框線的單字，至父控制項的框線時，使用父控制項的<xref:System.Windows.Forms.Control.Padding%2A>搭配子控制項的屬性<xref:System.Windows.Forms.Control.Margin%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-144">When you want to specify the proximity of the child control's border to the parent control's border, use the parent control's <xref:System.Windows.Forms.Control.Padding%2A> property in conjunction with the child control's <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="59010-145"><xref:System.Windows.Forms.Control.Padding%2A>屬性也用來控制控制項內容的鄰近性 (例如<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性) 到其框線。</span><span class="sxs-lookup"><span data-stu-id="59010-145">The <xref:System.Windows.Forms.Control.Padding%2A> property is also used to control the proximity of a control's content (for example, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property) to its borders.</span></span>

### <a name="arrange-controls-on-your-form-using-padding"></a><span data-ttu-id="59010-146">您使用的填補的表單上的控制項排列</span><span class="sxs-lookup"><span data-stu-id="59010-146">Arrange controls on your form using padding</span></span>

1. <span data-ttu-id="59010-147">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-147">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="59010-148">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="59010-148">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>

3. <span data-ttu-id="59010-149">變更<xref:System.Windows.Forms.Control.Padding%2A>藉由展開的屬性<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性** 視窗和設定<xref:System.Windows.Forms.Padding.All%2A>為 5 的屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-149">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 5.</span></span>

     <span data-ttu-id="59010-150">控制項展開以提供新的邊框距離的空間。</span><span class="sxs-lookup"><span data-stu-id="59010-150">The control expands to provide room for the new padding.</span></span>

4. <span data-ttu-id="59010-151">從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-151">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="59010-152">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-152">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="59010-153">位置<xref:System.Windows.Forms.Button>控制項讓它與右下角齊<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-153">Position the <xref:System.Windows.Forms.Button> control so it is flush with the lower-right corner of the <xref:System.Windows.Forms.GroupBox> control.</span></span>

     <span data-ttu-id="59010-154">觀察如下所示的對齊線<xref:System.Windows.Forms.Button>控制方法的下框線和右框線的<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-154">Observe the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="59010-155">這些對齊線會對應至<xref:System.Windows.Forms.Control.Margin%2A>屬性<xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="59010-155">These snaplines correspond to the <xref:System.Windows.Forms.Control.Margin%2A> property of the <xref:System.Windows.Forms.Button>.</span></span>

5. <span data-ttu-id="59010-156">變更<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性來擴充<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性為 20。</span><span class="sxs-lookup"><span data-stu-id="59010-156">Change the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 20.</span></span>

6. <span data-ttu-id="59010-157">選取 <xref:System.Windows.Forms.Button>控制項中<xref:System.Windows.Forms.GroupBox>控制項並將它移向的中央<xref:System.Windows.Forms.GroupBox>。</span><span class="sxs-lookup"><span data-stu-id="59010-157">Select the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and move it toward the center of the <xref:System.Windows.Forms.GroupBox>.</span></span>

     <span data-ttu-id="59010-158">從的框線對齊線會出現在較大的距離<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-158">The snaplines appear at a greater distance from the borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="59010-159">這個距離很總和<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性並<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-159">This distance is the sum of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property and the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>

## <a name="automatically-sizing-your-controls"></a><span data-ttu-id="59010-160">自動調整控制項大小</span><span class="sxs-lookup"><span data-stu-id="59010-160">Automatically Sizing Your Controls</span></span>

<span data-ttu-id="59010-161">在某些應用程式，控制項的大小將不會相同執行階段是在設計階段。</span><span class="sxs-lookup"><span data-stu-id="59010-161">In some applications, the size of a control will not be the same at run time as it was at design time.</span></span> <span data-ttu-id="59010-162">文字<xref:System.Windows.Forms.Button>控制項，例如，可能會從資料庫中，並會事先知道它的長度。</span><span class="sxs-lookup"><span data-stu-id="59010-162">The text of a <xref:System.Windows.Forms.Button> control, for example, may be taken from a database, and its length will not be known in advance.</span></span>

<span data-ttu-id="59010-163">當<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設定為`true`，控制項將其內容調整本身。</span><span class="sxs-lookup"><span data-stu-id="59010-163">When the <xref:System.Windows.Forms.Control.AutoSize%2A> property is set to `true`, the control will size itself to its content.</span></span> <span data-ttu-id="59010-164">如需詳細資訊，請參閱 < [AutoSize 屬性概觀](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="59010-164">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a><span data-ttu-id="59010-165">使用 AutoSize 屬性在表單上的控制項排列</span><span class="sxs-lookup"><span data-stu-id="59010-165">Arrange controls on your form using the AutoSize property</span></span>

1. <span data-ttu-id="59010-166">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-166">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="59010-167">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="59010-167">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>

3. <span data-ttu-id="59010-168">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性為"**此按鈕有其 Text 屬性一長串**。 」</span><span class="sxs-lookup"><span data-stu-id="59010-168">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property**."</span></span>

     <span data-ttu-id="59010-169">當您認可變更，<xref:System.Windows.Forms.Button>控制項自動調整大小以容納新的文字。</span><span class="sxs-lookup"><span data-stu-id="59010-169">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself to fit the new text.</span></span>

4. <span data-ttu-id="59010-170">將另一個<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-170">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="59010-171">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性為"**此按鈕會有一長串其 Text 屬性。**"</span><span class="sxs-lookup"><span data-stu-id="59010-171">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>

     <span data-ttu-id="59010-172">當您認可變更，<xref:System.Windows.Forms.Button>控制項調整本身，都不大小和文字由控制項的右邊緣裁剪。</span><span class="sxs-lookup"><span data-stu-id="59010-172">When you commit the change, the <xref:System.Windows.Forms.Button> control does not resize itself, and the text is clipped by the right edge of the control.</span></span>

6. <span data-ttu-id="59010-173">變更<xref:System.Windows.Forms.Control.Padding%2A>藉由展開的屬性<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性** 視窗和設定<xref:System.Windows.Forms.Padding.All%2A>為 5 的屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-173">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 5.</span></span>

     <span data-ttu-id="59010-174">在控制項的內部文字會裁剪四個邊。</span><span class="sxs-lookup"><span data-stu-id="59010-174">The text in the control's interior is clipped on all four sides.</span></span>

7. <span data-ttu-id="59010-175">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="59010-175">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>

     <span data-ttu-id="59010-176"><xref:System.Windows.Forms.Button>控制項調整大小，以包含整個字串。</span><span class="sxs-lookup"><span data-stu-id="59010-176">The <xref:System.Windows.Forms.Button> control resizes itself to encompass the entire string.</span></span> <span data-ttu-id="59010-177">填補此外，新增該文字周圍，造成<xref:System.Windows.Forms.Button>展開所有 4 個方向的控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-177">Also, padding has been added around the text, causing the <xref:System.Windows.Forms.Button> control to expand in all four directions.</span></span>

8. <span data-ttu-id="59010-178">從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-178">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="59010-179">請將它放置在表單的右下角附近。</span><span class="sxs-lookup"><span data-stu-id="59010-179">Position it near the lower-right corner of the form.</span></span>

9. <span data-ttu-id="59010-180">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="59010-180">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>

10. <span data-ttu-id="59010-181">設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設<xref:System.Windows.Forms.AnchorStyles.Right>， <xref:System.Windows.Forms.AnchorStyles.Bottom>。</span><span class="sxs-lookup"><span data-stu-id="59010-181">Set the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.</span></span>

11. <span data-ttu-id="59010-182">變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性為"**此按鈕會有一長串其 Text 屬性。**"</span><span class="sxs-lookup"><span data-stu-id="59010-182">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>

     <span data-ttu-id="59010-183">當您認可變更，<xref:System.Windows.Forms.Button>控制項調整其大小往左邊。</span><span class="sxs-lookup"><span data-stu-id="59010-183">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself toward the left.</span></span> <span data-ttu-id="59010-184">一般情況下，自動調整大小會增加在相反方向中控制項的大小及其<xref:System.Windows.Forms.Control.Anchor%2A>屬性設定。</span><span class="sxs-lookup"><span data-stu-id="59010-184">In general, automatic sizing will increase the size of a control in the direction opposite its <xref:System.Windows.Forms.Control.Anchor%2A> property setting.</span></span>

## <a name="autosize-and-autosizemode-properties"></a><span data-ttu-id="59010-185">AutoSize 和 AutoSizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="59010-185">AutoSize and AutoSizeMode Properties</span></span>

 <span data-ttu-id="59010-186">有些控制項支援`AutoSizeMode`屬性，可讓您進一步控制控制項的自動調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="59010-186">Some controls support the `AutoSizeMode` property, which gives you more fine-grained control over the automatic sizing behavior of a control.</span></span>

### <a name="use-the-autosizemode-property"></a><span data-ttu-id="59010-187">使用 AutoSizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="59010-187">Use the AutoSizeMode property</span></span>

1. <span data-ttu-id="59010-188">從 [工具箱] <xref:System.Windows.Forms.Panel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="59010-188">Drag a <xref:System.Windows.Forms.Panel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="59010-189">設定的值<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="59010-189">Set the value of the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>

3. <span data-ttu-id="59010-190">拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-190">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.Panel> control.</span></span>

4. <span data-ttu-id="59010-191">地方<xref:System.Windows.Forms.Button>右下角附近的控制項<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-191">Place the <xref:System.Windows.Forms.Button> control near the lower-right corner of the <xref:System.Windows.Forms.Panel> control.</span></span>

5. <span data-ttu-id="59010-192">選取<xref:System.Windows.Forms.Panel>控制項，並抓取的右下角調整大小控點。</span><span class="sxs-lookup"><span data-stu-id="59010-192">Select the <xref:System.Windows.Forms.Panel> control and grab the lower-right sizing handle.</span></span> <span data-ttu-id="59010-193">調整大小<xref:System.Windows.Forms.Panel>為較大且較小的控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-193">Resize the <xref:System.Windows.Forms.Panel> control to be larger and smaller.</span></span>

    > [!NOTE]
    > <span data-ttu-id="59010-194">您可以自由地調整大小<xref:System.Windows.Forms.Panel>控制項，但是您無法將其大小小於位置<xref:System.Windows.Forms.Button>控制項的右下角。</span><span class="sxs-lookup"><span data-stu-id="59010-194">You can freely resize the <xref:System.Windows.Forms.Panel> control, but you cannot size it smaller than the position of the <xref:System.Windows.Forms.Button> control's lower-right corner.</span></span> <span data-ttu-id="59010-195">此行為是預設值所指定的`AutoSizeMode`屬性，這是<xref:System.Windows.Forms.AutoSizeMode.GrowOnly>。</span><span class="sxs-lookup"><span data-stu-id="59010-195">This behavior is specified by the default value of the `AutoSizeMode` property, which is <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.</span></span>

6. <span data-ttu-id="59010-196">設定的值<xref:System.Windows.Forms.Panel>控制項的`AutoSizeMode`屬性設<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>。</span><span class="sxs-lookup"><span data-stu-id="59010-196">Set the value of the <xref:System.Windows.Forms.Panel> control's `AutoSizeMode` property to <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.</span></span>

     <span data-ttu-id="59010-197"><xref:System.Windows.Forms.Panel>控制大小本身來括住<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-197">The <xref:System.Windows.Forms.Panel> control sizes itself to surround the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="59010-198">您無法調整大小<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-198">You cannot resize the <xref:System.Windows.Forms.Panel> control.</span></span>

7. <span data-ttu-id="59010-199">拖曳<xref:System.Windows.Forms.Button>控制項左上角<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-199">Drag the <xref:System.Windows.Forms.Button> control toward the upper-left corner of the <xref:System.Windows.Forms.Panel> control.</span></span>

     <span data-ttu-id="59010-200"><xref:System.Windows.Forms.Panel>控制項會調整大小以<xref:System.Windows.Forms.Button>控制項的新位置。</span><span class="sxs-lookup"><span data-stu-id="59010-200">The <xref:System.Windows.Forms.Panel> control resizes to the <xref:System.Windows.Forms.Button> control's new position.</span></span>

## <a name="next-steps"></a><span data-ttu-id="59010-201">後續步驟</span><span class="sxs-lookup"><span data-stu-id="59010-201">Next steps</span></span>

<span data-ttu-id="59010-202">有許多其他版面配置功能，用來排列 Windows Forms 應用程式中的控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-202">There are many other layout features for arranging controls in your Windows Forms applications.</span></span> <span data-ttu-id="59010-203">以下是一些您可以嘗試的組合：</span><span class="sxs-lookup"><span data-stu-id="59010-203">Here are some combinations you might try:</span></span>

- <span data-ttu-id="59010-204">建置表單，使用<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-204">Build a form using a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="59010-205">如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="59010-205">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span> <span data-ttu-id="59010-206">請嘗試變更的值<xref:System.Windows.Forms.TableLayoutPanel>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性，以及<xref:System.Windows.Forms.Control.Margin%2A>上它的子控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="59010-206">Try changing the values of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.Control.Padding%2A> property, as well as the <xref:System.Windows.Forms.Control.Margin%2A> property on its child controls.</span></span>

- <span data-ttu-id="59010-207">請嘗試相同的實驗使用<xref:System.Windows.Forms.FlowLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-207">Try the same experiment using a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="59010-208">如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="59010-208">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).</span></span>

- <span data-ttu-id="59010-209">實驗中的子控制項的停駐<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="59010-209">Experiment with docking child controls in a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="59010-210"><xref:System.Windows.Forms.Control.Padding%2A>值的較通用實現<xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>屬性，而且可以滿足您自己，是藉由將子控制項置於<xref:System.Windows.Forms.Panel>控制項，並設定子控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="59010-210">The <xref:System.Windows.Forms.Control.Padding%2A> property is a more general realization of the <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> property, and you can satisfy yourself that this is the case by putting a child control in a <xref:System.Windows.Forms.Panel> control and setting the child control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="59010-211">設定<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性，以不同的值和附註的效果。</span><span class="sxs-lookup"><span data-stu-id="59010-211">Set the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.Padding%2A> property to various values and note the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="59010-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59010-212">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [<span data-ttu-id="59010-213">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="59010-213">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="59010-214">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="59010-214">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="59010-215">逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="59010-215">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="59010-216">逐步解說：使用對齊線的 Windows Form 上排列控制項</span><span class="sxs-lookup"><span data-stu-id="59010-216">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
