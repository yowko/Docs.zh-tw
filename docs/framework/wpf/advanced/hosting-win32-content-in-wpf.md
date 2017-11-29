---
title: "在 WPF 中裝載 Win32 內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e82d18cd765fc3ac4f4982a71d187a3741f4f03a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="hosting-win32-content-in-wpf"></a>在 WPF 中裝載 Win32 內容
## <a name="prerequisites"></a>必要條件  
 請參閱[WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Win32 Windows Presentation Framework (HwndHost) 內的逐步解說  
 若要重複使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]內容內[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式會使用<xref:System.Windows.Interop.HwndHost>，這是一個控制項，讓 Hwnd 看起來像[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。  像<xref:System.Windows.Interop.HwndSource>，<xref:System.Windows.Interop.HwndHost>是直接使用： 衍生自<xref:System.Windows.Interop.HwndHost>並實作`BuildWindowCore`和`DestroyWindowCore`方法，然後具現化您<xref:System.Windows.Interop.HwndHost>衍生類別，並放在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
 如果您[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]邏輯已封裝做為控制項，則您`BuildWindowCore`實作是比呼叫`CreateWindow`。  例如，若要建立[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]LISTBOX 控制項中的[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:  
  
```  
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
    HWND handle = CreateWindowEx(0, L"LISTBOX",   
    L"this is a Win32 listbox",  
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY  
    | WS_VSCROLL | WS_BORDER,  
    0, 0, // x, y  
    30, 70, // height, width  
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd  
    0, // hmenu  
    0, // hinstance  
    0); // lparam  
  
    return HandleRef(this, IntPtr(handle));  
}  
  
virtual void DestroyWindowCore(HandleRef hwnd) override {  
    // HwndHost will dispose the hwnd for us  
}  
```  
  
 但假設[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]不是那麼獨立的程式碼？ 因此，您可以建立如果[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊方塊，並將其內容內嵌到較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  此範例會示範在[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]，不過它也可能在不同的語言，或在命令列執行這項操作。  
  
 使用簡單的對話方塊，會先編譯成啟動[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)][!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]專案。  
  
 接下來中, 導入對話中較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式：  
  
-   編譯[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]為受管理 (`/clr`)  
  
-   開啟對話方塊控制項  
  
-   衍生的類別定義<xref:System.Windows.Interop.HwndHost>與`BuildWindowCore`和`DestroyWindowCore`方法  
  
-   覆寫`TranslateAccelerator`方法以處理對話方塊的索引鍵  
  
-   覆寫`TabInto`方法，以支援按下 tab 鍵  
  
-   覆寫`OnMnemonic`方法，以支援助憶鍵  
  
-   具現化<xref:System.Windows.Interop.HwndHost>子類別並將其放在右側[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目  
  
### <a name="turn-the-dialog-into-a-control"></a>開啟對話方塊控制項  
 您可以開啟的對話方塊到使用 WS_CHILD 和 DS_CONTROL 樣式的 HWND 的子系。  請移至定義 對話方塊所在的資源檔 (.rc)，並尋找開頭定義的對話方塊：  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 變更至第二行：  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 此動作不會不完整封裝為獨立的控制項;您仍然需要呼叫`IsDialogMessage()`讓[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]可以處理特定訊息，但控制項變更並提供簡單的方式放置在另一個 HWND 這些控制項。  
  
## <a name="subclass-hwndhost"></a>HwndHost 子類別  
 匯入下列命名空間：  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 然後建立的衍生的類別<xref:System.Windows.Interop.HwndHost>並覆寫`BuildWindowCore`和`DestroyWindowCore`方法：  
  
```  
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {  
    private:  
        HWND dialog;  
  
    protected:   
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
            InitializeGlobals();   
            dialog = CreateDialog(hInstance,   
                MAKEINTRESOURCE(IDD_DIALOG1),   
                (HWND) hwndParent.Handle.ToPointer(),  
                (DLGPROC) About);   
            return HandleRef(this, IntPtr(dialog));  
        }  
  
        virtual void DestroyWindowCore(HandleRef hwnd) override {  
            // hwnd will be disposed for us  
        }  
```  
  
 在此您可以使用`CreateDialog`建立實際上是控制項的對話方塊。  由於這是其中一個第一個方法內呼叫[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]，您也應執行某些標準[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]藉由呼叫的函式，您將更新版本中，定義初始化呼叫`InitializeGlobals()`:  
  
```  
bool initialized = false;  
    void InitializeGlobals() {  
        if (initialized) return;  
        initialized = true;  
  
        // TODO: Place code here.  
        MSG msg;  
        HACCEL hAccelTable;  
  
        // Initialize global strings  
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);  
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);  
        MyRegisterClass(hInstance);  
```  
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>覆寫 translateaccelerator 呼叫方法，以處理對話方塊的索引鍵  
 如果您執行此範例現在，您會收到顯示時，對話方塊控制項，但是它會忽略所有處理讓鍵盤對話方塊功能的對話方塊。  您現在應該覆寫`TranslateAccelerator`實作 (來自`IKeyboardInputSink`，介面的<xref:System.Windows.Interop.HwndHost>實作)。  當 WM_KEYDOWN 和 WM_SYSKEYDOWN，接收應用程式時，會呼叫這個方法。  
  
```  
#undef TranslateAccelerator  
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
            ModifierKeys modifiers) override   
        {  
            ::MSG m = ConvertMessage(msg);  
  
            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know   
            // what to do when it reaches the last tab stop  
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
                TraversalRequest^ request = nullptr;  
  
                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
                    // this code should work, but there’s a bug with interop shift-tab in current builds                      
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
                }  
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {  
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
                }  
  
                if (request != nullptr)  
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
  
            }  
  
            // Only call IsDialogMessage for keys it will do something with.  
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
                switch (m.wParam) {  
                    case VK_TAB:  
                    case VK_LEFT:  
                    case VK_UP:  
                    case VK_RIGHT:  
                    case VK_DOWN:  
                    case VK_EXECUTE:  
                    case VK_RETURN:  
                    case VK_ESCAPE:  
                    case VK_CANCEL:  
                        IsDialogMessage(dialog, &m);  
                        // IsDialogMessage should be called ProcessDialogMessage --  
                        // it processes messages without ever really telling you  
                        // if it handled a specific message or not  
                        return true;  
                }  
            }  
  
            return false; // not a key we handled  
        }  
```  
  
 這是大量程式碼中某項，因此它無法使用某些更詳細的說明。  首先，程式碼使用[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]巨集; 您需要知道已有名稱為巨集`TranslateAccelerator`，定義在 winuser.h:  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 因此請務必定義`TranslateAccelerator`方法而非`TranslateAcceleratorW`方法。  
  
 同樣地，沒有 unmanaged 的 winuser.h MSG 和 managed`Microsoft::Win32::MSG`結構。  您可以使用兩個區分[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]`::`運算子。  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 同時 MSGs 具有相同的資料，但有時候很容易使用未受管理的定義，因此在此範例中，您可以定義明顯的轉換常式：  
  
```  
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {  
    ::MSG m;  
    m.hwnd = (HWND) msg.hwnd.ToPointer();  
    m.lParam = (LPARAM) msg.lParam.ToPointer();  
    m.message = msg.message;  
    m.wParam = (WPARAM) msg.wParam.ToPointer();  
  
    m.time = msg.time;  
  
    POINT pt;  
    pt.x = msg.pt_x;  
    pt.y = msg.pt_y;  
    m.pt = pt;  
  
    return m;  
}  
```  
  
 回到`TranslateAccelerator`。  基本原則是呼叫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式`IsDialogMessage`盡可能最多工作，但`IsDialogMessage`沒有對話方塊外的任何內容的存取。 當使用者索引標籤周圍對話方塊中，按下 tab 鍵時執行超過我們對話方塊中的最後一個控制項時，您需要將焦點設定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由呼叫部分`IKeyboardInputSite::OnNoMoreStops`。  
  
```  
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know   
// what to do when it reaches the last tab stop  
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
    TraversalRequest^ request = nullptr;  
  
    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
    }  
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
    }  
  
    if (request != nullptr)  
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
}  
```  
  
 最後，請呼叫 `IsDialogMessage`。  其中一個責任`TranslateAccelerator`方法告訴[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是否您處理按鍵。 如果您並未處理，可以處理輸入的事件和應用程式的其餘的泡泡。 在這裡，您將公開鍵盤 messange 處理的突變和中的輸入架構性質[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]。 不幸的是，`IsDialogMessage`不會傳回以任何方式是否處理特定的按鍵輸入。  更糟的是，它會呼叫`DispatchMessage()`上不應該處理的按鍵動作 ！  因此您將需要進行反向工程`IsDialogMessage`，並只針對您知道它的索引鍵將會處理呼叫它：  
  
```  
// Only call IsDialogMessage for keys it will do something with.  
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
    switch (m.wParam) {  
        case VK_TAB:  
        case VK_LEFT:  
        case VK_UP:  
        case VK_RIGHT:  
        case VK_DOWN:  
        case VK_EXECUTE:  
        case VK_RETURN:  
        case VK_ESCAPE:  
        case VK_CANCEL:  
            IsDialogMessage(dialog, &m);  
            // IsDialogMessage should be called ProcessDialogMessage --  
            // it processes messages without ever really telling you  
            // if it handled a specific message or not  
            return true;  
    }  
```  
  
### <a name="override-tabinto-method-to-support-tabbing"></a>覆寫 TabInto 方法，以支援按下 tab 鍵  
 既然您已實作`TranslateAccelerator`，使用者可以使用 tab 鍵周圍對話方塊內方塊並且將定位跳到較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  但是，使用者不能跳回對話方塊。  若要解決的問題，您覆寫`TabInto`:  
  
```  
public:   
    virtual bool TabInto(TraversalRequest^ request) override {  
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {  
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
            SetFocus(lastTabStop);  
        }  
        else {  
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
            SetFocus(firstTabStop);  
        }  
        return true;  
    }  
```  
  
 `TraversalRequest`參數會告訴您的索引標籤的動作是否 tab 或 shift tab。  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a>覆寫 OnMnemonic 方法，以支援助憶鍵  
 鍵盤處理幾乎完成，但有一個項目遺漏 – 助憶鍵無法運作。  如果使用者按下 alt F，焦點 doe 不跳到 「 名字: 「 編輯方塊。 因此，您的覆寫`OnMnemonic`方法：  
  
```  
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {  
    ::MSG m = ConvertMessage(msg);  
  
    // If it's one of our mnemonics, set focus to the appropriate hwnd  
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {  
        int dialogitem = 9999;  
        switch (m.wParam) {  
            case 's': dialogitem = IDOK; break;  
            case 'c': dialogitem = IDCANCEL; break;  
            case 'f': dialogitem = IDC_EDIT1; break;  
            case 'l': dialogitem = IDC_EDIT2; break;  
            case 'p': dialogitem = IDC_EDIT3; break;  
            case 'a': dialogitem = IDC_EDIT4; break;  
            case 'i': dialogitem = IDC_EDIT5; break;  
            case 't': dialogitem = IDC_EDIT6; break;  
            case 'z': dialogitem = IDC_EDIT7; break;  
        }  
        if (dialogitem != 9999) {  
            HWND hwnd = GetDlgItem(dialog, dialogitem);  
            SetFocus(hwnd);  
            return true;  
        }  
    }  
    return false; // key unhandled  
};  
```  
  
 為什麼不呼叫`IsDialogMessage`這裡？  視需要能夠通知之前，具有相同的問題[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是否由您的程式碼已處理按鍵，和`IsDialogMessage`無法做到。  這也是第二個問題，因為`IsDialogMessage`拒絕處理助憶鍵，如果已取得焦點的 HWND 不是在對話方塊的方塊內。  
  
### <a name="instantiate-the-hwndhost-derived-class"></a>具現化 HwndHost 衍生的類別  
 最後，所有的索引鍵和索引標籤支援成為備妥之後，您可以將您<xref:System.Windows.Interop.HwndHost>成較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  如果主應用程式以[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，最簡單的方式將它放在正確的位置是將空<xref:System.Windows.Controls.Border>您要將項目的<xref:System.Windows.Interop.HwndHost>。  您在這裡建立<xref:System.Windows.Controls.Border>名為`insertHwndHostHere`:  
  
```  
<Window x:Class="WPFApplication1.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Windows Presentation Framework Application"  
    Loaded="Window1_Loaded"  
    >  
    <StackPanel>  
        <Button Content="WPF button"/>  
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>  
        <Button Content="WPF button"/>  
    </StackPanel>  
</Window>  
```  
  
 然後剩下的只有具現化的程式碼序列中尋找的好地方<xref:System.Windows.Interop.HwndHost>與它連接至<xref:System.Windows.Controls.Border>。  在此範例中，您會將它放在建構函式內<xref:System.Windows.Window>衍生的類別：  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 可讓您：  
  
 ![WPF 應用程式螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")  
  
## <a name="see-also"></a>另請參閱  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
