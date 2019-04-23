---
title: 逐步解說：在使用者控制項上啟用拖放功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: a628665ccfa0a423667344b1fe81f132d6691b12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321675"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="d101f-102">逐步解說：在使用者控制項上啟用拖放功能</span><span class="sxs-lookup"><span data-stu-id="d101f-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="d101f-103">本逐步解說示範如何建立自訂使用者控制項以參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的拖放資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="d101f-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="d101f-104">在本逐步解說中，您將建立的自訂 WPF<xref:System.Windows.Controls.UserControl>代表圓形圖形。</span><span class="sxs-lookup"><span data-stu-id="d101f-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="d101f-105">您將在控制項上實作功能，以啟用透過拖放的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="d101f-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="d101f-106">例如，如果您從某個 Circle 控制項拖曳至另一個 Circle 控制項，則會將填滿色彩資料從來源 Circle 複製至目標。</span><span class="sxs-lookup"><span data-stu-id="d101f-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="d101f-107">如果您從 Circle 控制項拖曳<xref:System.Windows.Controls.TextBox>，填滿色彩的字串表示複製到<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d101f-108">您也會建立一個小型的應用程式，其中包含兩個面板控制項和<xref:System.Windows.Controls.TextBox>來測試拖放功能。</span><span class="sxs-lookup"><span data-stu-id="d101f-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="d101f-109">您將撰寫讓面板處理所置放 Circle 資料的程式碼，以讓您將 Circle 從某個面版的子系集合移動或複製至另一個面板。</span><span class="sxs-lookup"><span data-stu-id="d101f-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="d101f-110">這個逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-110">This walkthrough illustrates the following tasks:</span></span>

-   <span data-ttu-id="d101f-111">建立自訂使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-111">Create a custom user control.</span></span>

-   <span data-ttu-id="d101f-112">可讓使用者控制項成為拖曳來源。</span><span class="sxs-lookup"><span data-stu-id="d101f-112">Enable the user control to be a drag source.</span></span>

-   <span data-ttu-id="d101f-113">讓使用者控制項成為置放目標。</span><span class="sxs-lookup"><span data-stu-id="d101f-113">Enable the user control to be a drop target.</span></span>

-   <span data-ttu-id="d101f-114">啟用面板，以接收從使用者控制項置放的資料。</span><span class="sxs-lookup"><span data-stu-id="d101f-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d101f-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="d101f-115">Prerequisites</span></span>

<span data-ttu-id="d101f-116">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d101f-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="d101f-117">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="d101f-117">Create the Application Project</span></span>
 <span data-ttu-id="d101f-118">在本節中，您將建立應用程式基礎結構，其中包含具有兩個面板的主頁面和<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="d101f-119">在 Visual Basic 或 Visual C# 中，建立名為 `DragDropExample` 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d101f-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="d101f-120">如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d101f-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="d101f-121">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="d101f-121">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="d101f-122">加入下列標記的開頭和結尾之間<xref:System.Windows.Controls.Grid>標記。</span><span class="sxs-lookup"><span data-stu-id="d101f-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="d101f-123">此標記會建立測試應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="d101f-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="d101f-124">將新的使用者控制項加入至專案</span><span class="sxs-lookup"><span data-stu-id="d101f-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="d101f-125">在本節中，您會將新的使用者控制項新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d101f-125">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="d101f-126">在 [專案] 功能表上，選取 [新增使用者控制項]。</span><span class="sxs-lookup"><span data-stu-id="d101f-126">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="d101f-127">在 **加入新項目**對話方塊方塊中，將名稱變更為`Circle.xaml`，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d101f-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="d101f-128">Circle.xaml 和其程式碼後置會新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d101f-128">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="d101f-129">開啟 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="d101f-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="d101f-130">此檔案將包含使用者控制項的使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="d101f-130">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="d101f-131">將下列標記新增至根<xref:System.Windows.Controls.Grid>建立將藍色圓形作為其 UI 的簡單使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="d101f-132">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="d101f-133">在 C# 中，於預設建構函式後面新增下列程式碼，以建立複製建構函式。</span><span class="sxs-lookup"><span data-stu-id="d101f-133">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="d101f-134">在 Visual Basic 中，新增下列程式碼，以建立預設建構函式和複製建構函式。</span><span class="sxs-lookup"><span data-stu-id="d101f-134">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>

     <span data-ttu-id="d101f-135">若要允許複製使用者控制項，您可以在程式碼後置檔案中新增複製建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="d101f-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="d101f-136">在簡化 Circle 使用者控制項中，您只會複製使用者控制項的填滿和大小。</span><span class="sxs-lookup"><span data-stu-id="d101f-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="d101f-137">將使用者控制項新增至主視窗</span><span class="sxs-lookup"><span data-stu-id="d101f-137">Add the user control to the main window</span></span>

1. <span data-ttu-id="d101f-138">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="d101f-138">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="d101f-139">將下列 XAML 加入至開啟<xref:System.Windows.Window>標記，以建立目前的應用程式的 XML 命名空間參考。</span><span class="sxs-lookup"><span data-stu-id="d101f-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="d101f-140">在第一個<xref:System.Windows.Controls.StackPanel>，加入下列 XAML 來建立 Circle 使用者控制項的兩個執行個體中第一個面板。</span><span class="sxs-lookup"><span data-stu-id="d101f-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="d101f-141">面板的完整 XAML 如下。</span><span class="sxs-lookup"><span data-stu-id="d101f-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="d101f-142">在 使用者控制項中實作拖曳來源事件</span><span class="sxs-lookup"><span data-stu-id="d101f-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="d101f-143">在本節中，您將會覆寫<xref:System.Windows.UIElement.OnMouseMove%2A>方法並起始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="d101f-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="d101f-144">如果開始拖曳 （按下滑鼠按鈕並在移動滑鼠），您將封裝的資料要傳送至<xref:System.Windows.DataObject>。</span><span class="sxs-lookup"><span data-stu-id="d101f-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="d101f-145">在此情況下，Circle 控制項將會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。</span><span class="sxs-lookup"><span data-stu-id="d101f-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="d101f-146">啟始拖放作業</span><span class="sxs-lookup"><span data-stu-id="d101f-146">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="d101f-147">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d101f-148">新增下列<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫，以提供類別處理<xref:System.Windows.UIElement.MouseMove>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="d101f-149">這<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-150">檢查是否在滑鼠移動時按下滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="d101f-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    -   <span data-ttu-id="d101f-151">將 Circle 資料封裝成<xref:System.Windows.DataObject>。</span><span class="sxs-lookup"><span data-stu-id="d101f-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="d101f-152">在此情況下，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。</span><span class="sxs-lookup"><span data-stu-id="d101f-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    -   <span data-ttu-id="d101f-153">呼叫靜態<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>方法來啟始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="d101f-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="d101f-154">傳遞下列三個參數，以<xref:System.Windows.DragDrop.DoDragDrop%2A>方法：</span><span class="sxs-lookup"><span data-stu-id="d101f-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        -   <span data-ttu-id="d101f-155">`dragSource` – 此控制項的參考。</span><span class="sxs-lookup"><span data-stu-id="d101f-155">`dragSource` – A reference to this control.</span></span>

        -   <span data-ttu-id="d101f-156">`data` –<xref:System.Windows.DataObject>在先前的程式碼中建立。</span><span class="sxs-lookup"><span data-stu-id="d101f-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        -   <span data-ttu-id="d101f-157">`allowedEffects` – 允許的拖放作業，也就是<xref:System.Windows.DragDropEffects.Copy>或<xref:System.Windows.DragDropEffects.Move>。</span><span class="sxs-lookup"><span data-stu-id="d101f-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="d101f-158">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d101f-158">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d101f-159">按一下其中一個 Circle 控制項，並將它拖曳面板，圓形，透過和<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d101f-160">當拖曳<xref:System.Windows.Controls.TextBox>，游標變更以表示移動。</span><span class="sxs-lookup"><span data-stu-id="d101f-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="d101f-161">同時將 Circle 拖曳<xref:System.Windows.Controls.TextBox>，按下**Ctrl**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d101f-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="d101f-162">請注意，游標變更以指出正在進行複製。</span><span class="sxs-lookup"><span data-stu-id="d101f-162">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="d101f-163">將拖放至 Circle <xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d101f-164">Circle 之填滿色彩的字串表示附加至<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="d101f-165">![Circle 之填滿色彩的字串表示](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="d101f-165">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="d101f-166">根據預設，游標會在拖放作業期間變更，表示置放資料的效果。</span><span class="sxs-lookup"><span data-stu-id="d101f-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="d101f-167">您可以自訂處理所提供給使用者的意見反應<xref:System.Windows.UIElement.GiveFeedback>事件，並設定不同的資料指標。</span><span class="sxs-lookup"><span data-stu-id="d101f-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="d101f-168">提供給使用者的意見反應</span><span class="sxs-lookup"><span data-stu-id="d101f-168">Give feedback to the user</span></span>

1. <span data-ttu-id="d101f-169">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d101f-170">新增下列<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫，以提供類別處理<xref:System.Windows.UIElement.GiveFeedback>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="d101f-171">這<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-172">會檢查<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>置放目標中所設定的值<xref:System.Windows.UIElement.DragOver>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d101f-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    -   <span data-ttu-id="d101f-173">設定自訂游標根據<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>值。</span><span class="sxs-lookup"><span data-stu-id="d101f-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="d101f-174">游標用於將資料置放效果的視覺化回饋提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="d101f-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="d101f-175">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d101f-175">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d101f-176">拖曳 Circle 的其中一個控制面板，圓形，而<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d101f-177">請注意，游標現在是您在中指定的自訂游標<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫。</span><span class="sxs-lookup"><span data-stu-id="d101f-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="d101f-178">![以自訂游標執行拖放作業](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="d101f-178">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="d101f-179">選取的文字`green`從<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="d101f-180">將 `green` 文字拖曳至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="d101f-181">請注意，會顯示預設游標，表示拖放作業的效果。</span><span class="sxs-lookup"><span data-stu-id="d101f-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="d101f-182">意見反應游標一律是由拖曳來源所設定。</span><span class="sxs-lookup"><span data-stu-id="d101f-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="d101f-183">在 使用者控制項中實作置放目標事件</span><span class="sxs-lookup"><span data-stu-id="d101f-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="d101f-184">在本節中，您將指定使用者控制項是置放目標、覆寫讓使用者控制項成為置放目標的方法，以及處理置放在其上的資料。</span><span class="sxs-lookup"><span data-stu-id="d101f-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="d101f-185">讓使用者控制項成為置放目標</span><span class="sxs-lookup"><span data-stu-id="d101f-185">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="d101f-186">開啟 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="d101f-186">Open Circle.xaml.</span></span>

2. <span data-ttu-id="d101f-187">在開頭<xref:System.Windows.Controls.UserControl>標記中加入<xref:System.Windows.UIElement.AllowDrop%2A>屬性並將它設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="d101f-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="d101f-188"><xref:System.Windows.UIElement.OnDrop%2A>方法時，會呼叫<xref:System.Windows.UIElement.AllowDrop%2A>屬性設定為`true`和從拖曳來源的資料放在 Circle 使用者控制項上。</span><span class="sxs-lookup"><span data-stu-id="d101f-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="d101f-189">在此方法中，您將處理置放的資料，並將資料套用至 Circle。</span><span class="sxs-lookup"><span data-stu-id="d101f-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="d101f-190">處理置放的資料</span><span class="sxs-lookup"><span data-stu-id="d101f-190">To process the dropped data</span></span>

1. <span data-ttu-id="d101f-191">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d101f-192">新增下列<xref:System.Windows.UIElement.OnDrop%2A>覆寫，以提供類別處理<xref:System.Windows.UIElement.Drop>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="d101f-193">這<xref:System.Windows.UIElement.OnDrop%2A>覆寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-194">使用<xref:System.Windows.DataObject.GetDataPresent%2A>方法來檢查所拖曳的資料是否包含字串物件。</span><span class="sxs-lookup"><span data-stu-id="d101f-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    -   <span data-ttu-id="d101f-195">使用<xref:System.Windows.DataObject.GetData%2A>方法來擷取字串資料，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="d101f-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    -   <span data-ttu-id="d101f-196">會使用<xref:System.Windows.Media.BrushConverter>嘗試將字串轉換為<xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="d101f-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    -   <span data-ttu-id="d101f-197">如果轉換成功，會套用到筆刷<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Ellipse>提供 Circle 控制項的 UI。</span><span class="sxs-lookup"><span data-stu-id="d101f-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    -   <span data-ttu-id="d101f-198">標記<xref:System.Windows.UIElement.Drop>為已處理的事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="d101f-199">您應該將置放事件標示為已處理，讓收到此事件的其他項目知道 Circle 使用者控制項已處理過它。</span><span class="sxs-lookup"><span data-stu-id="d101f-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="d101f-200">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d101f-200">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d101f-201">選取的文字`green`在<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="d101f-202">將文字拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="d101f-203">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="d101f-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="d101f-204">![將字串轉換成筆刷](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="d101f-204">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="d101f-205">輸入文字`green`在<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="d101f-206">選取的文字`gre`在<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="d101f-207">將它拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="d101f-208">請注意，游標變更以指出允許置放，但 Circle 的色彩不會變更，因為 `gre` 不是有效的色彩。</span><span class="sxs-lookup"><span data-stu-id="d101f-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="d101f-209">從綠色 Circle 控制項拖放至藍色 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="d101f-210">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="d101f-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="d101f-211">請注意，顯示的游標取決於是否<xref:System.Windows.Controls.TextBox>或 Circle 是拖曳來源。</span><span class="sxs-lookup"><span data-stu-id="d101f-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="d101f-212">設定<xref:System.Windows.UIElement.AllowDrop%2A>屬性設`true`並處理置放的資料就只需要啟用項目成為置放目標。</span><span class="sxs-lookup"><span data-stu-id="d101f-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="d101f-213">不過，若要提供較佳使用者體驗，您也應該處理<xref:System.Windows.UIElement.DragEnter>， <xref:System.Windows.UIElement.DragLeave>，和<xref:System.Windows.UIElement.DragOver>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="d101f-214">在這些事件中，您可以在置放資料之前執行檢查，並將其他意見反應提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="d101f-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="d101f-215">將資料拖曳至 Circle 使用者控制項上方時，控制項應該通知拖曳來源是否可以處理所拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="d101f-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="d101f-216">如果控制項不知道如何處理資料，則應該拒絕置放。</span><span class="sxs-lookup"><span data-stu-id="d101f-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="d101f-217">若要這樣做，您會處理<xref:System.Windows.UIElement.DragOver>事件，以及組<xref:System.Windows.DragEventArgs.Effects%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d101f-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="d101f-218">確認允許資料置放</span><span class="sxs-lookup"><span data-stu-id="d101f-218">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="d101f-219">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d101f-220">新增下列<xref:System.Windows.UIElement.OnDragOver%2A>覆寫，以提供類別處理<xref:System.Windows.UIElement.DragOver>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="d101f-221">這<xref:System.Windows.UIElement.OnDragOver%2A>覆寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-222">將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.None>。</span><span class="sxs-lookup"><span data-stu-id="d101f-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    -   <span data-ttu-id="d101f-223">執行中執行的相同檢查<xref:System.Windows.UIElement.OnDrop%2A>方法，以判斷 Circle 使用者控制項是否可以處理所拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="d101f-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    -   <span data-ttu-id="d101f-224">如果使用者控制項可以處理資料，設定<xref:System.Windows.DragEventArgs.Effects%2A>屬性，以<xref:System.Windows.DragDropEffects.Copy>或<xref:System.Windows.DragDropEffects.Move>。</span><span class="sxs-lookup"><span data-stu-id="d101f-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="d101f-225">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d101f-225">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d101f-226">選取的文字`gre`在<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="d101f-227">將文字拖曳至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="d101f-228">請注意，游標現在會變更以指出不允許置放，因為 `gre` 不是有效的色彩。</span><span class="sxs-lookup"><span data-stu-id="d101f-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="d101f-229">您可以套用置放作業的預覽，進一步增強使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="d101f-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="d101f-230">針對 Circle 使用者控制項，您將會覆寫<xref:System.Windows.UIElement.OnDragEnter%2A>和<xref:System.Windows.UIElement.OnDragLeave%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d101f-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="d101f-231">將資料拖曳到控制項，目前的背景時<xref:System.Windows.Shapes.Shape.Fill%2A>儲存在預留位置變數中。</span><span class="sxs-lookup"><span data-stu-id="d101f-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="d101f-232">然後轉換成筆刷並套用至字串<xref:System.Windows.Shapes.Ellipse>提供 Circle UI。</span><span class="sxs-lookup"><span data-stu-id="d101f-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="d101f-233">如果將資料拖曳出 Circle 但未置放原始<xref:System.Windows.Shapes.Shape.Fill%2A>值重新套用至 Circle。</span><span class="sxs-lookup"><span data-stu-id="d101f-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="d101f-234">預覽拖放作業的效果</span><span class="sxs-lookup"><span data-stu-id="d101f-234">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="d101f-235">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d101f-236">在 Circle 類別中，宣告私用<xref:System.Windows.Media.Brush>名`_previousFill`並將它初始化為`null`。</span><span class="sxs-lookup"><span data-stu-id="d101f-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="d101f-237">新增下列<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫，以提供類別處理<xref:System.Windows.UIElement.DragEnter>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="d101f-238">這<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-239">節省<xref:System.Windows.Shapes.Shape.Fill%2A>的屬性<xref:System.Windows.Shapes.Ellipse>在`_previousFill`變數。</span><span class="sxs-lookup"><span data-stu-id="d101f-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    -   <span data-ttu-id="d101f-240">執行中執行的相同檢查<xref:System.Windows.UIElement.OnDrop%2A>方法，以判斷資料是否可轉換成<xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="d101f-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    -   <span data-ttu-id="d101f-241">如果資料轉換成有效<xref:System.Windows.Media.Brush>，它套用至<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="d101f-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="d101f-242">新增下列<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫，以提供類別處理<xref:System.Windows.UIElement.DragLeave>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="d101f-243">這<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-244">適用於<xref:System.Windows.Media.Brush>存入`_previousFill`變數加入<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Ellipse>提供 Circle 使用者控制項的 UI。</span><span class="sxs-lookup"><span data-stu-id="d101f-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="d101f-245">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d101f-245">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="d101f-246">選取的文字`green`在<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="d101f-247">將文字拖曳至 Circle 控制項上方，但不置放文字。</span><span class="sxs-lookup"><span data-stu-id="d101f-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="d101f-248">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="d101f-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="d101f-249">![預覽拖放作業的效果](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="d101f-249">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="d101f-250">從 Circle 控制項拖離文字。</span><span class="sxs-lookup"><span data-stu-id="d101f-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="d101f-251">Circle 會從綠色變回藍色。</span><span class="sxs-lookup"><span data-stu-id="d101f-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="d101f-252">讓面板接收置放的資料</span><span class="sxs-lookup"><span data-stu-id="d101f-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="d101f-253">在本節中，您會啟用一些面板，以裝載 Circle 使用者控制項，做為拖曳 Circle 資料的置放目標。</span><span class="sxs-lookup"><span data-stu-id="d101f-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="d101f-254">您將實作程式碼，可讓您將 Circle 從一個面板移至另一個，或將一份 Circle 控制項按住**Ctrl**鍵同時拖曳和卸除一個圓形。</span><span class="sxs-lookup"><span data-stu-id="d101f-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="d101f-255">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="d101f-255">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="d101f-256">下列 XAML，在每個所示<xref:System.Windows.Controls.StackPanel>控制項，加入處理常式<xref:System.Windows.UIElement.DragOver>和<xref:System.Windows.UIElement.Drop>事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="d101f-257">名稱<xref:System.Windows.UIElement.DragOver>事件處理常式`panel_DragOver`，並命名<xref:System.Windows.UIElement.Drop>事件處理常式， `panel_Drop`。</span><span class="sxs-lookup"><span data-stu-id="d101f-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="d101f-258">開啟 MainWindows.xaml.cs 或 MainWindow.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d101f-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="d101f-259">新增下列程式碼<xref:System.Windows.UIElement.DragOver>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d101f-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="d101f-260">這<xref:System.Windows.UIElement.DragOver>事件處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-261">檢查所拖曳的資料包含已封裝在 「 物件 」 資料<xref:System.Windows.DataObject>Circle 使用者控制項所傳入的呼叫和<xref:System.Windows.DragDrop.DoDragDrop%2A>。</span><span class="sxs-lookup"><span data-stu-id="d101f-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    -   <span data-ttu-id="d101f-262">「 物件 」 資料是否存在，檢查是否**Ctrl**按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="d101f-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    -   <span data-ttu-id="d101f-263">如果**Ctrl**按鍵，集合<xref:System.Windows.DragEventArgs.Effects%2A>屬性設<xref:System.Windows.DragDropEffects.Copy>。</span><span class="sxs-lookup"><span data-stu-id="d101f-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="d101f-264">否則，請設定<xref:System.Windows.DragEventArgs.Effects%2A>屬性設<xref:System.Windows.DragDropEffects.Move>。</span><span class="sxs-lookup"><span data-stu-id="d101f-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="d101f-265">新增下列程式碼<xref:System.Windows.UIElement.Drop>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d101f-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="d101f-266">這<xref:System.Windows.UIElement.Drop>事件處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d101f-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    -   <span data-ttu-id="d101f-267">檢查是否<xref:System.Windows.UIElement.Drop>已處理事件。</span><span class="sxs-lookup"><span data-stu-id="d101f-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="d101f-268">比方說，如果一個圓圈卸除另一個圓圈，其控制代碼<xref:System.Windows.UIElement.Drop>事件，您不想包含也處理它 Circle 的面板。</span><span class="sxs-lookup"><span data-stu-id="d101f-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    -   <span data-ttu-id="d101f-269">如果<xref:System.Windows.UIElement.Drop>未處理事件，檢查是否**Ctrl**按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="d101f-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    -   <span data-ttu-id="d101f-270">如果**Ctrl**按下按鍵時<xref:System.Windows.UIElement.Drop>發生時，發出的圓形複本控制，並將它加入<xref:System.Windows.Controls.Panel.Children%2A>集合<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="d101f-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    -   <span data-ttu-id="d101f-271">如果**Ctrl**未按下按鍵時，將從圓形<xref:System.Windows.Controls.Panel.Children%2A>集合，以其父面板的<xref:System.Windows.Controls.Panel.Children%2A>面板，它已卸除的集合。</span><span class="sxs-lookup"><span data-stu-id="d101f-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    -   <span data-ttu-id="d101f-272">設定組<xref:System.Windows.DragEventArgs.Effects%2A>屬性，以通知<xref:System.Windows.DragDrop.DoDragDrop%2A>方法是否執行移動或複製作業。</span><span class="sxs-lookup"><span data-stu-id="d101f-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="d101f-273">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d101f-273">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="d101f-274">選取的文字`green`從<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d101f-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="d101f-275">將文字拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d101f-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="d101f-276">將 Circle 控制項從從左面板拖放至右面板。</span><span class="sxs-lookup"><span data-stu-id="d101f-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="d101f-277">圓形移除了<xref:System.Windows.Controls.Panel.Children%2A>左方面板中的集合，並加入右面板的 Children 集合。</span><span class="sxs-lookup"><span data-stu-id="d101f-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="d101f-278">將 Circle 控制項從另一個面板為面板拖放時按下**Ctrl**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d101f-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="d101f-279">會複製 Circle，並將複本新增至<xref:System.Windows.Controls.Panel.Children%2A>接收面板的集合。</span><span class="sxs-lookup"><span data-stu-id="d101f-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="d101f-280">![拖曳 Circle 時按住 CTRL 鍵](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="d101f-280">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="d101f-281">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d101f-281">See also</span></span>

- [<span data-ttu-id="d101f-282">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="d101f-282">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)