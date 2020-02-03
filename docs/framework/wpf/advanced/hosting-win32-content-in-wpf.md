---
title: 裝載 Win32 內容
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b3113d9f3146e1590363dc9db6f751a429dda74b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747021"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="34267-102">在 WPF 中裝載 Win32 內容</span><span class="sxs-lookup"><span data-stu-id="34267-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34267-103">必要條件</span><span class="sxs-lookup"><span data-stu-id="34267-103">Prerequisites</span></span>

<span data-ttu-id="34267-104">請參閱[WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="34267-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="34267-105">Windows Presentation Framework （HwndHost）中的 Win32 逐步解說</span><span class="sxs-lookup"><span data-stu-id="34267-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="34267-106">若要在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式內重複使用 Win32 內容，請使用 <xref:System.Windows.Interop.HwndHost>，這是讓 Hwnd 看起來像 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="34267-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="34267-107">如同 <xref:System.Windows.Interop.HwndSource>，<xref:System.Windows.Interop.HwndHost> 可以直接使用：從 <xref:System.Windows.Interop.HwndHost> 衍生並執行 `BuildWindowCore` 和 `DestroyWindowCore` 方法，然後將您 <xref:System.Windows.Interop.HwndHost> 衍生的類別具現化，並將它放在您的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="34267-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="34267-108">如果您的 Win32 邏輯已封裝為控制項，則您的 `BuildWindowCore` 實作為 `CreateWindow`的呼叫就少了。</span><span class="sxs-lookup"><span data-stu-id="34267-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="34267-109">例如，若要在中C++建立 Win32 LISTBOX 控制項：</span><span class="sxs-lookup"><span data-stu-id="34267-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

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

<span data-ttu-id="34267-110">但是，假設 Win32 程式碼不是完全獨立的，</span><span class="sxs-lookup"><span data-stu-id="34267-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="34267-111">若是如此，您可以建立 Win32 對話方塊，並將其內容內嵌至較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="34267-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="34267-112">此範例會在 Visual Studio 和C++中顯示這項功能，不過也可以使用不同的語言或在命令列中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="34267-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="34267-113">從簡單的對話方塊開始，它會編譯成C++ DLL 專案。</span><span class="sxs-lookup"><span data-stu-id="34267-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="34267-114">接下來，在較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中引進對話方塊：</span><span class="sxs-lookup"><span data-stu-id="34267-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="34267-115">將 DLL 編譯為受控（`/clr`）</span><span class="sxs-lookup"><span data-stu-id="34267-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="34267-116">將對話變成控制項</span><span class="sxs-lookup"><span data-stu-id="34267-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="34267-117">使用 `BuildWindowCore` 和 `DestroyWindowCore` 方法來定義 <xref:System.Windows.Interop.HwndHost> 的衍生類別</span><span class="sxs-lookup"><span data-stu-id="34267-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="34267-118">覆寫 `TranslateAccelerator` 方法以處理對話方塊索引鍵</span><span class="sxs-lookup"><span data-stu-id="34267-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="34267-119">覆寫 `TabInto` 方法以支援 tab 鍵</span><span class="sxs-lookup"><span data-stu-id="34267-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="34267-120">覆寫 `OnMnemonic` 方法以支援助憶鍵</span><span class="sxs-lookup"><span data-stu-id="34267-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="34267-121">將 <xref:System.Windows.Interop.HwndHost> 子類別具現化，並將其放在右邊的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素之下</span><span class="sxs-lookup"><span data-stu-id="34267-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="34267-122">將對話變成控制項</span><span class="sxs-lookup"><span data-stu-id="34267-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="34267-123">您可以使用 WS_CHILD 和 DS_CONTROL 樣式，將對話方塊變成子 HWND。</span><span class="sxs-lookup"><span data-stu-id="34267-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="34267-124">移至定義對話方塊的資源檔（.rc），並尋找對話方塊定義的開頭：</span><span class="sxs-lookup"><span data-stu-id="34267-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="34267-125">將第二行變更為：</span><span class="sxs-lookup"><span data-stu-id="34267-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="34267-126">此動作並不會將它完整封裝成獨立的控制項;您仍然需要呼叫 `IsDialogMessage()` 讓 Win32 可以處理特定訊息，但控制項變更的確提供了將這些控制項放在另一個 HWND 中的直接方式。</span><span class="sxs-lookup"><span data-stu-id="34267-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="34267-127">子類別 HwndHost</span><span class="sxs-lookup"><span data-stu-id="34267-127">Subclass HwndHost</span></span>

<span data-ttu-id="34267-128">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="34267-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="34267-129">然後，建立 <xref:System.Windows.Interop.HwndHost> 的衍生類別，並覆寫 `BuildWindowCore` 和 `DestroyWindowCore` 方法：</span><span class="sxs-lookup"><span data-stu-id="34267-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="34267-130">在這裡，您會使用 `CreateDialog` 來建立真正是控制項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="34267-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="34267-131">因為這是在 DLL 內呼叫的第一個方法，所以您也應該呼叫稍後定義的函式來進行一些標準的 Win32 初始化，稱為 `InitializeGlobals()`：</span><span class="sxs-lookup"><span data-stu-id="34267-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="34267-132">覆寫 TranslateAccelerator 方法以處理對話方塊索引鍵</span><span class="sxs-lookup"><span data-stu-id="34267-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="34267-133">如果您現在執行這個範例，您會看到顯示的對話方塊控制項，但它會忽略讓對話方塊成為功能對話方塊的所有鍵盤處理。</span><span class="sxs-lookup"><span data-stu-id="34267-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="34267-134">您現在應該覆寫 `TranslateAccelerator` 實（來自 `IKeyboardInputSink`，也就是 <xref:System.Windows.Interop.HwndHost> 所實行的介面）。</span><span class="sxs-lookup"><span data-stu-id="34267-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="34267-135">當應用程式收到 WM_KEYDOWN 並 WM_SYSKEYDOWN 時，就會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="34267-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="34267-136">這是一段很多的程式碼，因此可以使用一些更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="34267-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="34267-137">首先，使用C++和C++宏的程式碼;您必須注意，已有名為 `TranslateAccelerator`的宏是在 winuser 中定義的：</span><span class="sxs-lookup"><span data-stu-id="34267-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="34267-138">因此，請務必定義 `TranslateAccelerator` 方法，而不是 `TranslateAcceleratorW` 方法。</span><span class="sxs-lookup"><span data-stu-id="34267-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="34267-139">同樣地，也會同時有非受控 winuser 和 managed `Microsoft::Win32::MSG` 結構。</span><span class="sxs-lookup"><span data-stu-id="34267-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="34267-140">您可以使用C++ `::` 運算子來區分兩者。</span><span class="sxs-lookup"><span data-stu-id="34267-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

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

<span data-ttu-id="34267-141">回到 `TranslateAccelerator`。</span><span class="sxs-lookup"><span data-stu-id="34267-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="34267-142">基本原則是呼叫 Win32 函數 `IsDialogMessage` 盡可能地執行，但 `IsDialogMessage` 無法存取對話方塊以外的任何專案。</span><span class="sxs-lookup"><span data-stu-id="34267-142">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="34267-143">做為對話方塊周圍的使用者索引標籤，當 tab 鍵在對話方塊中的最後一個控制項之後執行時，您必須呼叫 `IKeyboardInputSite::OnNoMoreStops`，將焦點設定為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="34267-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="34267-144">最後，請呼叫 `IsDialogMessage`。</span><span class="sxs-lookup"><span data-stu-id="34267-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="34267-145">但是 `TranslateAccelerator` 方法的責任之一，就是告訴 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 您是否已處理此按鍵。</span><span class="sxs-lookup"><span data-stu-id="34267-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="34267-146">如果您沒有處理它，則輸入事件可以透過應用程式的其餘部分進行通道和反升。</span><span class="sxs-lookup"><span data-stu-id="34267-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="34267-147">在這裡，您將會公開鍵盤 messange 處理的怪癖，以及 Win32 中的輸入架構本質。</span><span class="sxs-lookup"><span data-stu-id="34267-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="34267-148">可惜的是，`IsDialogMessage` 不會以任何方式傳回，無論是否處理特定的按鍵。</span><span class="sxs-lookup"><span data-stu-id="34267-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="34267-149">更糟的是，它會在不應處理的擊鍵上呼叫 `DispatchMessage()`！</span><span class="sxs-lookup"><span data-stu-id="34267-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="34267-150">因此，您必須對 `IsDialogMessage`進行反向工程，並且只針對您知道它將處理的金鑰呼叫它：</span><span class="sxs-lookup"><span data-stu-id="34267-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="34267-151">覆寫 TabInto 方法以支援 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="34267-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="34267-152">現在您已實 `TranslateAccelerator`，使用者可以在對話方塊內部定位，並使用 tab 鍵移至較大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="34267-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="34267-153">但是使用者無法使用 tab 鍵回到對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="34267-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="34267-154">若要解決這個問題，您可以覆寫 `TabInto`：</span><span class="sxs-lookup"><span data-stu-id="34267-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="34267-155">`TraversalRequest` 參數會告訴您，索引標籤動作是 tab 鍵或 shift tab。</span><span class="sxs-lookup"><span data-stu-id="34267-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="34267-156">覆寫 OnMnemonic 方法以支援助憶鍵</span><span class="sxs-lookup"><span data-stu-id="34267-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="34267-157">鍵盤處理幾乎已完成，但有一件事遺漏–助憶鍵無法使用。</span><span class="sxs-lookup"><span data-stu-id="34267-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="34267-158">如果使用者按 alt-F，焦點 doe 不會跳至 [名字：] 編輯方塊。</span><span class="sxs-lookup"><span data-stu-id="34267-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="34267-159">因此，您會覆寫 `OnMnemonic` 方法：</span><span class="sxs-lookup"><span data-stu-id="34267-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="34267-160">為什麼不要在這裡呼叫 `IsDialogMessage`？</span><span class="sxs-lookup"><span data-stu-id="34267-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="34267-161">您的問題與之前相同，您必須能夠在程式碼是否處理按鍵時通知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式碼，`IsDialogMessage` 無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="34267-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="34267-162">另外還有第二個問題，因為如果焦點的 HWND 不在對話方塊內，`IsDialogMessage` 會拒絕處理助憶鍵。</span><span class="sxs-lookup"><span data-stu-id="34267-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="34267-163">具現化 HwndHost 衍生類別</span><span class="sxs-lookup"><span data-stu-id="34267-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="34267-164">最後，現在所有的索引鍵和索引標籤支援都已就緒，您可以將 <xref:System.Windows.Interop.HwndHost> 放入更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="34267-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="34267-165">如果主應用程式是以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]撰寫，則將它放在正確位置的最簡單方式，就是在您要放置 <xref:System.Windows.Interop.HwndHost>的位置留下一個空的 <xref:System.Windows.Controls.Border> 元素。</span><span class="sxs-lookup"><span data-stu-id="34267-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="34267-166">在這裡，您會建立名為 `insertHwndHostHere`的 <xref:System.Windows.Controls.Border>：</span><span class="sxs-lookup"><span data-stu-id="34267-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="34267-167">然後剩下的工作就是在程式碼序列中尋找一個不錯的位置來具現化 <xref:System.Windows.Interop.HwndHost>，並將它連接到 <xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="34267-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="34267-168">在此範例中，您會將它放在 <xref:System.Windows.Window> 衍生類別的函式內：</span><span class="sxs-lookup"><span data-stu-id="34267-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="34267-169">這會提供您：</span><span class="sxs-lookup"><span data-stu-id="34267-169">Which gives you:</span></span>

![執行之 WPF 應用程式的螢幕擷取畫面。](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="34267-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34267-171">See also</span></span>

- [<span data-ttu-id="34267-172">WPF 和 Win32 交互操作</span><span class="sxs-lookup"><span data-stu-id="34267-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
