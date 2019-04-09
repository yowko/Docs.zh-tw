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
# <a name="walkthrough-create-a-button-by-using-xaml"></a>逐步解說：使用 XAML 建立按鈕
本逐步解說的目的是要了解如何在 Windows Presentation Foundation (WPF) 應用程式中建立動畫的按鈕，供使用。 本逐步解說會使用樣式和範本來建立自訂的按鈕資源可讓您重複使用程式碼及從按鈕宣告按鈕的邏輯分隔開來。 本逐步解說完全在撰寫[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
> [!IMPORTANT]
>  本逐步解說會引導您完成建立應用程式，輸入或複製並貼上步驟[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Microsoft Visual Studio。 如果您想要了解如何使用設計工具 (Microsoft Expression Blend) 來建立相同的應用程式，請參閱[建立使用 Microsoft Expression Blend 按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。  
  
 下圖顯示 [完成] 按鈕。  
  
 ![使用 XAML 所建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>建立基本的按鈕  
 讓我們開始建立新的專案，並將幾個按鈕加入至視窗。  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>若要建立新的 WPF 專案，並將按鈕加入至視窗  
  
1.  啟動 Visual Studio。  
  
2.  **建立新的 WPF 專案：** 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。 尋找**Windows 應用程式 (WPF)** 範本並將專案命名為"AnimatedButton 」。 這會建立應用程式的基本架構。  
  
3.  **新增基本的預設按鈕：** 範本會提供本逐步解說所需的所有檔案。 按一下方案總管 中按兩下，開啟 Window1.xaml 檔案。 根據預設，沒有<xref:System.Windows.Controls.Grid>Window1.xaml 中的項目。 移除<xref:System.Windows.Controls.Grid>項目並將幾個按鈕加入[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]式輸入或複製並貼上下列反白顯示的程式碼，以 Window1.xaml 頁面：  
  
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
  
     按 f5 鍵執行應用程式。您應該會看到一組看起來像下圖的按鈕。  
  
     ![三個基本按鈕](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     既然您已建立基本的按鈕，您已完成在 Window1.xaml 檔案中工作。 本逐步解說的其餘部分著重於 app.xaml 檔案中，定義樣式和範本的按鈕。  
  
## <a name="set-basic-properties"></a>設定基本的屬性  
 接下來，讓我們在這些按鈕，以控制按鈕的外觀和版面配置上設定一些屬性。 而不是個別按鈕上設定屬性，您會使用資源來定義整個應用程式的按鈕屬性。 應用程式資源是在概念上類似於外部[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]網頁中; 不過，資源會比功能更強大[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]，如本逐步解說結束時，您會看到。 若要深入了解資源，請參閱[XAML 資源](../advanced/xaml-resources.md)。  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>若要使用樣式設定按鈕上的基本內容  
  
1.  **定義 Application.Resources 區塊：** 開啟 app.xaml，並新增下列醒目提示的標記，如果它已經不存在：  
  
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
  
     資源範圍取決於您用來定義資源。 定義中的資源`Application.Resources`在 app.xaml 檔案可讓用於從任何位置的應用程式中的資源。 若要深入了解定義您資源的範圍，請參閱[XAML 資源](../advanced/xaml-resources.md)。  
  
2.  **建立樣式，並定義與它的基本屬性值：** 新增下列標記來`Application.Resources`區塊。 此標記會建立<xref:System.Windows.Style>套用至的應用程式設定中的所有按鈕<xref:System.Windows.FrameworkElement.Width%2A>的按鈕為 90，<xref:System.Windows.FrameworkElement.Margin%2A>為 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A>屬性會指定這個樣式會套用至類型的所有物件<xref:System.Windows.Controls.Button>。 每個<xref:System.Windows.Setter>設定為不同的屬性值<xref:System.Windows.Style>。 因此，此時應用程式中的每個按鈕有寬度為 90 且邊界為 10。  如果您按 F5 執行應用程式時，您會看到下列視窗。  
  
     ![按鈕寬度為 90 且邊界為 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     還有更多您可以利用樣式，包括各種不同的微調哪些物件為目標的方法，指定複雜的屬性值，以及其他樣式即使使用做為輸入的樣式。 如需詳細資訊，請參閱 [設定樣式和範本](styling-and-templating.md)。  
  
3.  **樣式屬性值設定為資源：** 資源可讓重複使用一般定義的物件和值的簡單方法。 它是特別有用來定義複雜的值，讓程式碼更模組化中使用的資源。 App.xaml 中加入下列反白顯示的標記。  
  
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
  
     正下方`Application.Resources`區塊中，建立名為"GrayBlueGradientBrush 」 的資源。 此資源會定義水平漸層。 這項資源可用來當做屬性值從任何地方的應用程式，包括內的按鈕樣式 setter<xref:System.Windows.Controls.Control.Background%2A>屬性。 現在，所有的按鈕有<xref:System.Windows.Controls.Control.Background%2A>此漸層的屬性值。  
  
     按 F5 執行應用程式。 它看起來應該如下所示。  
  
     ![使用漸層背景的按鈕](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>建立範本定義按鈕的外觀  
 在本節中，您可以建立自訂按鈕的外觀 (presentation) 的範本。 呈現的按鈕是組成包括矩形和其他元件的數個物件來為按鈕提供獨特的外觀。  
  
 到目前為止，在應用程式中的按鈕外觀的控制項具有已侷限於變更按鈕的屬性。 如果您想要對按鈕外觀進行更巨大的變動嗎？ 範本可讓物件的簡報功能強大的控制。 樣式內，就可以使用範本，因為您可以套用範本樣式會套用到 （在此逐步解說中，按鈕） 的所有物件。  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>若要使用的範本定義按鈕的外觀  
  
1.  **將範本設定：** 因為控制項，例如<xref:System.Windows.Controls.Button>有<xref:System.Windows.Controls.Control.Template%2A>屬性，您可以定義範本的屬性值，就像我們已在中設定的其他屬性值一樣<xref:System.Windows.Style>使用<xref:System.Windows.Setter>。 按鈕樣式中加入下列反白顯示的標記。  
  
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
  
2.  **Alter 按鈕簡報：** 此時，您需要定義範本。 新增下列醒目提示的標記。 此標記會指定兩個<xref:System.Windows.Shapes.Rectangle>具有圓角邊緣、 項目後面<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Controls.DockPanel>用來裝載<xref:System.Windows.Controls.ContentPresenter>的按鈕。 A<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。 在本逐步解說中，內容會是文字 （"按鈕 1 」、 「 按鈕 2 」、 「 按鈕 3 」）。 所有範本的元件 (矩形， <xref:System.Windows.Controls.DockPanel>) 內的配置<xref:System.Windows.Controls.Grid>。  
  
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
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **將 glasseffect 新增到範本：** 接下來您要加入半透明效果。 首先，您會建立一些建立透明的漸層效果的資源。 漸層停駐將這些資源加入任何位置內`Application.Resources`區塊：  
  
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
  
     這些資源用做<xref:System.Windows.Shapes.Shape.Fill%2A>我們插入矩形<xref:System.Windows.Controls.Grid>的 [按鈕] 範本。 將下列反白顯示的標記加入至範本。  
  
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
  
     請注意，<xref:System.Windows.UIElement.Opacity%2A>與矩形的`x:Name`"glassCube 」 屬性為 0，因此當您執行範例時，您看不見玻璃矩形頂端上重疊。 這是因為我們稍後會將加入觸發程序的範本的使用者互動的按鈕時。 不過，您可以在其中看到按鈕的外觀如下現在藉由變更<xref:System.Windows.UIElement.Opacity%2A>1 」 和執行應用程式的值。 請參閱下圖。 在繼續之前的下一個步驟，變更<xref:System.Windows.UIElement.Opacity%2A>為 0。  
  
     ![使用 XAML 所建立的自訂按鈕](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>建立按鈕互動性  
 在本節中，您將建立屬性觸發程序和事件觸發程序來變更屬性值，執行動畫，以回應使用者動作，例如將滑鼠指標移到按鈕上方，然後按一下。  
  
 加入互動功能 （滑鼠停留、 滑鼠離開，按一下，等等） 的簡單方法是定義您的範本或樣式中的觸發程序。 若要建立<xref:System.Windows.Trigger>，例如將"condition"屬性定義：[] 按鈕<xref:System.Windows.UIElement.IsMouseOver%2A>屬性值等於`true`。 然後，您會定義觸發程序條件為 true 時，會發生的 setter （動作）。  
  
#### <a name="to-create-button-interactivity"></a>若要建立按鈕互動性  
  
1.  **新增範本觸發程序：** 將反白顯示的標記新增至您的範本。  
  
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
  
2.  **新增屬性觸發程序：** 反白顯示將標記新增至`ControlTemplate.Triggers`區塊：  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     按 f5 鍵執行應用程式，並查看效果，當您執行到按鈕的滑鼠指標。  
  
3.  **新增焦點觸發程序：** 接下來，我們將新增一些類似的 setter 來處理的情況，當按鈕具有焦點 （例如，在使用者按一下它之後）。  
  
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
  
     按 f5 鍵執行應用程式，然後按一下其中一個按鈕。 請注意，[] 按鈕之後會保持反白顯示您按一下它因為它仍具有焦點。 如果您按一下另一個按鈕時，[新增] 按鈕時的最後一個會失去它，就會取得焦點。  
  
4.  **新增動畫**<xref:System.Windows.UIElement.MouseEnter> **並** <xref:System.Windows.UIElement.MouseLeave> **:** 接下來我們加入一些動畫觸發程序。 新增下列任何一處內的標記`ControlTemplate.Triggers`區塊。  
  
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
  
     當滑鼠指標移到按鈕上方，並傳回給一般大小，當滑鼠指標離開時，會縮小玻璃矩形。  
  
     有兩個當滑鼠指標移至按鈕上時，會觸發的動畫 (<xref:System.Windows.UIElement.MouseEnter>就會引發事件)。 這些動畫壓縮玻璃矩形沿著 X 和 Y 軸。 請注意上的屬性<xref:System.Windows.Media.Animation.DoubleAnimation>項目 —<xref:System.Windows.Media.Animation.Timeline.Duration%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定動畫發生超過半秒，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>指定半透明效果壓縮 10%。  
  
     第二個事件觸發程序 (<xref:System.Windows.UIElement.MouseLeave>) 只會停止第一個。 當您停止<xref:System.Windows.Media.Animation.Storyboard>，所有動畫的屬性會傳回為其預設值。 因此，當使用者移出按鈕的指標，按鈕會回到之前的滑鼠游標移到按鈕的方式。 如需動畫的詳細資訊，請參閱[動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
5.  **加入按一下按鈕時的動畫：** 最後一個步驟是新增的觸發程序，當使用者按一下按鈕。 新增下列任何一處內的標記`ControlTemplate.Triggers`區塊：  
  
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
  
     按 f5 鍵執行應用程式，然後按一下其中一個按鈕。 當您按一下按鈕時，半透明矩形會旋轉。  
  
## <a name="summary"></a>總結  
 在本逐步解說中，您的練習如下：  
  
-   目標<xref:System.Windows.Style>成物件類型 (<xref:System.Windows.Controls.Button>)。  
  
-   控制在整個應用程式中使用按鈕的基本屬性<xref:System.Windows.Style>。  
  
-   建立資源，例如要用於屬性值的漸層<xref:System.Windows.Style>setter。  
  
-   將範本套用至按鈕來自訂整個應用程式中按鈕的外觀。  
  
-   自訂的按鈕，以回應使用者動作的行為 (例如<xref:System.Windows.UIElement.MouseEnter>， <xref:System.Windows.UIElement.MouseLeave>，和<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) 包含的動畫效果。  
  
## <a name="see-also"></a>另請參閱

- [使用 Microsoft Expression Blend 建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [樣式設定和範本化](styling-and-templating.md)
- [動畫概觀](../graphics-multimedia/animation-overview.md)
- [使用純色和漸層繪製的概觀](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [點陣圖效果概觀](../graphics-multimedia/bitmap-effects-overview.md)
