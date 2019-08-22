---
title: 逐步解說：設定 WPF 內容的樣式
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 287ed08db8a4266e5044a81d47a697949257e113
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658488"
---
# <a name="walkthrough-style-wpf-content"></a>逐步解說：樣式 WPF 內容

本文說明如何將樣式套用至裝載于 Windows Form 的 Windows Presentation Foundation (WPF) 控制項。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-the-project"></a>建立專案

開啟 Visual Studio, 並在 Visual Basic 或視覺效果C#中建立名為`StylingWpfContent`的新 Windows Forms 應用程式專案。

> [!NOTE]
> 裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。

## <a name="create-the-wpf-control-types"></a>建立 WPF 控制項類型

在將 WPF 控制項加入專案後，即可將它裝載至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。

1. 將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)于 Windows Forms 上建立新的 WPF 內容。

2. 在 [設計] 檢視中，確定已選取 `UserControl1`。

3. 在 [**屬性**] 視窗中, 將<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性的值設定為**200**。

4. 將控制項加入<xref:System.Windows.Controls.UserControl>至, 並將屬性的值設定<xref:System.Windows.Controls.ContentControl.Content%2A>為 [**取消**]。 <xref:System.Windows.Controls.Button?displayProperty=nameWithType>

5. 將第二<xref:System.Windows.Controls.Button?displayProperty=nameWithType>個控制項加入<xref:System.Windows.Controls.UserControl>至, 並<xref:System.Windows.Controls.ContentControl.Content%2A>將屬性的值設定為 **[確定]** 。

6. 建置專案。

## <a name="apply-a-style-to-a-wpf-control"></a>將樣式套用至 WPF 控制項

您可以套用不同的樣式至 WPF 控制項，以變更其外觀和行為。

1. 在 Windows Form 設計工具中開啟 `Form1`。

1. 在 [**工具箱**] 中, 按兩下`UserControl1`以在表單上`UserControl1`建立的實例。

   `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

1. 在的智慧標籤面板`elementHost1`中, 按一下下拉式清單中的 [**編輯主控內容**]。

   `UserControl1`在 WPF 設計工具中開啟。

1. 在 [XAML] 檢閱中，插入下列 XAML 到 `<UserControl>` 開頭標記後面。 此 XAML 會建立具有對比漸層框線的漸層。 按一下控制項時，漸層會變更，產生已按下的按鈕外觀。 如需詳細資訊，請參閱 [設定樣式和範本](../../wpf/controls/styling-and-templating.md)。

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

1. 藉由在 [**取消**] 按鈕的`<Button>`標記中插入下列 XAML, 將上一個步驟中定義的樣式套用至[取消]按鈕。`SimpleButton`

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   您的按鈕宣告將類似下列 XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. 建置專案。

1. 在 Windows Form 設計工具中開啟 `Form1`。

1. 新的樣式會套用至按鈕控制項。

1. 從 [**調試**程式] 功能表中, 選取 [**開始調試**] 以執行應用程式。

1. 按一下 [**確定]** 和 [**取消**] 按鈕, 並查看差異。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [XAML 概觀 (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [樣式設定和範本化](../../wpf/controls/styling-and-templating.md)
