---
title: "逐步解說：使用 XAML 建立按鈕 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "按鈕"
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 逐步解說：使用 XAML 建立按鈕
本逐步解說的目的在於學習如何建立用於 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式中的動畫按鈕。  本逐步解說會使用樣式與範本建立自訂的按鈕資源，以便重複使用程式碼並將按鈕邏輯與按鈕宣告分開。  本逐步解說完全以[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 撰寫。  
  
> [!IMPORTANT]
>  本逐步解說會引導您執行相關步驟，以藉由將[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 輸入或複製並貼上至 Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]，建立應用程式。  若您想學習如何使用設計工具 \(Microsoft Expression Blend\) 建立相同的應用程式，請參閱[使用 Microsoft Expression Blend 建立按鈕](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。  
  
 下圖顯示已完成的按鈕。  
  
 ![使用 XAML 建立的自訂按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.png "custom\_button\_AnimatedButton\_5")  
  
## 建立基本按鈕  
 首先建立新的專案並加入數個按鈕至視窗中。  
  
#### 建立新的 WPF 專案並加入按鈕至視窗中  
  
1.  啟動[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]。  
  
2.  **建立新的 WPF 專案**：指向 \[**檔案**\] 功能表上的 \[**加入**\]，然後按一下 \[**專案**\]。  尋找 \[**Windows 應用程式 \(WPF\)**\] 範本，並將專案命名為 "AnimatedButton"。  這將會建立應用程式的基本架構。  
  
3.  **加入基本預設按鈕**：您在本逐步解說中所需的所有檔案皆由範本提供。  請按兩下 \[方案總管\] 中的 Window1.xaml 檔案加以開啟。  Window1.xaml 中預設會有 <xref:System.Windows.Controls.Grid> 項目。  移除 <xref:System.Windows.Controls.Grid> 項目，然後在Window1.xaml 中輸入或複製並貼上下列粗體顯示的程式碼，將數個按鈕加入至[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 頁面中：  
  
    ```  
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
  
     按 F5 以執行應用程式；您應會看見一組按鈕，如下圖所示。  
  
     ![三個基本按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.png "custom\_button\_AnimatedButton\_1")  
  
     現在您已建立基本按鈕，Window1.xaml 檔案中的工作即告完成。  接下來的逐步解說將把重點放在 app.xaml 檔案，以定義按鈕的樣式與範本。  
  
## 設定基本屬性  
 接下來，我們將設定這些按鈕的某些屬性，以控制按鈕的外觀與配置。  您將不會個別設定按鈕的屬性，而是使用資源來定義整個應用程式的按鈕屬性。  應用程式資源在概念上類似於網頁的外部[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]；但資源的功能比[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] 更強大，在本逐步解說結束時您就會了解這一點。  若要進一步了解資源，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
#### 使用樣式設定按鈕的基本屬性  
  
1.  **定義 Application.Resources 區塊**：開啟 app.xaml，並加入下列粗體顯示的標記 \(如果沒有的話\)：  
  
    ```  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>  
  
        <!-- Resources for the entire application can be   
             defined here. -->  
  
      </Application.Resources>  
    </Application>  
    ```  
  
     資源範圍取決於您定義資源的位置。  在 app.xaml 檔案的 `Application.Resoureses` 中定義資源，可讓使用者從應用程式中的任一處使用該資源。  若要進一步了解定義資源範圍的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
2.  **建立樣式並定義其基本屬性值**：加入下列標記至 `Application.Resources` 區塊中。  這個標記可建立會套用至應用程式中所有按鈕的 <xref:System.Windows.Style>，以將按鈕的 <xref:System.Windows.FrameworkElement.Width%2A> 設定為 90、<xref:System.Windows.FrameworkElement.Margin%2A> 設定為 10：  
  
    ```  
    <Application.Resources>  
  
      <Style TargetType="Button">  
        <Setter Property="Width" Value="90" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> 屬性可指定將樣式套用於所有 <xref:System.Windows.Controls.Button> 類型的物件。  每個 <xref:System.Windows.Setter> 都會為 <xref:System.Windows.Style> 設定不同的屬性值。  因此，此時應用程式中的每個按鈕皆具有 90 的寬度與 10 的邊界。  如果您按 F5 執行應用程式，會看見下列視窗。  
  
     ![寬度為 90 且邊界為 10 的按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.png "custom\_button\_AnimatedButton\_2")  
  
     樣式的用途還有很多，包括各種為物件的目標進行微調的方法、指定複雜的屬性值，甚至以樣式做為其他樣式的輸入等等。  如需詳細資訊，請參閱 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
3.  **將樣式屬性值設定為資源**：資源可讓使用者輕鬆地重複使用一般定義的物件與值。  若要使用資源來定義複雜的值以進一步模組化您的程式碼，資源尤其有用。  將下列粗體顯示的標記加入至 app.xaml。  
  
    ```  
    <Application.Resources>  
  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background"   
          Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
  
    </Application.Resources>  
    ```  
  
     在 `Application.Resources` 區塊正下方，您建立了名為 "GrayBlueGradientBrush" 的資源。  這個資源定義了水平漸層。  使用者可在應用程式中的任一處將這個資源做為屬性值，包括在 <xref:System.Windows.Controls.Control.Background%2A> 屬性的按鈕樣式 setter 內。  現在，所有按鈕都會擁有這種漸層效果的 <xref:System.Windows.Controls.Control.Background%2A> 屬性值。  
  
     按下 F5 執行應用程式。  其外觀應如下。  
  
     ![具有漸層背景的按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.png "custom\_button\_AnimatedButton\_3")  
  
## 建立可定義按鈕外觀的範本  
 在本節中，您會建立使用自訂按鈕外觀 \(顯示方式\) 的範本。  呈現的按鈕是由矩形與其他元件等數個物件所組成，形成按鈕的獨特外觀。  
  
 到目前為止，只有透過變更按鈕屬性來控制應用程式中各按鈕的外觀。  但想要對按鈕外觀做更大的變化時該怎麼辦？  範本可提供對物件顯示方式的強大控制。  由於範本可用於樣式內，因此您可以將範本套用至樣式適用的所有物件 \(在本逐步解說中為按鈕\)。  
  
#### 使用範本定義按鈕外觀  
  
1.  **設定範本**：由於 <xref:System.Windows.Controls.Button> 之類的控制項具有 <xref:System.Windows.Controls.Control.Template%2A> 屬性，因此您可以比照我們使用 <xref:System.Windows.Setter> 在 <xref:System.Windows.Style> 中設定的其他屬性值，來定義範本屬性值。  將下列粗體顯示的標記加入至您的按鈕樣式。  
  
    ```  
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
  
2.  **改變按鈕顯示方式**：在這個步驟，您必須定義範本。  加入下列粗體顯示的標記。  這個標記會指定兩個具有圓角的 <xref:System.Windows.Shapes.Rectangle> 項目，後面再加上一個 <xref:System.Windows.Controls.DockPanel>。  <xref:System.Windows.Controls.DockPanel> 可用以裝載按鈕的 <xref:System.Windows.Controls.ContentPresenter>。  <xref:System.Windows.Controls.ContentPresenter> 會顯示按鈕的內容。  在本逐步解說中，這些內容為文字 \("Button 1"、"Button 2"、"Button 3"\)。  所有範本元件 \(矩形與 <xref:System.Windows.Controls.DockPanel>\) 都會配置於 <xref:System.Windows.Controls.Grid> 內。  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">  
        <Grid Width="{TemplateBinding Width}"   
         Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle"   
            HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch"   
            Stroke="{TemplateBinding Background}"   
            RadiusX="20" RadiusY="20" StrokeThickness="5"   
            Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle"   
            HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}"   
            RadiusX="20" RadiusY="20"   />  
  
          <!-- Present Content (text) of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}"   
              TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     按下 F5 執行應用程式。  其外觀應如下。  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom\_button\_AnimatedButton\_4")  
  
3.  **加入半透明效果至範本中**：接下來您將加入半透明效果。  首先您必須建立一些可產生透明漸層效果的資源。  將這些漸層資源加入至 `Application.Resources` 區塊內的任一處：  
  
    ```  
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
  
     這些資源會做為我們在按鈕範本的 <xref:System.Windows.Controls.Grid> 中所插入矩形的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  將下列粗體顯示的標記加入至範本中。  
  
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
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     請注意，`x:Name` 屬性為 "glassCube" 之矩形的 <xref:System.Windows.UIElement.Opacity%2A> 為 0，因此執行範例時，您將不會看見半透明矩形覆蓋於頂端。  這是因為我們稍後會將觸發程序 \(Trigger\) 加入至範本中，以在使用者與按鈕互動時進行觸發。  但現在您可以將 <xref:System.Windows.UIElement.Opacity%2A> 值變更為 1 並執行應用程式，以檢視按鈕的外觀。  請參閱下圖。  繼續進行下個步驟前，請先將 <xref:System.Windows.UIElement.Opacity%2A> 回復為 0。  
  
     ![使用 XAML 建立的自訂按鈕](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.png "custom\_button\_AnimatedButton\_5")  
  
## 建立按鈕互動性  
 在本節中，您將會建立屬性觸發程序與事件觸發程序，以在使用者將滑鼠指標移至按鈕上及執行按一下滑鼠等動作時，變更屬性值並執行動畫。  
  
 要加入互動性 \(移入滑鼠、移開滑鼠、按一下滑鼠等等\)，最簡單的方式就是在範本或樣式內定義觸發程序。  若要建立 <xref:System.Windows.Trigger>，您必須定義屬性「條件」，例如：按鈕的 <xref:System.Windows.UIElement.IsMouseOver%2A> 屬性值等於 `true`。  接著，您必須定義觸發程序條件成立時所執行的 setter \(動作\)。  
  
#### 建立按鈕互動性  
  
1.  **加入範本觸發程序**：將下列粗體顯示的標記加入至範本中。  
  
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
  
        <ControlTemplate.Triggers>  
          <!-- Set action triggers for the buttons and define  
               what the button does in response to those triggers. -->  
        </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **加入屬性觸發程序**：將下列粗體顯示的標記加入至 `ControlTemplate.Triggers` 區塊中：  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user   
             mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the   
             glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you   
             were looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"   
          TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     按 F5 以執行應用程式，並觀察您將滑鼠指標置於按鈕上時的效果。  
  
3.  **加入焦點觸發程序**：接下來，我們將加入某些類似的 setter 以處理按鈕具有焦點時的情形 \(例如在使用者加以點選後\)。  
  
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
      <!-- Set properties when button has focus. -->  
      <Trigger Property="IsFocused" Value="true">  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
        <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
        <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />  
      </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     按 F5 以執行應用程式，再按一下其中一個按鈕。  請注意，按鈕在您點選後即會維持反白狀態，因為它仍具有焦點。  如果您按一下另一個按鈕，新的按鈕即會取得焦點，而前一個按鈕即失去焦點。  
  
4.  **加入表示**  <xref:System.Windows.UIElement.MouseEnter> **和** <xref:System.Windows.UIElement.MouseLeave> **的動畫：**接下來我們將在觸發程序中加入一些動畫。  將下列標記加入至 `ControlTemplate.Triggers` 區塊內的任一處。  
  
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
  
     半透明矩形會在滑鼠指標移至按鈕上時縮小，並在指標移走時恢復原有大小。  
  
     指標移至按鈕上時 \(引發 <xref:System.Windows.UIElement.MouseEnter> 事件\) 會觸發兩個動畫。  這些動畫會沿著 X 與 Y 軸使半透明矩形縮小。  請注意 <xref:System.Windows.Media.Animation.DoubleAnimation> 項目的屬性：<xref:System.Windows.Media.Animation.Timeline.Duration%2A> 與 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>。  <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 指定動畫要顯示半秒以上，而 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 則指定玻璃矩形要縮小 10%。  
  
     第二個事件觸發程序 \(<xref:System.Windows.UIElement.MouseLeave>\) 會直接停止第一個觸發事件。  當您停止 <xref:System.Windows.Media.Animation.Storyboard> 時，所有動畫屬性皆會恢復為其預設值。  因此，當使用者將指標從按鈕上移走時，按鈕即會恢復為滑鼠指標未移至其上方前的狀態。  如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
5.  **加入按一下按鈕時顯示的動畫**：最後一個步驟是加入使用者按一下按鈕時要執行的觸發程序。  將下列標記加入至 `ControlTemplate.Triggers` 區塊內的任一處：  
  
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
  
     按 F5 以執行應用程式，再按一下其中一個按鈕。  當您按一下按鈕時，半透明矩形即會旋轉。  
  
## 摘要  
 在這個逐步解說中，您已執行下列練習：  
  
-   設定將 <xref:System.Windows.Style> 套用至物件型別 \(<xref:System.Windows.Controls.Button>\)。  
  
-   使用 <xref:System.Windows.Style> 控制整個應用程式中的基本按鈕屬性。  
  
-   建立漸層等資源，以做為 <xref:System.Windows.Style> setter 的屬性值。  
  
-   對按鈕套用範本，以自訂整個應用程式的按鈕外觀。  
  
-   自訂含有動畫效果的按鈕行為以回應使用者動作 \(如 <xref:System.Windows.UIElement.MouseEnter>、<xref:System.Windows.UIElement.MouseLeave> 與 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\)。  
  
## 請參閱  
 [使用 Microsoft Expression Blend 建立按鈕](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [點陣圖效果概觀](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)