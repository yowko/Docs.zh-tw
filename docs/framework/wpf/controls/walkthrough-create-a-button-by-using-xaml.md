---
title: 逐步解說：使用 XAML 建立按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: c092ad49f40257467245a07a6e4b9849822e1835
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076558"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="473ec-102">逐步解說：使用 XAML 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="473ec-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="473ec-103">本逐步解說的目的是要了解如何在 Windows Presentation Foundation (WPF) 應用程式中建立動畫的按鈕，供使用。</span><span class="sxs-lookup"><span data-stu-id="473ec-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="473ec-104">本逐步解說會使用樣式和範本來建立自訂的按鈕資源可讓您重複使用程式碼及從按鈕宣告按鈕的邏輯分隔開來。</span><span class="sxs-lookup"><span data-stu-id="473ec-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="473ec-105">本逐步解說完全在撰寫[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="473ec-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="473ec-106">本逐步解說會引導您完成建立應用程式，輸入或複製並貼上步驟[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Microsoft Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="473ec-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft Visual Studio.</span></span> <span data-ttu-id="473ec-107">如果您想要了解如何使用設計工具 (Microsoft Expression Blend) 來建立相同的應用程式，請參閱[建立使用 Microsoft Expression Blend 按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。</span><span class="sxs-lookup"><span data-stu-id="473ec-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="473ec-108">下圖顯示 [完成] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="473ec-109">![使用 XAML 所建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="473ec-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="473ec-110">建立基本的按鈕</span><span class="sxs-lookup"><span data-stu-id="473ec-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="473ec-111">讓我們開始建立新的專案，並將幾個按鈕加入至視窗。</span><span class="sxs-lookup"><span data-stu-id="473ec-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="473ec-112">若要建立新的 WPF 專案，並將按鈕加入至視窗</span><span class="sxs-lookup"><span data-stu-id="473ec-112">To create a new WPF project and add buttons to the window</span></span>  
  
1.  <span data-ttu-id="473ec-113">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="473ec-113">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="473ec-114">**建立新的 WPF 專案：** 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。</span><span class="sxs-lookup"><span data-stu-id="473ec-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="473ec-115">尋找**Windows 應用程式 (WPF)** 範本並將專案命名為"AnimatedButton 」。</span><span class="sxs-lookup"><span data-stu-id="473ec-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="473ec-116">這會建立應用程式的基本架構。</span><span class="sxs-lookup"><span data-stu-id="473ec-116">This will create the skeleton for the application.</span></span>  
  
3.  <span data-ttu-id="473ec-117">**新增基本的預設按鈕：** 範本會提供本逐步解說所需的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="473ec-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="473ec-118">按一下方案總管 中按兩下，開啟 Window1.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="473ec-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="473ec-119">根據預設，沒有<xref:System.Windows.Controls.Grid>Window1.xaml 中的項目。</span><span class="sxs-lookup"><span data-stu-id="473ec-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="473ec-120">移除<xref:System.Windows.Controls.Grid>項目並將幾個按鈕加入[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]式輸入或複製並貼上下列反白顯示的程式碼，以 Window1.xaml 頁面：</span><span class="sxs-lookup"><span data-stu-id="473ec-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
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
  
     <span data-ttu-id="473ec-121">按 f5 鍵執行應用程式。您應該會看到一組看起來像下圖的按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="473ec-122">![三個基本按鈕](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="473ec-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="473ec-123">既然您已建立基本的按鈕，您已完成在 Window1.xaml 檔案中工作。</span><span class="sxs-lookup"><span data-stu-id="473ec-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="473ec-124">本逐步解說的其餘部分著重於 app.xaml 檔案中，定義樣式和範本的按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="473ec-125">設定基本的屬性</span><span class="sxs-lookup"><span data-stu-id="473ec-125">Set Basic Properties</span></span>  
 <span data-ttu-id="473ec-126">接下來，讓我們在這些按鈕，以控制按鈕的外觀和版面配置上設定一些屬性。</span><span class="sxs-lookup"><span data-stu-id="473ec-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="473ec-127">而不是個別按鈕上設定屬性，您會使用資源來定義整個應用程式的按鈕屬性。</span><span class="sxs-lookup"><span data-stu-id="473ec-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="473ec-128">應用程式資源是在概念上類似於外部[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]網頁中; 不過，資源會比功能更強大[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]，如本逐步解說結束時，您會看到。</span><span class="sxs-lookup"><span data-stu-id="473ec-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="473ec-129">若要深入了解資源，請參閱[XAML 資源](../advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="473ec-129">To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="473ec-130">若要使用樣式設定按鈕上的基本內容</span><span class="sxs-lookup"><span data-stu-id="473ec-130">To use styles to set basic properties on the buttons</span></span>  
  
1.  <span data-ttu-id="473ec-131">**定義 Application.Resources 區塊：** 開啟 app.xaml，並新增下列醒目提示的標記，如果它已經不存在：</span><span class="sxs-lookup"><span data-stu-id="473ec-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
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
  
     <span data-ttu-id="473ec-132">資源範圍取決於您用來定義資源。</span><span class="sxs-lookup"><span data-stu-id="473ec-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="473ec-133">定義中的資源`Application.Resources`在 app.xaml 檔案可讓用於從任何位置的應用程式中的資源。</span><span class="sxs-lookup"><span data-stu-id="473ec-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="473ec-134">若要深入了解定義您資源的範圍，請參閱[XAML 資源](../advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="473ec-134">To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>  
  
2.  <span data-ttu-id="473ec-135">**建立樣式，並定義與它的基本屬性值：** 新增下列標記來`Application.Resources`區塊。</span><span class="sxs-lookup"><span data-stu-id="473ec-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="473ec-136">此標記會建立<xref:System.Windows.Style>套用至的應用程式設定中的所有按鈕<xref:System.Windows.FrameworkElement.Width%2A>的按鈕為 90，<xref:System.Windows.FrameworkElement.Margin%2A>為 10:</span><span class="sxs-lookup"><span data-stu-id="473ec-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="473ec-137"><xref:System.Windows.Style.TargetType%2A>屬性會指定這個樣式會套用至類型的所有物件<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="473ec-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="473ec-138">每個<xref:System.Windows.Setter>設定為不同的屬性值<xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="473ec-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="473ec-139">因此，此時應用程式中的每個按鈕有寬度為 90 且邊界為 10。</span><span class="sxs-lookup"><span data-stu-id="473ec-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="473ec-140">如果您按 F5 執行應用程式時，您會看到下列視窗。</span><span class="sxs-lookup"><span data-stu-id="473ec-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="473ec-141">![按鈕寬度為 90 且邊界為 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="473ec-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="473ec-142">還有更多您可以利用樣式，包括各種不同的微調哪些物件為目標的方法，指定複雜的屬性值，以及其他樣式即使使用做為輸入的樣式。</span><span class="sxs-lookup"><span data-stu-id="473ec-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="473ec-143">如需詳細資訊，請參閱 [設定樣式和範本](styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="473ec-143">For more information, see [Styling and Templating](styling-and-templating.md).</span></span>  
  
3.  <span data-ttu-id="473ec-144">**樣式屬性值設定為資源：** 資源可讓重複使用一般定義的物件和值的簡單方法。</span><span class="sxs-lookup"><span data-stu-id="473ec-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="473ec-145">它是特別有用來定義複雜的值，讓程式碼更模組化中使用的資源。</span><span class="sxs-lookup"><span data-stu-id="473ec-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="473ec-146">App.xaml 中加入下列反白顯示的標記。</span><span class="sxs-lookup"><span data-stu-id="473ec-146">Add the following highlighted markup to app.xaml.</span></span>  
  
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
  
     <span data-ttu-id="473ec-147">正下方`Application.Resources`區塊中，建立名為"GrayBlueGradientBrush 」 的資源。</span><span class="sxs-lookup"><span data-stu-id="473ec-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="473ec-148">此資源會定義水平漸層。</span><span class="sxs-lookup"><span data-stu-id="473ec-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="473ec-149">這項資源可用來當做屬性值從任何地方的應用程式，包括內的按鈕樣式 setter<xref:System.Windows.Controls.Control.Background%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="473ec-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="473ec-150">現在，所有的按鈕有<xref:System.Windows.Controls.Control.Background%2A>此漸層的屬性值。</span><span class="sxs-lookup"><span data-stu-id="473ec-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="473ec-151">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="473ec-151">Press F5 to run the application.</span></span> <span data-ttu-id="473ec-152">它看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="473ec-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="473ec-153">![使用漸層背景的按鈕](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="473ec-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="473ec-154">建立範本定義按鈕的外觀</span><span class="sxs-lookup"><span data-stu-id="473ec-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="473ec-155">在本節中，您可以建立自訂按鈕的外觀 (presentation) 的範本。</span><span class="sxs-lookup"><span data-stu-id="473ec-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="473ec-156">呈現的按鈕是組成包括矩形和其他元件的數個物件來為按鈕提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="473ec-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="473ec-157">到目前為止，在應用程式中的按鈕外觀的控制項具有已侷限於變更按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="473ec-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="473ec-158">如果您想要對按鈕外觀進行更巨大的變動嗎？</span><span class="sxs-lookup"><span data-stu-id="473ec-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="473ec-159">範本可讓物件的簡報功能強大的控制。</span><span class="sxs-lookup"><span data-stu-id="473ec-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="473ec-160">樣式內，就可以使用範本，因為您可以套用範本樣式會套用到 （在此逐步解說中，按鈕） 的所有物件。</span><span class="sxs-lookup"><span data-stu-id="473ec-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="473ec-161">若要使用的範本定義按鈕的外觀</span><span class="sxs-lookup"><span data-stu-id="473ec-161">To use the template to define the look of the button</span></span>  
  
1.  <span data-ttu-id="473ec-162">**將範本設定：** 因為控制項，例如<xref:System.Windows.Controls.Button>有<xref:System.Windows.Controls.Control.Template%2A>屬性，您可以定義範本的屬性值，就像我們已在中設定的其他屬性值一樣<xref:System.Windows.Style>使用<xref:System.Windows.Setter>。</span><span class="sxs-lookup"><span data-stu-id="473ec-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="473ec-163">按鈕樣式中加入下列反白顯示的標記。</span><span class="sxs-lookup"><span data-stu-id="473ec-163">Add the following highlighted markup to your button style.</span></span>  
  
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
  
2.  <span data-ttu-id="473ec-164">**Alter 按鈕簡報：** 此時，您需要定義範本。</span><span class="sxs-lookup"><span data-stu-id="473ec-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="473ec-165">新增下列醒目提示的標記。</span><span class="sxs-lookup"><span data-stu-id="473ec-165">Add the following highlighted markup.</span></span> <span data-ttu-id="473ec-166">此標記會指定兩個<xref:System.Windows.Shapes.Rectangle>具有圓角邊緣、 項目後面<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="473ec-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="473ec-167"><xref:System.Windows.Controls.DockPanel>用來裝載<xref:System.Windows.Controls.ContentPresenter>的按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="473ec-168">A<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。</span><span class="sxs-lookup"><span data-stu-id="473ec-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="473ec-169">在本逐步解說中，內容會是文字 （"按鈕 1 」、 「 按鈕 2 」、 「 按鈕 3 」）。</span><span class="sxs-lookup"><span data-stu-id="473ec-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="473ec-170">所有範本的元件 (矩形， <xref:System.Windows.Controls.DockPanel>) 內的配置<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="473ec-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
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
  
     <span data-ttu-id="473ec-171">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="473ec-171">Press F5 to run the application.</span></span> <span data-ttu-id="473ec-172">它看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="473ec-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="473ec-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="473ec-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3.  <span data-ttu-id="473ec-174">**將 glasseffect 新增到範本：** 接下來您要加入半透明效果。</span><span class="sxs-lookup"><span data-stu-id="473ec-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="473ec-175">首先，您會建立一些建立透明的漸層效果的資源。</span><span class="sxs-lookup"><span data-stu-id="473ec-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="473ec-176">漸層停駐將這些資源加入任何位置內`Application.Resources`區塊：</span><span class="sxs-lookup"><span data-stu-id="473ec-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
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
  
     <span data-ttu-id="473ec-177">這些資源用做<xref:System.Windows.Shapes.Shape.Fill%2A>我們插入矩形<xref:System.Windows.Controls.Grid>的 [按鈕] 範本。</span><span class="sxs-lookup"><span data-stu-id="473ec-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="473ec-178">將下列反白顯示的標記加入至範本。</span><span class="sxs-lookup"><span data-stu-id="473ec-178">Add the following highlighted markup to the template.</span></span>  
  
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
  
     <span data-ttu-id="473ec-179">請注意，<xref:System.Windows.UIElement.Opacity%2A>與矩形的`x:Name`"glassCube 」 屬性為 0，因此當您執行範例時，您看不見玻璃矩形頂端上重疊。</span><span class="sxs-lookup"><span data-stu-id="473ec-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="473ec-180">這是因為我們稍後會將加入觸發程序的範本的使用者互動的按鈕時。</span><span class="sxs-lookup"><span data-stu-id="473ec-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="473ec-181">不過，您可以在其中看到按鈕的外觀如下現在藉由變更<xref:System.Windows.UIElement.Opacity%2A>1 」 和執行應用程式的值。</span><span class="sxs-lookup"><span data-stu-id="473ec-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="473ec-182">請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="473ec-182">See the following figure.</span></span> <span data-ttu-id="473ec-183">在繼續之前的下一個步驟，變更<xref:System.Windows.UIElement.Opacity%2A>為 0。</span><span class="sxs-lookup"><span data-stu-id="473ec-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="473ec-184">![使用 XAML 所建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="473ec-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="473ec-185">建立按鈕互動性</span><span class="sxs-lookup"><span data-stu-id="473ec-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="473ec-186">在本節中，您將建立屬性觸發程序和事件觸發程序來變更屬性值，執行動畫，以回應使用者動作，例如將滑鼠指標移到按鈕上方，然後按一下。</span><span class="sxs-lookup"><span data-stu-id="473ec-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="473ec-187">加入互動功能 （滑鼠停留、 滑鼠離開，按一下，等等） 的簡單方法是定義您的範本或樣式中的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="473ec-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="473ec-188">若要建立<xref:System.Windows.Trigger>，例如將"condition"屬性定義：[] 按鈕<xref:System.Windows.UIElement.IsMouseOver%2A>屬性值等於`true`。</span><span class="sxs-lookup"><span data-stu-id="473ec-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="473ec-189">然後，您會定義觸發程序條件為 true 時，會發生的 setter （動作）。</span><span class="sxs-lookup"><span data-stu-id="473ec-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="473ec-190">若要建立按鈕互動性</span><span class="sxs-lookup"><span data-stu-id="473ec-190">To create button interactivity</span></span>  
  
1.  <span data-ttu-id="473ec-191">**新增範本觸發程序：** 將反白顯示的標記新增至您的範本。</span><span class="sxs-lookup"><span data-stu-id="473ec-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
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
  
2.  <span data-ttu-id="473ec-192">**新增屬性觸發程序：** 反白顯示將標記新增至`ControlTemplate.Triggers`區塊：</span><span class="sxs-lookup"><span data-stu-id="473ec-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="473ec-193">按 f5 鍵執行應用程式，並查看效果，當您執行到按鈕的滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="473ec-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3.  <span data-ttu-id="473ec-194">**新增焦點觸發程序：** 接下來，我們將新增一些類似的 setter 來處理的情況，當按鈕具有焦點 （例如，在使用者按一下它之後）。</span><span class="sxs-lookup"><span data-stu-id="473ec-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
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
  
     <span data-ttu-id="473ec-195">按 f5 鍵執行應用程式，然後按一下其中一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="473ec-196">請注意，[] 按鈕之後會保持反白顯示您按一下它因為它仍具有焦點。</span><span class="sxs-lookup"><span data-stu-id="473ec-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="473ec-197">如果您按一下另一個按鈕時，[新增] 按鈕時的最後一個會失去它，就會取得焦點。</span><span class="sxs-lookup"><span data-stu-id="473ec-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4.  <span data-ttu-id="473ec-198">**新增動畫**<xref:System.Windows.UIElement.MouseEnter> **並** <xref:System.Windows.UIElement.MouseLeave> **:** 接下來我們加入一些動畫觸發程序。</span><span class="sxs-lookup"><span data-stu-id="473ec-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="473ec-199">新增下列任何一處內的標記`ControlTemplate.Triggers`區塊。</span><span class="sxs-lookup"><span data-stu-id="473ec-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
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
  
     <span data-ttu-id="473ec-200">當滑鼠指標移到按鈕上方，並傳回給一般大小，當滑鼠指標離開時，會縮小玻璃矩形。</span><span class="sxs-lookup"><span data-stu-id="473ec-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="473ec-201">有兩個當滑鼠指標移至按鈕上時，會觸發的動畫 (<xref:System.Windows.UIElement.MouseEnter>就會引發事件)。</span><span class="sxs-lookup"><span data-stu-id="473ec-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="473ec-202">這些動畫壓縮玻璃矩形沿著 X 和 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="473ec-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="473ec-203">請注意上的屬性<xref:System.Windows.Media.Animation.DoubleAnimation>項目 —<xref:System.Windows.Media.Animation.Timeline.Duration%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>。</span><span class="sxs-lookup"><span data-stu-id="473ec-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="473ec-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定動畫發生超過半秒，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>指定半透明效果壓縮 10%。</span><span class="sxs-lookup"><span data-stu-id="473ec-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="473ec-205">第二個事件觸發程序 (<xref:System.Windows.UIElement.MouseLeave>) 只會停止第一個。</span><span class="sxs-lookup"><span data-stu-id="473ec-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="473ec-206">當您停止<xref:System.Windows.Media.Animation.Storyboard>，所有動畫的屬性會傳回為其預設值。</span><span class="sxs-lookup"><span data-stu-id="473ec-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="473ec-207">因此，當使用者移出按鈕的指標，按鈕會回到之前的滑鼠游標移到按鈕的方式。</span><span class="sxs-lookup"><span data-stu-id="473ec-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="473ec-208">如需動畫的詳細資訊，請參閱[動畫概觀](../graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="473ec-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>  
  
5.  <span data-ttu-id="473ec-209">**加入按一下按鈕時的動畫：** 最後一個步驟是新增的觸發程序，當使用者按一下按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="473ec-210">新增下列任何一處內的標記`ControlTemplate.Triggers`區塊：</span><span class="sxs-lookup"><span data-stu-id="473ec-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
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
  
     <span data-ttu-id="473ec-211">按 f5 鍵執行應用程式，然後按一下其中一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="473ec-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="473ec-212">當您按一下按鈕時，半透明矩形會旋轉。</span><span class="sxs-lookup"><span data-stu-id="473ec-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="473ec-213">總結</span><span class="sxs-lookup"><span data-stu-id="473ec-213">Summary</span></span>  
 <span data-ttu-id="473ec-214">在本逐步解說中，您的練習如下：</span><span class="sxs-lookup"><span data-stu-id="473ec-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="473ec-215">目標<xref:System.Windows.Style>成物件類型 (<xref:System.Windows.Controls.Button>)。</span><span class="sxs-lookup"><span data-stu-id="473ec-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="473ec-216">控制在整個應用程式中使用按鈕的基本屬性<xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="473ec-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="473ec-217">建立資源，例如要用於屬性值的漸層<xref:System.Windows.Style>setter。</span><span class="sxs-lookup"><span data-stu-id="473ec-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="473ec-218">將範本套用至按鈕來自訂整個應用程式中按鈕的外觀。</span><span class="sxs-lookup"><span data-stu-id="473ec-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="473ec-219">自訂的按鈕，以回應使用者動作的行為 (例如<xref:System.Windows.UIElement.MouseEnter>， <xref:System.Windows.UIElement.MouseLeave>，和<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) 包含的動畫效果。</span><span class="sxs-lookup"><span data-stu-id="473ec-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473ec-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="473ec-220">See also</span></span>

- [<span data-ttu-id="473ec-221">使用 Microsoft Expression Blend 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="473ec-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="473ec-222">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="473ec-222">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="473ec-223">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="473ec-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="473ec-224">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="473ec-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="473ec-225">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="473ec-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
