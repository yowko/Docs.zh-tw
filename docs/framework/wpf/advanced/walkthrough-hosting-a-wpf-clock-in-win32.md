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
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="c09f2-102">逐步解說：將 WPF 時鐘裝載在 Win32 中</span><span class="sxs-lookup"><span data-stu-id="c09f2-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>

<span data-ttu-id="c09f2-103">若要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]將[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]放在應用<xref:System.Windows.Interop.HwndSource>程式內, 請使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 它會提供包含內容的 HWND。</span><span class="sxs-lookup"><span data-stu-id="c09f2-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="c09f2-104">首先您要建立<xref:System.Windows.Interop.HwndSource>, 並提供類似于 CreateWindow 的參數。</span><span class="sxs-lookup"><span data-stu-id="c09f2-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="c09f2-105">然後您會告訴<xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]您想要的內容。</span><span class="sxs-lookup"><span data-stu-id="c09f2-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="c09f2-106">最後, 您會從<xref:System.Windows.Interop.HwndSource>取得 HWND。</span><span class="sxs-lookup"><span data-stu-id="c09f2-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="c09f2-107">本逐步解說說明如何在實作作業系統[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **日期和時間屬性**對話方塊的應用程式中[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]建立混合式。</span><span class="sxs-lookup"><span data-stu-id="c09f2-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c09f2-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="c09f2-108">Prerequisites</span></span>

<span data-ttu-id="c09f2-109">請參閱[WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="c09f2-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="c09f2-110">如何使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="c09f2-110">How to Use This Tutorial</span></span>

<span data-ttu-id="c09f2-111">本教學課程著重在產生交互操作應用程式的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="c09f2-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="c09f2-112">本教學課程是以範例、 [Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)為後盾, 但該範例會反映出最終產品。</span><span class="sxs-lookup"><span data-stu-id="c09f2-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="c09f2-113">本教學課程記載的步驟, 就像您是從自己[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的現有專案開始, 或許是既有的專案, 而且您已將裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="c09f2-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="c09f2-114">您可以比較您的終端產品與[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。</span><span class="sxs-lookup"><span data-stu-id="c09f2-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="c09f2-115">Win32 內 Windows Presentation Framework 的逐步解說 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="c09f2-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="c09f2-116">下圖顯示本教學課程的預期最終產品︰</span><span class="sxs-lookup"><span data-stu-id="c09f2-116">The following graphic shows the intended end product of this tutorial:</span></span>

![顯示 [日期和時間內容] 對話方塊的螢幕擷取畫面。](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="c09f2-118">您可以在 Visual Studio 中建立C++ Win32 專案, 然後使用對話方塊編輯器來建立下列內容, 以重新建立此對話方塊:</span><span class="sxs-lookup"><span data-stu-id="c09f2-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![重新建立日期和時間屬性對話方塊](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="c09f2-120">(您[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]不需要使用來使用<xref:System.Windows.Interop.HwndSource>, 也不需要使用C++來撰寫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式, 但這是相當常見的方法, 而且非常適合逐步的教學課程說明)。</span><span class="sxs-lookup"><span data-stu-id="c09f2-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="c09f2-121">您必須完成五個特定子步驟, 才能將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘放入對話方塊中:</span><span class="sxs-lookup"><span data-stu-id="c09f2-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="c09f2-122">藉由[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]變更中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]的專案設定, 讓您的專案呼叫 managed 程式碼 ( **/clr**)。</span><span class="sxs-lookup"><span data-stu-id="c09f2-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>

2. <span data-ttu-id="c09f2-123">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 在個別<xref:System.Windows.Controls.Page>的 DLL 中建立。</span><span class="sxs-lookup"><span data-stu-id="c09f2-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="c09f2-124">將它[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>放在<xref:System.Windows.Interop.HwndSource>內。</span><span class="sxs-lookup"><span data-stu-id="c09f2-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="c09f2-125">使用屬性取得的<xref:System.Windows.Controls.Page>HWND <xref:System.Windows.Interop.HwndSource.Handle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c09f2-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="c09f2-126">用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]來決定要在較大[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的應用程式中放置 HWND 的位置</span><span class="sxs-lookup"><span data-stu-id="c09f2-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>

## <a name="clr"></a><span data-ttu-id="c09f2-127">/clr</span><span class="sxs-lookup"><span data-stu-id="c09f2-127">/clr</span></span>

<span data-ttu-id="c09f2-128">第一個步驟是將此非[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]受控專案轉換成一個可以呼叫 managed 程式碼的專案。</span><span class="sxs-lookup"><span data-stu-id="c09f2-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span> <span data-ttu-id="c09f2-129">您可以使用/clr 編譯器選項, 這會連結到您想要使用的必要 Dll, 並調整 Main 方法以與[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]搭配使用。</span><span class="sxs-lookup"><span data-stu-id="c09f2-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="c09f2-130">若要在C++專案內啟用 managed 程式碼的使用:以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="c09f2-131">在 [**一般**] 屬性頁 (預設值) 上, 將 [Common Language `/clr`Runtime 支援] 變更為。</span><span class="sxs-lookup"><span data-stu-id="c09f2-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="c09f2-132">接下來, 將參考新增至所[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]需的 dll:PresentationCore .dll、PresentationFramework、system.string、WindowsBase、.dll、Uiautomationprovider.dll 和 UIAutomationTypes .dll。</span><span class="sxs-lookup"><span data-stu-id="c09f2-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="c09f2-133">(下列指示假設作業系統安裝在 C: 磁碟機上)。</span><span class="sxs-lookup"><span data-stu-id="c09f2-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="c09f2-134">以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**參考 ...** ], 然後在該對話方塊內:</span><span class="sxs-lookup"><span data-stu-id="c09f2-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="c09f2-135">以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**參考 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="c09f2-136">按一下 [**加入新參考**], 按一下 [流覽] 索引標籤, 輸入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, 然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="c09f2-137">針對 PresentationFramework 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。</span><span class="sxs-lookup"><span data-stu-id="c09f2-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="c09f2-138">針對 WindowsBase 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。</span><span class="sxs-lookup"><span data-stu-id="c09f2-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="c09f2-139">針對 UIAutomationTypes 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。</span><span class="sxs-lookup"><span data-stu-id="c09f2-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="c09f2-140">針對 Uiautomationprovider.dll 重複執行:C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。</span><span class="sxs-lookup"><span data-stu-id="c09f2-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="c09f2-141">按一下 [**新增參考**], 選取 [system.object], 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c09f2-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="c09f2-142">按一下 **[確定]** , 結束 Win32clock 屬性頁以加入參考。</span><span class="sxs-lookup"><span data-stu-id="c09f2-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="c09f2-143">最後, 將新增`STAThreadAttribute` `_tWinMain`至方法以搭配使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c09f2-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="c09f2-144">這個屬性會告知 common language runtime (CLR), 當它初始化[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]時, 它應該使用單一執行緒單元模型 (STA), 這是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]) 的必要動作。</span><span class="sxs-lookup"><span data-stu-id="c09f2-144">This attribute tells the common language runtime (CLR) that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="c09f2-145">建立 Windows Presentation Framework 頁面</span><span class="sxs-lookup"><span data-stu-id="c09f2-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="c09f2-146">接下來, 您會建立定義的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>DLL。</span><span class="sxs-lookup"><span data-stu-id="c09f2-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="c09f2-147">將建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>為獨立應用程式通常是最簡單的方法, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]並以這種方式撰寫和調試部分。</span><span class="sxs-lookup"><span data-stu-id="c09f2-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="c09f2-148">完成後, 即可將該專案轉換成 DLL, 方法是以滑鼠右鍵按一下專案, 按一下 [**屬性**], 前往 [應用程式], 然後將 [輸出類型] 變更為 [Windows 類別庫]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="c09f2-149">然後, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dll 專案可以與專案 (其中一個包含兩個專案的方案) 合併–以滑鼠右鍵按一下方案, 然後選取 [ **Add\Existing 專案**]。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c09f2-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="c09f2-150">若要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]從專案使用該 dll, 您需要新增參考:</span><span class="sxs-lookup"><span data-stu-id="c09f2-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>

1. <span data-ttu-id="c09f2-151">以滑鼠右鍵按一下 [win32clock 專案], 然後選取 [**參考 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="c09f2-152">按一下 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="c09f2-153">按一下 [專案] 索引標籤。選取 WPFClock，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c09f2-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="c09f2-154">按一下 **[確定]** , 結束 Win32clock 屬性頁以加入參考。</span><span class="sxs-lookup"><span data-stu-id="c09f2-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="c09f2-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="c09f2-155">HwndSource</span></span>

<span data-ttu-id="c09f2-156">接下來, 您<xref:System.Windows.Interop.HwndSource>可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>讓看起來像是 HWND。</span><span class="sxs-lookup"><span data-stu-id="c09f2-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="c09f2-157">您可以將此程式碼區塊新增至 C++ 檔案：</span><span class="sxs-lookup"><span data-stu-id="c09f2-157">You add this block of code to a C++ file:</span></span>

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

 <span data-ttu-id="c09f2-158">這是可使用一些說明的長程式碼。</span><span class="sxs-lookup"><span data-stu-id="c09f2-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="c09f2-159">第一個部分是各種子句，讓您不需要完整限定所有呼叫︰</span><span class="sxs-lookup"><span data-stu-id="c09f2-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="c09f2-160">接著, 您要定義一個函式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndSource>來建立內容、將它放在其周圍, 然後傳回 HWND:</span><span class="sxs-lookup"><span data-stu-id="c09f2-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="c09f2-161">首先您要建立<xref:System.Windows.Interop.HwndSource>, 其參數與 CreateWindow 類似:</span><span class="sxs-lookup"><span data-stu-id="c09f2-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

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

<span data-ttu-id="c09f2-162">接著, 您可以[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由呼叫其「它的」來建立內容類別別:</span><span class="sxs-lookup"><span data-stu-id="c09f2-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="c09f2-163">接著, 您可以將頁面連線<xref:System.Windows.Interop.HwndSource>到:</span><span class="sxs-lookup"><span data-stu-id="c09f2-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="c09f2-164">在最後一行中, 傳回的 HWND <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="c09f2-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="c09f2-165">定位 Hwnd</span><span class="sxs-lookup"><span data-stu-id="c09f2-165">Positioning the Hwnd</span></span>

<span data-ttu-id="c09f2-166">現在您已經有包含[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘的 hwnd, 您需要將該 hwnd 放在[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="c09f2-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span> <span data-ttu-id="c09f2-167">如果您知道要放置 HWND 的位置, 只要將該大小和位置傳遞至您稍早`GetHwnd`定義的函式即可。</span><span class="sxs-lookup"><span data-stu-id="c09f2-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="c09f2-168">但是，您已使用資源檔來定義對話方塊，因此，您未完全確定放置任何 HWND 的位置。</span><span class="sxs-lookup"><span data-stu-id="c09f2-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="c09f2-169">您可以使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]對話方塊編輯器, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]將靜態控制項放在您想要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用的時鐘 (「在此插入時鐘」), 並用它來定位時鐘。</span><span class="sxs-lookup"><span data-stu-id="c09f2-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="c09f2-170">在您處理 WM_INITDIALOG 的位置, `GetDlgItem`您可以使用來抓取預留位置 STATIC 的 HWND:</span><span class="sxs-lookup"><span data-stu-id="c09f2-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="c09f2-171">接著, 您會計算該預留位置的大小和位置, 讓您可以將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘放在該位置:</span><span class="sxs-lookup"><span data-stu-id="c09f2-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="c09f2-172">RECT 矩形；</span><span class="sxs-lookup"><span data-stu-id="c09f2-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="c09f2-173">然後，您可以隱藏預留位置 STATIC︰</span><span class="sxs-lookup"><span data-stu-id="c09f2-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="c09f2-174">並在該[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]位置建立時鐘 HWND:</span><span class="sxs-lookup"><span data-stu-id="c09f2-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="c09f2-175">若要讓教學課程更有趣, 並產生真正[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的時鐘, 您必須在此時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立時鐘控制項。</span><span class="sxs-lookup"><span data-stu-id="c09f2-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="c09f2-176">您大部分都可以透過標記完成，而且只需要程式碼後置中的一些事件處理常式即可。</span><span class="sxs-lookup"><span data-stu-id="c09f2-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="c09f2-177">由於本教學課程是關於互通性, 而不是控制項設計, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]因此在這裡以程式碼區塊的形式提供時鐘的完整程式碼, 而不需要個別的指示來建立它或每個部分所代表的意義。</span><span class="sxs-lookup"><span data-stu-id="c09f2-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="c09f2-178">請自由實驗此程式碼，來變更控制項功能的外觀或操作。</span><span class="sxs-lookup"><span data-stu-id="c09f2-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="c09f2-179">標記如下：</span><span class="sxs-lookup"><span data-stu-id="c09f2-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="c09f2-180">這裡是隨附的程式碼後置︰</span><span class="sxs-lookup"><span data-stu-id="c09f2-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="c09f2-181">最終結果如下：</span><span class="sxs-lookup"><span data-stu-id="c09f2-181">The final result looks like:</span></span>

![最終結果日期和時間屬性對話方塊](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="c09f2-183">若要比較您的最終結果與產生此螢幕擷取畫面的程式碼, 請參閱[Win32 時鐘交互操作範例](https://go.microsoft.com/fwlink/?LinkID=160051)。</span><span class="sxs-lookup"><span data-stu-id="c09f2-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="c09f2-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c09f2-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="c09f2-185">WPF 和 Win32 交互操作</span><span class="sxs-lookup"><span data-stu-id="c09f2-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="c09f2-186">Win32 時鐘交互操作範例</span><span class="sxs-lookup"><span data-stu-id="c09f2-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
