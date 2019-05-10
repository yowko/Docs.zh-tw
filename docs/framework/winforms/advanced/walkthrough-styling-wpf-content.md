---
title: 逐步解說：設定 WPF 內容的樣式
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: d815311a89ba09ade7e3092ca4eeab67cbe20bd0
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211246"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="aab21-102">逐步解說：樣式的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="aab21-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="aab21-103">本逐步解說示範如何將樣式套用至 Windows Form 上裝載的 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="aab21-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="aab21-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="aab21-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="aab21-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="aab21-105">Create the project.</span></span>

- <span data-ttu-id="aab21-106">建立 WPF 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="aab21-106">Create the WPF control type.</span></span>

- <span data-ttu-id="aab21-107">將樣式套用至 WPF control.a</span><span class="sxs-lookup"><span data-stu-id="aab21-107">Apply a style to the WPF control.a</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aab21-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="aab21-108">Prerequisites</span></span>

<span data-ttu-id="aab21-109">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="aab21-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="aab21-110">建立專案</span><span class="sxs-lookup"><span data-stu-id="aab21-110">Create the project</span></span>

<span data-ttu-id="aab21-111">開啟 Visual Studio 並建立新的 Windows Forms 應用程式專案在 Visual Basic 或 VisualC#名為`StylingWpfContent`。</span><span class="sxs-lookup"><span data-stu-id="aab21-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="aab21-112">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="aab21-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="aab21-113">建立 WPF 控制項類型</span><span class="sxs-lookup"><span data-stu-id="aab21-113">Create the WPF control types</span></span>

<span data-ttu-id="aab21-114">在將 WPF 控制項加入專案後，即可將它裝載至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。</span><span class="sxs-lookup"><span data-stu-id="aab21-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="aab21-115">將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="aab21-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="aab21-116">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="aab21-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="aab21-117">如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="aab21-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="aab21-118">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="aab21-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="aab21-119">如需詳細資訊，請參閱[如何：選取並移動設計介面上的項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="aab21-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="aab21-120">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="aab21-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="aab21-121">新增<xref:System.Windows.Controls.Button?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.ContentControl.Content%2A>屬性設**取消**。</span><span class="sxs-lookup"><span data-stu-id="aab21-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="aab21-122">新增第二<xref:System.Windows.Controls.Button?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.ContentControl.Content%2A>屬性設 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aab21-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="aab21-123">建置專案。</span><span class="sxs-lookup"><span data-stu-id="aab21-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="aab21-124">套用樣式至 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="aab21-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="aab21-125">您可以套用不同的樣式至 WPF 控制項，以變更其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="aab21-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="aab21-126">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="aab21-126">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="aab21-127">在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`表單上。</span><span class="sxs-lookup"><span data-stu-id="aab21-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="aab21-128">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="aab21-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="aab21-129">中的智慧標籤面板`elementHost1`，按一下**編輯裝載內容**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="aab21-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="aab21-130">`UserControl1` 會在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="aab21-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

4. <span data-ttu-id="aab21-131">在 [XAML] 檢閱中，插入下列 XAML 到 `<UserControl>` 開頭標記後面。</span><span class="sxs-lookup"><span data-stu-id="aab21-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="aab21-132">此 XAML 會建立具有對比漸層框線的漸層。</span><span class="sxs-lookup"><span data-stu-id="aab21-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="aab21-133">按一下控制項時，漸層會變更，產生已按下的按鈕外觀。</span><span class="sxs-lookup"><span data-stu-id="aab21-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="aab21-134">如需詳細資訊，請參閱 [設定樣式和範本](../../wpf/controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="aab21-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

4. <span data-ttu-id="aab21-135">藉由插入 [取消] 按鈕`<Button>` 標籤中的下列 XAML，套用前一個步驟中定義的 `SimpleButton` 樣式到 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab21-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="aab21-136">按鈕宣告將會類似下列的 XAML:</span><span class="sxs-lookup"><span data-stu-id="aab21-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

5. <span data-ttu-id="aab21-137">建置專案。</span><span class="sxs-lookup"><span data-stu-id="aab21-137">Build the project.</span></span>

6. <span data-ttu-id="aab21-138">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="aab21-138">Open `Form1` in the Windows Forms Designer.</span></span>

7. <span data-ttu-id="aab21-139">新的樣式會套用至按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="aab21-139">The new style is applied to the button control.</span></span>

8. <span data-ttu-id="aab21-140">從**偵錯**功能表上，選取**開始偵錯**執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="aab21-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

9. <span data-ttu-id="aab21-141">按一下 [確定] 和 [取消] 按鈕，然後檢視其差異。</span><span class="sxs-lookup"><span data-stu-id="aab21-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="aab21-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aab21-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="aab21-143">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="aab21-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="aab21-144">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="aab21-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="aab21-145">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="aab21-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="aab21-146">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="aab21-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="aab21-147">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="aab21-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
