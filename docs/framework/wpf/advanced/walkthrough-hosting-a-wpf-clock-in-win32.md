---
title: 逐步解說：在 Win32 中裝載 WPF 時鐘
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: ce8209c89430988f57c211d388c6e73b2dc17004
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507884"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>逐步解說：在 Win32 中裝載 WPF 時鐘
把[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式，使用<xref:System.Windows.Interop.HwndSource>，以提供包含 HWND 您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。 第一次建立<xref:System.Windows.Interop.HwndSource>，讓它將與 CreateWindow 類似的參數。  接著您告訴<xref:System.Windows.Interop.HwndSource>關於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容要放在其內。  最後，您可以放大的 HWND <xref:System.Windows.Interop.HwndSource>。 此逐步解說將說明如何建立混合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]實作作業系統的應用程式**日期和時間內容**對話方塊。  
  
## <a name="prerequisites"></a>必要條件  
 請參閱[WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
## <a name="how-to-use-this-tutorial"></a>如何使用本教學課程  
 本教學課程著重在產生交互操作應用程式的重要步驟。 本教學課程做為後盾的範例中， [Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)，但該範例會反映最終產品。 本教學課程中說明的步驟，如同您已啟動與現有[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]您自己的專案，可能是既有的專案，並已新增裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]您的應用程式。 您可以比較最終產品與[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 內 Windows Presentation Framework 的逐步解說 (HwndSource)  
 下圖顯示本教學課程的預期最終產品︰  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 您可以藉由建立 c + + 來重建此對話方塊[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，並使用對話方塊編輯器來建立下列：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (您不需要使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]若要使用<xref:System.Windows.Interop.HwndSource>，而且您不需要使用 c + + 撰寫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式，而這是相當常見的作法，並可逐步進行教學課程說明)。  
  
 您需要完成五個特定的子步驟，才能將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘放在對話方塊：  
  
1.  啟用您[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案呼叫 managed 程式碼 (**/clr**) 中的專案設定 來變更[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]。  
  
2.  建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>中不同的 DLL。  
  
3.  將它放[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>內<xref:System.Windows.Interop.HwndSource>。  
  
4.  取得 HWND<xref:System.Windows.Controls.Page>使用<xref:System.Windows.Interop.HwndSource.Handle%2A>屬性。  
  
5.  使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]決定在何處放置在較大的 HWND[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式  
  
## <a name="clr"></a>/clr  
 第一個步驟是將此 unmanaged[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案成一個可呼叫 managed 程式碼。  您使用 /clr 編譯器選項，將連結至您想要使用，並調整 Main 方法，用於將必要的 Dll [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
 若要啟用 c + + 專案內的 managed 程式碼： 以滑鼠右鍵按一下 win32clock 專案，然後選取**屬性**。  在 **一般**屬性頁 （預設值），變更 Common Language Runtime 支援`/clr`。  
  
 接下來，新增所需 dll 的參考[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll、 PresentationFramework.dll、 System.dll、 WindowsBase.dll、 UIAutomationProvider.dll 和 UIAutomationTypes.dll。 (下列指示假設作業系統安裝在 C: 磁碟機上)。  
  
1.  以滑鼠右鍵按一下 win32clock 專案，然後選取**參考...**，並在該對話方塊內：  
  
2.  以滑鼠右鍵按一下 win32clock 專案，然後選取**參考...**.  
  
3.  按一下 [**加入新參考**、 按一下瀏覽] 索引標籤、 輸入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll，然後按一下 [確定]。  
  
4.  針對 PresentationFramework.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。  
  
5.  針對 WindowsBase.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。  
  
6.  針對 UIAutomationTypes.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。  
  
7.  針對 UIAutomationProvider.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。  
  
8.  按一下 **加入新參考**，選取 System.dll，然後按一下**確定**。  
  
9. 按一下 **確定**結束 win32clock 屬性頁 來新增參考。  
  
 最後，新增`STAThreadAttribute`要`_tWinMain`方法搭配[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 此屬性會告知[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]，在它初始化[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]，它應該使用單一執行緒的 apartment 模型 (STA)，這是所需[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)])。  
  
## <a name="create-a-windows-presentation-framework-page"></a>建立 Windows Presentation Framework 頁面  
 接下來，您可以建立定義的 DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>。 它通常是最簡單的方式建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>做為獨立的應用程式，以及撰寫和偵錯[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分如此。  完成後，該專案可以轉換成 DLL 以滑鼠右鍵按一下專案中，按一下**屬性**、 移至應用程式，並輸出類型變更為 Windows 類別庫。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll 專案可以再結合[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案 （一個方案包含兩個專案） – 以滑鼠右鍵按一下方案，選取**新增 \ 現有專案**。  
  
 若要使用該[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dll[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案中，您需要將參考加入：  
  
1.  以滑鼠右鍵按一下 win32clock 專案，然後選取**參考...**.  
  
2.  按一下 **加入新參考**。  
  
3.  按一下 [專案] 索引標籤。選取 WPFClock，然後按一下 [確定]。  
  
4.  按一下 **確定**結束 win32clock 屬性頁 來新增參考。  
  
## <a name="hwndsource"></a>HwndSource  
 接下來，使用<xref:System.Windows.Interop.HwndSource>進行[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>看起來像 HWND。  您可以將此程式碼區塊新增至 C++ 檔案：  
  
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
  
 接著，您定義來建立函式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容，將<xref:System.Windows.Interop.HwndSource>周圍，並傳回 HWND:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 第一次建立<xref:System.Windows.Interop.HwndSource>，其參數會將與 CreateWindow 類似：  
  
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
  
 您接著建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容類別，藉由呼叫其建構函式：  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 您接著連線頁面以<xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 在最後一行中，會傳回的 HWND 和<xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>定位 Hwnd  
 您現在已包含 HWND[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘，您需要在該 HWND 放入[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊。  如果您知道裏放置 HWND，您可以只傳遞該大小和位置`GetHwnd`您稍早定義的函式。  但是，您已使用資源檔來定義對話方塊，因此，您未完全確定放置任何 HWND 的位置。  您可以使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]對話方塊編輯器來放置[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]靜態可讓您控制您想要前往的時鐘 ("Insert clock here")，然後使用它來定位[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘。  
  
 當您處理 WM_INITDIALOG，您使用 「`GetDlgItem`來擷取預留位置 STATIC 的 HWND:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 您就可以計算的大小和位置，該預留位置 STATIC，所以您可以將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘在該位置：  
  
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
  
 建立教學課程更為有趣，以及產生真實[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘，您必須建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]此時時鐘控制項。 您大部分都可以透過標記完成，而且只需要程式碼後置中的一些事件處理常式即可。 由於本教學課程是有關交互操作而不是控制項設計，完成程式碼[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘會提供為程式碼區塊，而不需要連續指示建置它或每個部分所代表的意義。 請自由實驗此程式碼，來變更控制項功能的外觀或操作。  
  
 標記如下：  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 這裡是隨附的程式碼後置︰  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 最終結果如下：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 若要比較的程式碼產生此螢幕擷取畫面，您最後結果，請參閱[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)
