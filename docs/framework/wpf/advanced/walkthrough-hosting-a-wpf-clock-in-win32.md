---
title: 逐步解說：在 Win32 中裝載 WPF 時鐘
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 79f79e42652ca51c409fabb12a572485ad734b35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744894"
---
# <a name="walkthrough-host-a-wpf-clock-in-win32"></a><span data-ttu-id="5720e-102">逐步解說：在 Win32 中裝載 WPF 時鐘</span><span class="sxs-lookup"><span data-stu-id="5720e-102">Walkthrough: Host a WPF Clock in Win32</span></span>

<span data-ttu-id="5720e-103">若要將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 放在 Win32 應用程式中，請使用 <xref:System.Windows.Interop.HwndSource>，它會提供包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的 HWND。</span><span class="sxs-lookup"><span data-stu-id="5720e-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="5720e-104">首先，您會建立 <xref:System.Windows.Interop.HwndSource>，並提供類似于 CreateWindow 的參數。</span><span class="sxs-lookup"><span data-stu-id="5720e-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="5720e-105">接著，您會告訴 <xref:System.Windows.Interop.HwndSource> 您要在其中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。</span><span class="sxs-lookup"><span data-stu-id="5720e-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="5720e-106">最後，您可以從 <xref:System.Windows.Interop.HwndSource>取得 HWND。</span><span class="sxs-lookup"><span data-stu-id="5720e-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="5720e-107">本逐步解說說明如何在實作作業系統**日期和時間屬性**對話方塊的 Win32 應用程式內建立混合 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5720e-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5720e-108">必要條件：</span><span class="sxs-lookup"><span data-stu-id="5720e-108">Prerequisites</span></span>

<span data-ttu-id="5720e-109">請參閱[WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="5720e-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="5720e-110">如何使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="5720e-110">How to Use This Tutorial</span></span>

<span data-ttu-id="5720e-111">本教學課程著重在產生交互操作應用程式的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="5720e-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="5720e-112">本教學課程是以範例、 [Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)為後盾，但該範例會反映出最終產品。</span><span class="sxs-lookup"><span data-stu-id="5720e-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="5720e-113">本教學課程記載的步驟，就像您是從自己的現有 Win32 專案開始著手，或許是既有的專案，而且您已將託管的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="5720e-113">This tutorial documents the steps as if you were starting with an existing Win32 project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="5720e-114">您可以比較您的終端產品與[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。</span><span class="sxs-lookup"><span data-stu-id="5720e-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="5720e-115">Win32 內 Windows Presentation Framework 的逐步解說 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="5720e-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="5720e-116">下圖顯示本教學課程的預期最終產品︰</span><span class="sxs-lookup"><span data-stu-id="5720e-116">The following graphic shows the intended end product of this tutorial:</span></span>

![顯示 [日期和時間內容] 對話方塊的螢幕擷取畫面。](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="5720e-118">您可以在 Visual Studio 中建立C++ Win32 專案，然後使用對話方塊編輯器來建立下列內容，以重新建立此對話方塊：</span><span class="sxs-lookup"><span data-stu-id="5720e-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![重新建立日期和時間屬性對話方塊](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="5720e-120">（您不需要使用 Visual Studio 來使用 <xref:System.Windows.Interop.HwndSource>，而且您不需要使用C++來撰寫 Win32 程式，但這是相當常見的方法，而且很適合逐步的教學課程說明）。</span><span class="sxs-lookup"><span data-stu-id="5720e-120">(You do not need to use Visual Studio to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write Win32 programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="5720e-121">您必須完成五個特定的子步驟，才能將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的時鐘放入對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="5720e-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="5720e-122">藉由變更 Visual Studio 中的專案設定，讓您的 Win32 專案呼叫 managed 程式碼（ **/clr**）。</span><span class="sxs-lookup"><span data-stu-id="5720e-122">Enable your Win32 project to call managed code (**/clr**) by changing project settings in Visual Studio.</span></span>

2. <span data-ttu-id="5720e-123">在個別的 DLL 中建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>。</span><span class="sxs-lookup"><span data-stu-id="5720e-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="5720e-124">將該 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> 放在 <xref:System.Windows.Interop.HwndSource>內。</span><span class="sxs-lookup"><span data-stu-id="5720e-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="5720e-125">使用 <xref:System.Windows.Interop.HwndSource.Handle%2A> 屬性取得該 <xref:System.Windows.Controls.Page> 的 HWND。</span><span class="sxs-lookup"><span data-stu-id="5720e-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="5720e-126">使用 Win32 決定在較大的 Win32 應用程式中放置 HWND 的位置</span><span class="sxs-lookup"><span data-stu-id="5720e-126">Use Win32 to decide where to place the HWND within the larger Win32 application</span></span>

## <a name="clr"></a><span data-ttu-id="5720e-127">/clr</span><span class="sxs-lookup"><span data-stu-id="5720e-127">/clr</span></span>

<span data-ttu-id="5720e-128">第一個步驟是將此非受控 Win32 專案轉換成可以呼叫 managed 程式碼的專案。</span><span class="sxs-lookup"><span data-stu-id="5720e-128">The first step is to turn this unmanaged Win32 project into one that can call managed code.</span></span> <span data-ttu-id="5720e-129">您可以使用/clr 編譯器選項，這會連結到您想要使用的必要 Dll，並調整 Main 方法以與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]搭配使用。</span><span class="sxs-lookup"><span data-stu-id="5720e-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="5720e-130">若要啟用在專案內使用 managed 程式C++代碼：以滑鼠右鍵按一下 [win32clock 專案]，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="5720e-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="5720e-131">在 [**一般**] 屬性頁（預設值）上，將 [Common Language Runtime 支援] 變更為 `/clr`。</span><span class="sxs-lookup"><span data-stu-id="5720e-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="5720e-132">接下來，加入 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]所需 Dll 的參考： PresentationCore、PresentationFramework、System.web、WindowsBase、.dll、Uiautomationprovider.dll 和 UIAutomationTypes。</span><span class="sxs-lookup"><span data-stu-id="5720e-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="5720e-133">(下列指示假設作業系統安裝在 C: 磁碟機上)。</span><span class="sxs-lookup"><span data-stu-id="5720e-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="5720e-134">以滑鼠右鍵按一下 [win32clock 專案]，然後選取 [**參考 ...** ]，然後在該對話方塊內：</span><span class="sxs-lookup"><span data-stu-id="5720e-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="5720e-135">以滑鼠右鍵按一下 [win32clock 專案]，然後選取 [**參考 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="5720e-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="5720e-136">按一下 [**加入新參考**]，按一下 [流覽] 索引標籤，輸入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="5720e-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="5720e-137">針對 PresentationFramework.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。</span><span class="sxs-lookup"><span data-stu-id="5720e-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="5720e-138">針對 WindowsBase.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。</span><span class="sxs-lookup"><span data-stu-id="5720e-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="5720e-139">針對 UIAutomationTypes.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。</span><span class="sxs-lookup"><span data-stu-id="5720e-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="5720e-140">針對 UIAutomationProvider.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。</span><span class="sxs-lookup"><span data-stu-id="5720e-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="5720e-141">按一下 [**新增參考**]，選取 [system.object]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5720e-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="5720e-142">按一下 **[確定]** ，結束 Win32clock 屬性頁以加入參考。</span><span class="sxs-lookup"><span data-stu-id="5720e-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="5720e-143">最後，將 `STAThreadAttribute` 新增至 `_tWinMain` 方法以與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]搭配使用：</span><span class="sxs-lookup"><span data-stu-id="5720e-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="5720e-144">這個屬性會告知 common language runtime （CLR），當它初始化元件物件模型（COM）時，它應該使用單一執行緒單元模型（STA），這是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] （和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]）的必要動作。</span><span class="sxs-lookup"><span data-stu-id="5720e-144">This attribute tells the common language runtime (CLR) that when it initializes Component Object Model (COM), it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="5720e-145">建立 Windows Presentation Framework 頁面</span><span class="sxs-lookup"><span data-stu-id="5720e-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="5720e-146">接下來，您會建立定義 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>的 DLL。</span><span class="sxs-lookup"><span data-stu-id="5720e-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="5720e-147">以獨立應用程式的形式建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> 通常是最簡單的方法，並以這種方式撰寫和 debug [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="5720e-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="5720e-148">完成後，即可將該專案轉換成 DLL，方法是以滑鼠右鍵按一下專案，按一下 [**屬性**]，前往 [應用程式]，然後將 [輸出類型] 變更為 [Windows 類別庫]。</span><span class="sxs-lookup"><span data-stu-id="5720e-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="5720e-149">然後，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll 專案可以與 Win32 專案結合（一個包含兩個專案的方案）–以滑鼠右鍵按一下方案，然後選取 [ **Add\Existing 專案**]。</span><span class="sxs-lookup"><span data-stu-id="5720e-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the Win32 project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="5720e-150">若要從 Win32 專案使用該 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll，您需要新增參考：</span><span class="sxs-lookup"><span data-stu-id="5720e-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the Win32 project, you need to add a reference:</span></span>

1. <span data-ttu-id="5720e-151">以滑鼠右鍵按一下 [win32clock 專案]，然後選取 [**參考 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="5720e-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="5720e-152">按一下 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="5720e-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="5720e-153">按一下 [**專案**] 索引標籤。選取 [WPFClock]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="5720e-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="5720e-154">按一下 **[確定]** ，結束 Win32clock 屬性頁以加入參考。</span><span class="sxs-lookup"><span data-stu-id="5720e-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="5720e-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="5720e-155">HwndSource</span></span>

<span data-ttu-id="5720e-156">接下來，您可以使用 <xref:System.Windows.Interop.HwndSource>，讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> 看起來像是 HWND。</span><span class="sxs-lookup"><span data-stu-id="5720e-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="5720e-157">您可以將此程式碼區塊新增至 C++ 檔案：</span><span class="sxs-lookup"><span data-stu-id="5720e-157">You add this block of code to a C++ file:</span></span>

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

 <span data-ttu-id="5720e-158">這是可使用一些說明的長程式碼。</span><span class="sxs-lookup"><span data-stu-id="5720e-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="5720e-159">第一個部分是各種子句，讓您不需要完整限定所有呼叫︰</span><span class="sxs-lookup"><span data-stu-id="5720e-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="5720e-160">接著，您會定義一個函式來建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容、將 <xref:System.Windows.Interop.HwndSource> 放在其周圍，然後傳回 HWND：</span><span class="sxs-lookup"><span data-stu-id="5720e-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="5720e-161">首先，您會建立一個 <xref:System.Windows.Interop.HwndSource>，其參數與 CreateWindow 類似：</span><span class="sxs-lookup"><span data-stu-id="5720e-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

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

<span data-ttu-id="5720e-162">接著，您可以藉由呼叫其「其」來建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別別：</span><span class="sxs-lookup"><span data-stu-id="5720e-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="5720e-163">然後將頁面連接到 <xref:System.Windows.Interop.HwndSource>：</span><span class="sxs-lookup"><span data-stu-id="5720e-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="5720e-164">在最後一行中，傳回 <xref:System.Windows.Interop.HwndSource>的 HWND：</span><span class="sxs-lookup"><span data-stu-id="5720e-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="5720e-165">定位 Hwnd</span><span class="sxs-lookup"><span data-stu-id="5720e-165">Positioning the Hwnd</span></span>

<span data-ttu-id="5720e-166">現在您已經有包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘的 HWND，您需要將該 HWND 放在 Win32 對話方塊內。</span><span class="sxs-lookup"><span data-stu-id="5720e-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the Win32 dialog.</span></span> <span data-ttu-id="5720e-167">如果您知道要在哪裡放置 HWND，只需要將該大小和位置傳遞至您稍早定義的 `GetHwnd` 函式。</span><span class="sxs-lookup"><span data-stu-id="5720e-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="5720e-168">但是，您已使用資源檔來定義對話方塊，因此，您未完全確定放置任何 HWND 的位置。</span><span class="sxs-lookup"><span data-stu-id="5720e-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="5720e-169">您可以使用 [Visual Studio 對話方塊編輯器]，將 Win32 靜態控制項放在您想要使用的時鐘（「在此插入時鐘」），並用它來定位 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的時鐘。</span><span class="sxs-lookup"><span data-stu-id="5720e-169">You can use the Visual Studio dialog editor to put a Win32 STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="5720e-170">當您處理 WM_INITDIALOG 時，您可以使用 `GetDlgItem` 來抓取預留位置 STATIC 的 HWND：</span><span class="sxs-lookup"><span data-stu-id="5720e-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="5720e-171">接著，您會計算該預留位置的大小和位置，讓您可以將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘放在該位置：</span><span class="sxs-lookup"><span data-stu-id="5720e-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="5720e-172">RECT 矩形；</span><span class="sxs-lookup"><span data-stu-id="5720e-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="5720e-173">然後，您可以隱藏預留位置 STATIC︰</span><span class="sxs-lookup"><span data-stu-id="5720e-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="5720e-174">並在該位置建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘 HWND：</span><span class="sxs-lookup"><span data-stu-id="5720e-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="5720e-175">若要讓教學課程更有趣，並產生真實的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘，您必須在此時建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘控制項。</span><span class="sxs-lookup"><span data-stu-id="5720e-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="5720e-176">您大部分都可以透過標記完成，而且只需要程式碼後置中的一些事件處理常式即可。</span><span class="sxs-lookup"><span data-stu-id="5720e-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="5720e-177">由於本教學課程是關於互通性，而不是控制項設計，因此在這裡提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時鐘的完整程式碼，作為程式碼區塊，而不需要建立它或每個部分所代表之意義的個別指示。</span><span class="sxs-lookup"><span data-stu-id="5720e-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="5720e-178">請自由實驗此程式碼，來變更控制項功能的外觀或操作。</span><span class="sxs-lookup"><span data-stu-id="5720e-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="5720e-179">標記如下：</span><span class="sxs-lookup"><span data-stu-id="5720e-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="5720e-180">這裡是隨附的程式碼後置︰</span><span class="sxs-lookup"><span data-stu-id="5720e-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="5720e-181">最終結果如下：</span><span class="sxs-lookup"><span data-stu-id="5720e-181">The final result looks like:</span></span>

![最終結果日期和時間屬性對話方塊](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="5720e-183">若要比較您的最終結果與產生此螢幕擷取畫面的程式碼，請參閱[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。</span><span class="sxs-lookup"><span data-stu-id="5720e-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="5720e-184">請參閱</span><span class="sxs-lookup"><span data-stu-id="5720e-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="5720e-185">WPF 和 Win32 交互操作</span><span class="sxs-lookup"><span data-stu-id="5720e-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="5720e-186">Win32 時鐘交互操作範例</span><span class="sxs-lookup"><span data-stu-id="5720e-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
