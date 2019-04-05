---
title: 在 WPF 中裝載 Win32 內容
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 8773cac1e421ecdca036e88d79797dae16f72b17
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055075"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="8a87a-102">在 WPF 中裝載 Win32 內容</span><span class="sxs-lookup"><span data-stu-id="8a87a-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a87a-103">必要條件</span><span class="sxs-lookup"><span data-stu-id="8a87a-103">Prerequisites</span></span>

<span data-ttu-id="8a87a-104">請參閱[WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="8a87a-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="8a87a-105">逐步解說中的 Win32 內 Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="8a87a-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="8a87a-106">若要重複使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]內的內容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，使用<xref:System.Windows.Interop.HwndHost>，即會看起來像 Hwnd 控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。</span><span class="sxs-lookup"><span data-stu-id="8a87a-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="8a87a-107">類似<xref:System.Windows.Interop.HwndSource>，<xref:System.Windows.Interop.HwndHost>是直接使用： 衍生自<xref:System.Windows.Interop.HwndHost>並實作`BuildWindowCore`並`DestroyWindowCore`方法，然後具現化您<xref:System.Windows.Interop.HwndHost>衍生類別，並將其內部放置您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a87a-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="8a87a-108">如果您[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]邏輯已封裝做為控制項，則您`BuildWindowCore`實作會比呼叫`CreateWindow`。</span><span class="sxs-lookup"><span data-stu-id="8a87a-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="8a87a-109">例如，若要建立[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]LISTBOX 控制項中的[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8a87a-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>

```cpp
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

<span data-ttu-id="8a87a-110">但假設[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]不是那麼獨立的程式碼嗎？</span><span class="sxs-lookup"><span data-stu-id="8a87a-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="8a87a-111">因此，您可以建立如果[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊方塊中，並將其內容內嵌至更大的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a87a-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="8a87a-112">此範例會示範這[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]和[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]，不過它也可在不同的語言，或在命令列執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="8a87a-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="8a87a-113">開始使用簡單的對話方塊，會編譯成[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)][!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="8a87a-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>

<span data-ttu-id="8a87a-114">接下來，引入 [] 對話方塊中較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式：</span><span class="sxs-lookup"><span data-stu-id="8a87a-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="8a87a-115">編譯[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]為受管理 (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="8a87a-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>

- <span data-ttu-id="8a87a-116">變成控制項 對話方塊</span><span class="sxs-lookup"><span data-stu-id="8a87a-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="8a87a-117">定義衍生的類別<xref:System.Windows.Interop.HwndHost>具有`BuildWindowCore`和`DestroyWindowCore`方法</span><span class="sxs-lookup"><span data-stu-id="8a87a-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="8a87a-118">覆寫`TranslateAccelerator`方法，以處理對話方塊的索引鍵</span><span class="sxs-lookup"><span data-stu-id="8a87a-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="8a87a-119">覆寫`TabInto`方法，以支援定位停駐點</span><span class="sxs-lookup"><span data-stu-id="8a87a-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="8a87a-120">覆寫`OnMnemonic`方法，以支援助憶鍵</span><span class="sxs-lookup"><span data-stu-id="8a87a-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="8a87a-121">具現化<xref:System.Windows.Interop.HwndHost>子類別並將它放在右邊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目</span><span class="sxs-lookup"><span data-stu-id="8a87a-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="8a87a-122">變成控制項 對話方塊</span><span class="sxs-lookup"><span data-stu-id="8a87a-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="8a87a-123">您可以將對話方塊轉換成使用 WS_CHILD 和 DS_CONTROL 樣式的 HWND 的子系。</span><span class="sxs-lookup"><span data-stu-id="8a87a-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="8a87a-124">移入其中定義的對話方塊中，資源檔 (.rc)，並尋找 [] 對話方塊中定義的開頭：</span><span class="sxs-lookup"><span data-stu-id="8a87a-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="8a87a-125">將第二個一行變更為：</span><span class="sxs-lookup"><span data-stu-id="8a87a-125">Change the second line to:</span></span>

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="8a87a-126">此動作不會不完整它封裝成獨立的控制項;您仍然需要呼叫`IsDialogMessage()`因此[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]可以處理特定訊息，但控制項變更並提供直接的方法，將放在另一個 HWND 內的控制項。</span><span class="sxs-lookup"><span data-stu-id="8a87a-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="8a87a-127">子類別 HwndHost</span><span class="sxs-lookup"><span data-stu-id="8a87a-127">Subclass HwndHost</span></span>

<span data-ttu-id="8a87a-128">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="8a87a-128">Import the following namespaces:</span></span>

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

<span data-ttu-id="8a87a-129">然後建立的衍生的類別<xref:System.Windows.Interop.HwndHost>，並覆寫`BuildWindowCore`和`DestroyWindowCore`方法：</span><span class="sxs-lookup"><span data-stu-id="8a87a-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

```cpp
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

<span data-ttu-id="8a87a-130">您在這裡使用`CreateDialog`建立實際上是控制項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8a87a-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="8a87a-131">由於這是其中一個第一個方法內呼叫[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]，您應該也會執行一些標準[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]藉由呼叫的函式，您將在更新版本中，定義初始化呼叫`InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="8a87a-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

```cpp
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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="8a87a-132">覆寫 TranslateAccelerator 方法以處理對話方塊的索引鍵</span><span class="sxs-lookup"><span data-stu-id="8a87a-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="8a87a-133">如果您執行此範例現在，就會收到顯示的對話方塊控制項，但是它會忽略所有的鍵盤處理，讓對話方塊功能的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8a87a-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="8a87a-134">您現在應該覆寫`TranslateAccelerator`實作 (這是來自`IKeyboardInputSink`，介面，<xref:System.Windows.Interop.HwndHost>實作)。</span><span class="sxs-lookup"><span data-stu-id="8a87a-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="8a87a-135">當應用程式收到 WM_KEYDOWN 和 WM_SYSKEYDOWN 時，會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="8a87a-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

```cpp
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

<span data-ttu-id="8a87a-136">這是許多部分的程式碼，因此它無法使用一些更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="8a87a-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="8a87a-137">首先，程式碼使用[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]並[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]巨集; 您需要知道已有名稱為巨集`TranslateAccelerator`，其定義於 winuser.h:</span><span class="sxs-lookup"><span data-stu-id="8a87a-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="8a87a-138">因此請務必定義`TranslateAccelerator`方法而非`TranslateAcceleratorW`方法。</span><span class="sxs-lookup"><span data-stu-id="8a87a-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="8a87a-139">同樣地，沒有未受管理的 winuser.h MSG 和 managed`Microsoft::Win32::MSG`結構。</span><span class="sxs-lookup"><span data-stu-id="8a87a-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="8a87a-140">您可以使用兩個釐清[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]`::`運算子。</span><span class="sxs-lookup"><span data-stu-id="8a87a-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
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

<span data-ttu-id="8a87a-141">回到`TranslateAccelerator`。</span><span class="sxs-lookup"><span data-stu-id="8a87a-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="8a87a-142">基本原則就是呼叫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式`IsDialogMessage`若要盡可能執行工作越好，但`IsDialogMessage`並沒有存取權的對話方塊外的任何內容。</span><span class="sxs-lookup"><span data-stu-id="8a87a-142">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="8a87a-143">當 [使用者] 索引標籤周圍的對話方塊中，按下 tab 鍵時執行過去在對話方塊中的最後一個控制項時，您需要將焦點設定為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分，藉由呼叫`IKeyboardInputSite::OnNoMoreStops`。</span><span class="sxs-lookup"><span data-stu-id="8a87a-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

```cpp
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

<span data-ttu-id="8a87a-144">最後，請呼叫 `IsDialogMessage`。</span><span class="sxs-lookup"><span data-stu-id="8a87a-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="8a87a-145">但的責任之一`TranslateAccelerator`方法告訴[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是否您處理的按鍵輸入與否。</span><span class="sxs-lookup"><span data-stu-id="8a87a-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="8a87a-146">如果您沒有處理，可以處理輸入的事件和應用程式的其餘部分的泡泡。</span><span class="sxs-lookup"><span data-stu-id="8a87a-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="8a87a-147">在這裡，您會在此對話方塊中公開鍵盤 messange 處理的小怪癖和中的輸入架構性質[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a87a-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="8a87a-148">不幸的是，`IsDialogMessage`不會傳回以任何方式是否處理特定的按鍵輸入。</span><span class="sxs-lookup"><span data-stu-id="8a87a-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="8a87a-149">更糟的是，它會呼叫`DispatchMessage()`上不應該處理的按鍵動作 ！</span><span class="sxs-lookup"><span data-stu-id="8a87a-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="8a87a-150">因此您必須進行反向工程`IsDialogMessage`，並只針對您知道它的索引鍵將會處理呼叫它：</span><span class="sxs-lookup"><span data-stu-id="8a87a-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

```cpp
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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="8a87a-151">覆寫 TabInto 方法，以支援定位停駐點</span><span class="sxs-lookup"><span data-stu-id="8a87a-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="8a87a-152">既然您已實作`TranslateAccelerator`，使用者可以使用 tab 鍵周圍內對話方塊方塊並且將定位跳到較大者[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a87a-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="8a87a-153">但是，使用者不能跳回對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8a87a-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="8a87a-154">若要解決的問題，您覆寫`TabInto`:</span><span class="sxs-lookup"><span data-stu-id="8a87a-154">To solve that, you override `TabInto`:</span></span>

```cpp
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

<span data-ttu-id="8a87a-155">`TraversalRequest`參數會告訴您是否 索引標籤上的動作 索引標籤或 shift 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8a87a-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="8a87a-156">覆寫 OnMnemonic 方法，以支援助憶鍵</span><span class="sxs-lookup"><span data-stu-id="8a87a-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="8a87a-157">鍵盤處理幾乎已完成，但有一個項目遺漏 – 助憶鍵無法運作。</span><span class="sxs-lookup"><span data-stu-id="8a87a-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="8a87a-158">如果使用者按下 alt-F，焦點 doe 並未跳至 「 名字:"編輯方塊。</span><span class="sxs-lookup"><span data-stu-id="8a87a-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="8a87a-159">因此，您的覆寫`OnMnemonic`方法：</span><span class="sxs-lookup"><span data-stu-id="8a87a-159">So, you override the `OnMnemonic` method:</span></span>

```cpp
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

<span data-ttu-id="8a87a-160">為什麼不呼叫`IsDialogMessage`這裡？</span><span class="sxs-lookup"><span data-stu-id="8a87a-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="8a87a-161">如之前，您必須能夠通知，您會擁有相同的問題[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式碼，您的程式碼處理的按鍵輸入，或不是，是否和`IsDialogMessage`無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="8a87a-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="8a87a-162">另外還有第二個的問題，因為`IsDialogMessage`拒絕處理這個助憶鍵，如果具有焦點的 HWND 不是在對話方塊的方塊內。</span><span class="sxs-lookup"><span data-stu-id="8a87a-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="8a87a-163">具現化 HwndHost 衍生的類別</span><span class="sxs-lookup"><span data-stu-id="8a87a-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="8a87a-164">最後，所有的索引鍵和索引標籤支援已就緒，您可以將您<xref:System.Windows.Interop.HwndHost>成較大[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a87a-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="8a87a-165">如果主應用程式以[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，將它放在正確的位置最簡單的方式是將空<xref:System.Windows.Controls.Border>項目，您要放置<xref:System.Windows.Interop.HwndHost>。</span><span class="sxs-lookup"><span data-stu-id="8a87a-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="8a87a-166">您在此處建立<xref:System.Windows.Controls.Border>名為`insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="8a87a-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

```xaml
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

<span data-ttu-id="8a87a-167">然後是具現化的程式碼序列中尋找的好地方<xref:System.Windows.Interop.HwndHost>並將其連接到<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="8a87a-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="8a87a-168">在此範例中，您會將它放在建構函式內<xref:System.Windows.Window>衍生的類別：</span><span class="sxs-lookup"><span data-stu-id="8a87a-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

<span data-ttu-id="8a87a-169">可讓您：</span><span class="sxs-lookup"><span data-stu-id="8a87a-169">Which gives you:</span></span>

<span data-ttu-id="8a87a-170">![WPF 應用程式螢幕擷取畫面](./media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="8a87a-170">![WPF application screenshot](./media/interoparch09.PNG "InteropArch09")</span></span>

## <a name="see-also"></a><span data-ttu-id="8a87a-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a87a-171">See also</span></span>

- [<span data-ttu-id="8a87a-172">WPF 和 Win32 互通</span><span class="sxs-lookup"><span data-stu-id="8a87a-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
