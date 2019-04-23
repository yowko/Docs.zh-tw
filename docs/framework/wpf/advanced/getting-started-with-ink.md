---
title: 在 Visual Studio 中的 WPF 應用程式中建立 InkCanvas
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 4309b1108b2ea96eb298ff3bb876a0f63b80dc32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343586"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="8a385-102">開始使用 WPF 中的筆墨</span><span class="sxs-lookup"><span data-stu-id="8a385-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="8a385-103">Windows Presentation Foundation (WPF) 具有筆跡功能，可讓您輕鬆地將您的應用程式的數位筆跡。</span><span class="sxs-lookup"><span data-stu-id="8a385-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a385-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="8a385-104">Prerequisites</span></span>

<span data-ttu-id="8a385-105">若要使用下列的範例，請先安裝[Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="8a385-105">To use the following examples, first install [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="8a385-106">它也有助於了解如何撰寫基本的 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a385-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="8a385-107">開始使用 WPF 的協助，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8a385-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="8a385-108">快速入門</span><span class="sxs-lookup"><span data-stu-id="8a385-108">Quick Start</span></span>

<span data-ttu-id="8a385-109">本節可協助您撰寫簡單的 WPF 應用程式會收集筆跡。</span><span class="sxs-lookup"><span data-stu-id="8a385-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="8a385-110">有筆墨嗎？</span><span class="sxs-lookup"><span data-stu-id="8a385-110">Got Ink?</span></span>

<span data-ttu-id="8a385-111">若要建立支援筆墨的 WPF 應用程式：</span><span class="sxs-lookup"><span data-stu-id="8a385-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="8a385-112">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8a385-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="8a385-113">建立新**WPF 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8a385-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="8a385-114">在 [**新的專案**] 對話方塊中，展開**已安裝** > **Visual C#** 或**Visual Basic**  >  **Windows 桌面**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="8a385-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="8a385-115">然後，選取**WPF 應用程式 (.NET Framework)** 應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="8a385-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="8a385-116">輸入名稱，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="8a385-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="8a385-117">Visual Studio 建立專案，並*MainWindow.xaml*會在設計工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="8a385-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="8a385-118">型別`<InkCanvas/>`之間`<Grid>`標記。</span><span class="sxs-lookup"><span data-stu-id="8a385-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![InkCanvas 標記的 XAML 設計工具](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="8a385-120">按下**F5**來啟動您的應用程式偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8a385-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="8a385-121">使用手寫筆或滑鼠，撰寫**hello world**  視窗中。</span><span class="sxs-lookup"><span data-stu-id="8a385-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="8a385-122">您已撰寫筆墨相當於只有 12 的按鍵輸入的"hello world"應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="8a385-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="8a385-123">為您的應用程式增添</span><span class="sxs-lookup"><span data-stu-id="8a385-123">Spice Up Your App</span></span>

<span data-ttu-id="8a385-124">讓我們好好利用 WPF 的某些功能。</span><span class="sxs-lookup"><span data-stu-id="8a385-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="8a385-125">取代所有項目之間的開頭和結尾\<視窗 > 標記，以下列標記：</span><span class="sxs-lookup"><span data-stu-id="8a385-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

<span data-ttu-id="8a385-126">此 XAML 會建立漸層筆刷背景筆跡的介面上。</span><span class="sxs-lookup"><span data-stu-id="8a385-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![在筆跡介面在 WPF 應用程式中的漸層色彩](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="8a385-128">加入一些程式碼背後的 XAML</span><span class="sxs-lookup"><span data-stu-id="8a385-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="8a385-129">XAML 可以很容易就能設計使用者介面，而任何實際的應用程式必須加入程式碼來處理事件。</span><span class="sxs-lookup"><span data-stu-id="8a385-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="8a385-130">以下是簡單的範例，以滑鼠右鍵按一下的滑鼠回應中的筆墨會放大。</span><span class="sxs-lookup"><span data-stu-id="8a385-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="8a385-131">設定`MouseRightButtonUp`在您的 XAML 中的處理常式：</span><span class="sxs-lookup"><span data-stu-id="8a385-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="8a385-132">在 [**方案總管] 中**、 展開 MainWindow.xaml 並開啟程式碼後置檔案 （MainWindow.xaml.cs 或 MainWindow.xaml.vb）。</span><span class="sxs-lookup"><span data-stu-id="8a385-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="8a385-133">新增下列事件處理常式程式碼：</span><span class="sxs-lookup"><span data-stu-id="8a385-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="8a385-134">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a385-134">Run the application.</span></span> <span data-ttu-id="8a385-135">新增一些墨水，然後以滑鼠右鍵按一下滑鼠或手寫筆使用中執行按保留對等項目。</span><span class="sxs-lookup"><span data-stu-id="8a385-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="8a385-136">顯示您以滑鼠右鍵按一下 每次會放大。</span><span class="sxs-lookup"><span data-stu-id="8a385-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="8a385-137">使用程序程式碼，而不是 XAML</span><span class="sxs-lookup"><span data-stu-id="8a385-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="8a385-138">您可以存取所有的 WPF 功能從程序性程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a385-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="8a385-139">請遵循下列步驟來建立不使用任何 XAML 的 WPF 的"Hello 筆墨 World"應用程式。</span><span class="sxs-lookup"><span data-stu-id="8a385-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="8a385-140">Visual Studio 中建立新的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="8a385-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="8a385-141">在 [**新的專案**] 對話方塊中，展開**已安裝** > **Visual C#** 或**Visual Basic**  >  **Windows 桌面**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="8a385-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="8a385-142">然後，選取**主控台應用程式 (.NET Framework)** 應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="8a385-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="8a385-143">輸入名稱，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="8a385-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="8a385-144">將下列程式碼貼到 Program.cs 或 Program.vb 檔案中：</span><span class="sxs-lookup"><span data-stu-id="8a385-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="8a385-145">新增 PresentationCore、 PresentationFramework、 與 WindowsBase 組件的參考，以滑鼠右鍵按一下**參考**中**方案總管**，然後選擇**加入參考**.</span><span class="sxs-lookup"><span data-stu-id="8a385-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![顯示 PresentationCore 與 PresentationFramework 參考管理員](./media/getting-started-with-ink/references.png)

1. <span data-ttu-id="8a385-147">建置應用程式藉由按下**F5**。</span><span class="sxs-lookup"><span data-stu-id="8a385-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a385-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a385-148">See also</span></span>

- [<span data-ttu-id="8a385-149">數位筆跡</span><span class="sxs-lookup"><span data-stu-id="8a385-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="8a385-150">收集筆墨</span><span class="sxs-lookup"><span data-stu-id="8a385-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="8a385-151">手寫辨識</span><span class="sxs-lookup"><span data-stu-id="8a385-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="8a385-152">儲存筆墨</span><span class="sxs-lookup"><span data-stu-id="8a385-152">Storing Ink</span></span>](storing-ink.md)
