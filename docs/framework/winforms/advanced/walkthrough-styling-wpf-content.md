---
title: 演練:樣式 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646322"
---
# <a name="walkthrough-style-wpf-content"></a>演練:樣式 WPF 內容

本文介紹如何將樣式應用於 Windows 窗體上託管的 Windows 演示文稿基礎 (WPF) 控制項。

## <a name="prerequisites"></a>Prerequisites

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-the-project"></a>建立專案

打開視覺化工作室,並在名為`StylingWpfContent`的「視覺基本」或「視覺 C#」中創建新的 Windows 窗體應用程式專案。

> [!NOTE]
> 裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。

## <a name="create-the-wpf-control-types"></a>建立 WPF 控制項型態

在將 WPF 控制項加入專案後，即可將它裝載至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。

1. 將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 有關詳細資訊,請參閱[演練:在設計時間在 Windows 窗體上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。

2. 在 [設計] 檢視中，確定已選取 `UserControl1`。

3. 在 **「屬性」** 視窗中,<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Height%2A>將與屬性的值設定為**200**。

4. 將<xref:System.Windows.Controls.Button?displayProperty=nameWithType>控制項加入,<xref:System.Windows.Controls.UserControl><xref:System.Windows.Controls.ContentControl.Content%2A>並將屬性的值設定為 **"取消**" 。

5. 將第二<xref:System.Windows.Controls.Button?displayProperty=nameWithType>個控制項添加<xref:System.Windows.Controls.UserControl>到<xref:System.Windows.Controls.ContentControl.Content%2A>,並將屬性的值設置為 **"確定**"

6. 建置專案。

## <a name="apply-a-style-to-a-wpf-control"></a>將樣式應用於 WPF 控制項

您可以套用不同的樣式至 WPF 控制項，以變更其外觀和行為。

1. 在 Windows Form 設計工具中開啟 `Form1`。

1. 在**工具箱**中,按`UserControl1`兩下 以在窗`UserControl1`體上創建的實例。

   `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

1. 在`elementHost1`的智慧標記面板中,按一下拉清單中**的「編輯託管內容**」 。。

   `UserControl1`在 WPF 設計器中打開。

1. 在 [XAML] 檢閱中，插入下列 XAML 到 `<UserControl>` 開頭標記後面。 此 XAML 會建立具有對比漸層框線的漸層。 按一下控制項時，漸層會變更，產生已按下的按鈕外觀。 有關詳細資訊,請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。

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

1. 通過在「`SimpleButton`取消」`<Button>`按鈕的標記中插入以下 XAML,將上一步中定義的樣式應用於「**取消」** 按鈕。

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   您的按鈕宣告類似於以下 XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. 建置專案。

1. 在 Windows Form 設計工具中開啟 `Form1`。

1. 新的樣式會套用至按鈕控制項。

1. 在 **「調試」** 選單中,選擇 **「開始除錯」** 以執行應用程式。

1. 按下「**確定****」 與「取消」** 按鈕並查看差異。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
