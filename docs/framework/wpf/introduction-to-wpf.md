---
title: WPF 簡介
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: ecdd3b3c24b71917efb0d982d1f23737673622f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744717"
---
# <a name="wpf-overview"></a><span data-ttu-id="51b3a-102">WPF 概觀</span><span class="sxs-lookup"><span data-stu-id="51b3a-102">WPF overview</span></span>

<span data-ttu-id="51b3a-103">Windows Presentation Foundation (WPF) 可讓您建立具有豐富視覺效果之使用者介面的 Windows 桌面用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Contoso Healthcare UI 範例](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="51b3a-105">WPF 的核心是與解析度無關並以向量為基礎的轉譯引擎，其建置目的是為了利用現代化圖形硬體。</span><span class="sxs-lookup"><span data-stu-id="51b3a-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="51b3a-106">WPF 利用一組完整的應用程式開發功能來擴充核心，包括 Extensible Application Markup Language (XAML)、控制項、資料繫結、版面配置、2D 和 3D 圖形、動畫、樣式、範本、文件、媒體、文字，以及印刷樣式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="51b3a-107">WPF 是 .NET 的一部分，因此您可以建置能納入 .NET API 其他元素的應用程式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="51b3a-108">本概觀適用於初學者，內容涵蓋 WPF 的主要功能和概念。</span><span class="sxs-lookup"><span data-stu-id="51b3a-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="51b3a-109">使用 WPF 的程式</span><span class="sxs-lookup"><span data-stu-id="51b3a-109">Program with WPF</span></span>

<span data-ttu-id="51b3a-110">WPF 是以 .NET 類型的子集來表示，這些類型大部分位於 <xref:System.Windows> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="51b3a-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="51b3a-111">如果您之前曾使用 ASP.NET 和 Windows Forms 等受控技術來搭配 .NET 建置應用程式，便應該很熟悉基本 WPF 程式設計功能；您可以具現化類別、設定屬性、呼叫方法，以及處理事件；這些工作都可以透過您最愛的 .NET 程式設計語言 (例如 C# 或 Visual Basic) 來完成。</span><span class="sxs-lookup"><span data-stu-id="51b3a-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="51b3a-112">WPF 包含可增強屬性和事件的額外程式設計建構： [相依性屬性](advanced/dependency-properties-overview.md) 和 [路由事件](advanced/routed-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="51b3a-113">標記和程式碼後置</span><span class="sxs-lookup"><span data-stu-id="51b3a-113">Markup and code-behind</span></span>

<span data-ttu-id="51b3a-114">WPF 可讓您使用「標記」和「程式碼後置」來開發應用程式，這是 ASP.NET 開發人員應該很熟悉的功能。</span><span class="sxs-lookup"><span data-stu-id="51b3a-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="51b3a-115">您通常會使用 XAML 標記來實作應用程式的外觀，同時使用 Managed 程式設計語言 (程式碼後置) 來實作其行為。</span><span class="sxs-lookup"><span data-stu-id="51b3a-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="51b3a-116">將外觀與行為區隔開來的優點如下：</span><span class="sxs-lookup"><span data-stu-id="51b3a-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="51b3a-117">由於外觀特定標記未與行為特定程式碼緊密結合，因此可降低開發和維護成本。</span><span class="sxs-lookup"><span data-stu-id="51b3a-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="51b3a-118">由於實作應用程式外觀的設計人員可以與實作應用程式行為的設計人員同時進行，因此開發作業會更有效率。</span><span class="sxs-lookup"><span data-stu-id="51b3a-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="51b3a-119">WPF 應用程式的[全球化和當地語系化](advanced/wpf-globalization-and-localization-overview.md) 已經過簡化。</span><span class="sxs-lookup"><span data-stu-id="51b3a-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="51b3a-120">標記</span><span class="sxs-lookup"><span data-stu-id="51b3a-120">Markup</span></span>

<span data-ttu-id="51b3a-121">XAML 是以宣告方式來實作應用程式外觀的 XML 標記語言。</span><span class="sxs-lookup"><span data-stu-id="51b3a-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="51b3a-122">您通常可以使用它來建立視窗、對話方塊、頁面和使用者控制項，並填入控制項、圖案和圖形。</span><span class="sxs-lookup"><span data-stu-id="51b3a-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="51b3a-123">下列範例會使用 XAML 來執行包含單一按鈕的視窗外觀：</span><span class="sxs-lookup"><span data-stu-id="51b3a-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="51b3a-124">具體而言，這個 XAML 會分別使用 `Window` 和 `Button` 項目來定義一個視窗和一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="51b3a-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="51b3a-125">每個項目都會透過屬性進行設定，例如 `Window` 項目的 `Title` 屬性可指定視窗的標題列文字。</span><span class="sxs-lookup"><span data-stu-id="51b3a-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="51b3a-126">在執行階段，WPF 會將標記中定義的項目和屬性轉換成 WPF 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="51b3a-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="51b3a-127">例如， `Window` 項目會轉換成 <xref:System.Windows.Window> 類別的執行個體，其 <xref:System.Windows.Window.Title%2A> 屬性即為 `Title` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="51b3a-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="51b3a-128">下圖顯示上一個範例中的 XAML 所定義的使用者介面（UI）：</span><span class="sxs-lookup"><span data-stu-id="51b3a-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![包含按鈕的視窗](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="51b3a-130">由於 XAML 是以 XML 為基礎，您以此撰寫的 UI 會組合成巢狀項目階層架構，稱為 [項目樹狀結構](advanced/trees-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="51b3a-131">項目樹狀結構提供一個邏輯和直覺方式來建立及管理 UI。</span><span class="sxs-lookup"><span data-stu-id="51b3a-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="51b3a-132">程式碼後置</span><span class="sxs-lookup"><span data-stu-id="51b3a-132">Code-behind</span></span>

<span data-ttu-id="51b3a-133">應用程式的主要行為是實作回應使用者互動的功能，包括處理事件 (例如按一下功能表、工具列或按鈕)，以及呼叫商務邏輯和資料存取邏輯進行回應。</span><span class="sxs-lookup"><span data-stu-id="51b3a-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="51b3a-134">在 WPF 中，這項行為會在與標記建立關聯的程式碼中實作。</span><span class="sxs-lookup"><span data-stu-id="51b3a-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="51b3a-135">這種類型的程式碼稱為程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="51b3a-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="51b3a-136">下列範例顯示上一個範例中的更新標記和程式碼後置：</span><span class="sxs-lookup"><span data-stu-id="51b3a-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

<span data-ttu-id="51b3a-137">在這個範例中，程式碼後置會實作一個衍生自 <xref:System.Windows.Window> 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="51b3a-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="51b3a-138">它使用 `x:Class` 屬性來建立標記與程式碼後置類別的關聯，</span><span class="sxs-lookup"><span data-stu-id="51b3a-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="51b3a-139">並從程式碼後置類別的建構函式呼叫`InitializeComponent` ，以合併標記中定義的 UI 與程式碼後置類別</span><span class="sxs-lookup"><span data-stu-id="51b3a-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="51b3a-140">（當您建立應用程式時，系統會為您產生`InitializeComponent`，這就是您不需要手動執行的原因）。`x:Class` 和 `InitializeComponent` 的組合，可確保您的執行會在建立時正確地初始化。</span><span class="sxs-lookup"><span data-stu-id="51b3a-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="51b3a-141">程式碼後置類別也會針對按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件實作事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="51b3a-142">當您按一下按鈕時，事件處理常式會呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> 方法來顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="51b3a-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="51b3a-143">下圖顯示按一下按鈕時的結果：</span><span class="sxs-lookup"><span data-stu-id="51b3a-143">The following figure shows the result when the button is clicked:</span></span>

![MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="51b3a-145">Controls</span><span class="sxs-lookup"><span data-stu-id="51b3a-145">Controls</span></span>

<span data-ttu-id="51b3a-146">應用程式模型所傳遞的使用者體驗是已建構的控制項。</span><span class="sxs-lookup"><span data-stu-id="51b3a-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="51b3a-147">在 WPF 中，「控制項」是一個籠統的名詞，泛指裝載於視窗或頁面上之具有使用者介面並實作一些行為的某種 WPF 類別。</span><span class="sxs-lookup"><span data-stu-id="51b3a-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="51b3a-148">如需詳細資訊，請參閱 [控制項](controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="51b3a-149">依功能列出 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="51b3a-149">WPF controls by function</span></span>

<span data-ttu-id="51b3a-150">內建的 WPF 控制項列示如下：</span><span class="sxs-lookup"><span data-stu-id="51b3a-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="51b3a-151">**按鈕**： <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.Primitives.RepeatButton>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="51b3a-152">**資料顯示**： <xref:System.Windows.Controls.DataGrid>、<xref:System.Windows.Controls.ListView>和 <xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="51b3a-153">**日期顯示和選取**： <xref:System.Windows.Controls.Calendar> 和 <xref:System.Windows.Controls.DatePicker>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="51b3a-154">**對話方塊**： <xref:Microsoft.Win32.OpenFileDialog>、 <xref:System.Windows.Controls.PrintDialog>和 <xref:Microsoft.Win32.SaveFileDialog>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="51b3a-155">**數位筆跡**： <xref:System.Windows.Controls.InkCanvas> 和 <xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="51b3a-156">**文件**： <xref:System.Windows.Controls.DocumentViewer>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、 <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentScrollViewer>和 <xref:System.Windows.Controls.StickyNoteControl>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="51b3a-157">**輸入**： <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>和 <xref:System.Windows.Controls.PasswordBox>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="51b3a-158">**版面配置**： <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Primitives.BulletDecorator>、 <xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Expander>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.GridView>、 <xref:System.Windows.Controls.GridSplitter>、 <xref:System.Windows.Controls.GroupBox>、 <xref:System.Windows.Controls.Panel>、 <xref:System.Windows.Controls.Primitives.ResizeGrip>、 <xref:System.Windows.Controls.Separator>、 <xref:System.Windows.Controls.Primitives.ScrollBar>、 <xref:System.Windows.Controls.ScrollViewer>、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.Primitives.Thumb>、 <xref:System.Windows.Controls.Viewbox>、 <xref:System.Windows.Controls.VirtualizingStackPanel>、 <xref:System.Windows.Window>和 <xref:System.Windows.Controls.WrapPanel>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="51b3a-159">**媒體**： <xref:System.Windows.Controls.Image>、 <xref:System.Windows.Controls.MediaElement>和 <xref:System.Windows.Controls.SoundPlayerAction>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="51b3a-160">**功能表**： <xref:System.Windows.Controls.ContextMenu>、 <xref:System.Windows.Controls.Menu>和 <xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="51b3a-161">**巡覽**： <xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Documents.Hyperlink>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>和 <xref:System.Windows.Controls.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="51b3a-162">**選取**： <xref:System.Windows.Controls.CheckBox>、 <xref:System.Windows.Controls.ComboBox>、 <xref:System.Windows.Controls.ListBox>、 <xref:System.Windows.Controls.RadioButton>和 <xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="51b3a-163">**使用者資訊**： <xref:System.Windows.Controls.AccessText>、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Primitives.Popup>、 <xref:System.Windows.Controls.ProgressBar>、 <xref:System.Windows.Controls.Primitives.StatusBar>、 <xref:System.Windows.Controls.TextBlock>和 <xref:System.Windows.Controls.ToolTip>。</span><span class="sxs-lookup"><span data-stu-id="51b3a-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="51b3a-164">輸入和命令</span><span class="sxs-lookup"><span data-stu-id="51b3a-164">Input and commands</span></span>

<span data-ttu-id="51b3a-165">控制項最常用來偵測及回應使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="51b3a-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="51b3a-166">[WPF 輸入系統](advanced/input-overview.md) 使用直接和路由事件來支援文字輸入、焦點管理和滑鼠定位。</span><span class="sxs-lookup"><span data-stu-id="51b3a-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="51b3a-167">應用程式通常具有複雜的輸入需求。</span><span class="sxs-lookup"><span data-stu-id="51b3a-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="51b3a-168">WPF 提供一個[命令系統](advanced/commanding-overview.md)，將使用者輸入動作與回應這些動作的程式碼區隔開。</span><span class="sxs-lookup"><span data-stu-id="51b3a-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="51b3a-169">配置</span><span class="sxs-lookup"><span data-stu-id="51b3a-169">Layout</span></span>

<span data-ttu-id="51b3a-170">當您建立使用者介面時，您可依位置和大小排列控制項，以形成一個版面配置。</span><span class="sxs-lookup"><span data-stu-id="51b3a-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="51b3a-171">所有版面配置的一個關鍵需求是隨視窗大小和顯示設定的變更進行調整。</span><span class="sxs-lookup"><span data-stu-id="51b3a-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="51b3a-172">WPF 為您提供一流且可擴充的版面配置系統，而不是強迫您在這些情況下撰寫程式碼來調整版面配置。</span><span class="sxs-lookup"><span data-stu-id="51b3a-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="51b3a-173">這個版面配置系統是以相對定位為基礎，藉此提升依視窗和顯示狀況變更來做調整的能力。</span><span class="sxs-lookup"><span data-stu-id="51b3a-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="51b3a-174">此外，這個版面配置系統可管理控制項之間的交涉，以決定版面配置。</span><span class="sxs-lookup"><span data-stu-id="51b3a-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="51b3a-175">此交涉是兩個步驟的程序：控制項會先指示其父代所需的位置和大小，然後再由父代指示控制項其可擁有的空間。</span><span class="sxs-lookup"><span data-stu-id="51b3a-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="51b3a-176">版面配置系統會透過基底 WPF 類別公開給子控制項。</span><span class="sxs-lookup"><span data-stu-id="51b3a-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="51b3a-177">WPF 針對格線、堆疊和停駐等常見版面配置，提供了數個版面配置控制項：</span><span class="sxs-lookup"><span data-stu-id="51b3a-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="51b3a-178"><xref:System.Windows.Controls.Canvas>：子控制項會提供自己的版面配置。</span><span class="sxs-lookup"><span data-stu-id="51b3a-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="51b3a-179"><xref:System.Windows.Controls.DockPanel>：子控制項會沿著面板邊緣對齊。</span><span class="sxs-lookup"><span data-stu-id="51b3a-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="51b3a-180"><xref:System.Windows.Controls.Grid>：子控制項會依資料列和資料行定位。</span><span class="sxs-lookup"><span data-stu-id="51b3a-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="51b3a-181"><xref:System.Windows.Controls.StackPanel>：子控制項會垂直或水平堆疊。</span><span class="sxs-lookup"><span data-stu-id="51b3a-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="51b3a-182"><xref:System.Windows.Controls.VirtualizingStackPanel>：子控制項會依水平或垂直方向，以單行顯示及排列。</span><span class="sxs-lookup"><span data-stu-id="51b3a-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="51b3a-183"><xref:System.Windows.Controls.WrapPanel>：子控制項會從左至右排序定位，並在目前這一行的控制項超出空間所允許的數目時，換至下一行。</span><span class="sxs-lookup"><span data-stu-id="51b3a-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="51b3a-184">下列範例會使用 <xref:System.Windows.Controls.DockPanel> 來配置數個 <xref:System.Windows.Controls.TextBox> 控制項：</span><span class="sxs-lookup"><span data-stu-id="51b3a-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="51b3a-185"><xref:System.Windows.Controls.DockPanel> 可讓子 <xref:System.Windows.Controls.TextBox> 控制項指示排列方式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="51b3a-186">為了執行這項操作，<xref:System.Windows.Controls.DockPanel> 會實作公開給子控制項的 `Dock` 附加屬性，讓每個控制項都能指定停駐樣式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="51b3a-187">WPF 建構是由父控制項實作並可供子控制項使用的屬性，又稱為[附加屬性](advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="51b3a-188">下圖顯示上述範例中 XAML 標記的結果：</span><span class="sxs-lookup"><span data-stu-id="51b3a-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![DockPanel 頁面](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="51b3a-190">資料繫結</span><span class="sxs-lookup"><span data-stu-id="51b3a-190">Data binding</span></span>

<span data-ttu-id="51b3a-191">大多數已建立的應用程式會為使用者提供檢視及編輯資料的方法。</span><span class="sxs-lookup"><span data-stu-id="51b3a-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="51b3a-192">至於 WPF 應用程式，儲存和存取資料的工作已由 SQL Server 和 ADO.NET 等技術提供。</span><span class="sxs-lookup"><span data-stu-id="51b3a-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="51b3a-193">存取資料並將資料載入應用程式的 Managed 物件之後，才會開始 WPF 應用程式的困難工作。</span><span class="sxs-lookup"><span data-stu-id="51b3a-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="51b3a-194">基本上，這涉及兩個動作：</span><span class="sxs-lookup"><span data-stu-id="51b3a-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="51b3a-195">將資料從 Managed 物件複製到控制項，以在其中顯示及編輯資料。</span><span class="sxs-lookup"><span data-stu-id="51b3a-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="51b3a-196">確保使用控制項對資料所做的變更，會複製回 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="51b3a-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="51b3a-197">為了簡化應用程式開發工作，WPF 提供資料繫結引擎以自動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="51b3a-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="51b3a-198">資料繫結引擎的核心單位是 <xref:System.Windows.Data.Binding> 類別，其工作是將控制項 (繫結目標) 繫結至資料物件 (繫結來源)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="51b3a-199">下圖說明這個關聯性：</span><span class="sxs-lookup"><span data-stu-id="51b3a-199">This relationship is illustrated by the following figure:</span></span>

![基本資料繫結圖表](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="51b3a-201">下個範例示範如何將 <xref:System.Windows.Controls.TextBox> 繫結至自訂 `Person` 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="51b3a-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="51b3a-202">`Person` 實作則如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="51b3a-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="51b3a-203">下列標記會將 <xref:System.Windows.Controls.TextBox> 系結至自訂 `Person` 物件的實例：</span><span class="sxs-lookup"><span data-stu-id="51b3a-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

<span data-ttu-id="51b3a-204">在這個範例中， `Person` 類別會在程式碼後置中具現化，並已設定為 `DataBindingWindow`的資料內容。</span><span class="sxs-lookup"><span data-stu-id="51b3a-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="51b3a-205">在標記中， <xref:System.Windows.Controls.TextBox.Text%2A> 的 <xref:System.Windows.Controls.TextBox> 屬性已繫結至 `Person.Name` 屬性 (使用"`{Binding ... }`" XAML 語法)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="51b3a-206">這個 XAML 會指示 WPF 將 <xref:System.Windows.Controls.TextBox> 控制項繫結至儲存在視窗之 `Person` 屬性中的 <xref:System.Windows.FrameworkElement.DataContext%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="51b3a-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="51b3a-207">WPF 資料繫結引擎還提供其他支援，包括驗證、排序、篩選和群組。</span><span class="sxs-lookup"><span data-stu-id="51b3a-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="51b3a-208">此外，資料繫結可在標準 WPF 控制項所顯示的使用者介面不適用時，使用資料範本來建立繫結資料的自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="51b3a-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="51b3a-209">如需詳細資訊，請參閱[資料繫結概觀](../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="51b3a-210">圖形</span><span class="sxs-lookup"><span data-stu-id="51b3a-210">Graphics</span></span>

<span data-ttu-id="51b3a-211">WPF 引進了一組詳盡、可擴充且彈性的圖形功能，其優點如下：</span><span class="sxs-lookup"><span data-stu-id="51b3a-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="51b3a-212">**解析度獨立與裝置獨立圖形**。</span><span class="sxs-lookup"><span data-stu-id="51b3a-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="51b3a-213">WPF 圖形系統的基本測量單位是裝置獨立畫素，不論實際螢幕解析度為何，都是 1 英吋的 1/96，並會為解析度獨立與裝置獨立轉譯提供基礎。</span><span class="sxs-lookup"><span data-stu-id="51b3a-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="51b3a-214">每個裝置獨立畫素會依轉譯所在系統的 DPI (每英吋的點數) 設定來自動調整。</span><span class="sxs-lookup"><span data-stu-id="51b3a-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="51b3a-215">**改進精確度**。</span><span class="sxs-lookup"><span data-stu-id="51b3a-215">**Improved precision**.</span></span> <span data-ttu-id="51b3a-216">WPF 座標系統是使用雙精確度浮點數進行測量，而不是單精確度。</span><span class="sxs-lookup"><span data-stu-id="51b3a-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="51b3a-217">轉換和透明度值也會以雙精確度來表示。</span><span class="sxs-lookup"><span data-stu-id="51b3a-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="51b3a-218">WPF 也支援廣色域 (scRGB)，並提供整合式支援，以管理來自不同色彩空間的輸入。</span><span class="sxs-lookup"><span data-stu-id="51b3a-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="51b3a-219">**進階圖形和動畫支援**：</span><span class="sxs-lookup"><span data-stu-id="51b3a-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="51b3a-220">WPF 藉由為您管理動畫場景來簡化圖形程式設計；您不需要擔心場景處理、轉譯迴圈和雙線性插補。</span><span class="sxs-lookup"><span data-stu-id="51b3a-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="51b3a-221">此外，WPF 還提供叫用測試支援和完整的 alpha 複合支援。</span><span class="sxs-lookup"><span data-stu-id="51b3a-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="51b3a-222">**硬體加速**：</span><span class="sxs-lookup"><span data-stu-id="51b3a-222">**Hardware acceleration**.</span></span> <span data-ttu-id="51b3a-223">WPF 圖形系統利用圖形硬體將 CPU 使用量降到最低。</span><span class="sxs-lookup"><span data-stu-id="51b3a-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="51b3a-224">2D 圖形</span><span class="sxs-lookup"><span data-stu-id="51b3a-224">2D shapes</span></span>

<span data-ttu-id="51b3a-225">WPF 提供以通用向量繪製之 2D 圖形的圖庫，例如下圖所示的矩形和橢圓形：</span><span class="sxs-lookup"><span data-stu-id="51b3a-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![橢圓形和矩形](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="51b3a-227">圖案有趣的一點是它不僅用於顯示，還可實作許多您預期控制項會有的功能，包括鍵盤和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="51b3a-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="51b3a-228">下列範例顯示正在處理之 <xref:System.Windows.Shapes.Ellipse> 的 <xref:System.Windows.UIElement.MouseUp> 事件：</span><span class="sxs-lookup"><span data-stu-id="51b3a-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="51b3a-229">下圖顯示上述程式碼所產生的結果：</span><span class="sxs-lookup"><span data-stu-id="51b3a-229">The following figure shows what is produced by the preceding code:</span></span>

![包含「您已經按一下這個橢圓形&#33;」文字的視窗](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="51b3a-231">如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="51b3a-232">2D 幾何</span><span class="sxs-lookup"><span data-stu-id="51b3a-232">2D geometries</span></span>

<span data-ttu-id="51b3a-233">WPF 提供的 2D 圖形涵蓋一組標準的基本圖形。</span><span class="sxs-lookup"><span data-stu-id="51b3a-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="51b3a-234">不過，您可能需要建立自訂圖案，來實現自訂使用者介面的設計。</span><span class="sxs-lookup"><span data-stu-id="51b3a-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="51b3a-235">為了達成這個目的，WPF 提供了幾何。</span><span class="sxs-lookup"><span data-stu-id="51b3a-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="51b3a-236">下圖示範如何使用幾何來建立自訂圖案，您可以直接繪製、當做筆刷來使用，或是用來裁剪其他圖案和控制項。</span><span class="sxs-lookup"><span data-stu-id="51b3a-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="51b3a-237"><xref:System.Windows.Shapes.Path> 物件可用來繪製封閉或開放的圖案、多個圖案，甚至是彎曲的圖案。</span><span class="sxs-lookup"><span data-stu-id="51b3a-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="51b3a-238"><xref:System.Windows.Media.Geometry> 物件可用來裁剪、叫用測試及轉譯 2D 圖表資料。</span><span class="sxs-lookup"><span data-stu-id="51b3a-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![各種路徑用法](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="51b3a-240">如需詳細資訊，請參閱[幾何概觀](graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="51b3a-241">2D 效果</span><span class="sxs-lookup"><span data-stu-id="51b3a-241">2D effects</span></span>

<span data-ttu-id="51b3a-242">WPF 2D 功能子集包含漸層、點陣圖、繪圖、利用視訊繪製、旋轉、縮放和傾斜等視覺效果。</span><span class="sxs-lookup"><span data-stu-id="51b3a-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="51b3a-243">這些全都是透過筆刷達成;下圖顯示一些範例：</span><span class="sxs-lookup"><span data-stu-id="51b3a-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![不同筆刷的圖例](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="51b3a-245">如需詳細資訊，請參閱 [WPF 筆刷概觀](graphics-multimedia/wpf-brushes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="51b3a-246">3D 轉譯</span><span class="sxs-lookup"><span data-stu-id="51b3a-246">3D rendering</span></span>

<span data-ttu-id="51b3a-247">WPF 也包含可與 2D 圖形互動的 3D 轉譯功能，以便建立更生動有趣的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="51b3a-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="51b3a-248">例如，下圖顯示轉譯成3D 圖案的2D 影像：</span><span class="sxs-lookup"><span data-stu-id="51b3a-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Visual3D 範例螢幕擷取畫面](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="51b3a-250">如需詳細資訊，請參閱 [3D 圖形診斷](graphics-multimedia/3-d-graphics-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="51b3a-251">動畫</span><span class="sxs-lookup"><span data-stu-id="51b3a-251">Animation</span></span>

<span data-ttu-id="51b3a-252">WPF 動畫支援可讓您將控制項設為放大、搖晃、旋轉和淡出，以建立有趣的網頁切換及執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="51b3a-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="51b3a-253">您可以建立大多數 WPF 類別的動畫，甚至是自訂類別。</span><span class="sxs-lookup"><span data-stu-id="51b3a-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="51b3a-254">下圖顯示作用中的簡單動畫：</span><span class="sxs-lookup"><span data-stu-id="51b3a-254">The following figure shows a simple animation in action:</span></span>

![立方體動畫的影像](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="51b3a-256">如需詳細資訊，請參閱[動畫概觀](graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="51b3a-257">媒體</span><span class="sxs-lookup"><span data-stu-id="51b3a-257">Media</span></span>

<span data-ttu-id="51b3a-258">傳達豐富內容的一個方式是透過視聽媒體。</span><span class="sxs-lookup"><span data-stu-id="51b3a-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="51b3a-259">WPF 提供對影像、視訊和音訊的特殊支援。</span><span class="sxs-lookup"><span data-stu-id="51b3a-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="51b3a-260">影像</span><span class="sxs-lookup"><span data-stu-id="51b3a-260">Images</span></span>

<span data-ttu-id="51b3a-261">影像是大多數應用程式的共通功能，WPF 提供數種方式來使用影像。</span><span class="sxs-lookup"><span data-stu-id="51b3a-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="51b3a-262">下圖顯示具有包含縮圖影像之清單方塊的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="51b3a-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="51b3a-263">選取縮圖時，會顯示完整大小的影像。</span><span class="sxs-lookup"><span data-stu-id="51b3a-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![縮圖影像與完整影像](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="51b3a-265">如需詳細資訊，請參閱[影像處理概觀](graphics-multimedia/imaging-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="51b3a-266">影片和音訊</span><span class="sxs-lookup"><span data-stu-id="51b3a-266">Video and audio</span></span>

<span data-ttu-id="51b3a-267"><xref:System.Windows.Controls.MediaElement> 控制項可播放視訊和音訊，而且有足夠的彈性可做為自訂媒體播放程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="51b3a-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="51b3a-268">下列 XAML 標記會實行媒體播放機：</span><span class="sxs-lookup"><span data-stu-id="51b3a-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="51b3a-269">下圖中的視窗顯示作用中的 <xref:System.Windows.Controls.MediaElement> 控制項：</span><span class="sxs-lookup"><span data-stu-id="51b3a-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![具有視訊與音訊的 MediaElement 控制項](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="51b3a-271">如需詳細資訊，請參閱[圖形和多媒體](graphics-multimedia/index.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="51b3a-272">文字和印刷樣式</span><span class="sxs-lookup"><span data-stu-id="51b3a-272">Text and typography</span></span>

<span data-ttu-id="51b3a-273">為了達成高品質文字轉譯，WPF 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="51b3a-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="51b3a-274">OpenType 字型支援。</span><span class="sxs-lookup"><span data-stu-id="51b3a-274">OpenType font support.</span></span>

- <span data-ttu-id="51b3a-275">ClearType 增強功能。</span><span class="sxs-lookup"><span data-stu-id="51b3a-275">ClearType enhancements.</span></span>

- <span data-ttu-id="51b3a-276">利用硬體加速的高效能。</span><span class="sxs-lookup"><span data-stu-id="51b3a-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="51b3a-277">將文字與媒體、圖形和動畫進行整合。</span><span class="sxs-lookup"><span data-stu-id="51b3a-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="51b3a-278">國際字型支援和後援機制。</span><span class="sxs-lookup"><span data-stu-id="51b3a-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="51b3a-279">如需文字與圖形的整合示範，下圖顯示文字裝飾的應用：</span><span class="sxs-lookup"><span data-stu-id="51b3a-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![搭配各種文字裝飾的文字](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="51b3a-281">如需詳細資訊，請參閱 [Windows Presentation Foundation 中的印刷樣式](advanced/typography-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="51b3a-282">自訂 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="51b3a-282">Customize WPF apps</span></span>

<span data-ttu-id="51b3a-283">到目前為止，您已經認識用於開發應用程式的核心 WPF 建置組塊。</span><span class="sxs-lookup"><span data-stu-id="51b3a-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="51b3a-284">您可以使用應用程式模型，來裝載及傳遞主要由控制項所組成的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="51b3a-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="51b3a-285">為了簡化使用者介面中的控制項排列方式，並確保不論視窗大小和顯示設定如何變更，都能維持此排列方式，您可以使用 WPF 版面配置系統。</span><span class="sxs-lookup"><span data-stu-id="51b3a-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="51b3a-286">大多數應用程式可讓使用者與資料互動，因此您可以使用資料繫結來減少使用者介面與資料整合的工作。</span><span class="sxs-lookup"><span data-stu-id="51b3a-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="51b3a-287">若要改進應用程式的視覺外觀，您可以使用的 WPF 所提供的各種圖形、動畫和媒體支援。</span><span class="sxs-lookup"><span data-stu-id="51b3a-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="51b3a-288">不過，這些基本功能通常並不足以建立及管理與眾不同且具有豐富視覺效果的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="51b3a-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="51b3a-289">標準 WPF 控制項可能未與應用程式所需的外觀進行整合。</span><span class="sxs-lookup"><span data-stu-id="51b3a-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="51b3a-290">資料可能不會以最有效的方式來顯示。</span><span class="sxs-lookup"><span data-stu-id="51b3a-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="51b3a-291">Windows 佈景主題的預設外觀和風格可能不適合您應用程式的整體使用者介面。</span><span class="sxs-lookup"><span data-stu-id="51b3a-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="51b3a-292">在許多方面，呈現技術除了其他任何類型的擴充性之外，也需要視覺擴充性。</span><span class="sxs-lookup"><span data-stu-id="51b3a-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="51b3a-293">因此，WPF 會提供各種不同的機制來建立唯一的使用者介面，包括控制項、觸發程序、控制項和資料範本、樣式、使用者介面資源，以及佈景主題和面板的豐富內容模型。</span><span class="sxs-lookup"><span data-stu-id="51b3a-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="51b3a-294">內容模型</span><span class="sxs-lookup"><span data-stu-id="51b3a-294">Content model</span></span>

<span data-ttu-id="51b3a-295">大多數 WPF 控制項的主要用途在於顯示內容。</span><span class="sxs-lookup"><span data-stu-id="51b3a-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="51b3a-296">在 WPF 中，可構成控制項內容的項目類型和數目，稱為控制項的 *「內容模型」* (Content Model)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="51b3a-297">有些控制項可能包含單一內容類型的單一項目；例如， <xref:System.Windows.Controls.TextBox> 的內容是指派給 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的字串值。</span><span class="sxs-lookup"><span data-stu-id="51b3a-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="51b3a-298">下列範例會設定 <xref:System.Windows.Controls.TextBox>的內容：</span><span class="sxs-lookup"><span data-stu-id="51b3a-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="51b3a-299">下圖顯示結果：</span><span class="sxs-lookup"><span data-stu-id="51b3a-299">The following figure shows the result:</span></span>

![包含文字的 TextBox 控制項](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="51b3a-301">不過，其他控制項可能包含不同內容類型的多個項目； <xref:System.Windows.Controls.Button>屬性所指定的 <xref:System.Windows.Controls.ContentControl.Content%2A> 內容可包含各種項目，包括版面配置控制項、文字、影像和圖案。</span><span class="sxs-lookup"><span data-stu-id="51b3a-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="51b3a-302">下列範例顯示內容包含 <xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.Border>和 <xref:System.Windows.Controls.MediaElement>的 <xref:System.Windows.Controls.Button>：</span><span class="sxs-lookup"><span data-stu-id="51b3a-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

<span data-ttu-id="51b3a-303">下圖顯示此按鈕的內容：</span><span class="sxs-lookup"><span data-stu-id="51b3a-303">The following figure shows the content of this button:</span></span>

![包含多種類型內容的按鈕](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="51b3a-305">如需各種控制項所支援之內容類型的詳細資訊，請參閱 [WPF 內容模型](controls/wpf-content-model.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="51b3a-306">觸發程序</span><span class="sxs-lookup"><span data-stu-id="51b3a-306">Triggers</span></span>

<span data-ttu-id="51b3a-307">雖然 XAML 標記的主要目的是要實作應用程式的外觀，您也可以使用 XAML 來實作某些方面的應用程式行為。</span><span class="sxs-lookup"><span data-stu-id="51b3a-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="51b3a-308">其中一個範例是使用觸發程序，根據使用者互動來變更應用程式的外觀。</span><span class="sxs-lookup"><span data-stu-id="51b3a-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="51b3a-309">如需詳細資訊，請參閱[樣式和範本](../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="51b3a-310">控制項範本</span><span class="sxs-lookup"><span data-stu-id="51b3a-310">Control templates</span></span>

<span data-ttu-id="51b3a-311">WPF 控制項的預設使用者介面通常是從其他控制項和圖案建構而來。</span><span class="sxs-lookup"><span data-stu-id="51b3a-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="51b3a-312">例如， <xref:System.Windows.Controls.Button> 是由 <xref:Microsoft.Windows.Themes.ButtonChrome> 和 <xref:System.Windows.Controls.ContentPresenter> 控制項所組成。</span><span class="sxs-lookup"><span data-stu-id="51b3a-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="51b3a-313"><xref:Microsoft.Windows.Themes.ButtonChrome> 提供標準按鈕外觀，而 <xref:System.Windows.Controls.ContentPresenter> 則顯示 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性所指定的按鈕內容。</span><span class="sxs-lookup"><span data-stu-id="51b3a-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="51b3a-314">有時候，控制項的預設外觀可能與應用程式的整體外觀不搭。</span><span class="sxs-lookup"><span data-stu-id="51b3a-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="51b3a-315">在這種情況下，您可以使用 <xref:System.Windows.Controls.ControlTemplate> 變更控制項使用者介面的外觀，而不需要變更其內容和行為。</span><span class="sxs-lookup"><span data-stu-id="51b3a-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="51b3a-316">下列範例顯示如何使用 <xref:System.Windows.Controls.ControlTemplate>變更 <xref:System.Windows.Controls.Button> 的外觀：</span><span class="sxs-lookup"><span data-stu-id="51b3a-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="51b3a-317">在這個範例中，預設按鈕的使用者介面已取代成具有深藍色框線的 <xref:System.Windows.Shapes.Ellipse> ，並使用 <xref:System.Windows.Media.RadialGradientBrush>填滿。</span><span class="sxs-lookup"><span data-stu-id="51b3a-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="51b3a-318"><xref:System.Windows.Controls.ContentPresenter> 控制項會顯示 <xref:System.Windows.Controls.Button>的內容："Click Me!"</span><span class="sxs-lookup"><span data-stu-id="51b3a-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="51b3a-319">按下 <xref:System.Windows.Controls.Button> 之後，仍會引發 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件做為 <xref:System.Windows.Controls.Button> 控制項預設行為的一部分。</span><span class="sxs-lookup"><span data-stu-id="51b3a-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="51b3a-320">其結果如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="51b3a-320">The result is shown in the following figure:</span></span>

![橢圓形按鈕和第二個視窗](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="51b3a-322">資料範本</span><span class="sxs-lookup"><span data-stu-id="51b3a-322">Data templates</span></span>

<span data-ttu-id="51b3a-323">控制項範本可讓您指定控制項的外觀，而資料範本則可讓您指定控制項內容的外觀。</span><span class="sxs-lookup"><span data-stu-id="51b3a-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="51b3a-324">資料範本通常可用來增強繫結資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="51b3a-325">下圖顯示系結至 `Task` 物件集合之 <xref:System.Windows.Controls.ListBox> 的預設面板，其中每個工作都有名稱、描述和優先順序：</span><span class="sxs-lookup"><span data-stu-id="51b3a-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![具有預設外觀的清單方塊](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="51b3a-327">預設外觀是您可預期的 <xref:System.Windows.Controls.ListBox>外觀。</span><span class="sxs-lookup"><span data-stu-id="51b3a-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="51b3a-328">不過，每項工作的預設外觀只包含工作名稱。</span><span class="sxs-lookup"><span data-stu-id="51b3a-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="51b3a-329">若要顯示工作名稱、描述和優先權，則必須使用 <xref:System.Windows.Controls.ListBox> 變更 <xref:System.Windows.DataTemplate>控制項之繫結清單項目的預設外觀。</span><span class="sxs-lookup"><span data-stu-id="51b3a-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="51b3a-330">下列 XAML 會定義這類 <xref:System.Windows.DataTemplate>，這會使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性套用至每項工作：</span><span class="sxs-lookup"><span data-stu-id="51b3a-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

<span data-ttu-id="51b3a-331">下圖顯示此程式碼的效果：</span><span class="sxs-lookup"><span data-stu-id="51b3a-331">The following figure shows the effect of this code:</span></span>

![使用資料範本的清單方塊](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="51b3a-333">請注意， <xref:System.Windows.Controls.ListBox> 已保留其行為和整體外觀，只會變更清單方塊所要顯示的內容外觀。</span><span class="sxs-lookup"><span data-stu-id="51b3a-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="51b3a-334">如需詳細資訊，請參閱[資料範本化概觀](data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="51b3a-335">樣式</span><span class="sxs-lookup"><span data-stu-id="51b3a-335">Styles</span></span>

<span data-ttu-id="51b3a-336">樣式可讓開發人員和設計人員標準化其產品的特定外觀。</span><span class="sxs-lookup"><span data-stu-id="51b3a-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="51b3a-337">WPF 提供強式樣式模型，其中的基礎就是 <xref:System.Windows.Style> 項目。</span><span class="sxs-lookup"><span data-stu-id="51b3a-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="51b3a-338">下列範例會建立一個樣式，以將視窗上每個 <xref:System.Windows.Controls.Button> 的背景色彩設定為 `Orange`：</span><span class="sxs-lookup"><span data-stu-id="51b3a-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

<span data-ttu-id="51b3a-339">由於這種樣式是以所有 <xref:System.Windows.Controls.Button> 控制項為目標，系統會將該樣式自動套用至視窗中的所有按鈕，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="51b3a-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![兩個橙色按鈕](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="51b3a-341">如需詳細資訊，請參閱[樣式和範本](../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="51b3a-342">資源</span><span class="sxs-lookup"><span data-stu-id="51b3a-342">Resources</span></span>

<span data-ttu-id="51b3a-343">應用程式中的控制項應該共用相同的外觀，可包含從字型和背景色彩，到控制項範本、資料範本和樣式的任何項目。</span><span class="sxs-lookup"><span data-stu-id="51b3a-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="51b3a-344">您可以使用 WPF 對使用者介面資源的支援，將這些資源封裝到單一位置以重複使用。</span><span class="sxs-lookup"><span data-stu-id="51b3a-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="51b3a-345">下列範例會定義 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.Label>共用的一般背景色彩：</span><span class="sxs-lookup"><span data-stu-id="51b3a-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

<span data-ttu-id="51b3a-346">這個範例使用 `Window.Resources` 屬性項目來實作背景色彩資源。</span><span class="sxs-lookup"><span data-stu-id="51b3a-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="51b3a-347">這項資源可供 <xref:System.Windows.Window>的所有子系使用。</span><span class="sxs-lookup"><span data-stu-id="51b3a-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="51b3a-348">以下依其解析順序列出各種資源範圍，包括：</span><span class="sxs-lookup"><span data-stu-id="51b3a-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="51b3a-349">個別控制項 (使用繼承的 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="51b3a-350"><xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Page> (也使用繼承的 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="51b3a-351"><xref:System.Windows.Application> (使用 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="51b3a-352">上述各種範圍可讓您彈性地定義及共用資源。</span><span class="sxs-lookup"><span data-stu-id="51b3a-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="51b3a-353">除了直接建立資源與特定範圍的關聯之外，您還可以使用個別 <xref:System.Windows.ResourceDictionary> 封裝一或多項資源，以做為應用程式的其他組件來參考。</span><span class="sxs-lookup"><span data-stu-id="51b3a-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="51b3a-354">例如，下列範例會定義資源字典中的預設背景色彩：</span><span class="sxs-lookup"><span data-stu-id="51b3a-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="51b3a-355">下列範例會參考先前範例中定義的資源字典，使其可在應用程式之間共用：</span><span class="sxs-lookup"><span data-stu-id="51b3a-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

<span data-ttu-id="51b3a-356">資源與資源字典是 WPF 支援佈景主題和面板的基礎。</span><span class="sxs-lookup"><span data-stu-id="51b3a-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="51b3a-357">如需詳細資訊，請參閱[資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="51b3a-358">自訂控制項</span><span class="sxs-lookup"><span data-stu-id="51b3a-358">Custom controls</span></span>

<span data-ttu-id="51b3a-359">雖然 WPF 提供許多自訂支援，但是您可能還是會遇到現有 WPF 控制項不符合應用程式或其使用者需求的情況。</span><span class="sxs-lookup"><span data-stu-id="51b3a-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="51b3a-360">可能發生的原因有：</span><span class="sxs-lookup"><span data-stu-id="51b3a-360">This can occur when:</span></span>

- <span data-ttu-id="51b3a-361">您無法藉由自訂現有 WPF 實作的外觀和風格，來建立所需的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="51b3a-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="51b3a-362">現有 WPF 實作不支援 (或無法輕易支援) 您需要的行為。</span><span class="sxs-lookup"><span data-stu-id="51b3a-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="51b3a-363">不過在這種情況下，您可以利用三種 WPF 模型之一來建立新的控制項。</span><span class="sxs-lookup"><span data-stu-id="51b3a-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="51b3a-364">每個模型各有適用的特定情況，並要求您的自訂控制項衍生自特定 WPF 基底類別。</span><span class="sxs-lookup"><span data-stu-id="51b3a-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="51b3a-365">以下列出這三種模型：</span><span class="sxs-lookup"><span data-stu-id="51b3a-365">The three models are listed here:</span></span>

- <span data-ttu-id="51b3a-366">**使用者控制項模型**：</span><span class="sxs-lookup"><span data-stu-id="51b3a-366">**User Control Model**.</span></span> <span data-ttu-id="51b3a-367">自訂控制項衍生自 <xref:System.Windows.Controls.UserControl> ，並由一或多個其他控制項所組成。</span><span class="sxs-lookup"><span data-stu-id="51b3a-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="51b3a-368">**控制項模型**：</span><span class="sxs-lookup"><span data-stu-id="51b3a-368">**Control Model**.</span></span> <span data-ttu-id="51b3a-369">自訂控制項衍生自 <xref:System.Windows.Controls.Control> ，並使用範本來建置實作以區隔其行為和外觀，與大多數 WPF 控制項非常類似。</span><span class="sxs-lookup"><span data-stu-id="51b3a-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="51b3a-370">衍生自 <xref:System.Windows.Controls.Control> 比使用者控制項更能夠讓您自由地建立自訂使用者介面，但可能需要投入更多時間。</span><span class="sxs-lookup"><span data-stu-id="51b3a-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="51b3a-371">**架構項目模型**：</span><span class="sxs-lookup"><span data-stu-id="51b3a-371">**Framework Element Model**.</span></span> <span data-ttu-id="51b3a-372">如果其外觀是由自訂轉譯邏輯 (而不是範本) 所定義，自訂控制項衍生自 <xref:System.Windows.FrameworkElement> 。</span><span class="sxs-lookup"><span data-stu-id="51b3a-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="51b3a-373">下列範例顯示從 <xref:System.Windows.Controls.UserControl>衍生的自訂數值上/下控制項：</span><span class="sxs-lookup"><span data-stu-id="51b3a-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="51b3a-374">下列範例說明將使用者控制項併入 <xref:System.Windows.Window>所需的 XAML：</span><span class="sxs-lookup"><span data-stu-id="51b3a-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="51b3a-375">下圖顯示 <xref:System.Windows.Window>中裝載的 `NumericUpDown` 控制項：</span><span class="sxs-lookup"><span data-stu-id="51b3a-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![自訂 UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="51b3a-377">如需自訂控制項的詳細資訊，請參閱[控制項撰寫概觀](controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="51b3a-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="51b3a-378">WPF 最佳做法</span><span class="sxs-lookup"><span data-stu-id="51b3a-378">WPF best practices</span></span>

<span data-ttu-id="51b3a-379">如同任何開發平台，您可以透過各種方式來使用 WPF，以取得想要的結果。</span><span class="sxs-lookup"><span data-stu-id="51b3a-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="51b3a-380">為了確保您的 WPF 應用程式提供所需的使用者體驗，並符合一般大眾的需求，已針對協助工具、全球化和當地語系化，以及效能提供了建議的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="51b3a-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="51b3a-381">如需詳細資訊，請參閱＜＞。</span><span class="sxs-lookup"><span data-stu-id="51b3a-381">For more information, see:</span></span>

- [<span data-ttu-id="51b3a-382">協助工具選項</span><span class="sxs-lookup"><span data-stu-id="51b3a-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="51b3a-383">WPF 全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="51b3a-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="51b3a-384">WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="51b3a-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="51b3a-385">WPF 安全性</span><span class="sxs-lookup"><span data-stu-id="51b3a-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="51b3a-386">後續步驟</span><span class="sxs-lookup"><span data-stu-id="51b3a-386">Next steps</span></span>

<span data-ttu-id="51b3a-387">我們已經討論過 WPF 的主要功能。</span><span class="sxs-lookup"><span data-stu-id="51b3a-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="51b3a-388">現在是時候建置您的第一個 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="51b3a-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51b3a-389">逐步解說：我的第一個 WPF 桌面應用程式</span><span class="sxs-lookup"><span data-stu-id="51b3a-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="51b3a-390">請參閱</span><span class="sxs-lookup"><span data-stu-id="51b3a-390">See also</span></span>

- [<span data-ttu-id="51b3a-391">開始使用 WPF</span><span class="sxs-lookup"><span data-stu-id="51b3a-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="51b3a-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="51b3a-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="51b3a-393">WPF 社群資源</span><span class="sxs-lookup"><span data-stu-id="51b3a-393">WPF community resources</span></span>](getting-started/community-feedback.md)
