---
title: "在 WPF 中裝載 Win32 內容 | Microsoft Docs"
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
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 在 WPF 中裝載 Win32 內容
## 必要條件  
 請參閱 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
## Windows Presentation Framework 內的 Win32 逐步解說 \(HwndHost\)  
 若要重複使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式內的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 內容，請使用 <xref:System.Windows.Interop.HwndHost>；這個控制項可以讓 HWND 看起來就像 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容一樣。  如同 <xref:System.Windows.Interop.HwndSource>，<xref:System.Windows.Interop.HwndHost> 的使用方式非常直接：從 <xref:System.Windows.Interop.HwndHost> 衍生並實作 `BuildWindowCore` 和 `DestroyWindowCore` 方法，然後執行個體化 <xref:System.Windows.Interop.HwndHost> 衍生類別 \(Derived Class\)，並將它放在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式內。  
  
 如果您的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 邏輯已經封裝成控制項，您的 `BuildWindowCore` 實作幾乎等於呼叫 `CreateWindow`。  例如，若要在 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] 中建立 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX 控制項：  
  
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
  
 但如果 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼不全然是獨立的 \(Self\-Contained\) 程式碼呢？  如果是這樣，您可以建立 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 對話方塊，並將它的內容嵌入較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中。  此範例顯示 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 和 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] 中的這項作業，不過您也可以使用不同的語言或在命令列中執行此程序。  
  
 從簡單的對話方塊開始，將它編譯成 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 專案。  
  
 接著，將對話方塊引入較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式：  
  
-   將 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 編譯成 Managed \(`/clr`\)  
  
-   將對話方塊轉換成控制項  
  
-   使用 `BuildWindowCore` 和 `DestroyWindowCore` 方法定義 <xref:System.Windows.Interop.HwndHost> 的衍生類別  
  
-   覆寫 `TranslateAccelerator` 方法以處理對話方塊按鍵  
  
-   覆寫 `TabInto` 方法以支援定位  
  
-   覆寫 `OnMnemonic` 方法以支援助憶鍵 \(Mnemonic\)  
  
-   執行個體化 <xref:System.Windows.Interop.HwndHost> 子類別 \(Subclass\)，並將它放在正確的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目底下  
  
### 將對話方塊轉換成控制項  
 您可以使用 WS\_CHILD 和 DS\_CONTROL 樣式將對話方塊轉換成子 HWND。  請進入定義對話方塊的資源檔 \(.rc\)，並找出對話方塊定義的開頭。  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 將第二行改成：  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 這個動作不會將它完全封裝成獨立的控制項；您還是必須呼叫 `IsDialogMessage()`，[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 才能處理某些訊息，但是控制項變更確實提供了一種直接的方式，使您可以將這些控制項放到其他 HWND 內。  
  
## 子類別 HwndHost  
 請匯入下列命名空間：  
  
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
  
 接著，請建立 <xref:System.Windows.Interop.HwndHost> 的衍生類別，並覆寫 `BuildWindowCore` 和 `DestroyWindowCore` 方法：  
  
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
  
 在這裡，您會使用 `CreateDialog` 建立實際上是一個控制項的對話方塊。  因為這是在 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 內率先呼叫的其中一個方法，所以您也應該呼叫稍後所要定義的函式 \(名稱為 `InitializeGlobals()`\)，以執行某些標準的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 初始設定：  
  
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
  
### 覆寫 TranslateAccelerator 方法以處理對話方塊按鍵  
 如果您在此時執行這個範例，對話方塊便會顯示，但是它會忽略讓對話方塊成為功能對話方塊的所有鍵盤處理。  您應該立即覆寫 `TranslateAccelerator` 實作 \(來自 `IKeyboardInputSink`，也就是 <xref:System.Windows.Interop.HwndHost> 所實作的介面\)。  當應用程式收到 WM\_KEYDOWN 和 WM\_SYSKEYDOWN 時，便會呼叫這個方法。  
  
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
  
 這是一段很長的程式碼，因此可以使用某些較詳盡的說明。  首先是使用 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] 和 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] 巨集的程式碼；請注意，winuser.h 中已定義一個名為 `TranslateAccelerator` 的巨集：  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 因此，請務必定義 `TranslateAccelerator` 方法，而非 `TranslateAcceleratorW` 方法。  
  
 同樣地，此程式碼也同時有 Unmanaged winuser.h MSG 和 Managed `Microsoft::Win32::MSG` 結構 \(Struct\)。  您可以使用 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` 運算子，以釐清這兩者。  
  
```  
  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 這兩個 MSG 擁有相同的資料，但是某些情況下使用 Unmanaged 定義比較容易，因此在這個範例中，您可以定義明顯的轉換常式。  
  
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
  
 返回 `TranslateAccelerator`。  基本原則是呼叫 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 函式 `IsDialogMessage` 來盡量完成許多工作，但是 `IsDialogMessage` 無法存取對話方塊以外的任何內容。當使用者在對話方塊內使用 Tab 鍵到處移動，而 Tab 鍵超過對話方塊的最後一個控制項時，您需要呼叫 `IKeyboardInputSite::OnNoMoreStops`，將焦點設定到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 部分。  
  
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
  
 最後，請呼叫 `IsDialogMessage`。  但是 `TranslateAccelerator` 方法的其中一項責任是告知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 您是否已處理按鍵。  如果尚未處理，輸入事件可以在應用程式的其他部分向下和向上傳遞。  在此，您會公開 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 中變通的鍵盤訊息處理，以及輸入架構的性質。  不巧地是，`IsDialogMessage` 不會以任何方式傳回它是否已處理特定按鍵。  更糟的是，它會在不應該處理的按鍵上呼叫 `DispatchMessage()`！  因此您必須對 `IsDialogMessage` 進行反向工程，而且只能針對確定它會處理的按鍵來呼叫它。  
  
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
  
### 覆寫 TabInto 方法以支援定位  
 現在您已實作 `TranslateAccelerator`，使用者可以使用定位鍵瀏覽對話方塊內部，也可以離開對話方塊，跳到較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中。  但是使用者不能跳回對話方塊中。  若要解除這個問題，請覆寫 `TabInto`：  
  
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
  
 `TraversalRequest` 參數會告訴您定位動作是 TAB 還是 SHIFT\+TAB。  
  
### 覆寫 OnMnemonic 方法以支援助憶鍵  
 鍵盤處理已接近完成的階段，但是還有一項工作尚未完成：助憶鍵沒有作用。  如果使用者按下 ALT\-F，焦點不會跳到 \[First name:\] 編輯方塊。  因此，請覆寫 `OnMnemonic` 方法：  
  
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
  
 為什麼這裡呼叫的不是 `IsDialogMessage`？  這裡的問題和前面一樣 \-\- 您必須能夠通知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式碼，讓它知道您的程式碼是否已經處理按鍵，但是 `IsDialogMessage` 無法提供這項功能。  另外還有一個問題，因為如果取得焦點的 HWND 不在對話方塊內，`IsDialogMessage` 就會拒絕處理助憶鍵。  
  
### 執行個體化 HwndHost 衍生類別  
 最後，所有的按鍵和定位鍵支援都已就緒，您可以將 <xref:System.Windows.Interop.HwndHost> 放入較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中。  如果主要應用程式是以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 撰寫，將它放到正確位置最簡單的方法就是在想要放入 <xref:System.Windows.Interop.HwndHost> 的位置，保留空白的 <xref:System.Windows.Controls.Border> 項目。  在這裡您會建立一個名為 `insertHwndHostHere` 的 <xref:System.Windows.Controls.Border>：  
  
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
  
 如此一來，剩下的工作就只有在程式碼序列中找出適當的位置，以便執行個體化 <xref:System.Windows.Interop.HwndHost>，並將它連接到 <xref:System.Windows.Controls.Border>。  在這個範例中，您會將它放在 <xref:System.Windows.Window> 衍生類別的建構函式內：  
  
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
  
 其結果如下：  
  
 ![WPF 應用程式螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/interoparch09.png "InteropArch09")  
  
## 請參閱  
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)