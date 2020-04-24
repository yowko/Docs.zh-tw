---
title: 逐步解說：使用 XAML 建立按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646472"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="49c19-102">逐步解說：使用 XAML 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="49c19-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="49c19-103">本演練的目的是瞭解如何創建用於 Windows 演示文稿基礎 (WPF) 應用程式的動畫按鈕。</span><span class="sxs-lookup"><span data-stu-id="49c19-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="49c19-104">本演練使用樣式和範本創建自定義按鈕資源,允許重用代碼並將按鈕邏輯與按鈕聲明分離。</span><span class="sxs-lookup"><span data-stu-id="49c19-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="49c19-105">這個演練完全寫在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中 。</span><span class="sxs-lookup"><span data-stu-id="49c19-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49c19-106">本演練將指導您完成通過鍵入或複製並貼上[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Visual Studio 來創建應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="49c19-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="49c19-107">如果您希望瞭解如何使用設計器建立相同的應用程式,請參閱[使用 Microsoft 運算式混合建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。</span><span class="sxs-lookup"><span data-stu-id="49c19-107">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="49c19-108">下圖顯示了已完成的按鈕。</span><span class="sxs-lookup"><span data-stu-id="49c19-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="49c19-109">![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="49c19-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="49c19-110">建立基本按鈕</span><span class="sxs-lookup"><span data-stu-id="49c19-110">Create Basic Buttons</span></span>

<span data-ttu-id="49c19-111">讓我們從創建新專案並向視窗添加幾個按鈕開始。</span><span class="sxs-lookup"><span data-stu-id="49c19-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="49c19-112">建立新的 WPF 專案將按鈕新增到視窗</span><span class="sxs-lookup"><span data-stu-id="49c19-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="49c19-113">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="49c19-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="49c19-114">**建立新的 WPF 專案:** 在 **「檔」** 選單上,指向 **"新建**",然後按一下「**專案**」。</span><span class="sxs-lookup"><span data-stu-id="49c19-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="49c19-115">尋找**Windows 應用程式 (WPF)** 樣本並將專案命名為「動畫按鈕」。</span><span class="sxs-lookup"><span data-stu-id="49c19-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="49c19-116">這將為應用程式創建骨架。</span><span class="sxs-lookup"><span data-stu-id="49c19-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="49c19-117">**新增基本預設按鈕:** 本演練所需的所有檔都由範本提供。</span><span class="sxs-lookup"><span data-stu-id="49c19-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="49c19-118">通過在解決方案資源管理器中按兩下 Window1.xaml 檔案來打開該檔。</span><span class="sxs-lookup"><span data-stu-id="49c19-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="49c19-119">默認情況下,Window1.xaml 中存在一<xref:System.Windows.Controls.Grid>個 元素。</span><span class="sxs-lookup"><span data-stu-id="49c19-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="49c19-120">以鍵入<xref:System.Windows.Controls.Grid>或複製並將以下突出顯示的代碼貼上[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Window1.xaml,刪除元素並將幾個按鈕新增到頁面:</span><span class="sxs-lookup"><span data-stu-id="49c19-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

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

     <span data-ttu-id="49c19-121">按 F5 運行應用程式;您應該會看到一組按鈕,如下所示。</span><span class="sxs-lookup"><span data-stu-id="49c19-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="49c19-122">![三個基本按鈕](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="49c19-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="49c19-123">現在,您已經創建了基本按鈕,您已完成在 Window1.xaml 檔中的工作。</span><span class="sxs-lookup"><span data-stu-id="49c19-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="49c19-124">演練的其餘部分將側重於 app.xaml 檔,定義樣式和按鈕的範本。</span><span class="sxs-lookup"><span data-stu-id="49c19-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="49c19-125">設定基本屬性</span><span class="sxs-lookup"><span data-stu-id="49c19-125">Set Basic Properties</span></span>

<span data-ttu-id="49c19-126">接下來,讓我們在這些按鈕上設置一些屬性,以控制按鈕的外觀和佈局。</span><span class="sxs-lookup"><span data-stu-id="49c19-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="49c19-127">您將使用資源為整個應用程式定義按鈕屬性,而不是單獨設置按鈕上的屬性。</span><span class="sxs-lookup"><span data-stu-id="49c19-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="49c19-128">應用程式資源在概念上類似於網頁的外部級聯樣式表 (CSS);但是,資源比級聯樣式表 (CSS) 更強大,正如在本演練結束時看到的。</span><span class="sxs-lookup"><span data-stu-id="49c19-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="49c19-129">要瞭解有關資源的更多資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="49c19-129">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="49c19-130">使用樣式在按鈕上設定基本屬性</span><span class="sxs-lookup"><span data-stu-id="49c19-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="49c19-131">**定義應用程式.資源區塊:** 開啟 app.xaml 並新增以下突出顯示的標記(如果尚未出現):</span><span class="sxs-lookup"><span data-stu-id="49c19-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

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

     <span data-ttu-id="49c19-132">資源範圍由定義資源的位置確定。</span><span class="sxs-lookup"><span data-stu-id="49c19-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="49c19-133">在 app.xaml`Application.Resources`檔中定義資源,可以從應用程式中的任何位置使用資源。</span><span class="sxs-lookup"><span data-stu-id="49c19-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="49c19-134">要瞭解有關定義資源範圍的更多資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="49c19-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="49c19-135">**建立樣式並使用它定義基本屬性值:** 將以下標記加入區塊中`Application.Resources`。</span><span class="sxs-lookup"><span data-stu-id="49c19-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="49c19-136">此標記建立<xref:System.Windows.Style>應用於應用程式中的所有按鈕,將按鈕設定為 90,將<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Margin%2A>設定為 10:</span><span class="sxs-lookup"><span data-stu-id="49c19-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="49c19-137">屬性<xref:System.Windows.Style.TargetType%2A>指定樣式應用於<xref:System.Windows.Controls.Button>類型的所有物件。</span><span class="sxs-lookup"><span data-stu-id="49c19-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="49c19-138">每個<xref:System.Windows.Setter>設置 不同的屬性值<xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="49c19-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="49c19-139">因此,此時應用程式中的每個按鈕的寬度為 90,邊距為 10。</span><span class="sxs-lookup"><span data-stu-id="49c19-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="49c19-140">如果按 F5 執行應用程式,您將看到以下視窗。</span><span class="sxs-lookup"><span data-stu-id="49c19-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="49c19-141">![寬度為 90 且邊界為 10 的按鈕](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="49c19-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="49c19-142">可以使用樣式執行更多操作,包括調整目標物件、指定複雜屬性值,甚至使用樣式作為其他樣式的輸入的各種方法。</span><span class="sxs-lookup"><span data-stu-id="49c19-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="49c19-143">有關詳細資訊,請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。</span><span class="sxs-lookup"><span data-stu-id="49c19-143">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="49c19-144">**將樣式屬性值設定為資源:** 資源支援一種簡單方法來重用通常定義的物件和值。</span><span class="sxs-lookup"><span data-stu-id="49c19-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="49c19-145">使用資源定義複雜值以使代碼更加模組化尤其有用。</span><span class="sxs-lookup"><span data-stu-id="49c19-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="49c19-146">將以下突出顯示的標記添加到 app.xaml。</span><span class="sxs-lookup"><span data-stu-id="49c19-146">Add the following highlighted markup to app.xaml.</span></span>

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

     <span data-ttu-id="49c19-147">直接在`Application.Resources`塊下,您創建了一個名為"灰藍漸變畫筆"的資源。</span><span class="sxs-lookup"><span data-stu-id="49c19-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="49c19-148">此資源定義水準漸變。</span><span class="sxs-lookup"><span data-stu-id="49c19-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="49c19-149">此資源可以從應用程式的任何位置用作屬性值,包括在<xref:System.Windows.Controls.Control.Background%2A>屬性的按鈕樣式設置器內。</span><span class="sxs-lookup"><span data-stu-id="49c19-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="49c19-150">現在,所有按鈕都有此漸變<xref:System.Windows.Controls.Control.Background%2A>的屬性值。</span><span class="sxs-lookup"><span data-stu-id="49c19-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="49c19-151">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="49c19-151">Press F5 to run the application.</span></span> <span data-ttu-id="49c19-152">它應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="49c19-152">It should look like the following.</span></span>

     <span data-ttu-id="49c19-153">![具有漸層背景的按鈕](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="49c19-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="49c19-154">建立定義按鈕外觀的樣本</span><span class="sxs-lookup"><span data-stu-id="49c19-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="49c19-155">在本節中,您將創建一個範本,用於自定義按鈕的外觀(表示)。</span><span class="sxs-lookup"><span data-stu-id="49c19-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="49c19-156">按鈕表示由多個物件組成,包括矩形和其他元件,使按鈕的外觀獨一無二。</span><span class="sxs-lookup"><span data-stu-id="49c19-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="49c19-157">到目前為止,對按鈕在應用程式中的外觀的控制僅限於更改按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="49c19-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="49c19-158">如果你想對按鈕的外觀進行更徹底的更改,該怎麼辦?</span><span class="sxs-lookup"><span data-stu-id="49c19-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="49c19-159">範本能夠對物件的表示進行強大的控制。</span><span class="sxs-lookup"><span data-stu-id="49c19-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="49c19-160">由於範本可以在樣式中使用,因此可以將範本應用於樣式應用於的所有物件(在本演練中,按鈕)。</span><span class="sxs-lookup"><span data-stu-id="49c19-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="49c19-161">使用樣本定義按鈕的外觀</span><span class="sxs-lookup"><span data-stu-id="49c19-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="49c19-162">**設定樣本:** 由於控制項(<xref:System.Windows.Controls.Button>如<xref:System.Windows.Controls.Control.Template%2A>具有 屬性)可以定義樣本屬性值,就像<xref:System.Windows.Style>我們使用 中設置的其他屬性<xref:System.Windows.Setter>值一樣。</span><span class="sxs-lookup"><span data-stu-id="49c19-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="49c19-163">將以下突出顯示的標記添加到按鈕樣式中。</span><span class="sxs-lookup"><span data-stu-id="49c19-163">Add the following highlighted markup to your button style.</span></span>

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

2. <span data-ttu-id="49c19-164">**變更按鈕簡報文件:** 此時,您需要定義範本。</span><span class="sxs-lookup"><span data-stu-id="49c19-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="49c19-165">添加以下突出顯示的標記。</span><span class="sxs-lookup"><span data-stu-id="49c19-165">Add the following highlighted markup.</span></span> <span data-ttu-id="49c19-166">這個標記指定兩<xref:System.Windows.Shapes.Rectangle>個圓邊元素,後跟<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="49c19-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="49c19-167"><xref:System.Windows.Controls.DockPanel>承載按鍵<xref:System.Windows.Controls.ContentPresenter>的 。</span><span class="sxs-lookup"><span data-stu-id="49c19-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="49c19-168">顯示<xref:System.Windows.Controls.ContentPresenter>按鈕的內容。</span><span class="sxs-lookup"><span data-stu-id="49c19-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="49c19-169">在本演練中,內容是文本("按鈕 1","按鈕 2","按鈕 3")。</span><span class="sxs-lookup"><span data-stu-id="49c19-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="49c19-170">所有範本元件(矩形和<xref:System.Windows.Controls.DockPanel>) 都位於的<xref:System.Windows.Controls.Grid>內部。</span><span class="sxs-lookup"><span data-stu-id="49c19-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

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

     <span data-ttu-id="49c19-171">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="49c19-171">Press F5 to run the application.</span></span> <span data-ttu-id="49c19-172">它應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="49c19-172">It should look like the following.</span></span>

     ![帶 3 個按鈕的視窗](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="49c19-174">**加入樣本加入玻璃效果:** 接下來,您將添加玻璃。</span><span class="sxs-lookup"><span data-stu-id="49c19-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="49c19-175">首先,創建一些創建玻璃漸變效果的資源。</span><span class="sxs-lookup"><span data-stu-id="49c19-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="49c19-176">在`Application.Resources`區塊內的任何位置新增這些漸層來源:</span><span class="sxs-lookup"><span data-stu-id="49c19-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

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

     <span data-ttu-id="49c19-177">這些資源用作<xref:System.Windows.Shapes.Shape.Fill%2A>我們插入到按鈕範<xref:System.Windows.Controls.Grid>本 中的矩形。</span><span class="sxs-lookup"><span data-stu-id="49c19-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="49c19-178">向範本添加以下突出顯示的標記。</span><span class="sxs-lookup"><span data-stu-id="49c19-178">Add the following highlighted markup to the template.</span></span>

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

     <span data-ttu-id="49c19-179">請注意,<xref:System.Windows.UIElement.Opacity%2A>具有"glassCube"`x:Name`屬性的矩形為 0,因此當您運行範例時,您看不到覆蓋在頂部的玻璃矩形。</span><span class="sxs-lookup"><span data-stu-id="49c19-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="49c19-180">這是因為我們稍後將向範本添加觸發器,用於使用者與按鈕互動時。</span><span class="sxs-lookup"><span data-stu-id="49c19-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="49c19-181">但是,通過將<xref:System.Windows.UIElement.Opacity%2A>值更改為 1 並運行應用程式,您可以看到按鈕現在的外觀。</span><span class="sxs-lookup"><span data-stu-id="49c19-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="49c19-182">請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="49c19-182">See the following figure.</span></span> <span data-ttu-id="49c19-183">在繼續下一步之前,將<xref:System.Windows.UIElement.Opacity%2A>返回更改為 0。</span><span class="sxs-lookup"><span data-stu-id="49c19-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="49c19-184">![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="49c19-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="49c19-185">建立按鈕互動性</span><span class="sxs-lookup"><span data-stu-id="49c19-185">Create Button Interactivity</span></span>

<span data-ttu-id="49c19-186">在本節中,您將創建屬性觸發器和事件觸發器以更改屬性值並運行動畫以回應使用者操作,例如將滑鼠指標移到按鈕上並按一下。</span><span class="sxs-lookup"><span data-stu-id="49c19-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="49c19-187">添加互動性(滑鼠懸停、滑鼠離開、按一下等)的一種簡單方法是在範本或樣式中定義觸發器。</span><span class="sxs-lookup"><span data-stu-id="49c19-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="49c19-188">要建立<xref:System.Windows.Trigger>,定義屬性「條件」,例如:<xref:System.Windows.UIElement.IsMouseOver%2A>按鈕 屬性值`true`等於 。</span><span class="sxs-lookup"><span data-stu-id="49c19-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="49c19-189">然後定義在觸發條件為 true 時發生的設置器(操作)。</span><span class="sxs-lookup"><span data-stu-id="49c19-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="49c19-190">建立按鈕互動性</span><span class="sxs-lookup"><span data-stu-id="49c19-190">To create button interactivity</span></span>

1. <span data-ttu-id="49c19-191">**新增樣本觸發器:** 將突出顯示的標記添加到範本中。</span><span class="sxs-lookup"><span data-stu-id="49c19-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

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

2. <span data-ttu-id="49c19-192">**新增屬性觸發器:** 將突顯的標記加入區`ControlTemplate.Triggers`塊:</span><span class="sxs-lookup"><span data-stu-id="49c19-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="49c19-193">按 F5 以執行應用程式,並在在按鈕上運行滑鼠指標時看到效果。</span><span class="sxs-lookup"><span data-stu-id="49c19-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="49c19-194">**新增焦點觸發器:** 接下來,我們將添加一些類似的設置器來處理按鈕具有焦點時(例如,在用戶按一下按鈕後)的情況。</span><span class="sxs-lookup"><span data-stu-id="49c19-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

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

     <span data-ttu-id="49c19-195">按 F5 運行應用程式,然後按一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="49c19-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="49c19-196">請注意,按一下該按鈕后,該按鈕將保持突出顯示,因為它仍有焦點。</span><span class="sxs-lookup"><span data-stu-id="49c19-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="49c19-197">如果按一下按鈕,則新按鈕在上次按鈕丟失時獲得焦點。</span><span class="sxs-lookup"><span data-stu-id="49c19-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="49c19-198">**為**<xref:System.Windows.UIElement.MouseEnter>**and**和<xref:System.Windows.UIElement.MouseLeave>添加動畫 **:** 接下來,我們將一些動畫添加到觸發器中。  </span><span class="sxs-lookup"><span data-stu-id="49c19-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="49c19-199">在`ControlTemplate.Triggers`塊內的任意位置添加以下標記。</span><span class="sxs-lookup"><span data-stu-id="49c19-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

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

     <span data-ttu-id="49c19-200">當滑鼠指標在按鈕上移動時,玻璃矩形將縮小,當指標離開時返回正常大小。</span><span class="sxs-lookup"><span data-stu-id="49c19-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="49c19-201">指標超過按鈕時將觸發兩個動畫(<xref:System.Windows.UIElement.MouseEnter>引發事件)。</span><span class="sxs-lookup"><span data-stu-id="49c19-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="49c19-202">這些動畫沿 X 軸和 Y 軸收縮玻璃矩形。</span><span class="sxs-lookup"><span data-stu-id="49c19-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="49c19-203">請注意<xref:System.Windows.Media.Animation.DoubleAnimation>元素<xref:System.Windows.Media.Animation.Timeline.Duration%2A>與與上的<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性 。</span><span class="sxs-lookup"><span data-stu-id="49c19-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="49c19-204">指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫在半秒以上發生,<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>並指定玻璃收縮 10%。</span><span class="sxs-lookup"><span data-stu-id="49c19-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="49c19-205">第二個事件觸發器<xref:System.Windows.UIElement.MouseLeave>( ) 只是停止第一個事件觸發器。</span><span class="sxs-lookup"><span data-stu-id="49c19-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="49c19-206">停止 時<xref:System.Windows.Media.Animation.Storyboard>, 所有動畫屬性將返回到其預設值。</span><span class="sxs-lookup"><span data-stu-id="49c19-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="49c19-207">因此,當使用者將指標移出按鈕時,該按鈕將回到滑鼠指標移到按鈕之前的方式。</span><span class="sxs-lookup"><span data-stu-id="49c19-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="49c19-208">有關動畫的詳細資訊,請參閱[動畫概述](../graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="49c19-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="49c19-209">**新增按下按鈕時的動畫:** 最後一步是添加用戶按一下按鈕時的觸發器。</span><span class="sxs-lookup"><span data-stu-id="49c19-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="49c19-210">在`ControlTemplate.Triggers`區塊的任何位置加入以下標記:</span><span class="sxs-lookup"><span data-stu-id="49c19-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

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

     <span data-ttu-id="49c19-211">按 F5 運行應用程式,然後按一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="49c19-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="49c19-212">按下按鈕時,玻璃矩形會旋轉。</span><span class="sxs-lookup"><span data-stu-id="49c19-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="49c19-213">摘要</span><span class="sxs-lookup"><span data-stu-id="49c19-213">Summary</span></span>
 <span data-ttu-id="49c19-214">在本演練中,您執行以下練習:</span><span class="sxs-lookup"><span data-stu-id="49c19-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="49c19-215">將<xref:System.Windows.Style>目標物件型<xref:System.Windows.Controls.Button>態 ( 。</span><span class="sxs-lookup"><span data-stu-id="49c19-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="49c19-216">使用 控制整個應用程式中按鈕的基本<xref:System.Windows.Style>屬性 。</span><span class="sxs-lookup"><span data-stu-id="49c19-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="49c19-217">建立的資源(如漸變)用於<xref:System.Windows.Style>設置器的屬性值。</span><span class="sxs-lookup"><span data-stu-id="49c19-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="49c19-218">通過將範本應用於按鈕,自定義整個應用程式中的按鈕外觀。</span><span class="sxs-lookup"><span data-stu-id="49c19-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="49c19-219">按鈕的自定義行為,以回應包含動畫效果的使用者操作(如<xref:System.Windows.UIElement.MouseEnter><xref:System.Windows.UIElement.MouseLeave>、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>和)。</span><span class="sxs-lookup"><span data-stu-id="49c19-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c19-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49c19-220">See also</span></span>

- [<span data-ttu-id="49c19-221">使用 Microsoft Expression Blend 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="49c19-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="49c19-222">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="49c19-222">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="49c19-223">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="49c19-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="49c19-224">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="49c19-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="49c19-225">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="49c19-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
