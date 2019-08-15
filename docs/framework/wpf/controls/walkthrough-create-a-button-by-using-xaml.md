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
# <a name="walkthrough-create-a-button-by-using-xaml"></a>逐步解說：使用 XAML 建立按鈕

本逐步解說的目的是要瞭解如何建立動畫按鈕, 以便在 Windows Presentation Foundation (WPF) 應用程式中使用。 本逐步解說會使用樣式和範本來建立自訂的按鈕資源, 以允許重複使用程式碼, 並從按鈕宣告中分隔按鈕邏輯。 這個逐步解說完全寫在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中。

> [!IMPORTANT]
> 本逐步解說會引導您完成建立應用程式的步驟, 方法是輸入或[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]複製並貼入 Microsoft Visual Studio。 如果您想要瞭解如何使用設計工具 (Microsoft Expression Blend) 來建立相同的應用程式, 請參閱[使用 Microsoft Expression Blend 建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。

下圖顯示 [已完成] 按鈕。

![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>建立基本按鈕

讓我們先建立新的專案, 然後在視窗中加入幾個按鈕。

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>若要建立新的 WPF 專案並將按鈕加入至視窗

1. 啟動 Visual Studio。

2. **建立新的 WPF 專案:** 在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。 尋找**Windows 應用程式 (WPF)** 範本, 並將專案命名為 "AnimatedButton"。 這會建立應用程式的基本架構。

3. **新增基本的預設按鈕:** 此逐步解說所需的所有檔案都是由範本提供。 在方案總管中按兩下 Window1.xaml, 以開啟該檔案。 根據預設, window1.xaml 中有<xref:System.Windows.Controls.Grid>一個元素。 藉由輸入或複製下列反白顯示的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼並貼到 window1.xaml 中, 移除元素並將一些按鈕新增至頁面:<xref:System.Windows.Controls.Grid>

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

     按 F5 執行應用程式;您應該會看到如下圖所示的一組按鈕。

     ![三個基本按鈕](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     現在您已建立基本按鈕, 您已完成使用 Window1.xaml。 本逐步解說的其餘部分著重于 app.xaml 檔案, 定義樣式和按鈕的範本。

## <a name="set-basic-properties"></a>設定基本屬性

接下來, 我們要在這些按鈕上設定一些屬性, 以控制按鈕的外觀和版面配置。 您不需要個別設定按鈕的屬性, 而是使用資源來定義整個應用程式的按鈕屬性。 應用程式資源在概念上類似于 Web 網頁的外部階層式樣式表 (CSS);不過, 資源比階層式樣式表 (CSS) 更強大, 因為您會在本逐步解說的結尾看到此內容。 若要深入瞭解資源, 請參閱[XAML 資源](../advanced/xaml-resources.md)。

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>若要使用樣式來設定按鈕的基本屬性

1. **定義應用程式 .Resources 區塊:** 開啟 app.xaml, 並新增下列反白顯示的標記 (如果尚未存在):

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

     資源範圍取決於您定義資源的位置。 在應用程式`Application.Resources`中定義中的資源。 xaml 檔案可讓您從應用程式中的任何位置使用資源。 若要深入瞭解如何定義資源的範圍, 請參閱[XAML 資源](../advanced/xaml-resources.md)。

2. **建立樣式, 並使用它定義基本的屬性值:** 將下列標記新增至`Application.Resources`區塊。 此標記會建立<xref:System.Windows.Style>一個, 其適用于應用程式中的所有按鈕<xref:System.Windows.FrameworkElement.Width%2A> , 並將<xref:System.Windows.FrameworkElement.Margin%2A>按鈕的設定為 90, 並將設為 10:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     屬性會指定該樣式套用至類型<xref:System.Windows.Controls.Button>的所有物件。 <xref:System.Windows.Style.TargetType%2A> 每<xref:System.Windows.Setter>個都會<xref:System.Windows.Style>為設定不同的屬性值。 因此, 在此時, 應用程式中的每個按鈕寬度為 90, 邊界為10。  如果您按 F5 執行應用程式, 您會看到下列視窗。

     ![寬度為90且邊界為10的按鈕](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     您可以使用樣式來執行更多動作, 包括微調目標物件的各種方式、指定複雜的屬性值, 甚至使用樣式做為其他樣式的輸入。 如需詳細資訊，請參閱 [設定樣式和範本](styling-and-templating.md)。

3. **將樣式屬性值設定為資源:** 資源可讓您以簡單的方式重複使用常用定義的物件和值。 使用資源來定義複雜的值, 讓您的程式碼更模組化是特別有用。 將下列反白顯示的標記新增至 app.xaml。

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

     在區塊的`Application.Resources`正下方, 您已建立名為 "GrayBlueGradientBrush" 的資源。 此資源會定義水準漸層。 此資源可用來做為應用程式中任何位置的屬性值, 包括<xref:System.Windows.Controls.Control.Background%2A>屬性的按鈕樣式 setter 內部。 現在, 所有按鈕都具有<xref:System.Windows.Controls.Control.Background%2A>此漸層的屬性值。

     按 F5 執行應用程式。 看起來應該如下所示。

     ![具有漸層背景的按鈕](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>建立定義按鈕外觀的範本

在本節中, 您會建立範本, 以自訂按鈕的外觀 (呈現)。 按鈕呈現是由數個物件所組成, 包括矩形和其他元件, 讓按鈕具有獨特的外觀。

到目前為止, 控制項按鈕在應用程式中的顯示方式, 已局限于變更按鈕的屬性。 如果您想要對按鈕的外觀進行更多的變更, 該怎麼做？ 範本可讓您強大控制物件的呈現。 因為範本可以在樣式內使用, 所以您可以將範本套用至樣式適用的所有物件 (在此逐步解說中為按鈕)。

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>若要使用範本來定義按鈕的外觀

1. **設定範本:** 因為的控制項<xref:System.Windows.Controls.Button> (如<xref:System.Windows.Controls.Control.Template%2A> ) 具有屬性, 所以您可以定義樣板屬性值, 就像<xref:System.Windows.Style>我們在中使用所<xref:System.Windows.Setter>設定的其他屬性值一樣。 將下列反白顯示的標記新增至您的按鈕樣式。

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

2. **改變按鈕呈現方式:** 此時, 您必須定義範本。 新增下列反白顯示的標記。 此標記會指定<xref:System.Windows.Shapes.Rectangle>兩個具有圓角的元素, <xref:System.Windows.Controls.DockPanel>後面接著。 是用來<xref:System.Windows.Controls.ContentPresenter>裝載按鈕的。 <xref:System.Windows.Controls.DockPanel> 會<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。 在本逐步解說中, 內容是文字 ("Button 1", "Button 2", "Button 3")。 所有範本元件 (矩形和<xref:System.Windows.Controls.DockPanel>) 都是在內<xref:System.Windows.Controls.Grid>配置。

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

     按 F5 執行應用程式。 看起來應該如下所示。

     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")

3. **將 glasseffect 新增至範本:** 接下來, 您會加入玻璃。 首先, 您要建立一些資源來建立半透明漸層效果。 將這些漸層資源新增至`Application.Resources`區塊內的任何位置:

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

     這些資源會當做矩形的<xref:System.Windows.Shapes.Shape.Fill%2A>使用, 我們會將其插入<xref:System.Windows.Controls.Grid>按鈕範本的。 將下列反白顯示的標記新增至範本。

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

     請注意, `x:Name`屬性為 "glassCube" 的矩形的為 0, 因此當您執行範例時, 您看不到在上方重迭的玻璃矩形。 <xref:System.Windows.UIElement.Opacity%2A> 這是因為我們稍後會將觸發程式新增至範本, 以供使用者與按鈕互動時使用。 不過, 您現在可以藉由將<xref:System.Windows.UIElement.Opacity%2A>值變更為1並執行應用程式, 來查看按鈕的外觀。 請參閱下圖。 繼續進行下一個步驟之前, 請將<xref:System.Windows.UIElement.Opacity%2A>變更回0。

     ![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>建立按鈕互動性

在本節中, 您將建立屬性觸發程式和事件觸發程式來變更屬性值和執行動畫, 以回應使用者動作, 例如將滑鼠指標移至按鈕上, 然後按一下。

新增互動性 (滑鼠停留、滑鼠離開、按一下等等) 的簡單方式, 是在您的範本或樣式內定義觸發程式。 若要建立<xref:System.Windows.Trigger>, 您可以定義屬性「條件」, 例如:按鈕<xref:System.Windows.UIElement.IsMouseOver%2A>屬性值`true`等於。 接著, 您可以定義在觸發條件為 true 時所發生的 setter (動作)。

### <a name="to-create-button-interactivity"></a>建立按鈕互動性

1. **新增範本觸發程式:** 將反白顯示的標記新增至您的範本。

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

2. **新增屬性觸發程式:** 將反白顯示的標記`ControlTemplate.Triggers`新增至區塊:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     按 F5 鍵執行應用程式, 並在您執行滑鼠指標停留在按鈕上時查看效果。

3. **新增焦點觸發程式:** 接下來, 我們將新增一些類似的 setter, 以處理按鈕有焦點時的情況 (例如, 在使用者按一下之後)。

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

     按 F5 執行應用程式, 然後按一下其中一個按鈕。 請注意, 當您按一下按鈕時, 它仍會反白顯示, 因為它仍然具有焦點。 如果您按一下另一個按鈕, [新增] 按鈕會取得焦點, 而最後一項則會失去焦點。

4. **新增**<xref:System.Windows.UIElement.MouseEnter>和的<xref:System.Windows.UIElement.MouseLeave>動畫 **:**  接下來, 我們會將一些動畫新增至觸發程式。 在`ControlTemplate.Triggers`區塊內的任何位置新增下列標記。

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

     當滑鼠指標移至按鈕上方時, 半透明矩形會縮小, 並在指標離開時返回正常大小。

     當指標移至按鈕上方時, 會觸發兩個動畫 (<xref:System.Windows.UIElement.MouseEnter>引發事件)。 這些動畫會沿著 X 和 Y 軸縮小半透明矩形的範圍。 請注意<xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>元素上的屬性,以及。<xref:System.Windows.Media.Animation.Timeline.Duration%2A> 會指定動畫出現在半秒的時間, 並<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>指定玻璃縮小 10%。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>

     第二個事件觸發<xref:System.Windows.UIElement.MouseLeave>程式 () 只會停止第一個。 當您停止<xref:System.Windows.Media.Animation.Storyboard>時, 所有動畫屬性都會回到其預設值。 因此, 當使用者將指標移開按鈕時, 按鈕會回到滑鼠指標移至按鈕上方的方式。 如需動畫的詳細資訊, 請參閱[動畫總覽](../graphics-multimedia/animation-overview.md)。

5. **在按一下按鈕時新增動畫:** 最後一個步驟是在使用者按一下按鈕時新增的觸發程式。 在`ControlTemplate.Triggers`區塊內的任何位置新增下列標記:

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

     按 F5 執行應用程式, 然後按一下其中一個按鈕。 當您按一下按鈕時, 半透明矩形就會旋轉。

## <a name="summary"></a>總結
 在此逐步解說中, 您已執行下列練習:

- 將目標設為物件類型 (<xref:System.Windows.Controls.Button>)。 <xref:System.Windows.Style>

- 使用, <xref:System.Windows.Style>在整個應用程式中控制按鈕的基本屬性。

- 建立用來做為<xref:System.Windows.Style> setter 屬性值的資源, 例如漸層。

- 藉由將範本套用至按鈕, 自訂整個應用程式中的按鈕外觀。

- 回應包含動畫效果的使用者動作 (例如<xref:System.Windows.UIElement.MouseEnter>、 <xref:System.Windows.UIElement.MouseLeave>和<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) 之按鈕的自訂行為。

## <a name="see-also"></a>另請參閱

- [使用 Microsoft Expression Blend 建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [樣式設定和範本化](styling-and-templating.md)
- [動畫概觀](../graphics-multimedia/animation-overview.md)
- [使用純色和漸層繪製的概觀](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [點陣圖效果概觀](../graphics-multimedia/bitmap-effects-overview.md)
