---
title: 逐步解說：使用 XAML 建立按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 6d41d0894aa85f342deafb77434771b2c89e4150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557988"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>逐步解說：使用 XAML 建立按鈕
本逐步解說的目標是了解如何在 Windows Presentation Foundation (WPF) 應用程式中建立的動畫的按鈕，供使用。 本逐步解說會使用樣式和範本建立自訂的按鈕的資源，讓重複使用程式碼，以及從按鈕宣告按鈕邏輯分離。 這個逐步解說完全在撰寫[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
> [!IMPORTANT]
>  本逐步解說會引導您逐步完成建立應用程式，輸入或複製並貼上[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Microsoft Visual Studio。 如果您想要了解如何使用設計工具 (Microsoft Expression Blend) 來建立相同的應用程式，請參閱[建立按鈕所使用的 Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。  
  
 下圖顯示已完成的按鈕。  
  
 ![使用 XAML 所建立的自訂按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>建立基本按鈕  
 讓我們開始建立新的專案，並將數個按鈕加入至視窗。  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>若要建立新的 WPF 專案，並加入視窗 按鈕  
  
1.  啟動 Visual Studio。  
  
2.  **建立新的 WPF 專案：** 上**檔案**功能表上，指向**新增**，然後按一下 **專案**。 尋找**Windows 應用程式 (WPF)** 範本和名稱"AnimatedButton"的專案。 這會建立應用程式的基本架構。  
  
3.  **新增基本的預設按鈕：** 範本會提供本逐步解說所需的所有檔案。 按兩下 [方案總管] 中開啟 Window1.xaml 檔案。 根據預設，沒有<xref:System.Windows.Controls.Grid>Window1.xaml 中的項目。 移除<xref:System.Windows.Controls.Grid>元素並加入一些按鈕，[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]輸入或複製並貼上下列反白顯示的程式碼，以 Window1.xaml 頁面：  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     按 F5 執行應用程式。您應該會看到一組按鈕，看起來像下圖。  
  
     ![三個基本按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     現在您已經建立基本的按鈕，就完成 Window1.xaml 檔案中的工作。 逐步解說的其餘部分著重在 app.xaml 檔案，定義樣式和範本的按鈕。  
  
## <a name="set-basic-properties"></a>設定基本內容  
 接下來，讓我們在這些按鈕，以控制按鈕的外觀和版面配置上設定某些屬性。 而不是個別按鈕上設定屬性，您會使用資源來定義整個應用程式的按鈕內容。 應用程式資源在概念上類似外部[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]網頁; 不過，資源會比功能更為強大[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]，如可以看到依本逐步解說的結尾。 若要深入了解資源，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>若要使用樣式設定按鈕上的基本內容  
  
1.  **定義 Application.Resources 區塊：** 開啟 app.xaml 並加入下列反白顯示的標記，如果它已經不存在：  
  
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
  
     資源範圍取決於您用來定義資源。 定義中的資源`Application.Resources`app.xaml 檔案可讓要從任何地方使用應用程式的資源。 若要深入了解定義資源的範圍，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
2.  **建立樣式，並定義與它的基本屬性值：** 加入下列標記以`Application.Resources`區塊。 這個標記會建立<xref:System.Windows.Style>可套用至應用程式設定中的所有按鈕<xref:System.Windows.FrameworkElement.Width%2A>為 90 的按鈕和<xref:System.Windows.FrameworkElement.Margin%2A>為 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A>屬性會指定樣式套用至類型的所有物件<xref:System.Windows.Controls.Button>。 每個<xref:System.Windows.Setter>設定不同的屬性值，如<xref:System.Windows.Style>。 因此，此時應用程式中的每個按鈕有寬度為 90 且邊界為 10。  如果您按 F5 執行應用程式，您會看到下列視窗。  
  
     ![按鈕的寬度為 90 且邊界為 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     還有更多您可以使用樣式，包括各種微調哪些物件為目標的方法、 指定複雜的屬性值，以及其他樣式甚至使用做為輸入的樣式。 如需詳細資訊，請參閱 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
3.  **樣式屬性值設定為資源：** 資源可讓重複使用一般定義的物件和值的簡單方法。 它特別適合用於定義複雜的值使用，讓程式碼更模組化的資源。 App.xaml 中加入下列反白顯示的標記。  
  
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
  
     直接在`Application.Resources`區塊中，建立稱為 「 GrayBlueGradientBrush"的資源。 此資源定義水平漸層。 這項資源可用來當做屬性值從任何地方在應用程式，包括內部的按鈕樣式 setter<xref:System.Windows.Controls.Control.Background%2A>屬性。 現在，所有的按鈕有<xref:System.Windows.Controls.Control.Background%2A>這個漸層的屬性值。  
  
     按 F5 執行應用程式。 它看起來應該如下所示。  
  
     ![使用漸層背景的按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>建立範本會定義按鈕的外觀  
 在本節中，您可以建立自訂按鈕的外觀 (presentation) 的範本。 呈現的按鈕所組成的數個物件，包括矩形和其他元件，讓按鈕獨特的外觀。  
  
 若要變更按鈕的屬性到目前為止，只有透過控制按鈕的應用程式中的外觀。 如果您要變更多字根按鈕的外觀？ 範本可讓物件的簡報功能強大的控制。 因為樣式內，就可以使用範本，您可以套用範本樣式會套用到 （在此逐步解說中，按鈕） 的所有物件。  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>若要使用範本來定義按鈕的外觀  
  
1.  **設定範本：** 因為控制項喜歡<xref:System.Windows.Controls.Button>有<xref:System.Windows.Controls.Control.Template%2A>屬性，您可以定義範本的屬性值，就像其他我們已在中設定的屬性值一樣<xref:System.Windows.Style>使用<xref:System.Windows.Setter>。 將下列反白顯示的標記加入至按鈕樣式。  
  
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
  
2.  **Alter 按鈕簡報：** 此時，您需要定義範本。 加入下列反白顯示的標記。 這個標記可以指定兩個<xref:System.Windows.Shapes.Rectangle>具有圓角邊緣、 項目後面<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Controls.DockPanel>用來裝載<xref:System.Windows.Controls.ContentPresenter> 按鈕。 A<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。 本逐步解說的內容是文字 （"按鈕 1 」、 「 按鈕 2 」、 「 按鈕 3 」）。 所有範本元件 (矩形和<xref:System.Windows.Controls.DockPanel>) 內的配置<xref:System.Windows.Controls.Grid>。  
  
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
  
     按 F5 執行應用程式。 它看起來應該如下所示。  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **新增至範本 glasseffect:** 接下來您將加入玻璃。 首先，您會建立一些建立透明漸層效果的資源。 漸層停駐將這些資源加入任何位置內`Application.Resources`區塊：  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     這些資源用做為<xref:System.Windows.Shapes.Shape.Fill%2A>我們插入矩形<xref:System.Windows.Controls.Grid>的 button 範本。 將下列反白顯示的標記加入至範本。  
  
    ```  
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
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     請注意，<xref:System.Windows.UIElement.Opacity%2A>與矩形的`x:Name`"glassCube 」 屬性為 0，因此當您執行範例時，看不到最上層顯示重疊的玻璃矩形。 這是因為我們將稍後加入觸發程序的範本使用者互動的按鈕時。 不過，您可以看到按鈕的外觀現在藉由變更<xref:System.Windows.UIElement.Opacity%2A>1 並執行應用程式的值。 請參閱下圖。 下一個步驟之前，變更<xref:System.Windows.UIElement.Opacity%2A>為 0。  
  
     ![使用 XAML 所建立的自訂按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>建立按鈕互動性  
 在本節中，您將建立屬性觸發程序和事件觸發程序來變更屬性值，以回應使用者動作，例如移動滑鼠指標停留在按鈕，然後按一下執行動畫。  
  
 加入互動功能 （滑鼠停留、 滑鼠離開，按一下，等等） 的簡單方法是定義您的範本或樣式的觸發程序。 若要建立<xref:System.Windows.Trigger>，例如將 「 條件 」 屬性定義： 按鈕<xref:System.Windows.UIElement.IsMouseOver%2A>屬性值等於`true`。 接著，您會定義觸發程序條件為 true 時，會發生的 setter （動作）。  
  
#### <a name="to-create-button-interactivity"></a>若要建立按鈕互動性  
  
1.  **新增範本觸發程序：** 將反白顯示的標記加入至您的範本。  
  
    ```  
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
  
2.  **加入屬性觸發程序：** 新增的反白顯示的標記`ControlTemplate.Triggers`區塊：  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     按 F5 執行應用程式，並查看其效果的按鈕執行滑鼠指標。  
  
3.  **將焦點觸發程序：** 接下來，我們要在其中加入一些類似的 setter，以處理的情況時 （例如，在使用者按一下它之後） 的焦點按鈕的。  
  
    ```  
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
  
     按 F5 執行應用程式，然後按一下其中一個按鈕。 請注意，按鈕會維持反白顯示之後，按一下因為仍有焦點。 如果您按一下另一個按鈕時，[新增] 按鈕時的最後一個失去它，就會取得焦點。  
  
4.  **加入表示**<xref:System.Windows.UIElement.MouseEnter> **和** <xref:System.Windows.UIElement.MouseLeave> **:** 接下來我們將某些動畫加入至觸發程序。 加入下列任何位置內的標記`ControlTemplate.Triggers`區塊。  
  
    ```  
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
  
     當滑鼠指標移到按鈕上方，並傳回回一般的大小，當指標離開時，會縮小玻璃矩形。  
  
     有兩個動畫，當滑鼠指標變成按鈕上方時觸發 (<xref:System.Windows.UIElement.MouseEnter>引發)。 這些動畫壓縮玻璃矩形 X 和 Y 軸。 注意到屬性<xref:System.Windows.Media.Animation.DoubleAnimation>項目-<xref:System.Windows.Media.Animation.Timeline.Duration%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定動畫發生超過半秒，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>指定玻璃壓縮 10%。  
  
     第二個事件觸發程序 (<xref:System.Windows.UIElement.MouseLeave>) 只會停止的第一個。 當您停止<xref:System.Windows.Media.Animation.Storyboard>，所有動畫的屬性會傳回成為其預設值。 因此，當使用者移出按鈕的指標，按鈕回到前滑鼠指標移至按鈕上方的方式。 如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
5.  **加入按一下按鈕時的動畫：** 最後一個步驟是加入當使用者按一下按鈕的觸發程序。 加入下列任何位置內的標記`ControlTemplate.Triggers`區塊：  
  
    ```  
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
  
     按 F5 執行應用程式，然後按一下其中一個按鈕。 當您按一下按鈕時，玻璃矩形會旋轉。  
  
## <a name="summary"></a>總結  
 在本逐步解說，您可以執行下列練習：  
  
-   目標<xref:System.Windows.Style>至物件類型 (<xref:System.Windows.Controls.Button>)。  
  
-   控制整個應用程式使用中按鈕的基本內容<xref:System.Windows.Style>。  
  
-   建立資源，例如要用於屬性值的漸層<xref:System.Windows.Style>setter。  
  
-   將範本套用至按鈕，以自訂整個應用程式中的按鈕外觀。  
  
-   自訂的按鈕，以回應使用者動作的行為 (例如<xref:System.Windows.UIElement.MouseEnter>， <xref:System.Windows.UIElement.MouseLeave>，和<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) 包含的動畫效果。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Microsoft Expression Blend 建立按鈕](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [點陣圖效果概觀](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
