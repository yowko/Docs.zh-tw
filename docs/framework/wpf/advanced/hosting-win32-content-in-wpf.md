---
title: 在 WPF 中裝載 Win32 內容
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: beb7d5e6e1f934b89bb7516eb7e9bbbaad696238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547351"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="31ee3-102">在 WPF 中裝載 Win32 內容</span><span class="sxs-lookup"><span data-stu-id="31ee3-102">Hosting Win32 Content in WPF</span></span>
## <a name="prerequisites"></a><span data-ttu-id="31ee3-103">必要條件</span><span class="sxs-lookup"><span data-stu-id="31ee3-103">Prerequisites</span></span>  
 <span data-ttu-id="31ee3-104">請參閱[WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="31ee3-104">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="31ee3-105">Win32 Windows Presentation Framework (HwndHost) 內的逐步解說</span><span class="sxs-lookup"><span data-stu-id="31ee3-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>  
 <span data-ttu-id="31ee3-106">若要重複使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]內容內[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式會使用<xref:System.Windows.Interop.HwndHost>，這是一個控制項，讓 Hwnd 看起來像[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。</span><span class="sxs-lookup"><span data-stu-id="31ee3-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  <span data-ttu-id="31ee3-107">像<xref:System.Windows.Interop.HwndSource>，<xref:System.Windows.Interop.HwndHost>是直接使用： 衍生自<xref:System.Windows.Interop.HwndHost>並實作`BuildWindowCore`和`DestroyWindowCore`方法，然後具現化您<xref:System.Windows.Interop.HwndHost>衍生類別，並放在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="31ee3-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
 <span data-ttu-id="31ee3-108">如果您[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]邏輯已封裝做為控制項，則您`BuildWindowCore`實作是比呼叫`CreateWindow`。</span><span class="sxs-lookup"><span data-stu-id="31ee3-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span>  <span data-ttu-id="31ee3-109">例如，若要建立[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]LISTBOX 控制項中的[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="31ee3-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-110">但假設[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]不是那麼獨立的程式碼？</span><span class="sxs-lookup"><span data-stu-id="31ee3-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="31ee3-111">因此，您可以建立如果[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊方塊，並將其內容內嵌到較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="31ee3-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="31ee3-112">此範例會示範在[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]，不過它也可能在不同的語言，或在命令列執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="31ee3-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>  
  
 <span data-ttu-id="31ee3-113">使用簡單的對話方塊，會先編譯成啟動[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)][!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="31ee3-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>  
  
 <span data-ttu-id="31ee3-114">接下來中, 導入對話中較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式：</span><span class="sxs-lookup"><span data-stu-id="31ee3-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>  
  
-   <span data-ttu-id="31ee3-115">編譯[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]為受管理 (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="31ee3-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>  
  
-   <span data-ttu-id="31ee3-116">開啟對話方塊控制項</span><span class="sxs-lookup"><span data-stu-id="31ee3-116">Turn the dialog into a control</span></span>  
  
-   <span data-ttu-id="31ee3-117">衍生的類別定義<xref:System.Windows.Interop.HwndHost>與`BuildWindowCore`和`DestroyWindowCore`方法</span><span class="sxs-lookup"><span data-stu-id="31ee3-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>  
  
-   <span data-ttu-id="31ee3-118">覆寫`TranslateAccelerator`方法以處理對話方塊的索引鍵</span><span class="sxs-lookup"><span data-stu-id="31ee3-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>  
  
-   <span data-ttu-id="31ee3-119">覆寫`TabInto`方法，以支援按下 tab 鍵</span><span class="sxs-lookup"><span data-stu-id="31ee3-119">Override `TabInto` method to support tabbing</span></span>  
  
-   <span data-ttu-id="31ee3-120">覆寫`OnMnemonic`方法，以支援助憶鍵</span><span class="sxs-lookup"><span data-stu-id="31ee3-120">Override `OnMnemonic` method to support mnemonics</span></span>  
  
-   <span data-ttu-id="31ee3-121">具現化<xref:System.Windows.Interop.HwndHost>子類別並將其放在右側[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目</span><span class="sxs-lookup"><span data-stu-id="31ee3-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>  
  
### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="31ee3-122">開啟對話方塊控制項</span><span class="sxs-lookup"><span data-stu-id="31ee3-122">Turn the Dialog into a Control</span></span>  
 <span data-ttu-id="31ee3-123">您可以開啟的對話方塊到使用 WS_CHILD 和 DS_CONTROL 樣式的 HWND 的子系。</span><span class="sxs-lookup"><span data-stu-id="31ee3-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span>  <span data-ttu-id="31ee3-124">請移至定義 對話方塊所在的資源檔 (.rc)，並尋找開頭定義的對話方塊：</span><span class="sxs-lookup"><span data-stu-id="31ee3-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 <span data-ttu-id="31ee3-125">變更至第二行：</span><span class="sxs-lookup"><span data-stu-id="31ee3-125">Change the second line to:</span></span>  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 <span data-ttu-id="31ee3-126">此動作不會不完整封裝為獨立的控制項;您仍然需要呼叫`IsDialogMessage()`讓[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]可以處理特定訊息，但控制項變更並提供簡單的方式放置在另一個 HWND 這些控制項。</span><span class="sxs-lookup"><span data-stu-id="31ee3-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>  
  
## <a name="subclass-hwndhost"></a><span data-ttu-id="31ee3-127">HwndHost 子類別</span><span class="sxs-lookup"><span data-stu-id="31ee3-127">Subclass HwndHost</span></span>  
 <span data-ttu-id="31ee3-128">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="31ee3-128">Import the following namespaces:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-129">然後建立的衍生的類別<xref:System.Windows.Interop.HwndHost>並覆寫`BuildWindowCore`和`DestroyWindowCore`方法：</span><span class="sxs-lookup"><span data-stu-id="31ee3-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-130">在此您可以使用`CreateDialog`建立實際上是控制項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="31ee3-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span>  <span data-ttu-id="31ee3-131">由於這是其中一個第一個方法內呼叫[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]，您也應執行某些標準[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]藉由呼叫的函式，您將更新版本中，定義初始化呼叫`InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="31ee3-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>  
  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="31ee3-132">覆寫 translateaccelerator 呼叫方法，以處理對話方塊的索引鍵</span><span class="sxs-lookup"><span data-stu-id="31ee3-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>  
 <span data-ttu-id="31ee3-133">如果您執行此範例現在，您會收到顯示時，對話方塊控制項，但是它會忽略所有處理讓鍵盤對話方塊功能的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="31ee3-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span>  <span data-ttu-id="31ee3-134">您現在應該覆寫`TranslateAccelerator`實作 (來自`IKeyboardInputSink`，介面的<xref:System.Windows.Interop.HwndHost>實作)。</span><span class="sxs-lookup"><span data-stu-id="31ee3-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span>  <span data-ttu-id="31ee3-135">當 WM_KEYDOWN 和 WM_SYSKEYDOWN，接收應用程式時，會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="31ee3-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>  
  
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
  
 <span data-ttu-id="31ee3-136">這是大量程式碼中某項，因此它無法使用某些更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="31ee3-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span>  <span data-ttu-id="31ee3-137">首先，程式碼使用[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]巨集; 您需要知道已有名稱為巨集`TranslateAccelerator`，定義在 winuser.h:</span><span class="sxs-lookup"><span data-stu-id="31ee3-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 <span data-ttu-id="31ee3-138">因此請務必定義`TranslateAccelerator`方法而非`TranslateAcceleratorW`方法。</span><span class="sxs-lookup"><span data-stu-id="31ee3-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>  
  
 <span data-ttu-id="31ee3-139">同樣地，沒有 unmanaged 的 winuser.h MSG 和 managed`Microsoft::Win32::MSG`結構。</span><span class="sxs-lookup"><span data-stu-id="31ee3-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span>  <span data-ttu-id="31ee3-140">您可以使用兩個區分[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]`::`運算子。</span><span class="sxs-lookup"><span data-stu-id="31ee3-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 <span data-ttu-id="31ee3-141">同時 MSGs 具有相同的資料，但有時候很容易使用未受管理的定義，因此在此範例中，您可以定義明顯的轉換常式：</span><span class="sxs-lookup"><span data-stu-id="31ee3-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-142">回到`TranslateAccelerator`。</span><span class="sxs-lookup"><span data-stu-id="31ee3-142">Back to `TranslateAccelerator`.</span></span>  <span data-ttu-id="31ee3-143">基本原則是呼叫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式`IsDialogMessage`盡可能最多工作，但`IsDialogMessage`沒有對話方塊外的任何內容的存取。</span><span class="sxs-lookup"><span data-stu-id="31ee3-143">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="31ee3-144">當使用者索引標籤周圍對話方塊中，按下 tab 鍵時執行超過我們對話方塊中的最後一個控制項時，您需要將焦點設定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由呼叫部分`IKeyboardInputSite::OnNoMoreStops`。</span><span class="sxs-lookup"><span data-stu-id="31ee3-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>  
  
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
  
 <span data-ttu-id="31ee3-145">最後，請呼叫 `IsDialogMessage`。</span><span class="sxs-lookup"><span data-stu-id="31ee3-145">Finally, call `IsDialogMessage`.</span></span>  <span data-ttu-id="31ee3-146">其中一個責任`TranslateAccelerator`方法告訴[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是否您處理按鍵。</span><span class="sxs-lookup"><span data-stu-id="31ee3-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="31ee3-147">如果您並未處理，可以處理輸入的事件和應用程式的其餘的泡泡。</span><span class="sxs-lookup"><span data-stu-id="31ee3-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="31ee3-148">在這裡，您將公開鍵盤 messange 處理的突變和中的輸入架構性質[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31ee3-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="31ee3-149">不幸的是，`IsDialogMessage`不會傳回以任何方式是否處理特定的按鍵輸入。</span><span class="sxs-lookup"><span data-stu-id="31ee3-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span>  <span data-ttu-id="31ee3-150">更糟的是，它會呼叫`DispatchMessage()`上不應該處理的按鍵動作 ！</span><span class="sxs-lookup"><span data-stu-id="31ee3-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="31ee3-151">因此您將需要進行反向工程`IsDialogMessage`，並只針對您知道它的索引鍵將會處理呼叫它：</span><span class="sxs-lookup"><span data-stu-id="31ee3-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>  
  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="31ee3-152">覆寫 TabInto 方法，以支援按下 tab 鍵</span><span class="sxs-lookup"><span data-stu-id="31ee3-152">Override TabInto Method to Support Tabbing</span></span>  
 <span data-ttu-id="31ee3-153">既然您已實作`TranslateAccelerator`，使用者可以使用 tab 鍵周圍對話方塊內方塊並且將定位跳到較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="31ee3-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="31ee3-154">但是，使用者不能跳回對話方塊。</span><span class="sxs-lookup"><span data-stu-id="31ee3-154">But a user cannot tab back into the dialog box.</span></span>  <span data-ttu-id="31ee3-155">若要解決的問題，您覆寫`TabInto`:</span><span class="sxs-lookup"><span data-stu-id="31ee3-155">To solve that, you override `TabInto`:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-156">`TraversalRequest`參數會告訴您的索引標籤的動作是否 tab 或 shift tab。</span><span class="sxs-lookup"><span data-stu-id="31ee3-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="31ee3-157">覆寫 OnMnemonic 方法，以支援助憶鍵</span><span class="sxs-lookup"><span data-stu-id="31ee3-157">Override OnMnemonic Method to Support Mnemonics</span></span>  
 <span data-ttu-id="31ee3-158">鍵盤處理幾乎完成，但有一個項目遺漏 – 助憶鍵無法運作。</span><span class="sxs-lookup"><span data-stu-id="31ee3-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span>  <span data-ttu-id="31ee3-159">如果使用者按下 alt F，焦點 doe 不跳到 「 名字: 「 編輯方塊。</span><span class="sxs-lookup"><span data-stu-id="31ee3-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="31ee3-160">因此，您的覆寫`OnMnemonic`方法：</span><span class="sxs-lookup"><span data-stu-id="31ee3-160">So, you override the `OnMnemonic` method:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-161">為什麼不呼叫`IsDialogMessage`這裡？</span><span class="sxs-lookup"><span data-stu-id="31ee3-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="31ee3-162">視需要能夠通知之前，具有相同的問題[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是否由您的程式碼已處理按鍵，和`IsDialogMessage`無法做到。</span><span class="sxs-lookup"><span data-stu-id="31ee3-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span>  <span data-ttu-id="31ee3-163">這也是第二個問題，因為`IsDialogMessage`拒絕處理助憶鍵，如果已取得焦點的 HWND 不是在對話方塊的方塊內。</span><span class="sxs-lookup"><span data-stu-id="31ee3-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>  
  
### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="31ee3-164">具現化 HwndHost 衍生的類別</span><span class="sxs-lookup"><span data-stu-id="31ee3-164">Instantiate the HwndHost Derived Class</span></span>  
 <span data-ttu-id="31ee3-165">最後，所有的索引鍵和索引標籤支援成為備妥之後，您可以將您<xref:System.Windows.Interop.HwndHost>成較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="31ee3-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="31ee3-166">如果主應用程式以[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，最簡單的方式將它放在正確的位置是將空<xref:System.Windows.Controls.Border>您要將項目的<xref:System.Windows.Interop.HwndHost>。</span><span class="sxs-lookup"><span data-stu-id="31ee3-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span>  <span data-ttu-id="31ee3-167">您在這裡建立<xref:System.Windows.Controls.Border>名為`insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="31ee3-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-168">然後剩下的只有具現化的程式碼序列中尋找的好地方<xref:System.Windows.Interop.HwndHost>與它連接至<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="31ee3-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span>  <span data-ttu-id="31ee3-169">在此範例中，您會將它放在建構函式內<xref:System.Windows.Window>衍生的類別：</span><span class="sxs-lookup"><span data-stu-id="31ee3-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>  
  
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
  
 <span data-ttu-id="31ee3-170">可讓您：</span><span class="sxs-lookup"><span data-stu-id="31ee3-170">Which gives you:</span></span>  
  
 <span data-ttu-id="31ee3-171">![WPF 應用程式螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="31ee3-171">![WPF application screen shot](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ee3-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31ee3-172">See Also</span></span>  
 [<span data-ttu-id="31ee3-173">WPF 和 Win32 交互操作</span><span class="sxs-lookup"><span data-stu-id="31ee3-173">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
