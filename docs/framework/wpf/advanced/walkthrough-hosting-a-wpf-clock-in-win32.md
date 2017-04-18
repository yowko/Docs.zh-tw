---
title: "逐步解說：在 Win32 中裝載 WPF 時鐘 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "互通性 [WPF], 教學課程"
  - "互通性 [WPF], Win32"
  - "Win32 程式碼, WPF 互通"
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 逐步解說：在 Win32 中裝載 WPF 時鐘
若要將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 放入 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式內，請使用 <xref:System.Windows.Interop.HwndSource>，它會提供包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的 HWND。  首先請建立 <xref:System.Windows.Interop.HwndSource>，並為其指定類似 CreateWindow 的參數。  接著告知 <xref:System.Windows.Interop.HwndSource> 要包含的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  最後，請從 <xref:System.Windows.Interop.HwndSource> 取得 HWND。  此逐步解說在說明如何在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式內建立混合的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，以實作作業系統的 \[**日期和時間內容**\] 對話方塊。  
  
## 必要條件  
 請參閱 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
## 如何使用本教學課程  
 本教學課程的重點為產生互通性應用程式的重要步驟。  教學課程中以 [Win32 時鐘互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051) \(英文\) 做為教學輔助，不過這個範例反映的是最終成果。  本教學課程記載步驟的方式就像您以自己現有的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 專案 \(可能是預先存在的專案\) 開始作業，並將裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 加入您的應用程式中。  您可以將您的最終成果與 [Win32 時鐘互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)做比較。  
  
## Win32 內的 Windows Presentation Framework 逐步解說 \(HwndSource\)  
 下圖顯示本教學課程預定產生的最終成果：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch06.png "InteropArch06")  
  
 您可以在 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 中建立 C\+\+ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 專案，並使用對話方塊編輯器建立下列項目，以便重新建立這個對話方塊：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch07.png "InteropArch07")  
  
 \(您不需要使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 來使用 <xref:System.Windows.Interop.HwndSource>，也不需要使用 C\+\+ 來撰寫 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式，但這是執行這項工作相當典型的方式，而且可為其本身提供逐步的教學說明\)。  
  
 您必須完成五個特殊的子步驟，才能將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘放入對話方塊中。  
  
1.  在 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 中變更專案設定，讓您的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 專案能夠呼叫 Managed 程式碼 \(**\/clr**\)。  
  
2.  在另一個 DLL 中建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>。  
  
3.  將該 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> 放入 <xref:System.Windows.Interop.HwndSource> 內。  
  
4.  使用 <xref:System.Windows.Interop.HwndSource.Handle%2A> 屬性取得該 <xref:System.Windows.Controls.Page> 的 HWND。  
  
5.  使用 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 決定在完整的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式內放置 HWND 的位置。  
  
## \/clr  
 第一個步驟是要將這個 Unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 專案變成可以呼叫 Managed 程式碼的專案。  使用 \/clr 編譯器選項連結到您想使用的必要 DLL，並調整 Main 方法以搭配 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用。  
  
 若要啟用在 C\+\+ 專案中使用 Managed 程式碼的功能，請以滑鼠右鍵按一下 win32clock 專案，然後選取 \[**屬性**\]。  接著在 \[**一般**\] 屬性頁 \(預設值\) 上，將 Common Language Runtime 支援變更為 `/clr`。  
  
 接下來，加入 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所需 DLL 的參考：PresentationCore.dll、PresentationFramework.dll、System.dll、WindowsBase.dll、UIAutomationProvider.dll 和 UIAutomationTypes.dll   \(下列指示假設作業系統安裝在 C: 磁碟機上\)。  
  
1.  以滑鼠右鍵按一下 win32clock 專案，並選取 \[**參考**\]，然後在該對話方塊內：  
  
2.  以滑鼠右鍵按一下 win32clock，並選取 \[**參考**\]。  
  
3.  按一下 \[**加入新參考**\]，再按一下 \[瀏覽\] 索引標籤，輸入 C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\PresentationCore.dll，然後按 \[確定\]。  
  
4.  對 PresentationFramework.dll 重複相同的動作：C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\PresentationFramework.dll。  
  
5.  對 WindowsBase.dll 重複相同的動作：C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\WindowsBase.dll。  
  
6.  對 UIAutomationTypes.dll 重複相同的動作：C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\UIAutomationTypes.dll。  
  
7.  對 UIAutomationProvider.dll 重複相同的動作：C:\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.0\\UIAutomationProvider.dll。  
  
8.  按一下 \[**加入新參考**\]，選取 System.dll，然後按一下 \[**確定**\]。  
  
9. 按一下 \[**確定**\]，結束用來加入參考的 \[win32clock 屬性頁\]。  
  
 最後，將 `STAThreadAttribute` 加入至 `_tWinMain` 方法以搭配 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用：  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 這個屬性會告知 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]，當它初始化 [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] 時，應該使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]\) 所需的單一執行緒 Apartment 模型 \(STA\)。  
  
## 建立 Windows Presentation Framework 頁面  
 接著建立定義 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> 的 DLL。  最簡單的方法通常是建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> 做為獨立的應用程式，然後再以這種方式撰寫並偵錯 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的部分。  完成之後，可以使用滑鼠右鍵按一下該專案，再按一下 \[**屬性**\]，移到 \[應用程式\]，然後將 \[輸出類型\] 改成 \[Windows 類別庫\]，將專案轉換成 DLL。  
  
 接著 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll 專案可以和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 專案合併 \(一個方案包含兩個專案\) \- 以滑鼠右鍵按一下方案，並選取 \[**加入現有專案**\]。  
  
 若要使用 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 專案中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll，則需要加入參考：  
  
1.  以滑鼠右鍵按一下 win32clock，並選取 \[**參考**\]。  
  
2.  按一下 \[**加入新參考**\]。  
  
3.  按一下 \[**專案**\] 索引標籤。  選取 WPFClock，再按一下 \[確定\]。  
  
4.  按一下 \[**確定**\]，結束用來加入參考的 \[win32clock 屬性頁\]。  
  
## HwndSource  
 接著使用 <xref:System.Windows.Interop.HwndSource>，讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> 看起來像 HWND。  請將下列程式碼區塊加入至 C\+\+ 檔案：  
  
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
  
 這段程式碼較長，可以使用部分說明。  第一個部分是各種不同的子句，因此您不需要完整限定所有的呼叫：  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 接著定義建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容、在其周圍放置 <xref:System.Windows.Interop.HwndSource> 並傳回 HWND 的函式：  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 首先請建立 <xref:System.Windows.Interop.HwndSource>，其參數與 CreateWindow 類似：  
  
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
  
 接著透過呼叫其建構函式的方式，建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別：  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 接著將頁面連接到 <xref:System.Windows.Interop.HwndSource>：  
  
```  
source->RootVisual = page;  
```  
  
 在最後一行，傳回 <xref:System.Windows.Interop.HwndSource> 的 HWND：  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## 定位 Hwnd  
 現在您已經有一個包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘的 HWND，接下來必須將該 HWND 放入 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 對話方塊中。  如果您知道放置 HWND 的正確位置，可直接將大小和位置傳遞至您稍早定義的 `GetHwnd` 函式。  但是您是使用資源檔來定義對話方塊，所以無法確定任何 HWND 的正確位置。  您可以使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 對話方塊編輯器，將 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC 控制項放在要顯示時鐘的位置 \(「在此插入時鐘」\)，並使用該控制項來定位 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘。  
  
 處理 WM\_INITDIALOG 時，您會使用 `GetDlgItem` 來擷取預留位置 STATIC 的 HWND：  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 接著再計算預留位置 STATIC 的大小和位置，使您可以將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘放在該位置：  
  
 RECT rectangle;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 接著您會隱藏預留位置 STATIC：  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 然後在該位置建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘 HWND：  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 為了讓教學課程更為有趣並且產生真實的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘，此時您必須建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘控制項。  您大多可以在標記中執行這項作業，而程式碼後置 \(Code\-Behind\) 中只需包含幾個事件處理常式 \(Event Handler\)。  由於這個教學課程是關於互通性，而不是關於控制項設計，因此這裡提供了 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘的完整程式碼做為程式碼區塊，而沒有建置該段程式碼的指示以及各部分所代表意思。  請依需要使用此程式碼自行學習如何變更控制項的外觀、操作及功能。  
  
 標記如下：  
  
 [!code-xml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 隨附的程式碼後置則如下：  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 最終成果的外觀如下：  
  
 ![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch08.png "InteropArch08")  
  
 若要將您的最終結果與產生此螢幕擷取畫面的程式碼做比較，請參閱 [Win32 時鐘互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Interop.HwndSource>   
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [Win32 時鐘互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)