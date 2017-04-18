---
title: "逐步解說：設定 WPF 內容的樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "互通性 [WDF]"
  - "樣式, WPF 內容"
  - "WPF Designer, 設定 WPF 內容的樣式"
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 逐步解說：設定 WPF 內容的樣式
本逐步解說示範如何將樣式套用至 Windows Form 上裝載的 Windows Presentation Foundation \(WPF\) 控制項。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立專案。  
  
-   建立 WPF 控制項類型。  
  
-   將樣式套用至 WPF 控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## 建立專案  
 第一個步驟是建立 Windows Form 專案。  
  
> [!NOTE]
>  裝載 WPF 內容時，只支援 C\# 和 Visual Basic 專案。  
  
#### 若要建立專案  
  
-   在 Visual Basic 或 Visual C\# 中，建立名為 `StylingWpfContent` 的新 Windows Form 應用程式專案。  
  
## 建立 WPF 控制項類型  
 在將 WPF 控制項加入專案後，即可將它裝載至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
#### 建立 WPF 控制項類型  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。  使用控制項類型的預設名稱 `UserControl1.xaml`。  如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在 \[設計\] 檢視中，確定已選取 `UserControl1`。  如需詳細資訊，請參閱[HOW TO：在設計介面上選取並移動項目](http://msdn.microsoft.com/zh-tw/54cb70b6-b35b-46e4-a0cc-65189399c474)。  
  
3.  在 \[屬性\] 視窗中，將 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的值設定為 `200`。  
  
4.  將 <xref:System.Windows.Controls.Button?displayProperty=fullName> 控制項加入 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性的值設定為 \[取消\]。  
  
5.  將第二個 <xref:System.Windows.Controls.Button?displayProperty=fullName> 控制項加入 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性的值設定為 \[確定\]。  
  
6.  建置專案。  
  
## 套用樣式至 WPF 控制項  
 您可以套用不同的樣式至 WPF 控制項，以變更其外觀和行為。  
  
#### 套用樣式至 WPF 控制項  
  
1.  在 Windows Form 設計工具中開啟 `Form1`。  
  
2.  在 \[工具箱\] 中，按兩下 `UserControl1`，在表單上建立 `UserControl1` 的執行個體。  
  
     `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
3.  在 `elementHost1` 的智慧標籤面板中，在下拉式清單中按一下 \[編輯裝載內容\]。  
  
     `UserControl1` 會在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 中開啟。  
  
4.  在 \[XAML\] 檢視中，插入下列 XAML 到 `<UserControl>` 開頭標記後面。  
  
     此 XAML 會建立具有對比漸層框線的漸層。  按一下控制項時，漸層會變更，產生已按下的按鈕外觀。  如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
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
  
1.  藉由插入 \[取消\] 按鈕`<Button>` 標籤中的下列 XAML，套用前一個步驟中定義的 `SimpleButton` 樣式到 \[取消\] 按鈕。  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     按鈕宣告將類似下列的 XAML。  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  建置專案。  
  
2.  在 Windows Form 設計工具中開啟 `Form1`。  
  
3.  新的樣式會套用至按鈕控制項。  
  
4.  在 \[偵錯\] 功能表中選取 \[開始偵錯\]，以執行應用程式。  
  
5.  按一下 \[確定\] 和 \[取消\] 按鈕，然後檢視其差異。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)