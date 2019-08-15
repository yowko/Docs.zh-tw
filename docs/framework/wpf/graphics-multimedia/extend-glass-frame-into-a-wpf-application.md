---
title: 將玻璃框架擴充至 WPF 應用程式中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: f8d50cb4d0112232f86579542650418a1906bda2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039837"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>將玻璃框架擴充至 WPF 應用程式中

本主題示範如何將[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]玻璃框架擴充至 Windows Presentation Foundation (WPF) 應用程式的工作區。

> [!NOTE]
> 此範例只能在執行桌面視窗管理員 (DWM) 且已啟用玻璃效果的 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 機器上使用。 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 家用入門版不支援透明的玻璃效果。 在 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 其他版本上通常以透明玻璃效果呈現的區域會呈現不透明。

## <a name="example"></a>範例

下圖說明延伸到 Internet Explorer 7 網址列的玻璃框架:

![螢幕擷取畫面, 顯示在 IE7 網址列後方擴充的玻璃框架。](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

若要擴充[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式的玻璃框架, 需要存取非受控 API。 下列程式碼範例會針對將框架擴充到工作區所需的兩個 API, 執行平台叫用 (pinvoke)。 這些 API 中的每一個都是在名為**NonClientRegionAPI**的類別中宣告。

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) 是會將框架擴充至工作區的 DWM 函式。 它接受兩個參數：視窗控制代碼和 [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) 結構。 [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) 是用來告知 DWM 應該額外將多少框架擴充至工作區。

## <a name="example"></a>範例

若要使用 [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) 函式，必須取得視窗控制代碼。 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 您可以從的<xref:System.Windows.Interop.HwndSource.Handle%2A>屬性<xref:System.Windows.Interop.HwndSource>取得視窗控制碼。 在下列範例中, 畫面格會延伸到視窗<xref:System.Windows.FrameworkElement.Loaded>事件的工作區中。

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a>範例

下列範例示範將框架擴充至工作區的簡單視窗。 畫面格會延伸到包含兩個<xref:System.Windows.Controls.TextBox>物件的上框線後面。

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

下圖說明擴充至[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式的玻璃框架:

![螢幕擷取畫面: 顯示擴充至 WPF 應用程式的玻璃框架。](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a>另請參閱

- [桌面視窗管理員總覽](/windows/desktop/dwm/dwm-overview)
- [桌面視窗管理員模糊總覽](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
