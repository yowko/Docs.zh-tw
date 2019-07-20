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
ms.openlocfilehash: 80fd55be9230729cb8336be91c1d8fb4f7f3f080
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364259"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="b95fb-102">逐步解說：在使用者控制項上啟用拖放功能</span><span class="sxs-lookup"><span data-stu-id="b95fb-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="b95fb-103">本逐步解說示範如何建立自訂使用者控制項以參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的拖放資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="b95fb-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="b95fb-104">在此逐步解說中, 您將建立代表<xref:System.Windows.Controls.UserControl>圓形圖形的自訂 WPF。</span><span class="sxs-lookup"><span data-stu-id="b95fb-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="b95fb-105">您將在控制項上實作功能，以啟用透過拖放的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="b95fb-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="b95fb-106">例如，如果您從某個 Circle 控制項拖曳至另一個 Circle 控制項，則會將填滿色彩資料從來源 Circle 複製至目標。</span><span class="sxs-lookup"><span data-stu-id="b95fb-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="b95fb-107">如果您從 Circle 控制項拖曳至<xref:System.Windows.Controls.TextBox>, 則填滿色彩的字串表示會複製<xref:System.Windows.Controls.TextBox>到。</span><span class="sxs-lookup"><span data-stu-id="b95fb-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b95fb-108">您也會建立一個包含兩個面板控制項的小型應用程式<xref:System.Windows.Controls.TextBox> , 以及一個測試拖放功能的。</span><span class="sxs-lookup"><span data-stu-id="b95fb-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="b95fb-109">您將撰寫讓面板處理所置放 Circle 資料的程式碼，以讓您將 Circle 從某個面版的子系集合移動或複製至另一個面板。</span><span class="sxs-lookup"><span data-stu-id="b95fb-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="b95fb-110">這個逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="b95fb-110">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="b95fb-111">建立自訂使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-111">Create a custom user control.</span></span>

- <span data-ttu-id="b95fb-112">可讓使用者控制項成為拖曳來源。</span><span class="sxs-lookup"><span data-stu-id="b95fb-112">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="b95fb-113">讓使用者控制項成為置放目標。</span><span class="sxs-lookup"><span data-stu-id="b95fb-113">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="b95fb-114">啟用面板，以接收從使用者控制項置放的資料。</span><span class="sxs-lookup"><span data-stu-id="b95fb-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b95fb-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="b95fb-115">Prerequisites</span></span>

<span data-ttu-id="b95fb-116">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b95fb-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="b95fb-117">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="b95fb-117">Create the Application Project</span></span>
 <span data-ttu-id="b95fb-118">在本節中, 您將建立應用程式基礎結構, 其中包含具有兩個面板和的<xref:System.Windows.Controls.TextBox>主頁面。</span><span class="sxs-lookup"><span data-stu-id="b95fb-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="b95fb-119">在 Visual Basic 或 Visual C# 中，建立名為 `DragDropExample` 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b95fb-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="b95fb-120">如需詳細資訊，請參閱[逐步解說：我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="b95fb-121">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="b95fb-121">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="b95fb-122">在開頭和結尾<xref:System.Windows.Controls.Grid>標記之間新增下列標記。</span><span class="sxs-lookup"><span data-stu-id="b95fb-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="b95fb-123">此標記會建立測試應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b95fb-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="b95fb-124">將新的使用者控制項加入至專案</span><span class="sxs-lookup"><span data-stu-id="b95fb-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="b95fb-125">在本節中，您會將新的使用者控制項新增至專案。</span><span class="sxs-lookup"><span data-stu-id="b95fb-125">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="b95fb-126">在 [專案] 功能表上，選取 [新增使用者控制項]  。</span><span class="sxs-lookup"><span data-stu-id="b95fb-126">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="b95fb-127">在 [**加入新專案**] 對話方塊中, 將名稱變更`Circle.xaml`為, 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b95fb-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="b95fb-128">Circle.xaml 和其程式碼後置會新增至專案。</span><span class="sxs-lookup"><span data-stu-id="b95fb-128">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="b95fb-129">開啟 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="b95fb-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="b95fb-130">此檔案將包含使用者控制項的使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="b95fb-130">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="b95fb-131">將下列標記新增至根<xref:System.Windows.Controls.Grid> , 以建立具有藍色圓圈作為其 UI 的簡單使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="b95fb-132">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="b95fb-133">在C#中, 于無參數的函式後面加入下列程式碼, 以建立複製的函式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-133">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="b95fb-134">在 Visual Basic 中, 新增下列程式碼, 以建立無參數的函式和複製的函式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-134">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="b95fb-135">若要允許複製使用者控制項，您可以在程式碼後置檔案中新增複製建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="b95fb-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="b95fb-136">在簡化 Circle 使用者控制項中，您只會複製使用者控制項的填滿和大小。</span><span class="sxs-lookup"><span data-stu-id="b95fb-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="b95fb-137">將使用者控制項加入至主視窗</span><span class="sxs-lookup"><span data-stu-id="b95fb-137">Add the user control to the main window</span></span>

1. <span data-ttu-id="b95fb-138">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="b95fb-138">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="b95fb-139">將下列 XAML 加入至開頭<xref:System.Windows.Window>標記, 以建立目前應用程式的 XML 命名空間參考。</span><span class="sxs-lookup"><span data-stu-id="b95fb-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="b95fb-140">在第一個<xref:System.Windows.Controls.StackPanel>中, 新增下列 XAML, 在第一個面板中建立 Circle 使用者控制項的兩個實例。</span><span class="sxs-lookup"><span data-stu-id="b95fb-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="b95fb-141">面板的完整 XAML 如下。</span><span class="sxs-lookup"><span data-stu-id="b95fb-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="b95fb-142">在使用者控制項中執行拖曳來源事件</span><span class="sxs-lookup"><span data-stu-id="b95fb-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="b95fb-143">在本節中, 您將覆寫<xref:System.Windows.UIElement.OnMouseMove%2A>方法, 並起始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="b95fb-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="b95fb-144">如果已啟動拖曳 (按下滑鼠按鍵並移動滑鼠), 您將會封裝要傳送至的<xref:System.Windows.DataObject>資料。</span><span class="sxs-lookup"><span data-stu-id="b95fb-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="b95fb-145">在此情況下，Circle 控制項將會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。</span><span class="sxs-lookup"><span data-stu-id="b95fb-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="b95fb-146">啟始拖放作業</span><span class="sxs-lookup"><span data-stu-id="b95fb-146">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="b95fb-147">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b95fb-148">新增下列<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫, 以提供<xref:System.Windows.UIElement.MouseMove>事件的類別處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="b95fb-149">此<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-150">檢查是否在滑鼠移動時按下滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="b95fb-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="b95fb-151">將圓形資料封裝成<xref:System.Windows.DataObject>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="b95fb-152">在此情況下，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。</span><span class="sxs-lookup"><span data-stu-id="b95fb-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="b95fb-153">呼叫靜態<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>方法, 以起始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="b95fb-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="b95fb-154">您會將下列三個參數傳遞<xref:System.Windows.DragDrop.DoDragDrop%2A>給方法:</span><span class="sxs-lookup"><span data-stu-id="b95fb-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="b95fb-155">`dragSource` – 此控制項的參考。</span><span class="sxs-lookup"><span data-stu-id="b95fb-155">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="b95fb-156">`data`–在<xref:System.Windows.DataObject>先前的程式碼中建立的。</span><span class="sxs-lookup"><span data-stu-id="b95fb-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="b95fb-157">`allowedEffects`–允許的拖放作業, 也就是<xref:System.Windows.DragDropEffects.Copy>或。 <xref:System.Windows.DragDropEffects.Move></span><span class="sxs-lookup"><span data-stu-id="b95fb-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="b95fb-158">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-158">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b95fb-159">按一下其中一個 Circle 控制項, 然後將它拖曳至面板、另一個圓形和<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b95fb-160">當拖曳<xref:System.Windows.Controls.TextBox>至時, 游標會變更以表示移動。</span><span class="sxs-lookup"><span data-stu-id="b95fb-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="b95fb-161">將<xref:System.Windows.Controls.TextBox>圓形拖曳到上時, 請按下**Ctrl**鍵。</span><span class="sxs-lookup"><span data-stu-id="b95fb-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="b95fb-162">請注意，游標變更以指出正在進行複製。</span><span class="sxs-lookup"><span data-stu-id="b95fb-162">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="b95fb-163">將圓形拖放到上<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b95fb-164">圓形填滿色彩的字串表示會附加至<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="b95fb-165">![Circle 之填滿色彩的字串表示](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="b95fb-165">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="b95fb-166">根據預設，游標會在拖放作業期間變更，表示置放資料的效果。</span><span class="sxs-lookup"><span data-stu-id="b95fb-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="b95fb-167">您可以藉由處理<xref:System.Windows.UIElement.GiveFeedback>事件並設定不同的資料指標, 自訂提供給使用者的意見反應。</span><span class="sxs-lookup"><span data-stu-id="b95fb-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="b95fb-168">將意見反應提供給使用者</span><span class="sxs-lookup"><span data-stu-id="b95fb-168">Give feedback to the user</span></span>

1. <span data-ttu-id="b95fb-169">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b95fb-170">新增下列<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫, 以提供<xref:System.Windows.UIElement.GiveFeedback>事件的類別處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="b95fb-171">此<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-172">檢查在放置目標的<xref:System.Windows.UIElement.DragOver>事件處理常式中設定的值。<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="b95fb-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="b95fb-173">根據<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>值設定自訂資料指標。</span><span class="sxs-lookup"><span data-stu-id="b95fb-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="b95fb-174">游標用於將資料置放效果的視覺化回饋提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="b95fb-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="b95fb-175">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-175">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b95fb-176">將其中一個 Circle 控制項拖曳至面板、另一個圓形和<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="b95fb-177">請注意, 資料指標現在是您在覆<xref:System.Windows.UIElement.OnGiveFeedback%2A>寫中指定的自訂資料指標。</span><span class="sxs-lookup"><span data-stu-id="b95fb-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="b95fb-178">![以自訂游標執行拖放作業](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="b95fb-178">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="b95fb-179">`green` 選取<xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="b95fb-180">將 `green` 文字拖曳至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="b95fb-181">請注意，會顯示預設游標，表示拖放作業的效果。</span><span class="sxs-lookup"><span data-stu-id="b95fb-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="b95fb-182">意見反應游標一律是由拖曳來源所設定。</span><span class="sxs-lookup"><span data-stu-id="b95fb-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="b95fb-183">在使用者控制項中執行放置目標事件</span><span class="sxs-lookup"><span data-stu-id="b95fb-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="b95fb-184">在本節中，您將指定使用者控制項是置放目標、覆寫讓使用者控制項成為置放目標的方法，以及處理置放在其上的資料。</span><span class="sxs-lookup"><span data-stu-id="b95fb-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="b95fb-185">讓使用者控制項成為置放目標</span><span class="sxs-lookup"><span data-stu-id="b95fb-185">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="b95fb-186">開啟 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="b95fb-186">Open Circle.xaml.</span></span>

2. <span data-ttu-id="b95fb-187">在開頭<xref:System.Windows.Controls.UserControl>標記中, <xref:System.Windows.UIElement.AllowDrop%2A>新增屬性, 並將它設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="b95fb-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="b95fb-188">當屬性設定為`true`時, 會呼叫方法,並將拖曳來源的資料放在Circle使用者控制項上。<xref:System.Windows.UIElement.OnDrop%2A> <xref:System.Windows.UIElement.AllowDrop%2A></span><span class="sxs-lookup"><span data-stu-id="b95fb-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="b95fb-189">在此方法中，您將處理置放的資料，並將資料套用至 Circle。</span><span class="sxs-lookup"><span data-stu-id="b95fb-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="b95fb-190">處理置放的資料</span><span class="sxs-lookup"><span data-stu-id="b95fb-190">To process the dropped data</span></span>

1. <span data-ttu-id="b95fb-191">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b95fb-192">新增下列<xref:System.Windows.UIElement.OnDrop%2A>覆寫, 以提供<xref:System.Windows.UIElement.Drop>事件的類別處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="b95fb-193">此<xref:System.Windows.UIElement.OnDrop%2A>覆寫會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-194"><xref:System.Windows.DataObject.GetDataPresent%2A>使用方法來檢查拖曳的資料是否包含 string 物件。</span><span class="sxs-lookup"><span data-stu-id="b95fb-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="b95fb-195">會使用<xref:System.Windows.DataObject.GetData%2A>方法來解壓縮字串資料 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="b95fb-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="b95fb-196">會使用<xref:System.Windows.Media.Brush>來嘗試將字串轉換成。 <xref:System.Windows.Media.BrushConverter></span><span class="sxs-lookup"><span data-stu-id="b95fb-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="b95fb-197">如果轉換成功, 會將筆刷套用至<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse>提供 Circle 控制項 UI 的的。</span><span class="sxs-lookup"><span data-stu-id="b95fb-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="b95fb-198">將<xref:System.Windows.UIElement.Drop>事件標示為已處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="b95fb-199">您應該將置放事件標示為已處理，讓收到此事件的其他項目知道 Circle 使用者控制項已處理過它。</span><span class="sxs-lookup"><span data-stu-id="b95fb-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="b95fb-200">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-200">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b95fb-201">`green` 選取<xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="b95fb-202">將文字拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="b95fb-203">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="b95fb-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="b95fb-204">![將字串轉換成筆刷](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="b95fb-204">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="b95fb-205">在中輸入`green`文字。 <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="b95fb-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="b95fb-206">`gre` 選取<xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="b95fb-207">將它拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="b95fb-208">請注意，游標變更以指出允許置放，但 Circle 的色彩不會變更，因為 `gre` 不是有效的色彩。</span><span class="sxs-lookup"><span data-stu-id="b95fb-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="b95fb-209">從綠色 Circle 控制項拖放至藍色 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="b95fb-210">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="b95fb-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="b95fb-211">請注意, 會顯示哪一個游標, 取決<xref:System.Windows.Controls.TextBox>于或圓形是否為拖曳來源。</span><span class="sxs-lookup"><span data-stu-id="b95fb-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="b95fb-212">將屬性設定為`true`並處理已捨棄的資料, 就是讓元素成為卸載目標所需的所有專案。 <xref:System.Windows.UIElement.AllowDrop%2A></span><span class="sxs-lookup"><span data-stu-id="b95fb-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="b95fb-213">不過, 為了提供更好的使用者體驗, 您也應該處理<xref:System.Windows.UIElement.DragEnter>、 <xref:System.Windows.UIElement.DragLeave>和<xref:System.Windows.UIElement.DragOver>事件。</span><span class="sxs-lookup"><span data-stu-id="b95fb-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="b95fb-214">在這些事件中，您可以在置放資料之前執行檢查，並將其他意見反應提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="b95fb-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="b95fb-215">將資料拖曳至 Circle 使用者控制項上方時，控制項應該通知拖曳來源是否可以處理所拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="b95fb-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="b95fb-216">如果控制項不知道如何處理資料，則應該拒絕置放。</span><span class="sxs-lookup"><span data-stu-id="b95fb-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="b95fb-217">若要這樣做, 您將會<xref:System.Windows.UIElement.DragOver>處理事件, 並<xref:System.Windows.DragEventArgs.Effects%2A>設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b95fb-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="b95fb-218">確認允許資料置放</span><span class="sxs-lookup"><span data-stu-id="b95fb-218">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="b95fb-219">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b95fb-220">新增下列<xref:System.Windows.UIElement.OnDragOver%2A>覆寫, 以提供<xref:System.Windows.UIElement.DragOver>事件的類別處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="b95fb-221">此<xref:System.Windows.UIElement.OnDragOver%2A>覆寫會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-222">將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.None>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="b95fb-223">執行在<xref:System.Windows.UIElement.OnDrop%2A>方法中執行的相同檢查, 以判斷 Circle 使用者控制項是否可以處理拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="b95fb-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="b95fb-224">如果使用者控制項可以處理資料, 請將<xref:System.Windows.DragEventArgs.Effects%2A>屬性設定為<xref:System.Windows.DragDropEffects.Copy>或<xref:System.Windows.DragDropEffects.Move>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="b95fb-225">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-225">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="b95fb-226">`gre` 選取<xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="b95fb-227">將文字拖曳至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="b95fb-228">請注意，游標現在會變更以指出不允許置放，因為 `gre` 不是有效的色彩。</span><span class="sxs-lookup"><span data-stu-id="b95fb-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="b95fb-229">您可以套用置放作業的預覽，進一步增強使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="b95fb-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="b95fb-230">對於 Circle 使用者控制項, 您將會覆寫<xref:System.Windows.UIElement.OnDragEnter%2A>和<xref:System.Windows.UIElement.OnDragLeave%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b95fb-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="b95fb-231">將資料拖曳至控制項上時, 會將目前的<xref:System.Windows.Shapes.Shape.Fill%2A>背景儲存在預留位置變數中。</span><span class="sxs-lookup"><span data-stu-id="b95fb-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="b95fb-232">然後, 此字串會轉換成筆刷, 並套用<xref:System.Windows.Shapes.Ellipse>至提供圓形 UI 的。</span><span class="sxs-lookup"><span data-stu-id="b95fb-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="b95fb-233">如果將資料從圓形拖曳掉而不卸載, 則會將原始<xref:System.Windows.Shapes.Shape.Fill%2A>值重新套用至圓形。</span><span class="sxs-lookup"><span data-stu-id="b95fb-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="b95fb-234">預覽拖放作業的效果</span><span class="sxs-lookup"><span data-stu-id="b95fb-234">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="b95fb-235">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="b95fb-236">在 Circle 類別中, 宣告名為<xref:System.Windows.Media.Brush> `_previousFill`的私用變數, 並`null`將它初始化為。</span><span class="sxs-lookup"><span data-stu-id="b95fb-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="b95fb-237">新增下列<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫, 以提供<xref:System.Windows.UIElement.DragEnter>事件的類別處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="b95fb-238">此<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-239">將的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse>屬性儲存在`_previousFill`變數中。</span><span class="sxs-lookup"><span data-stu-id="b95fb-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="b95fb-240">執行在<xref:System.Windows.UIElement.OnDrop%2A>方法中執行的相同檢查, 以判斷資料是否可以轉換<xref:System.Windows.Media.Brush>成。</span><span class="sxs-lookup"><span data-stu-id="b95fb-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="b95fb-241">如果資料轉換成有效<xref:System.Windows.Media.Brush>的, 則會將它套用<xref:System.Windows.Shapes.Shape.Fill%2A>至<xref:System.Windows.Shapes.Ellipse>的。</span><span class="sxs-lookup"><span data-stu-id="b95fb-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="b95fb-242">新增下列<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫, 以提供<xref:System.Windows.UIElement.DragLeave>事件的類別處理。</span><span class="sxs-lookup"><span data-stu-id="b95fb-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="b95fb-243">此<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-244">將儲存在`_previousFill` 變數中的套用<xref:System.Windows.Shapes.Shape.Fill%2A>到提供Circle使用者控制項之UI的。<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush></span><span class="sxs-lookup"><span data-stu-id="b95fb-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="b95fb-245">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-245">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="b95fb-246">`green` 選取<xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="b95fb-247">將文字拖曳至 Circle 控制項上方，但不置放文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="b95fb-248">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="b95fb-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="b95fb-249">![預覽拖放作業的效果](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="b95fb-249">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="b95fb-250">從 Circle 控制項拖離文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="b95fb-251">Circle 會從綠色變回藍色。</span><span class="sxs-lookup"><span data-stu-id="b95fb-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="b95fb-252">啟用面板以接收已捨棄的資料</span><span class="sxs-lookup"><span data-stu-id="b95fb-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="b95fb-253">在本節中, 您會啟用裝載 Circle 使用者控制項的面板, 做為拖曳的圓形資料的放置目標。</span><span class="sxs-lookup"><span data-stu-id="b95fb-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="b95fb-254">您將會執行程式碼, 讓您可以將圓形從一個面板移到另一個面板, 或在拖放圓形時按住**Ctrl**鍵來複製 circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="b95fb-255">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="b95fb-255">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="b95fb-256">如下列 XAML 所示, 在每個<xref:System.Windows.Controls.StackPanel>控制項中, 加入和<xref:System.Windows.UIElement.Drop>事件的<xref:System.Windows.UIElement.DragOver>處理常式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="b95fb-257">將事件<xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop>處理常式`panel_Drop`命名為, 並將事件處理常式命名為。 `panel_DragOver`</span><span class="sxs-lookup"><span data-stu-id="b95fb-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="b95fb-258">開啟 MainWindows.xaml.cs 或 MainWindow.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="b95fb-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="b95fb-259">為<xref:System.Windows.UIElement.DragOver>事件處理常式新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b95fb-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="b95fb-260">這個<xref:System.Windows.UIElement.DragOver>事件處理常式會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-261">檢查拖曳的資料是否包含<xref:System.Windows.DataObject>由 Circle 使用者控制項封裝在中, 並在<xref:System.Windows.DragDrop.DoDragDrop%2A>呼叫中傳遞的「物件」資料。</span><span class="sxs-lookup"><span data-stu-id="b95fb-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="b95fb-262">如果出現「物件」資料, 則會檢查是否按下**Ctrl**鍵。</span><span class="sxs-lookup"><span data-stu-id="b95fb-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="b95fb-263">如果按下**Ctrl**鍵, 則會將<xref:System.Windows.DragEventArgs.Effects%2A>屬性設定<xref:System.Windows.DragDropEffects.Copy>為。</span><span class="sxs-lookup"><span data-stu-id="b95fb-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="b95fb-264">否則, 請將<xref:System.Windows.DragEventArgs.Effects%2A>屬性設定<xref:System.Windows.DragDropEffects.Move>為。</span><span class="sxs-lookup"><span data-stu-id="b95fb-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="b95fb-265">為<xref:System.Windows.UIElement.Drop>事件處理常式新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b95fb-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="b95fb-266">這個<xref:System.Windows.UIElement.Drop>事件處理常式會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="b95fb-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="b95fb-267">檢查是否<xref:System.Windows.UIElement.Drop>已處理事件。</span><span class="sxs-lookup"><span data-stu-id="b95fb-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="b95fb-268">比方說, 如果在處理<xref:System.Windows.UIElement.Drop>事件的另一個圓圈上放置圓形, 您不想要包含圓形的面板也可以處理它。</span><span class="sxs-lookup"><span data-stu-id="b95fb-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="b95fb-269">如果未處理  事件,則會檢查是否按下Ctrl<xref:System.Windows.UIElement.Drop>鍵。</span><span class="sxs-lookup"><span data-stu-id="b95fb-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="b95fb-270">如果在  <xref:System.Windows.UIElement.Drop>發生時按下 Ctrl 鍵, 則會建立 Circle 控制項的複本, 並<xref:System.Windows.Controls.Panel.Children%2A>將它加入至的集合<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="b95fb-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="b95fb-271">如果未按下**Ctrl**鍵, 則會將圓形從<xref:System.Windows.Controls.Panel.Children%2A>其<xref:System.Windows.Controls.Panel.Children%2A>父面板集合移至其所放置的面板集合。</span><span class="sxs-lookup"><span data-stu-id="b95fb-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="b95fb-272">設定屬性, 以通知方法是否已執行移動或複製作業。 <xref:System.Windows.DragDrop.DoDragDrop%2A> <xref:System.Windows.DragEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="b95fb-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="b95fb-273">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b95fb-273">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="b95fb-274">`green` 選取<xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="b95fb-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="b95fb-275">將文字拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="b95fb-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="b95fb-276">將 Circle 控制項從從左面板拖放至右面板。</span><span class="sxs-lookup"><span data-stu-id="b95fb-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="b95fb-277">會從左側面板的<xref:System.Windows.Controls.Panel.Children%2A>集合中移除圓形, 並將其新增至右側面板的 [子系] 集合。</span><span class="sxs-lookup"><span data-stu-id="b95fb-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="b95fb-278">將 Circle 控制項從它所在的面板拖曳到另一個面板, 並在按下**Ctrl**鍵時放置它。</span><span class="sxs-lookup"><span data-stu-id="b95fb-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="b95fb-279">會複製圓形, 並將複本新增至<xref:System.Windows.Controls.Panel.Children%2A>接收面板的集合。</span><span class="sxs-lookup"><span data-stu-id="b95fb-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="b95fb-280">![拖曳 Circle 時按住 CTRL 鍵](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="b95fb-280">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="b95fb-281">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b95fb-281">See also</span></span>

- [<span data-ttu-id="b95fb-282">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="b95fb-282">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
