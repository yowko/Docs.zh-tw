---
title: 逐步解說：設定 WPF 內容的樣式
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 887a157494c2992c1ae5868229c442f31fafb276
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312146"
---
# <a name="walkthrough-styling-wpf-content"></a>逐步解說：設定 WPF 內容的樣式
本逐步解說示範如何將樣式套用至 Windows Form 上裝載的 Windows Presentation Foundation (WPF) 控制項。

 在這個逐步解說中，您將執行下列工作：

-   建立專案。

-   建立 WPF 控制項類型。

-   將樣式套用至 WPF 控制項。

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立 Windows Form 專案。  
  
> [!NOTE]
>  裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
-   建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`StylingWpfContent`。  
  
## <a name="creating-the-wpf-control-types"></a>建立 WPF 控制項類型  
 在將 WPF 控制項加入專案後，即可將它裝載至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
#### <a name="to-create-wpf-control-types"></a>建立 WPF 控制項類型  
  
1. 將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2. 在 [設計] 檢視中，確定已選取 `UserControl1`。 如需詳細資訊，請參閱[如何：選取並移動設計介面上的項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。  
  
3. 在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。  
  
4. 新增<xref:System.Windows.Controls.Button?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.ContentControl.Content%2A>屬性設**取消**。  
  
5. 新增第二<xref:System.Windows.Controls.Button?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.ContentControl.Content%2A>屬性設 **[確定]**。  
  
6. 建置專案。  
  
## <a name="applying-a-style-to-a-wpf-control"></a>套用樣式至 WPF 控制項  
 您可以套用不同的樣式至 WPF 控制項，以變更其外觀和行為。  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a>套用樣式至 WPF 控制項  
  
1. 在 Windows Form 設計工具中開啟 `Form1`。  
  
2. 在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`表單上。  
  
     `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
3. 中的智慧標籤面板`elementHost1`，按一下**編輯裝載內容**從下拉式清單。  
  
     `UserControl1` 在中開啟[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
4. 在 [XAML] 檢閱中，插入下列 XAML 到 `<UserControl>` 開頭標記後面。  
  
     此 XAML 會建立具有對比漸層框線的漸層。 按一下控制項時，漸層會變更，產生已按下的按鈕外觀。 如需詳細資訊，請參閱 [設定樣式和範本](../../wpf/controls/styling-and-templating.md)。  
  
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
  
1. 藉由插入 [取消] 按鈕`<Button>` 標籤中的下列 XAML，套用前一個步驟中定義的 `SimpleButton` 樣式到 [取消] 按鈕。  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     按鈕宣告將類似下列的 XAML。  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1. 建置專案。  
  
2. 在 Windows Form 設計工具中開啟 `Form1`。  
  
3. 新的樣式會套用至按鈕控制項。  
  
4. 從**偵錯**功能表上，選取**開始偵錯**執行應用程式。  
  
5. 按一下 [確定] 和 [取消] 按鈕，然後檢視其差異。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [XAML 概觀 (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [樣式設定和範本化](../../wpf/controls/styling-and-templating.md)
