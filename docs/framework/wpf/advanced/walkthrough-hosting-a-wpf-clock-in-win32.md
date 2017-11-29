---
title: "逐步解說：在 Win32 中裝載 WPF 時鐘"
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
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e5aa633e3d788ac8acaa09684c92b8608e7cfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="444e5-102">逐步解說：在 Win32 中裝載 WPF 時鐘</span><span class="sxs-lookup"><span data-stu-id="444e5-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>
<span data-ttu-id="444e5-103">要放置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式會使用<xref:System.Windows.Interop.HwndSource>，這樣會提供包含 HWND 您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。</span><span class="sxs-lookup"><span data-stu-id="444e5-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="444e5-104">第一次建立<xref:System.Windows.Interop.HwndSource>，讓它類似於 CreateWindow 參數。</span><span class="sxs-lookup"><span data-stu-id="444e5-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span>  <span data-ttu-id="444e5-105">接著您告訴<xref:System.Windows.Interop.HwndSource>有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容您想要在其中。</span><span class="sxs-lookup"><span data-stu-id="444e5-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span>  <span data-ttu-id="444e5-106">最後，您取得的 HWND 出<xref:System.Windows.Interop.HwndSource>。</span><span class="sxs-lookup"><span data-stu-id="444e5-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="444e5-107">這個逐步解說將說明如何建立了混合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]reimplements 作業系統的應用程式**日期和時間內容**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="444e5-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="444e5-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="444e5-108">Prerequisites</span></span>  
 <span data-ttu-id="444e5-109">請參閱[WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="444e5-109">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="444e5-110">如何使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="444e5-110">How to Use This Tutorial</span></span>  
 <span data-ttu-id="444e5-111">本教學課程著重在產生交互操作應用程式的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="444e5-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="444e5-112">本教學課程所需範例，支援[Win32 時鐘的互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)，但該範例會在最終產品的反射。</span><span class="sxs-lookup"><span data-stu-id="444e5-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="444e5-113">本教學課程中說明的步驟，您已啟動與現有[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]您自己的專案，可能是既有的專案，並且已加入裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="444e5-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="444e5-114">您可以比較與最終產品[Win32 時鐘的互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)。</span><span class="sxs-lookup"><span data-stu-id="444e5-114">You can compare your end product with [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="444e5-115">Win32 內 Windows Presentation Framework 的逐步解說 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="444e5-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>  
 <span data-ttu-id="444e5-116">下圖顯示本教學課程的預期最終產品︰</span><span class="sxs-lookup"><span data-stu-id="444e5-116">The following graphic shows the intended end product of this tutorial:</span></span>  
  
 <span data-ttu-id="444e5-117">![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span><span class="sxs-lookup"><span data-stu-id="444e5-117">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span></span>  
  
 <span data-ttu-id="444e5-118">您可以藉由建立 c + + 重新建立這個對話方塊[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，並且使用對話方塊編輯器建立下列：</span><span class="sxs-lookup"><span data-stu-id="444e5-118">You can recreate this dialog by creating C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and using the dialog editor to create the following:</span></span>  
  
 <span data-ttu-id="444e5-119">![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span><span class="sxs-lookup"><span data-stu-id="444e5-119">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span></span>  
  
 <span data-ttu-id="444e5-120">(您不需要使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]使用<xref:System.Windows.Interop.HwndSource>，而且您不需要使用 c + + 撰寫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式，但這是相當一般的做法，並能侷限於逐步教學課程說明)。</span><span class="sxs-lookup"><span data-stu-id="444e5-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>  
  
 <span data-ttu-id="444e5-121">您需要完成五個特定的子步驟，才能將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘對話方塊：</span><span class="sxs-lookup"><span data-stu-id="444e5-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>  
  
1.  <span data-ttu-id="444e5-122">啟用您[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案，以呼叫 managed 程式碼 (**/clr**) 中的專案設定變更[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="444e5-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="444e5-123">建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>在個別的 DLL。</span><span class="sxs-lookup"><span data-stu-id="444e5-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>  
  
3.  <span data-ttu-id="444e5-124">將它放[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>內<xref:System.Windows.Interop.HwndSource>。</span><span class="sxs-lookup"><span data-stu-id="444e5-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>  
  
4.  <span data-ttu-id="444e5-125">取得 HWND<xref:System.Windows.Controls.Page>使用<xref:System.Windows.Interop.HwndSource.Handle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="444e5-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>  
  
5.  <span data-ttu-id="444e5-126">使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]決定放置在較大的 HWND[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]應用程式</span><span class="sxs-lookup"><span data-stu-id="444e5-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>  
  
## <a name="clr"></a><span data-ttu-id="444e5-127">/clr</span><span class="sxs-lookup"><span data-stu-id="444e5-127">/clr</span></span>  
 <span data-ttu-id="444e5-128">第一個步驟是將此 unmanaged[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案合而為一可以呼叫 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="444e5-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span>  <span data-ttu-id="444e5-129">使用 /clr 編譯器選項，將會連結至您想要使用，並調整與搭配使用的 Main 方法所需 Dll [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="444e5-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="444e5-130">若要啟用 c + + 專案內的 managed 程式碼： win32clock 專案上按一下滑鼠右鍵，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="444e5-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span>  <span data-ttu-id="444e5-131">在**一般**屬性頁 （預設值），變更至 Common Language Runtime 支援`/clr`。</span><span class="sxs-lookup"><span data-stu-id="444e5-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>  
  
 <span data-ttu-id="444e5-132">接下來，加入所需的 Dll 的參考[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll、 PresentationFramework.dll、 System.dll、 WindowsBase.dll、 UIAutomationProvider.dll 和 UIAutomationTypes.dll。</span><span class="sxs-lookup"><span data-stu-id="444e5-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="444e5-133">(下列指示假設作業系統安裝在 C: 磁碟機上)。</span><span class="sxs-lookup"><span data-stu-id="444e5-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>  
  
1.  <span data-ttu-id="444e5-134">Win32clock 專案上按一下滑鼠右鍵，然後選取**參考...**，並在該對話方塊內：</span><span class="sxs-lookup"><span data-stu-id="444e5-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>  
  
2.  <span data-ttu-id="444e5-135">Win32clock 專案上按一下滑鼠右鍵，然後選取**參考...**.</span><span class="sxs-lookup"><span data-stu-id="444e5-135">Right-click win32clock project and select **References...**.</span></span>  
  
3.  <span data-ttu-id="444e5-136">按一下**加入新參考**，按一下 [瀏覽] 索引標籤，輸入 C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="444e5-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>  
  
4.  <span data-ttu-id="444e5-137">針對 PresentationFramework.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll。</span><span class="sxs-lookup"><span data-stu-id="444e5-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>  
  
5.  <span data-ttu-id="444e5-138">針對 WindowsBase.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll。</span><span class="sxs-lookup"><span data-stu-id="444e5-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>  
  
6.  <span data-ttu-id="444e5-139">針對 UIAutomationTypes.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll。</span><span class="sxs-lookup"><span data-stu-id="444e5-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>  
  
7.  <span data-ttu-id="444e5-140">針對 UIAutomationProvider.dll 重複執行：C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll。</span><span class="sxs-lookup"><span data-stu-id="444e5-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>  
  
8.  <span data-ttu-id="444e5-141">按一下**加入新參考**選取 System.dll，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="444e5-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>  
  
9. <span data-ttu-id="444e5-142">按一下**確定**結束 win32clock 屬性頁，以加入參考。</span><span class="sxs-lookup"><span data-stu-id="444e5-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
 <span data-ttu-id="444e5-143">最後，會加入`STAThreadAttribute`至`_tWinMain`方法搭配使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="444e5-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 <span data-ttu-id="444e5-144">這個屬性會告知[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]，它會初始化時[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]，應該使用單一執行緒的 apartment 模型 (STA)，這是所需的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)](和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="444e5-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>  
  
## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="444e5-145">建立 Windows Presentation Framework 頁面</span><span class="sxs-lookup"><span data-stu-id="444e5-145">Create a Windows Presentation Framework Page</span></span>  
 <span data-ttu-id="444e5-146">接下來，您可以建立定義 DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>。</span><span class="sxs-lookup"><span data-stu-id="444e5-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="444e5-147">通常是最簡單的方式建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>做為獨立應用程式，以及寫入和偵錯[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分的方式。</span><span class="sxs-lookup"><span data-stu-id="444e5-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span>  <span data-ttu-id="444e5-148">一旦完成，該專案可以開啟 dll 中以滑鼠右鍵按一下專案，按一下**屬性**、 移至應用程式，以及輸出類型變更為 Windows 類別庫。</span><span class="sxs-lookup"><span data-stu-id="444e5-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>  
  
 <span data-ttu-id="444e5-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll 專案可以再結合[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案 （一個方案包含兩個專案） – 以滑鼠右鍵按一下方案，並選取**Add\Existing 專案**。</span><span class="sxs-lookup"><span data-stu-id="444e5-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>  
  
 <span data-ttu-id="444e5-150">若要使用的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dll[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]專案中，您必須加入參考：</span><span class="sxs-lookup"><span data-stu-id="444e5-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>  
  
1.  <span data-ttu-id="444e5-151">Win32clock 專案上按一下滑鼠右鍵，然後選取**參考...**.</span><span class="sxs-lookup"><span data-stu-id="444e5-151">Right-click win32clock project and select **References...**.</span></span>  
  
2.  <span data-ttu-id="444e5-152">按一下**加入新參考**。</span><span class="sxs-lookup"><span data-stu-id="444e5-152">Click **Add New Reference**.</span></span>  
  
3.  <span data-ttu-id="444e5-153">按一下 [專案] 索引標籤。選取 WPFClock，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="444e5-153">Click the **Projects** tab.  Select WPFClock, click OK.</span></span>  
  
4.  <span data-ttu-id="444e5-154">按一下**確定**結束 win32clock 屬性頁，以加入參考。</span><span class="sxs-lookup"><span data-stu-id="444e5-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
## <a name="hwndsource"></a><span data-ttu-id="444e5-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="444e5-155">HwndSource</span></span>  
 <span data-ttu-id="444e5-156">接下來，您使用<xref:System.Windows.Interop.HwndSource>進行[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND 看起來。</span><span class="sxs-lookup"><span data-stu-id="444e5-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span>  <span data-ttu-id="444e5-157">您可以將此程式碼區塊新增至 C++ 檔案：</span><span class="sxs-lookup"><span data-stu-id="444e5-157">You add this block of code to a C++ file:</span></span>  
  
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
  
 <span data-ttu-id="444e5-158">這是可使用一些說明的長程式碼。</span><span class="sxs-lookup"><span data-stu-id="444e5-158">This is a long piece of code that could use some explanation.</span></span>  <span data-ttu-id="444e5-159">第一個部分是各種子句，讓您不需要完整限定所有呼叫︰</span><span class="sxs-lookup"><span data-stu-id="444e5-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 <span data-ttu-id="444e5-160">然後定義來建立函式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容，將<xref:System.Windows.Interop.HwndSource>周圍，並傳回 HWND:</span><span class="sxs-lookup"><span data-stu-id="444e5-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 <span data-ttu-id="444e5-161">第一次建立<xref:System.Windows.Interop.HwndSource>，CreateWindow 的參數如下：</span><span class="sxs-lookup"><span data-stu-id="444e5-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>  
  
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
  
 <span data-ttu-id="444e5-162">然後建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容類別，藉由呼叫其建構函式：</span><span class="sxs-lookup"><span data-stu-id="444e5-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 <span data-ttu-id="444e5-163">您接著連接頁面，即可<xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="444e5-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
source->RootVisual = page;  
```  
  
 <span data-ttu-id="444e5-164">並在最後一行中，傳回的 HWND <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="444e5-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a><span data-ttu-id="444e5-165">定位 Hwnd</span><span class="sxs-lookup"><span data-stu-id="444e5-165">Positioning the Hwnd</span></span>  
 <span data-ttu-id="444e5-166">您已經有包含 HWND[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘，您需要將該 HWND 內[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="444e5-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span>  <span data-ttu-id="444e5-167">如果您知道要放置 HWND 到何處，您可以只傳遞該大小和位置來`GetHwnd`先前定義的函式。</span><span class="sxs-lookup"><span data-stu-id="444e5-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span>  <span data-ttu-id="444e5-168">但是，您已使用資源檔來定義對話方塊，因此，您未完全確定放置任何 HWND 的位置。</span><span class="sxs-lookup"><span data-stu-id="444e5-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span>  <span data-ttu-id="444e5-169">您可以使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]對話方塊編輯器將[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]靜態控制您想要前往的時鐘 （「 插入時鐘這裡"），然後使用它來定位[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘。</span><span class="sxs-lookup"><span data-stu-id="444e5-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>  
  
 <span data-ttu-id="444e5-170">在您處理 WM_INITDIALOG，使用`GetDlgItem`HWND 擷取靜態的預留位置：</span><span class="sxs-lookup"><span data-stu-id="444e5-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 <span data-ttu-id="444e5-171">您再計算的大小和位置的預留位置靜態，因此您可以將放[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘於該位置：</span><span class="sxs-lookup"><span data-stu-id="444e5-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>  
  
 <span data-ttu-id="444e5-172">RECT 矩形；</span><span class="sxs-lookup"><span data-stu-id="444e5-172">RECT rectangle;</span></span>  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 <span data-ttu-id="444e5-173">然後，您可以隱藏預留位置 STATIC︰</span><span class="sxs-lookup"><span data-stu-id="444e5-173">Then you hide the placeholder STATIC:</span></span>  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 <span data-ttu-id="444e5-174">建立和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘在該位置的 HWND:</span><span class="sxs-lookup"><span data-stu-id="444e5-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 <span data-ttu-id="444e5-175">若要讓教學課程的有趣，並以產生真實[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘，您必須建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]此時時鐘控制項。</span><span class="sxs-lookup"><span data-stu-id="444e5-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="444e5-176">您大部分都可以透過標記完成，而且只需要程式碼後置中的一些事件處理常式即可。</span><span class="sxs-lookup"><span data-stu-id="444e5-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="444e5-177">由於本教學課程有關的互通性，以及不控制項的設計，完整程式碼[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時鐘會提供為程式碼區塊，而不指示建置它，或每個部分所代表的意義。</span><span class="sxs-lookup"><span data-stu-id="444e5-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="444e5-178">請自由實驗此程式碼，來變更控制項功能的外觀或操作。</span><span class="sxs-lookup"><span data-stu-id="444e5-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>  
  
 <span data-ttu-id="444e5-179">標記如下：</span><span class="sxs-lookup"><span data-stu-id="444e5-179">Here is the markup:</span></span>  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 <span data-ttu-id="444e5-180">這裡是隨附的程式碼後置︰</span><span class="sxs-lookup"><span data-stu-id="444e5-180">And here is the accompanying code-behind:</span></span>  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 <span data-ttu-id="444e5-181">最終結果如下：</span><span class="sxs-lookup"><span data-stu-id="444e5-181">The final result looks like:</span></span>  
  
 <span data-ttu-id="444e5-182">![日期和時間內容對話方塊](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span><span class="sxs-lookup"><span data-stu-id="444e5-182">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span></span>  
  
 <span data-ttu-id="444e5-183">若要比較您產生這個螢幕擷取畫面的程式碼的最後結果，請參閱[Win32 時鐘的互通性範例](http://go.microsoft.com/fwlink/?LinkID=160051)。</span><span class="sxs-lookup"><span data-stu-id="444e5-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444e5-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="444e5-184">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="444e5-185">WPF 和 Win32 交互操作</span><span class="sxs-lookup"><span data-stu-id="444e5-185">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [<span data-ttu-id="444e5-186">Win32 時鐘交互操作範例</span><span class="sxs-lookup"><span data-stu-id="444e5-186">Win32 Clock Interoperation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160051)
