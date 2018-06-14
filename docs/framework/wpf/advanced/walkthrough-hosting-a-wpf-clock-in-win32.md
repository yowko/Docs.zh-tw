---
title: 逐步解說：在 Win32 中裝載 WPF 時鐘
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 58e4b1dd311ccd6e1bbab79f4c4dda2207f96eaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549694"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>逐步解說：在 Win32 中裝載 WPF 時鐘
要放置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式會使用<xref:System.Windows.Interop.HwndSource>，這樣會提供包含 HWND 您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。 第一次建立<xref:System.Windows.Interop.HwndSource>，讓它類似於 CreateWindow 參數。  接著您告訴<xref:System.Windows.Interop.HwndSource>有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容您想要在其中。  最後，您取得的 HWND 出<xref:System.Windows.Interop.HwndSource>。 這個逐步解說將說明如何建立了混合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]reimplements 作業系統的應用程式**日期和時間內容**對話方塊。  
  
## <a name="prerequisites"></a>必要條件  
 請參閱[WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
## <a name="how-to-use-this-tutorial"></a>如何使用本教學課程  
 本教學課程著重在產生交互操作應用程式的重要步驟。 本教學課程所需範例，支援[Win32 時鐘的互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)，但該範例會在最終產品的反射。 本教學課程中說明的步驟，您已啟動與現有[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]您自己的專案，可能是既有的專案，並且已加入裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]您的應用程式。 您可以比較與最終產品[Win32 時鐘的互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)。  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 內 Windows Presentation Framework 的逐步解說 (HwndSource)  
 下圖顯示本教學課程的預期最終產品︰  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 您可以藉由建立 c + + 重新建立這個對話方塊[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，並且使用對話方塊編輯器建立下列：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (您不需要使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]使用<xref:System.Windows.Interop.HwndSource>，而且您不需要使用 c + + 撰寫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式，但這是相當一般的做法，並能侷限於逐步教學課程說明)。  
  
 您需要完成五個特定的子步驟，才能將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘對話方塊：  
  
1.  啟用您[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案，以呼叫 managed 程式碼 (**/clr**) 中的專案設定變更[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]。  
  
2.  建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>在個別的 DLL。  
  
3.  將它放[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>內<xref:System.Windows.Interop.HwndSource>。  
  
4.  取得 HWND<xref:System.Windows.Controls.Page>使用<xref:System.Windows.Interop.HwndSource.Handle%2A>屬性。  
  
5.  使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]決定放置在較大的 HWND[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式  
  
## <a name="clr"></a>/clr  
 第一個步驟是將此 unmanaged[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案合而為一可以呼叫 managed 程式碼。  使用 /clr 編譯器選項，將會連結至您想要使用，並調整與搭配使用的 Main 方法所需 Dll [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
 若要啟用 c + + 專案內的 managed 程式碼： win32clock 專案上按一下滑鼠右鍵，然後選取**屬性**。  在**一般**屬性頁 （預設值），變更至 Common Language Runtime 支援`/clr`。  
  
 接下來，加入所需的 Dll 的參考[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll、 PresentationFramework.dll、 System.dll、 WindowsBase.dll、 UIAutomationProvider.dll 和 UIAutomationTypes.dll。 (下列指示假設作業系統安裝在 C: 磁碟機上)。  
  
1.  Win32clock 專案上按一下滑鼠右鍵，然後選取**參考...**，並在該對話方塊內：  
  
2.  Win32clock 專案上按一下滑鼠右鍵，然後選取**參考...**.  
  
3.  按一下**加入新參考**，按一下 [瀏覽] 索引標籤，輸入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll，然後按一下 [確定]。  
  
4.  針對 PresentationFramework.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。  
  
5.  針對 WindowsBase.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。  
  
6.  針對 UIAutomationTypes.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。  
  
7.  針對 UIAutomationProvider.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。  
  
8.  按一下**加入新參考**選取 System.dll，然後按一下**確定**。  
  
9. 按一下**確定**結束 win32clock 屬性頁，以加入參考。  
  
 最後，會加入`STAThreadAttribute`至`_tWinMain`方法搭配使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 這個屬性會告知[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]，它會初始化時[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]，應該使用單一執行緒的 apartment 模型 (STA)，這是所需的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)])。  
  
## <a name="create-a-windows-presentation-framework-page"></a>建立 Windows Presentation Framework 頁面  
 接下來，您可以建立定義 DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>。 通常是最簡單的方式建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>做為獨立應用程式，以及寫入和偵錯[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分的方式。  一旦完成，該專案可以開啟 dll 中以滑鼠右鍵按一下專案，按一下**屬性**、 移至應用程式，以及輸出類型變更為 Windows 類別庫。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll 專案可以再結合[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案 （一個方案包含兩個專案） – 以滑鼠右鍵按一下方案，並選取**Add\Existing 專案**。  
  
 若要使用的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dll[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案中，您必須加入參考：  
  
1.  Win32clock 專案上按一下滑鼠右鍵，然後選取**參考...**.  
  
2.  按一下**加入新參考**。  
  
3.  按一下 [專案] 索引標籤。選取 WPFClock，然後按一下 [確定]。  
  
4.  按一下**確定**結束 win32clock 屬性頁，以加入參考。  
  
## <a name="hwndsource"></a>HwndSource  
 接下來，您使用<xref:System.Windows.Interop.HwndSource>進行[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND 看起來。  您可以將此程式碼區塊新增至 C++ 檔案：  
  
```  
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
  
 這是可使用一些說明的長程式碼。  第一個部分是各種子句，讓您不需要完整限定所有呼叫︰  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 然後定義來建立函式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容，將<xref:System.Windows.Interop.HwndSource>周圍，並傳回 HWND:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 第一次建立<xref:System.Windows.Interop.HwndSource>，CreateWindow 的參數如下：  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 然後建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容類別，藉由呼叫其建構函式：  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 您接著連接頁面，即可<xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 並在最後一行中，傳回的 HWND <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>定位 Hwnd  
 您已經有包含 HWND[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘，您需要將該 HWND 內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊。  如果您知道要放置 HWND 到何處，您可以只傳遞該大小和位置來`GetHwnd`先前定義的函式。  但是，您已使用資源檔來定義對話方塊，因此，您未完全確定放置任何 HWND 的位置。  您可以使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]對話方塊編輯器將[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]靜態控制您想要前往的時鐘 （「 插入時鐘這裡"），然後使用它來定位[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘。  
  
 在您處理 WM_INITDIALOG，使用`GetDlgItem`HWND 擷取靜態的預留位置：  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 您再計算的大小和位置的預留位置靜態，因此您可以將放[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘於該位置：  
  
 RECT 矩形；  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 然後，您可以隱藏預留位置 STATIC︰  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 建立和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘在該位置的 HWND:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 若要讓教學課程的有趣，並以產生真實[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘，您必須建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]此時時鐘控制項。 您大部分都可以透過標記完成，而且只需要程式碼後置中的一些事件處理常式即可。 由於本教學課程有關的互通性，以及不控制項的設計，完整程式碼[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘會提供為程式碼區塊，而不指示建置它，或每個部分所代表的意義。 請自由實驗此程式碼，來變更控制項功能的外觀或操作。  
  
 標記如下：  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 這裡是隨附的程式碼後置︰  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 最終結果如下：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 若要比較您產生這個螢幕擷取畫面的程式碼的最後結果，請參閱[Win32 時鐘的互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Win32 時鐘交互操作範例](http://go.microsoft.com/fwlink/?LinkID=160051)
