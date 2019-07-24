---
title: 逐步解說：將 WPF 時鐘裝載在 Win32 中
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 98e48060bbb82764e1e541797c666ca33f247c39
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400484"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>逐步解說：將 WPF 時鐘裝載在 Win32 中

若要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]將[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]放在應用<xref:System.Windows.Interop.HwndSource>程式內, 請使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 它會提供包含內容的 HWND。 首先您要建立<xref:System.Windows.Interop.HwndSource>, 並提供類似于 CreateWindow 的參數。 然後您會告訴<xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]您想要的內容。 最後, 您會從<xref:System.Windows.Interop.HwndSource>取得 HWND。 本逐步解說說明如何在實作作業系統[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **日期和時間屬性**對話方塊的應用程式中[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]建立混合式。

## <a name="prerequisites"></a>必要條件

請參閱[WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)。

## <a name="how-to-use-this-tutorial"></a>如何使用本教學課程

本教學課程著重在產生交互操作應用程式的重要步驟。 本教學課程是以範例、 [Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)為後盾, 但該範例會反映出最終產品。 本教學課程記載的步驟, 就像您是從自己[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的現有專案開始, 或許是既有的專案, 而且您已將裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的加入至應用程式。 您可以比較您的終端產品與[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 內 Windows Presentation Framework 的逐步解說 (HwndSource)

下圖顯示本教學課程的預期最終產品︰

![顯示 [日期和時間內容] 對話方塊的螢幕擷取畫面。](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

您可以在 Visual Studio 中建立C++ Win32 專案, 然後使用對話方塊編輯器來建立下列內容, 以重新建立此對話方塊:

![重新建立日期和時間屬性對話方塊](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(您[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]不需要使用來使用<xref:System.Windows.Interop.HwndSource>, 也不需要使用C++來撰寫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式, 但這是相當常見的方法, 而且非常適合逐步的教學課程說明)。

您必須完成五個特定子步驟, 才能將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘放入對話方塊中:

1. 藉由[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]變更中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]的專案設定, 讓您的專案呼叫 managed 程式碼 ( **/clr**)。

2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 在個別<xref:System.Windows.Controls.Page>的 DLL 中建立。

3. 將它[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>放在<xref:System.Windows.Interop.HwndSource>內。

4. 使用屬性取得的<xref:System.Windows.Controls.Page>HWND <xref:System.Windows.Interop.HwndSource.Handle%2A> 。

5. 用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]來決定要在較大[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的應用程式中放置 HWND 的位置

## <a name="clr"></a>/clr

第一個步驟是將此非[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]受控專案轉換成一個可以呼叫 managed 程式碼的專案。 您可以使用/clr 編譯器選項, 這會連結到您想要使用的必要 Dll, 並調整 Main 方法以與[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]搭配使用。

若要在C++專案內啟用 managed 程式碼的使用:以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**屬性**]。 在 [**一般**] 屬性頁 (預設值) 上, 將 [Common Language `/clr`Runtime 支援] 變更為。

接下來, 將參考新增至所[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]需的 dll:PresentationCore .dll、PresentationFramework、system.string、WindowsBase、.dll、Uiautomationprovider.dll 和 UIAutomationTypes .dll。 (下列指示假設作業系統安裝在 C: 磁碟機上)。

1. 以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**參考 ...** ], 然後在該對話方塊內:

2. 以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**參考 ...** ]。

3. 按一下 [**加入新參考**], 按一下 [流覽] 索引標籤, 輸入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, 然後按一下 [確定]。

4. 針對 PresentationFramework 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。

5. 針對 WindowsBase 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。

6. 針對 UIAutomationTypes 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。

7. 針對 Uiautomationprovider.dll 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。

8. 按一下 [**新增參考**], 選取 [system.object], 然後按一下 **[確定]** 。

9. 按一下 **[確定]** , 結束 Win32clock 屬性頁以加入參考。

 最後, 將新增`STAThreadAttribute` `_tWinMain`至方法以搭配使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

這個屬性會告知 common language runtime (CLR), 當它初始化[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]時, 它應該使用單一執行緒單元模型 (STA), 這是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]) 的必要動作。

## <a name="create-a-windows-presentation-framework-page"></a>建立 Windows Presentation Framework 頁面

接下來, 您會建立定義的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>DLL。 將建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>為獨立應用程式通常是最簡單的方法, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]並以這種方式撰寫和調試部分。 完成後, 即可將該專案轉換成 DLL, 方法是以滑鼠右鍵按一下專案, 按一下 [**屬性**], 前往 [應用程式], 然後將 [輸出類型] 變更為 [Windows 類別庫]。

然後, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dll 專案可以與專案 (其中一個包含兩個專案的方案) 合併–以滑鼠右鍵按一下方案, 然後選取 [ **Add\Existing 專案**]。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

若要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]從專案使用該 dll, 您需要新增參考:

1. 以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**參考 ...** ]。

2. 按一下 [**新增參考**]。

3. 按一下 [專案] 索引標籤。選取 WPFClock，然後按一下 [確定]。

4. 按一下 **[確定]** , 結束 Win32clock 屬性頁以加入參考。

## <a name="hwndsource"></a>HwndSource

接下來, 您<xref:System.Windows.Interop.HwndSource>可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>讓看起來像是 HWND。 您可以將此程式碼區塊新增至 C++ 檔案：

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 這是可使用一些說明的長程式碼。 第一個部分是各種子句，讓您不需要完整限定所有呼叫︰

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 接著, 您要定義一個函式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndSource>來建立內容、將它放在其周圍, 然後傳回 HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

首先您要建立<xref:System.Windows.Interop.HwndSource>, 其參數與 CreateWindow 類似:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

接著, 您可以[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由呼叫其「它的」來建立內容類別別:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

接著, 您可以將頁面連線<xref:System.Windows.Interop.HwndSource>到:

```cpp
source->RootVisual = page;
```

 在最後一行中, 傳回的 HWND <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>定位 Hwnd

現在您已經有包含[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘的 hwnd, 您需要將該 hwnd 放在[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊中。 如果您知道要放置 HWND 的位置, 只要將該大小和位置傳遞至您稍早`GetHwnd`定義的函式即可。 但是，您已使用資源檔來定義對話方塊，因此，您未完全確定放置任何 HWND 的位置。 您可以使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]對話方塊編輯器, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]將靜態控制項放在您想要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用的時鐘 (「在此插入時鐘」), 並用它來定位時鐘。

在您處理 WM_INITDIALOG 的位置, `GetDlgItem`您可以使用來抓取預留位置 STATIC 的 HWND:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

接著, 您會計算該預留位置的大小和位置, 讓您可以將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘放在該位置:

RECT 矩形；

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

然後，您可以隱藏預留位置 STATIC︰

```cpp
ShowWindow(placeholder, SW_HIDE);
```

並在該[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]位置建立時鐘 HWND:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

若要讓教學課程更有趣, 並產生真正[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的時鐘, 您必須在此時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立時鐘控制項。 您大部分都可以透過標記完成，而且只需要程式碼後置中的一些事件處理常式即可。 由於本教學課程是關於互通性, 而不是控制項設計, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]因此在這裡以程式碼區塊的形式提供時鐘的完整程式碼, 而不需要個別的指示來建立它或每個部分所代表的意義。 請自由實驗此程式碼，來變更控制項功能的外觀或操作。

標記如下：

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

這裡是隨附的程式碼後置︰

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

最終結果如下：

![最終結果日期和時間屬性對話方塊](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

若要比較您的最終結果與產生此螢幕擷取畫面的程式碼, 請參閱[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndSource>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)
