---
title: 逐步解說：使用 XAML 建立按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 3d8fb3fbbf31b547644ae171aaf81654812d8a20
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971905"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="55fae-102">逐步解說：使用 XAML 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="55fae-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="55fae-103">本逐步解說的目的是要瞭解如何建立動畫按鈕, 以便在 Windows Presentation Foundation (WPF) 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="55fae-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="55fae-104">本逐步解說會使用樣式和範本來建立自訂的按鈕資源, 以允許重複使用程式碼, 並從按鈕宣告中分隔按鈕邏輯。</span><span class="sxs-lookup"><span data-stu-id="55fae-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="55fae-105">這個逐步解說完全寫在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="55fae-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55fae-106">本逐步解說會引導您完成建立應用程式的步驟, 方法是輸入或[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]複製並貼入 Microsoft Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="55fae-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft Visual Studio.</span></span> <span data-ttu-id="55fae-107">如果您想要瞭解如何使用設計工具 (Microsoft Expression Blend) 來建立相同的應用程式, 請參閱[使用 Microsoft Expression Blend 建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。</span><span class="sxs-lookup"><span data-stu-id="55fae-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="55fae-108">下圖顯示 [已完成] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="55fae-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="55fae-109">![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="55fae-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="55fae-110">建立基本按鈕</span><span class="sxs-lookup"><span data-stu-id="55fae-110">Create Basic Buttons</span></span>

<span data-ttu-id="55fae-111">讓我們先建立新的專案, 然後在視窗中加入幾個按鈕。</span><span class="sxs-lookup"><span data-stu-id="55fae-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="55fae-112">若要建立新的 WPF 專案並將按鈕加入至視窗</span><span class="sxs-lookup"><span data-stu-id="55fae-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="55fae-113">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="55fae-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="55fae-114">**建立新的 WPF 專案:** 在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="55fae-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="55fae-115">尋找**Windows 應用程式 (WPF)** 範本, 並將專案命名為 "AnimatedButton"。</span><span class="sxs-lookup"><span data-stu-id="55fae-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="55fae-116">這會建立應用程式的基本架構。</span><span class="sxs-lookup"><span data-stu-id="55fae-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="55fae-117">**新增基本的預設按鈕:** 此逐步解說所需的所有檔案都是由範本提供。</span><span class="sxs-lookup"><span data-stu-id="55fae-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="55fae-118">在方案總管中按兩下 Window1.xaml, 以開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="55fae-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="55fae-119">根據預設, window1.xaml 中有<xref:System.Windows.Controls.Grid>一個元素。</span><span class="sxs-lookup"><span data-stu-id="55fae-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="55fae-120">藉由輸入或複製下列反白顯示的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼並貼到 window1.xaml 中, 移除元素並將一些按鈕新增至頁面:<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="55fae-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="55fae-121">按 F5 執行應用程式;您應該會看到如下圖所示的一組按鈕。</span><span class="sxs-lookup"><span data-stu-id="55fae-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="55fae-122">![三個基本按鈕](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="55fae-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="55fae-123">現在您已建立基本按鈕, 您已完成使用 Window1.xaml。</span><span class="sxs-lookup"><span data-stu-id="55fae-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="55fae-124">本逐步解說的其餘部分著重于 app.xaml 檔案, 定義樣式和按鈕的範本。</span><span class="sxs-lookup"><span data-stu-id="55fae-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="55fae-125">設定基本屬性</span><span class="sxs-lookup"><span data-stu-id="55fae-125">Set Basic Properties</span></span>

<span data-ttu-id="55fae-126">接下來, 我們要在這些按鈕上設定一些屬性, 以控制按鈕的外觀和版面配置。</span><span class="sxs-lookup"><span data-stu-id="55fae-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="55fae-127">您不需要個別設定按鈕的屬性, 而是使用資源來定義整個應用程式的按鈕屬性。</span><span class="sxs-lookup"><span data-stu-id="55fae-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="55fae-128">應用程式資源在概念上類似于 Web 網頁的外部階層式樣式表 (CSS);不過, 資源比階層式樣式表 (CSS) 更強大, 因為您會在本逐步解說的結尾看到此內容。</span><span class="sxs-lookup"><span data-stu-id="55fae-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="55fae-129">若要深入瞭解資源, 請參閱[XAML 資源](../advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="55fae-129">To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="55fae-130">若要使用樣式來設定按鈕的基本屬性</span><span class="sxs-lookup"><span data-stu-id="55fae-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="55fae-131">**定義應用程式 .Resources 區塊:** 開啟 app.xaml, 並新增下列反白顯示的標記 (如果尚未存在):</span><span class="sxs-lookup"><span data-stu-id="55fae-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     <span data-ttu-id="55fae-132">資源範圍取決於您定義資源的位置。</span><span class="sxs-lookup"><span data-stu-id="55fae-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="55fae-133">在應用程式`Application.Resources`中定義中的資源。 xaml 檔案可讓您從應用程式中的任何位置使用資源。</span><span class="sxs-lookup"><span data-stu-id="55fae-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="55fae-134">若要深入瞭解如何定義資源的範圍, 請參閱[XAML 資源](../advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="55fae-134">To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>

2. <span data-ttu-id="55fae-135">**建立樣式, 並使用它定義基本的屬性值:** 將下列標記新增至`Application.Resources`區塊。</span><span class="sxs-lookup"><span data-stu-id="55fae-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="55fae-136">此標記會建立<xref:System.Windows.Style>一個, 其適用于應用程式中的所有按鈕<xref:System.Windows.FrameworkElement.Width%2A> , 並將<xref:System.Windows.FrameworkElement.Margin%2A>按鈕的設定為 90, 並將設為 10:</span><span class="sxs-lookup"><span data-stu-id="55fae-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="55fae-137">屬性會指定該樣式套用至類型<xref:System.Windows.Controls.Button>的所有物件。 <xref:System.Windows.Style.TargetType%2A></span><span class="sxs-lookup"><span data-stu-id="55fae-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="55fae-138">每<xref:System.Windows.Setter>個都會<xref:System.Windows.Style>為設定不同的屬性值。</span><span class="sxs-lookup"><span data-stu-id="55fae-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="55fae-139">因此, 在此時, 應用程式中的每個按鈕寬度為 90, 邊界為10。</span><span class="sxs-lookup"><span data-stu-id="55fae-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="55fae-140">如果您按 F5 執行應用程式, 您會看到下列視窗。</span><span class="sxs-lookup"><span data-stu-id="55fae-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="55fae-141">![寬度為90且邊界為10的按鈕](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="55fae-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="55fae-142">您可以使用樣式來執行更多動作, 包括微調目標物件的各種方式、指定複雜的屬性值, 甚至使用樣式做為其他樣式的輸入。</span><span class="sxs-lookup"><span data-stu-id="55fae-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="55fae-143">如需詳細資訊，請參閱 [設定樣式和範本](styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="55fae-143">For more information, see [Styling and Templating](styling-and-templating.md).</span></span>

3. <span data-ttu-id="55fae-144">**將樣式屬性值設定為資源:** 資源可讓您以簡單的方式重複使用常用定義的物件和值。</span><span class="sxs-lookup"><span data-stu-id="55fae-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="55fae-145">使用資源來定義複雜的值, 讓您的程式碼更模組化是特別有用。</span><span class="sxs-lookup"><span data-stu-id="55fae-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="55fae-146">將下列反白顯示的標記新增至 app.xaml。</span><span class="sxs-lookup"><span data-stu-id="55fae-146">Add the following highlighted markup to app.xaml.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="55fae-147">在區塊的`Application.Resources`正下方, 您已建立名為 "GrayBlueGradientBrush" 的資源。</span><span class="sxs-lookup"><span data-stu-id="55fae-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="55fae-148">此資源會定義水準漸層。</span><span class="sxs-lookup"><span data-stu-id="55fae-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="55fae-149">此資源可用來做為應用程式中任何位置的屬性值, 包括<xref:System.Windows.Controls.Control.Background%2A>屬性的按鈕樣式 setter 內部。</span><span class="sxs-lookup"><span data-stu-id="55fae-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="55fae-150">現在, 所有按鈕都具有<xref:System.Windows.Controls.Control.Background%2A>此漸層的屬性值。</span><span class="sxs-lookup"><span data-stu-id="55fae-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="55fae-151">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="55fae-151">Press F5 to run the application.</span></span> <span data-ttu-id="55fae-152">看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="55fae-152">It should look like the following.</span></span>

     <span data-ttu-id="55fae-153">![具有漸層背景的按鈕](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="55fae-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="55fae-154">建立定義按鈕外觀的範本</span><span class="sxs-lookup"><span data-stu-id="55fae-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="55fae-155">在本節中, 您會建立範本, 以自訂按鈕的外觀 (呈現)。</span><span class="sxs-lookup"><span data-stu-id="55fae-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="55fae-156">按鈕呈現是由數個物件所組成, 包括矩形和其他元件, 讓按鈕具有獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="55fae-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="55fae-157">到目前為止, 控制項按鈕在應用程式中的顯示方式, 已局限于變更按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="55fae-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="55fae-158">如果您想要對按鈕的外觀進行更多的變更, 該怎麼做？</span><span class="sxs-lookup"><span data-stu-id="55fae-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="55fae-159">範本可讓您強大控制物件的呈現。</span><span class="sxs-lookup"><span data-stu-id="55fae-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="55fae-160">因為範本可以在樣式內使用, 所以您可以將範本套用至樣式適用的所有物件 (在此逐步解說中為按鈕)。</span><span class="sxs-lookup"><span data-stu-id="55fae-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="55fae-161">若要使用範本來定義按鈕的外觀</span><span class="sxs-lookup"><span data-stu-id="55fae-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="55fae-162">**設定範本:** 因為的控制項<xref:System.Windows.Controls.Button> (如<xref:System.Windows.Controls.Control.Template%2A> ) 具有屬性, 所以您可以定義樣板屬性值, 就像<xref:System.Windows.Style>我們在中使用所<xref:System.Windows.Setter>設定的其他屬性值一樣。</span><span class="sxs-lookup"><span data-stu-id="55fae-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="55fae-163">將下列反白顯示的標記新增至您的按鈕樣式。</span><span class="sxs-lookup"><span data-stu-id="55fae-163">Add the following highlighted markup to your button style.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. <span data-ttu-id="55fae-164">**改變按鈕呈現方式:** 此時, 您必須定義範本。</span><span class="sxs-lookup"><span data-stu-id="55fae-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="55fae-165">新增下列反白顯示的標記。</span><span class="sxs-lookup"><span data-stu-id="55fae-165">Add the following highlighted markup.</span></span> <span data-ttu-id="55fae-166">此標記會指定<xref:System.Windows.Shapes.Rectangle>兩個具有圓角的元素, <xref:System.Windows.Controls.DockPanel>後面接著。</span><span class="sxs-lookup"><span data-stu-id="55fae-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="55fae-167">是用來<xref:System.Windows.Controls.ContentPresenter>裝載按鈕的。 <xref:System.Windows.Controls.DockPanel></span><span class="sxs-lookup"><span data-stu-id="55fae-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="55fae-168">會<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。</span><span class="sxs-lookup"><span data-stu-id="55fae-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="55fae-169">在本逐步解說中, 內容是文字 ("Button 1", "Button 2", "Button 3")。</span><span class="sxs-lookup"><span data-stu-id="55fae-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="55fae-170">所有範本元件 (矩形和<xref:System.Windows.Controls.DockPanel>) 都是在內<xref:System.Windows.Controls.Grid>配置。</span><span class="sxs-lookup"><span data-stu-id="55fae-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="55fae-171">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="55fae-171">Press F5 to run the application.</span></span> <span data-ttu-id="55fae-172">看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="55fae-172">It should look like the following.</span></span>

     <span data-ttu-id="55fae-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="55fae-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>

3. <span data-ttu-id="55fae-174">**將 glasseffect 新增至範本:** 接下來, 您會加入玻璃。</span><span class="sxs-lookup"><span data-stu-id="55fae-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="55fae-175">首先, 您要建立一些資源來建立半透明漸層效果。</span><span class="sxs-lookup"><span data-stu-id="55fae-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="55fae-176">將這些漸層資源新增至`Application.Resources`區塊內的任何位置:</span><span class="sxs-lookup"><span data-stu-id="55fae-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="55fae-177">這些資源會當做矩形的<xref:System.Windows.Shapes.Shape.Fill%2A>使用, 我們會將其插入<xref:System.Windows.Controls.Grid>按鈕範本的。</span><span class="sxs-lookup"><span data-stu-id="55fae-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="55fae-178">將下列反白顯示的標記新增至範本。</span><span class="sxs-lookup"><span data-stu-id="55fae-178">Add the following highlighted markup to the template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="55fae-179">請注意, `x:Name`屬性為 "glassCube" 的矩形的為 0, 因此當您執行範例時, 您看不到在上方重迭的玻璃矩形。 <xref:System.Windows.UIElement.Opacity%2A></span><span class="sxs-lookup"><span data-stu-id="55fae-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="55fae-180">這是因為我們稍後會將觸發程式新增至範本, 以供使用者與按鈕互動時使用。</span><span class="sxs-lookup"><span data-stu-id="55fae-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="55fae-181">不過, 您現在可以藉由將<xref:System.Windows.UIElement.Opacity%2A>值變更為1並執行應用程式, 來查看按鈕的外觀。</span><span class="sxs-lookup"><span data-stu-id="55fae-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="55fae-182">請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="55fae-182">See the following figure.</span></span> <span data-ttu-id="55fae-183">繼續進行下一個步驟之前, 請將<xref:System.Windows.UIElement.Opacity%2A>變更回0。</span><span class="sxs-lookup"><span data-stu-id="55fae-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="55fae-184">![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="55fae-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="55fae-185">建立按鈕互動性</span><span class="sxs-lookup"><span data-stu-id="55fae-185">Create Button Interactivity</span></span>

<span data-ttu-id="55fae-186">在本節中, 您將建立屬性觸發程式和事件觸發程式來變更屬性值和執行動畫, 以回應使用者動作, 例如將滑鼠指標移至按鈕上, 然後按一下。</span><span class="sxs-lookup"><span data-stu-id="55fae-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="55fae-187">新增互動性 (滑鼠停留、滑鼠離開、按一下等等) 的簡單方式, 是在您的範本或樣式內定義觸發程式。</span><span class="sxs-lookup"><span data-stu-id="55fae-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="55fae-188">若要建立<xref:System.Windows.Trigger>, 您可以定義屬性「條件」, 例如:按鈕<xref:System.Windows.UIElement.IsMouseOver%2A>屬性值`true`等於。</span><span class="sxs-lookup"><span data-stu-id="55fae-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="55fae-189">接著, 您可以定義在觸發條件為 true 時所發生的 setter (動作)。</span><span class="sxs-lookup"><span data-stu-id="55fae-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="55fae-190">建立按鈕互動性</span><span class="sxs-lookup"><span data-stu-id="55fae-190">To create button interactivity</span></span>

1. <span data-ttu-id="55fae-191">**新增範本觸發程式:** 將反白顯示的標記新增至您的範本。</span><span class="sxs-lookup"><span data-stu-id="55fae-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. <span data-ttu-id="55fae-192">**新增屬性觸發程式:** 將反白顯示的標記`ControlTemplate.Triggers`新增至區塊:</span><span class="sxs-lookup"><span data-stu-id="55fae-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="55fae-193">按 F5 鍵執行應用程式, 並在您執行滑鼠指標停留在按鈕上時查看效果。</span><span class="sxs-lookup"><span data-stu-id="55fae-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="55fae-194">**新增焦點觸發程式:** 接下來, 我們將新增一些類似的 setter, 以處理按鈕有焦點時的情況 (例如, 在使用者按一下之後)。</span><span class="sxs-lookup"><span data-stu-id="55fae-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     <span data-ttu-id="55fae-195">按 F5 執行應用程式, 然後按一下其中一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="55fae-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="55fae-196">請注意, 當您按一下按鈕時, 它仍會反白顯示, 因為它仍然具有焦點。</span><span class="sxs-lookup"><span data-stu-id="55fae-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="55fae-197">如果您按一下另一個按鈕, [新增] 按鈕會取得焦點, 而最後一項則會失去焦點。</span><span class="sxs-lookup"><span data-stu-id="55fae-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="55fae-198">**新增**<xref:System.Windows.UIElement.MouseEnter>和的<xref:System.Windows.UIElement.MouseLeave>動畫 **:**  接下來, 我們會將一些動畫新增至觸發程式。</span><span class="sxs-lookup"><span data-stu-id="55fae-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="55fae-199">在`ControlTemplate.Triggers`區塊內的任何位置新增下列標記。</span><span class="sxs-lookup"><span data-stu-id="55fae-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="55fae-200">當滑鼠指標移至按鈕上方時, 半透明矩形會縮小, 並在指標離開時返回正常大小。</span><span class="sxs-lookup"><span data-stu-id="55fae-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="55fae-201">當指標移至按鈕上方時, 會觸發兩個動畫 (<xref:System.Windows.UIElement.MouseEnter>引發事件)。</span><span class="sxs-lookup"><span data-stu-id="55fae-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="55fae-202">這些動畫會沿著 X 和 Y 軸縮小半透明矩形的範圍。</span><span class="sxs-lookup"><span data-stu-id="55fae-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="55fae-203">請注意<xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>元素上的屬性,以及。<xref:System.Windows.Media.Animation.Timeline.Duration%2A></span><span class="sxs-lookup"><span data-stu-id="55fae-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="55fae-204">會指定動畫出現在半秒的時間, 並<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>指定玻璃縮小 10%。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A></span><span class="sxs-lookup"><span data-stu-id="55fae-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="55fae-205">第二個事件觸發<xref:System.Windows.UIElement.MouseLeave>程式 () 只會停止第一個。</span><span class="sxs-lookup"><span data-stu-id="55fae-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="55fae-206">當您停止<xref:System.Windows.Media.Animation.Storyboard>時, 所有動畫屬性都會回到其預設值。</span><span class="sxs-lookup"><span data-stu-id="55fae-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="55fae-207">因此, 當使用者將指標移開按鈕時, 按鈕會回到滑鼠指標移至按鈕上方的方式。</span><span class="sxs-lookup"><span data-stu-id="55fae-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="55fae-208">如需動畫的詳細資訊, 請參閱[動畫總覽](../graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="55fae-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="55fae-209">**在按一下按鈕時新增動畫:** 最後一個步驟是在使用者按一下按鈕時新增的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="55fae-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="55fae-210">在`ControlTemplate.Triggers`區塊內的任何位置新增下列標記:</span><span class="sxs-lookup"><span data-stu-id="55fae-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="55fae-211">按 F5 執行應用程式, 然後按一下其中一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="55fae-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="55fae-212">當您按一下按鈕時, 半透明矩形就會旋轉。</span><span class="sxs-lookup"><span data-stu-id="55fae-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="55fae-213">總結</span><span class="sxs-lookup"><span data-stu-id="55fae-213">Summary</span></span>
 <span data-ttu-id="55fae-214">在此逐步解說中, 您已執行下列練習:</span><span class="sxs-lookup"><span data-stu-id="55fae-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="55fae-215">將目標設為物件類型 (<xref:System.Windows.Controls.Button>)。 <xref:System.Windows.Style></span><span class="sxs-lookup"><span data-stu-id="55fae-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="55fae-216">使用, <xref:System.Windows.Style>在整個應用程式中控制按鈕的基本屬性。</span><span class="sxs-lookup"><span data-stu-id="55fae-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="55fae-217">建立用來做為<xref:System.Windows.Style> setter 屬性值的資源, 例如漸層。</span><span class="sxs-lookup"><span data-stu-id="55fae-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="55fae-218">藉由將範本套用至按鈕, 自訂整個應用程式中的按鈕外觀。</span><span class="sxs-lookup"><span data-stu-id="55fae-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="55fae-219">回應包含動畫效果的使用者動作 (例如<xref:System.Windows.UIElement.MouseEnter>、 <xref:System.Windows.UIElement.MouseLeave>和<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) 之按鈕的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="55fae-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="55fae-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55fae-220">See also</span></span>

- [<span data-ttu-id="55fae-221">使用 Microsoft Expression Blend 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="55fae-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="55fae-222">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="55fae-222">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="55fae-223">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="55fae-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="55fae-224">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="55fae-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="55fae-225">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="55fae-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
