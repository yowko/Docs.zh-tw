---
title: 筆墨入門
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 9a1b53d0513eeef377fe8e012a8d5d7ea3f8a984
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546233"
---
# <a name="getting-started-with-ink"></a><span data-ttu-id="dbf8c-102">筆墨入門</span><span class="sxs-lookup"><span data-stu-id="dbf8c-102">Getting Started with Ink</span></span>
<span data-ttu-id="dbf8c-103">數位筆跡併入您的應用程式是比以往更為容易。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-103">Incorporating digital ink into your applications is easier than ever.</span></span> <span data-ttu-id="dbf8c-104">從 COM 和 Windows Form 的方法達到完整地整合到程式設計必然發展筆墨[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-104">Ink has evolved from being a corollary to the COM and Windows Forms method of programming to achieving full integration into the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="dbf8c-105">您不需要安裝個別的 Sdk 或執行階段程式庫。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-105">You do not need to install separate SDKs or runtime libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dbf8c-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="dbf8c-106">Prerequisites</span></span>  
 <span data-ttu-id="dbf8c-107">若要使用下列的範例，您必須先安裝 Microsoft Visual Studio 2005 和[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-107">To use the following examples, you must first install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="dbf8c-108">您也應該了解如何撰寫適用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-108">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="dbf8c-109">如需開始使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-109">For more information about getting started with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="quick-start"></a><span data-ttu-id="dbf8c-110">快速入門</span><span class="sxs-lookup"><span data-stu-id="dbf8c-110">Quick Start</span></span>  
 <span data-ttu-id="dbf8c-111">本節可協助您撰寫簡單[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]收集筆墨的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-111">This section helps you write a simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that collects ink.</span></span>  
  
 <span data-ttu-id="dbf8c-112">如果您尚未這樣做，請安裝 Microsoft Visual Studio 2005 和[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-112">If you haven't already done so, install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="dbf8c-113"> 應用程式通常必須經過編譯，您可以檢視它們，即使它們是完全組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-113"> applications usually must be compiled before you can view them, even if they consist entirely of [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="dbf8c-114">不過，[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]包含應用程式，XamlPad，設計來加速實作的處理序[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-基礎 UI。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-114">However, the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] includes an application, XamlPad, designed to speed up the process of implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-based UI.</span></span> <span data-ttu-id="dbf8c-115">若要檢視和修補這份文件中的前幾個範例，您可以使用該應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-115">You can use that application to view and tinker with the first few samples in this document.</span></span> <span data-ttu-id="dbf8c-116">建立的程序編譯的應用程式從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]涵蓋在本文件稍後。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-116">The process of creating compiled applications from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is covered later in this document.</span></span>  
  
 <span data-ttu-id="dbf8c-117">若要啟動 XAMLPad，按一下 **啟動**功能表上，指向**所有程式**，指向**Microsoft Windows SDK**，指向**工具**，然後按一下**XAMLPad**。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-117">To launch XAMLPad, click the **Start** menu, point to **All Programs**, point to **Microsoft Windows SDK**, point to **Tools**, and click **XAMLPad**.</span></span> <span data-ttu-id="dbf8c-118">在 [轉譯] 窗格中，XAMLPad 會呈現撰寫程式碼窗格中的 XAML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-118">In the rendering pane, XAMLPad renders the XAML code written in the code pane.</span></span> <span data-ttu-id="dbf8c-119">您可以編輯 XAML 程式碼，所做的變更會立即顯示在 [轉譯] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-119">You can edit the XAML code, and the changes immediately appear in the rendering pane.</span></span>  
  
#### <a name="got-ink"></a><span data-ttu-id="dbf8c-120">有筆墨嗎？</span><span class="sxs-lookup"><span data-stu-id="dbf8c-120">Got Ink?</span></span>  
 <span data-ttu-id="dbf8c-121">若要啟動您的第一個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援筆墨的應用程式：</span><span class="sxs-lookup"><span data-stu-id="dbf8c-121">To start your first [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that supports ink:</span></span>  
  
1.  <span data-ttu-id="dbf8c-122">開啟 Microsoft Visual Studio 2005</span><span class="sxs-lookup"><span data-stu-id="dbf8c-122">Open Microsoft Visual Studio 2005</span></span>  
  
2.  <span data-ttu-id="dbf8c-123">建立新**Windows 應用程式 (WPF)**</span><span class="sxs-lookup"><span data-stu-id="dbf8c-123">Create a new **Windows Application (WPF)**</span></span>  
  
3.  <span data-ttu-id="dbf8c-124">型別`<InkCanvas/>`之間`<Grid>`標記</span><span class="sxs-lookup"><span data-stu-id="dbf8c-124">Type `<InkCanvas/>` between the `<Grid>` tags</span></span>  
  
4.  <span data-ttu-id="dbf8c-125">按**F5**來偵錯工具中啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="dbf8c-125">Press **F5** to launch your application in the debugger</span></span>  
  
5.  <span data-ttu-id="dbf8c-126">使用手寫筆或滑鼠，撰寫**hello world**視窗中</span><span class="sxs-lookup"><span data-stu-id="dbf8c-126">Using a stylus or mouse, write **hello world** in the window</span></span>  
  
 <span data-ttu-id="dbf8c-127">您已撰寫筆墨相當於使用只有 12 按鍵的"hello world"應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="dbf8c-127">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>  
  
#### <a name="spice-up-your-application"></a><span data-ttu-id="dbf8c-128">您的應用程式讓動</span><span class="sxs-lookup"><span data-stu-id="dbf8c-128">Spice Up Your Application</span></span>  
 <span data-ttu-id="dbf8c-129">讓我們來看的某些功能的優點[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-129">Let’s take advantage of some features of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  <span data-ttu-id="dbf8c-130">取代開頭之間的所有內容\<視窗 > 並關閉\</Window > 以取得筆墨表面背景漸層筆刷下列標記的標記。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-130">Replace everything between the opening \<Window> and closing \</Window> tags with the following markup to get a gradient brush background on your inking surface.</span></span>  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a><span data-ttu-id="dbf8c-131">使用動畫</span><span class="sxs-lookup"><span data-stu-id="dbf8c-131">Using Animation</span></span>  
 <span data-ttu-id="dbf8c-132">玩看，我們製作動畫漸層筆刷的色彩。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-132">For fun, let's animate the colors of the gradient brush.</span></span> <span data-ttu-id="dbf8c-133">加入下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]關閉後`</InkCanvas>`標記結束之前`</Page>`標記。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-133">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] after the closing `</InkCanvas>` tag but before the closing `</Page>` tag.</span></span>  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a><span data-ttu-id="dbf8c-134">加入一些程式碼背後的 XAML</span><span class="sxs-lookup"><span data-stu-id="dbf8c-134">Adding Some Code Behind the XAML</span></span>  
 <span data-ttu-id="dbf8c-135">雖然 XAML 會很容易就能設計使用者介面，任何真實世界應用程式必須加入程式碼來處理事件。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-135">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="dbf8c-136">以下是以滑鼠右鍵按一下回應來自滑鼠的筆墨會放大的簡單範例：</span><span class="sxs-lookup"><span data-stu-id="dbf8c-136">Here is a simple example that zooms in on the ink in response to a right-click from a mouse:</span></span>  
  
 <span data-ttu-id="dbf8c-137">設定`MouseRightButtonUp`處理常式中的您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="dbf8c-137">Set the `MouseRightButtonUp` handler in your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span></span>  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 <span data-ttu-id="dbf8c-138">在 Visual Studio 方案總管 中，展開 Windows1.xaml 並開啟 Window1.xaml.cs 或 Window1.xaml.vb，如果您使用 Visual Basic 的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-138">In Visual Studio’s Solution Explorer, expand Windows1.xaml and open the code-behind file, Window1.xaml.cs or Window1.xaml.vb if you are using Visual Basic.</span></span> <span data-ttu-id="dbf8c-139">加入下列事件處理常式程式碼：</span><span class="sxs-lookup"><span data-stu-id="dbf8c-139">Add the following event handler code:</span></span>  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 <span data-ttu-id="dbf8c-140">現在，執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-140">Now, run your application.</span></span> <span data-ttu-id="dbf8c-141">加入某些筆墨然後以滑鼠右鍵按一下使用滑鼠，或執行按保留對等項目具有手寫筆。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-141">Add some ink and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>  
  
#### <a name="using-procedural-code-instead-of-xaml"></a><span data-ttu-id="dbf8c-142">使用程序程式碼，而不 XAML</span><span class="sxs-lookup"><span data-stu-id="dbf8c-142">Using Procedural Code Instead of XAML</span></span>  
 <span data-ttu-id="dbf8c-143">您可以存取所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程序程式碼中的功能。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-143">You can access all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] features from procedural code.</span></span> <span data-ttu-id="dbf8c-144">以下是"Hello 筆墨 World"應用程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，不使用任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]完全。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-144">Here is a "Hello Ink World" application for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] that doesn’t use any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] at all.</span></span> <span data-ttu-id="dbf8c-145">將下列程式碼貼到空白 Visual Studio 中的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbf8c-145">Paste the code below into an empty Console Application in Visual Studio.</span></span> <span data-ttu-id="dbf8c-146">新增 PresentationCore、 PresentationFramework 和 WindowsBase 組件的參考，並按下建置應用程式**F5**:</span><span class="sxs-lookup"><span data-stu-id="dbf8c-146">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies, and build the application by pressing **F5**:</span></span>  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dbf8c-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbf8c-147">See Also</span></span>  
 [<span data-ttu-id="dbf8c-148">數位筆跡</span><span class="sxs-lookup"><span data-stu-id="dbf8c-148">Digital Ink</span></span>](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [<span data-ttu-id="dbf8c-149">收集筆墨</span><span class="sxs-lookup"><span data-stu-id="dbf8c-149">Collecting Ink</span></span>](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [<span data-ttu-id="dbf8c-150">手寫辨識</span><span class="sxs-lookup"><span data-stu-id="dbf8c-150">Handwriting Recognition</span></span>](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [<span data-ttu-id="dbf8c-151">儲存筆墨</span><span class="sxs-lookup"><span data-stu-id="dbf8c-151">Storing Ink</span></span>](../../../../docs/framework/wpf/advanced/storing-ink.md)
