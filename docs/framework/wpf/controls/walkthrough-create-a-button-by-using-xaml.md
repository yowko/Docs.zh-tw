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
# <a name="walkthrough-create-a-button-by-using-xaml"></a>逐步解說：使用 XAML 建立按鈕

本演練的目的是瞭解如何創建用於 Windows 演示文稿基礎 (WPF) 應用程式的動畫按鈕。 本演練使用樣式和範本創建自定義按鈕資源,允許重用代碼並將按鈕邏輯與按鈕聲明分離。 這個演練完全寫在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中 。

> [!IMPORTANT]
> 本演練將指導您完成通過鍵入或複製並貼上[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Visual Studio 來創建應用程式的步驟。 如果您希望瞭解如何使用設計器建立相同的應用程式,請參閱[使用 Microsoft 運算式混合建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。

下圖顯示了已完成的按鈕。

![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>建立基本按鈕

讓我們從創建新專案並向視窗添加幾個按鈕開始。

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>建立新的 WPF 專案將按鈕新增到視窗

1. 啟動 Visual Studio。

2. **建立新的 WPF 專案:** 在 **「檔」** 選單上,指向 **"新建**",然後按一下「**專案**」。 尋找**Windows 應用程式 (WPF)** 樣本並將專案命名為「動畫按鈕」。 這將為應用程式創建骨架。

3. **新增基本預設按鈕:** 本演練所需的所有檔都由範本提供。 通過在解決方案資源管理器中按兩下 Window1.xaml 檔案來打開該檔。 默認情況下,Window1.xaml 中存在一<xref:System.Windows.Controls.Grid>個 元素。 以鍵入<xref:System.Windows.Controls.Grid>或複製並將以下突出顯示的代碼貼上[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Window1.xaml,刪除元素並將幾個按鈕新增到頁面:

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

     按 F5 運行應用程式;您應該會看到一組按鈕,如下所示。

     ![三個基本按鈕](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     現在,您已經創建了基本按鈕,您已完成在 Window1.xaml 檔中的工作。 演練的其餘部分將側重於 app.xaml 檔,定義樣式和按鈕的範本。

## <a name="set-basic-properties"></a>設定基本屬性

接下來,讓我們在這些按鈕上設置一些屬性,以控制按鈕的外觀和佈局。 您將使用資源為整個應用程式定義按鈕屬性,而不是單獨設置按鈕上的屬性。 應用程式資源在概念上類似於網頁的外部級聯樣式表 (CSS);但是,資源比級聯樣式表 (CSS) 更強大,正如在本演練結束時看到的。 要瞭解有關資源的更多資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>使用樣式在按鈕上設定基本屬性

1. **定義應用程式.資源區塊:** 開啟 app.xaml 並新增以下突出顯示的標記(如果尚未出現):

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

     資源範圍由定義資源的位置確定。 在 app.xaml`Application.Resources`檔中定義資源,可以從應用程式中的任何位置使用資源。 要瞭解有關定義資源範圍的更多資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

2. **建立樣式並使用它定義基本屬性值:** 將以下標記加入區塊中`Application.Resources`。 此標記建立<xref:System.Windows.Style>應用於應用程式中的所有按鈕,將按鈕設定為 90,將<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Margin%2A>設定為 10:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     屬性<xref:System.Windows.Style.TargetType%2A>指定樣式應用於<xref:System.Windows.Controls.Button>類型的所有物件。 每個<xref:System.Windows.Setter>設置 不同的屬性值<xref:System.Windows.Style>。 因此,此時應用程式中的每個按鈕的寬度為 90,邊距為 10。  如果按 F5 執行應用程式,您將看到以下視窗。

     ![寬度為 90 且邊界為 10 的按鈕](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     可以使用樣式執行更多操作,包括調整目標物件、指定複雜屬性值,甚至使用樣式作為其他樣式的輸入的各種方法。 有關詳細資訊,請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。

3. **將樣式屬性值設定為資源:** 資源支援一種簡單方法來重用通常定義的物件和值。 使用資源定義複雜值以使代碼更加模組化尤其有用。 將以下突出顯示的標記添加到 app.xaml。

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

     直接在`Application.Resources`塊下,您創建了一個名為"灰藍漸變畫筆"的資源。 此資源定義水準漸變。 此資源可以從應用程式的任何位置用作屬性值,包括在<xref:System.Windows.Controls.Control.Background%2A>屬性的按鈕樣式設置器內。 現在,所有按鈕都有此漸變<xref:System.Windows.Controls.Control.Background%2A>的屬性值。

     按 F5 執行應用程式。 它應該如下所示。

     ![具有漸層背景的按鈕](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>建立定義按鈕外觀的樣本

在本節中,您將創建一個範本,用於自定義按鈕的外觀(表示)。 按鈕表示由多個物件組成,包括矩形和其他元件,使按鈕的外觀獨一無二。

到目前為止,對按鈕在應用程式中的外觀的控制僅限於更改按鈕的屬性。 如果你想對按鈕的外觀進行更徹底的更改,該怎麼辦? 範本能夠對物件的表示進行強大的控制。 由於範本可以在樣式中使用,因此可以將範本應用於樣式應用於的所有物件(在本演練中,按鈕)。

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>使用樣本定義按鈕的外觀

1. **設定樣本:** 由於控制項(<xref:System.Windows.Controls.Button>如<xref:System.Windows.Controls.Control.Template%2A>具有 屬性)可以定義樣本屬性值,就像<xref:System.Windows.Style>我們使用 中設置的其他屬性<xref:System.Windows.Setter>值一樣。 將以下突出顯示的標記添加到按鈕樣式中。

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

2. **變更按鈕簡報文件:** 此時,您需要定義範本。 添加以下突出顯示的標記。 這個標記指定兩<xref:System.Windows.Shapes.Rectangle>個圓邊元素,後跟<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Controls.DockPanel>承載按鍵<xref:System.Windows.Controls.ContentPresenter>的 。 顯示<xref:System.Windows.Controls.ContentPresenter>按鈕的內容。 在本演練中,內容是文本("按鈕 1","按鈕 2","按鈕 3")。 所有範本元件(矩形和<xref:System.Windows.Controls.DockPanel>) 都位於的<xref:System.Windows.Controls.Grid>內部。

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

     按 F5 執行應用程式。 它應該如下所示。

     ![帶 3 個按鈕的視窗](./media/custom-button-animatedbutton-4.gif)

3. **加入樣本加入玻璃效果:** 接下來,您將添加玻璃。 首先,創建一些創建玻璃漸變效果的資源。 在`Application.Resources`區塊內的任何位置新增這些漸層來源:

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

     這些資源用作<xref:System.Windows.Shapes.Shape.Fill%2A>我們插入到按鈕範<xref:System.Windows.Controls.Grid>本 中的矩形。 向範本添加以下突出顯示的標記。

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

     請注意,<xref:System.Windows.UIElement.Opacity%2A>具有"glassCube"`x:Name`屬性的矩形為 0,因此當您運行範例時,您看不到覆蓋在頂部的玻璃矩形。 這是因為我們稍後將向範本添加觸發器,用於使用者與按鈕互動時。 但是,通過將<xref:System.Windows.UIElement.Opacity%2A>值更改為 1 並運行應用程式,您可以看到按鈕現在的外觀。 請參閱下圖。 在繼續下一步之前,將<xref:System.Windows.UIElement.Opacity%2A>返回更改為 0。

     ![使用 XAML 建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>建立按鈕互動性

在本節中,您將創建屬性觸發器和事件觸發器以更改屬性值並運行動畫以回應使用者操作,例如將滑鼠指標移到按鈕上並按一下。

添加互動性(滑鼠懸停、滑鼠離開、按一下等)的一種簡單方法是在範本或樣式中定義觸發器。 要建立<xref:System.Windows.Trigger>,定義屬性「條件」,例如:<xref:System.Windows.UIElement.IsMouseOver%2A>按鈕 屬性值`true`等於 。 然後定義在觸發條件為 true 時發生的設置器(操作)。

### <a name="to-create-button-interactivity"></a>建立按鈕互動性

1. **新增樣本觸發器:** 將突出顯示的標記添加到範本中。

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

2. **新增屬性觸發器:** 將突顯的標記加入區`ControlTemplate.Triggers`塊:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     按 F5 以執行應用程式,並在在按鈕上運行滑鼠指標時看到效果。

3. **新增焦點觸發器:** 接下來,我們將添加一些類似的設置器來處理按鈕具有焦點時(例如,在用戶按一下按鈕後)的情況。

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

     按 F5 運行應用程式,然後按一個按鈕。 請注意,按一下該按鈕后,該按鈕將保持突出顯示,因為它仍有焦點。 如果按一下按鈕,則新按鈕在上次按鈕丟失時獲得焦點。

4. **為**<xref:System.Windows.UIElement.MouseEnter>**and**和<xref:System.Windows.UIElement.MouseLeave>添加動畫 **:** 接下來,我們將一些動畫添加到觸發器中。   在`ControlTemplate.Triggers`塊內的任意位置添加以下標記。

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

     當滑鼠指標在按鈕上移動時,玻璃矩形將縮小,當指標離開時返回正常大小。

     指標超過按鈕時將觸發兩個動畫(<xref:System.Windows.UIElement.MouseEnter>引發事件)。 這些動畫沿 X 軸和 Y 軸收縮玻璃矩形。 請注意<xref:System.Windows.Media.Animation.DoubleAnimation>元素<xref:System.Windows.Media.Animation.Timeline.Duration%2A>與與上的<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性 。 指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫在半秒以上發生,<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>並指定玻璃收縮 10%。

     第二個事件觸發器<xref:System.Windows.UIElement.MouseLeave>( ) 只是停止第一個事件觸發器。 停止 時<xref:System.Windows.Media.Animation.Storyboard>, 所有動畫屬性將返回到其預設值。 因此,當使用者將指標移出按鈕時,該按鈕將回到滑鼠指標移到按鈕之前的方式。 有關動畫的詳細資訊,請參閱[動畫概述](../graphics-multimedia/animation-overview.md)。

5. **新增按下按鈕時的動畫:** 最後一步是添加用戶按一下按鈕時的觸發器。 在`ControlTemplate.Triggers`區塊的任何位置加入以下標記:

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

     按 F5 運行應用程式,然後按一個按鈕。 按下按鈕時,玻璃矩形會旋轉。

## <a name="summary"></a>摘要
 在本演練中,您執行以下練習:

- 將<xref:System.Windows.Style>目標物件型<xref:System.Windows.Controls.Button>態 ( 。

- 使用 控制整個應用程式中按鈕的基本<xref:System.Windows.Style>屬性 。

- 建立的資源(如漸變)用於<xref:System.Windows.Style>設置器的屬性值。

- 通過將範本應用於按鈕,自定義整個應用程式中的按鈕外觀。

- 按鈕的自定義行為,以回應包含動畫效果的使用者操作(如<xref:System.Windows.UIElement.MouseEnter><xref:System.Windows.UIElement.MouseLeave>、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>和)。

## <a name="see-also"></a>另請參閱

- [使用 Microsoft Expression Blend 建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [動畫概觀](../graphics-multimedia/animation-overview.md)
- [使用純色和漸層繪製的概觀](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [點陣圖效果概觀](../graphics-multimedia/bitmap-effects-overview.md)
