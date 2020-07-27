---
title: 逐步解說：在使用者控制項上啟用拖放功能
description: 瞭解如何建立可在 Windows Presentation Foundation 中參與拖放資料傳輸的自訂使用者控制項。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168275"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="d5ec9-103">逐步解說：在使用者控制項上啟用拖放功能</span><span class="sxs-lookup"><span data-stu-id="d5ec9-103">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="d5ec9-104">本逐步解說示範如何建立自訂使用者控制項以參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的拖放資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-104">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="d5ec9-105">在此逐步解說中，您將建立 <xref:System.Windows.Controls.UserControl> 代表圓形圖形的自訂 WPF。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-105">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="d5ec9-106">您將在控制項上實作功能，以啟用透過拖放的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-106">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="d5ec9-107">例如，如果您從某個 Circle 控制項拖曳至另一個 Circle 控制項，則會將填滿色彩資料從來源 Circle 複製至目標。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-107">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="d5ec9-108">如果您從 Circle 控制項拖曳至，則 <xref:System.Windows.Controls.TextBox> 填滿色彩的字串表示會複製到 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-108">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d5ec9-109">您也會建立一個包含兩個面板控制項的小型應用程式，以及一個 <xref:System.Windows.Controls.TextBox> 測試拖放功能的。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-109">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="d5ec9-110">您將撰寫讓面板處理所置放 Circle 資料的程式碼，以讓您將 Circle 從某個面版的子系集合移動或複製至另一個面板。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-110">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="d5ec9-111">本逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-111">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="d5ec9-112">建立自訂使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-112">Create a custom user control.</span></span>

- <span data-ttu-id="d5ec9-113">可讓使用者控制項成為拖曳來源。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-113">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="d5ec9-114">讓使用者控制項成為置放目標。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-114">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="d5ec9-115">啟用面板，以接收從使用者控制項置放的資料。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-115">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d5ec9-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="d5ec9-116">Prerequisites</span></span>

<span data-ttu-id="d5ec9-117">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-117">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="d5ec9-118">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="d5ec9-118">Create the Application Project</span></span>
 <span data-ttu-id="d5ec9-119">在本節中，您將建立應用程式基礎結構，其中包含具有兩個面板和的主頁面 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="d5ec9-120">在 Visual Basic 或 Visual C# 中，建立名為 `DragDropExample` 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-120">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="d5ec9-121">如需詳細資訊，請參閱[逐步解說︰我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-121">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="d5ec9-122">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-122">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="d5ec9-123">在開頭和結束記號之間新增下列標記 <xref:System.Windows.Controls.Grid> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-123">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="d5ec9-124">此標記會建立測試應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-124">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="d5ec9-125">將新的使用者控制項加入至專案</span><span class="sxs-lookup"><span data-stu-id="d5ec9-125">Add a New User Control to the Project</span></span>
 <span data-ttu-id="d5ec9-126">在本節中，您會將新的使用者控制項新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-126">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="d5ec9-127">在 [專案] 功能表上，選取 [新增使用者控制項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-127">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="d5ec9-128">在 [**加入新專案**] 對話方塊中，將名稱變更為 `Circle.xaml` ，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-128">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="d5ec9-129">Circle.xaml 和其程式碼後置會新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-129">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="d5ec9-130">開啟 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-130">Open Circle.xaml.</span></span>

     <span data-ttu-id="d5ec9-131">此檔案將包含使用者控制項的使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-131">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="d5ec9-132">將下列標記新增至根， <xref:System.Windows.Controls.Grid> 以建立具有藍色圓圈作為其 UI 的簡單使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-132">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="d5ec9-133">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-133">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="d5ec9-134">在 c # 中，將下列程式碼新增至無參數的函式之後，以建立複製的函式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-134">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="d5ec9-135">在 Visual Basic 中，新增下列程式碼，以建立無參數的函式和複製的函式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-135">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="d5ec9-136">若要允許複製使用者控制項，您可以在程式碼後置檔案中新增複製建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-136">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="d5ec9-137">在簡化 Circle 使用者控制項中，您只會複製使用者控制項的填滿和大小。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-137">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="d5ec9-138">將使用者控制項加入至主視窗</span><span class="sxs-lookup"><span data-stu-id="d5ec9-138">Add the user control to the main window</span></span>

1. <span data-ttu-id="d5ec9-139">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-139">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="d5ec9-140">將下列 XAML 加入至開頭 <xref:System.Windows.Window> 標記，以建立目前應用程式的 XML 命名空間參考。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-140">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="d5ec9-141">在第一個中 <xref:System.Windows.Controls.StackPanel> ，新增下列 XAML，在第一個面板中建立 Circle 使用者控制項的兩個實例。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-141">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="d5ec9-142">面板的完整 XAML 如下。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-142">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="d5ec9-143">在使用者控制項中執行拖曳來源事件</span><span class="sxs-lookup"><span data-stu-id="d5ec9-143">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="d5ec9-144">在本節中，您將覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法，並起始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-144">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="d5ec9-145">如果已啟動拖曳（按下滑鼠按鍵並移動滑鼠），您將會封裝要傳送至的資料 <xref:System.Windows.DataObject> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-145">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="d5ec9-146">在此情況下，Circle 控制項將會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-146">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="d5ec9-147">啟始拖放作業</span><span class="sxs-lookup"><span data-stu-id="d5ec9-147">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="d5ec9-148">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-148">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d5ec9-149">新增下列覆 <xref:System.Windows.UIElement.OnMouseMove%2A> 寫，以提供事件的類別處理 <xref:System.Windows.UIElement.MouseMove> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-149">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="d5ec9-150">此覆 <xref:System.Windows.UIElement.OnMouseMove%2A> 寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-150">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-151">檢查是否在滑鼠移動時按下滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-151">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="d5ec9-152">將圓形資料封裝成 <xref:System.Windows.DataObject> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-152">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="d5ec9-153">在此情況下，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-153">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="d5ec9-154">呼叫靜態 <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> 方法，以起始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-154">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="d5ec9-155">您會將下列三個參數傳遞給 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-155">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="d5ec9-156">`dragSource` – 此控制項的參考。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-156">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="d5ec9-157">`data`– <xref:System.Windows.DataObject> 在先前的程式碼中建立的。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-157">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="d5ec9-158">`allowedEffects`–允許的拖放作業，也就是 <xref:System.Windows.DragDropEffects.Copy> 或 <xref:System.Windows.DragDropEffects.Move> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-158">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="d5ec9-159">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-159">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d5ec9-160">按一下其中一個 Circle 控制項，然後將它拖曳至面板、另一個圓形和 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-160">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d5ec9-161">當拖曳至時 <xref:System.Windows.Controls.TextBox> ，游標會變更以表示移動。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-161">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="d5ec9-162">將圓形拖曳到上時 <xref:System.Windows.Controls.TextBox> ，請按下**Ctrl**鍵。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-162">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="d5ec9-163">請注意，游標變更以指出正在進行複製。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-163">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="d5ec9-164">將圓形拖放到上 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-164">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d5ec9-165">圓形填滿色彩的字串表示會附加至 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-165">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="d5ec9-166">![Circle 之填滿色彩的字串表示](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="d5ec9-166">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="d5ec9-167">根據預設，游標會在拖放作業期間變更，表示置放資料的效果。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-167">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="d5ec9-168">您可以藉由處理 <xref:System.Windows.UIElement.GiveFeedback> 事件並設定不同的資料指標，自訂提供給使用者的意見反應。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-168">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="d5ec9-169">將意見反應提供給使用者</span><span class="sxs-lookup"><span data-stu-id="d5ec9-169">Give feedback to the user</span></span>

1. <span data-ttu-id="d5ec9-170">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-170">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d5ec9-171">新增下列覆 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 寫，以提供事件的類別處理 <xref:System.Windows.UIElement.GiveFeedback> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-171">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="d5ec9-172">此覆 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-172">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-173">檢查在 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 放置目標的事件處理常式中設定的值 <xref:System.Windows.UIElement.DragOver> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-173">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="d5ec9-174">根據值設定自訂資料指標 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-174">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="d5ec9-175">游標用於將資料置放效果的視覺化回饋提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-175">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="d5ec9-176">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-176">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d5ec9-177">將其中一個 Circle 控制項拖曳至面板、另一個圓形和 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-177">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d5ec9-178">請注意，資料指標現在是您在覆寫中指定的自訂資料指標 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-178">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="d5ec9-179">![以自訂游標執行拖放作業](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="d5ec9-179">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="d5ec9-180">選取中的文字 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-180">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="d5ec9-181">將 `green` 文字拖曳至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-181">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="d5ec9-182">請注意，會顯示預設游標，表示拖放作業的效果。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-182">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="d5ec9-183">意見反應游標一律是由拖曳來源所設定。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-183">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="d5ec9-184">在使用者控制項中執行放置目標事件</span><span class="sxs-lookup"><span data-stu-id="d5ec9-184">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="d5ec9-185">在本節中，您將指定使用者控制項是置放目標、覆寫讓使用者控制項成為置放目標的方法，以及處理置放在其上的資料。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-185">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="d5ec9-186">讓使用者控制項成為置放目標</span><span class="sxs-lookup"><span data-stu-id="d5ec9-186">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="d5ec9-187">開啟 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-187">Open Circle.xaml.</span></span>

2. <span data-ttu-id="d5ec9-188">在開頭 <xref:System.Windows.Controls.UserControl> 標記中，新增 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性，並將它設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-188">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="d5ec9-189"><xref:System.Windows.UIElement.OnDrop%2A>當屬性設定為時，會呼叫方法 <xref:System.Windows.UIElement.AllowDrop%2A> `true` ，並將拖曳來源的資料放在 Circle 使用者控制項上。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-189">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="d5ec9-190">在此方法中，您將處理置放的資料，並將資料套用至 Circle。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-190">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="d5ec9-191">處理置放的資料</span><span class="sxs-lookup"><span data-stu-id="d5ec9-191">To process the dropped data</span></span>

1. <span data-ttu-id="d5ec9-192">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-192">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d5ec9-193">新增下列覆 <xref:System.Windows.UIElement.OnDrop%2A> 寫，以提供事件的類別處理 <xref:System.Windows.UIElement.Drop> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-193">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="d5ec9-194">此覆 <xref:System.Windows.UIElement.OnDrop%2A> 寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-194">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-195">使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法來檢查拖曳的資料是否包含 string 物件。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-195">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="d5ec9-196">會使用 <xref:System.Windows.DataObject.GetData%2A> 方法來解壓縮字串資料（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-196">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="d5ec9-197">會使用 <xref:System.Windows.Media.BrushConverter> 來嘗試將字串轉換成 <xref:System.Windows.Media.Brush> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-197">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="d5ec9-198">如果轉換成功，會將筆刷套用至 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 提供 CIRCLE 控制項 UI 的的。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-198">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="d5ec9-199">將 <xref:System.Windows.UIElement.Drop> 事件標示為已處理。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-199">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="d5ec9-200">您應該將置放事件標示為已處理，讓收到此事件的其他項目知道 Circle 使用者控制項已處理過它。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-200">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="d5ec9-201">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-201">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d5ec9-202">選取中的文字 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-202">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="d5ec9-203">將文字拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-203">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="d5ec9-204">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-204">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="d5ec9-205">![將字串轉換成筆刷](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="d5ec9-205">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="d5ec9-206">`green`在中輸入文字 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-206">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="d5ec9-207">選取中的文字 `gre` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-207">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="d5ec9-208">將它拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-208">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="d5ec9-209">請注意，游標變更以指出允許置放，但 Circle 的色彩不會變更，因為 `gre` 不是有效的色彩。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-209">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="d5ec9-210">從綠色 Circle 控制項拖放至藍色 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-210">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="d5ec9-211">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-211">The Circle changes from blue to green.</span></span> <span data-ttu-id="d5ec9-212">請注意，會顯示哪一個游標，取決於 <xref:System.Windows.Controls.TextBox> 或圓形是否為拖曳來源。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-212">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="d5ec9-213">將 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性設定為 `true` 並處理已捨棄的資料，就是讓元素成為卸載目標所需的所有專案。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-213">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="d5ec9-214">不過，為了提供更好的使用者體驗，您也應該處理 <xref:System.Windows.UIElement.DragEnter> 、 <xref:System.Windows.UIElement.DragLeave> 和 <xref:System.Windows.UIElement.DragOver> 事件。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-214">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="d5ec9-215">在這些事件中，您可以在置放資料之前執行檢查，並將其他意見反應提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-215">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="d5ec9-216">將資料拖曳至 Circle 使用者控制項上方時，控制項應該通知拖曳來源是否可以處理所拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-216">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="d5ec9-217">如果控制項不知道如何處理資料，則應該拒絕置放。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-217">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="d5ec9-218">若要這樣做，您將會處理 <xref:System.Windows.UIElement.DragOver> 事件，並設定 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-218">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="d5ec9-219">確認允許資料置放</span><span class="sxs-lookup"><span data-stu-id="d5ec9-219">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="d5ec9-220">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-220">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d5ec9-221">新增下列覆 <xref:System.Windows.UIElement.OnDragOver%2A> 寫，以提供事件的類別處理 <xref:System.Windows.UIElement.DragOver> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-221">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="d5ec9-222">此覆 <xref:System.Windows.UIElement.OnDragOver%2A> 寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-222">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-223">將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.None>。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-223">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="d5ec9-224">執行在方法中執行的相同檢查， <xref:System.Windows.UIElement.OnDrop%2A> 以判斷 Circle 使用者控制項是否可以處理拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-224">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="d5ec9-225">如果使用者控制項可以處理資料，請將屬性設定 <xref:System.Windows.DragEventArgs.Effects%2A> 為 <xref:System.Windows.DragDropEffects.Copy> 或 <xref:System.Windows.DragDropEffects.Move> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-225">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="d5ec9-226">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-226">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="d5ec9-227">選取中的文字 `gre` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-227">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="d5ec9-228">將文字拖曳至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-228">Drag the text to a Circle control.</span></span> <span data-ttu-id="d5ec9-229">請注意，游標現在會變更以指出不允許置放，因為 `gre` 不是有效的色彩。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-229">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="d5ec9-230">您可以套用置放作業的預覽，進一步增強使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-230">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="d5ec9-231">對於 Circle 使用者控制項，您將會覆寫 <xref:System.Windows.UIElement.OnDragEnter%2A> 和 <xref:System.Windows.UIElement.OnDragLeave%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-231">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="d5ec9-232">將資料拖曳至控制項上時，會將目前的背景 <xref:System.Windows.Shapes.Shape.Fill%2A> 儲存在預留位置變數中。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-232">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="d5ec9-233">然後，此字串會轉換成筆刷，並套用至 <xref:System.Windows.Shapes.Ellipse> 提供圓形 UI 的。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-233">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="d5ec9-234">如果將資料從圓形拖曳掉而不卸載，則會將原始 <xref:System.Windows.Shapes.Shape.Fill%2A> 值重新套用至圓形。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-234">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="d5ec9-235">預覽拖放作業的效果</span><span class="sxs-lookup"><span data-stu-id="d5ec9-235">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="d5ec9-236">開啟 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-236">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="d5ec9-237">在 Circle 類別中，宣告名為的私用 <xref:System.Windows.Media.Brush> 變數， `_previousFill` 並將它初始化為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-237">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="d5ec9-238">新增下列覆 <xref:System.Windows.UIElement.OnDragEnter%2A> 寫，以提供事件的類別處理 <xref:System.Windows.UIElement.DragEnter> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-238">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="d5ec9-239">此覆 <xref:System.Windows.UIElement.OnDragEnter%2A> 寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-239">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-240">將 <xref:System.Windows.Shapes.Shape.Fill%2A> 的屬性儲存 <xref:System.Windows.Shapes.Ellipse> 在變數中 `_previousFill` 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-240">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="d5ec9-241">執行在方法中執行的相同檢查， <xref:System.Windows.UIElement.OnDrop%2A> 以判斷資料是否可以轉換成 <xref:System.Windows.Media.Brush> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-241">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="d5ec9-242">如果資料轉換成有效的，則 <xref:System.Windows.Media.Brush> 會將它套用至的 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-242">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="d5ec9-243">新增下列覆 <xref:System.Windows.UIElement.OnDragLeave%2A> 寫，以提供事件的類別處理 <xref:System.Windows.UIElement.DragLeave> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-243">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="d5ec9-244">此覆 <xref:System.Windows.UIElement.OnDragLeave%2A> 寫會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-244">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-245">將 <xref:System.Windows.Media.Brush> 儲存在變數中的套用 `_previousFill` 到 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 提供 CIRCLE 使用者控制項之 UI 的。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-245">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="d5ec9-246">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-246">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="d5ec9-247">選取中的文字 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-247">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="d5ec9-248">將文字拖曳至 Circle 控制項上方，但不置放文字。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-248">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="d5ec9-249">Circle 會從藍色變成綠色。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-249">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="d5ec9-250">![預覽拖曳&#45;和&#45;drop 作業的效果](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="d5ec9-250">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="d5ec9-251">從 Circle 控制項拖離文字。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-251">Drag the text away from the Circle control.</span></span> <span data-ttu-id="d5ec9-252">Circle 會從綠色變回藍色。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-252">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="d5ec9-253">啟用面板以接收已捨棄的資料</span><span class="sxs-lookup"><span data-stu-id="d5ec9-253">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="d5ec9-254">在本節中，您會啟用裝載 Circle 使用者控制項的面板，做為拖曳的圓形資料的放置目標。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-254">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="d5ec9-255">您將會執行程式碼，讓您可以將圓形從一個面板移到另一個面板，或在拖放圓形時按住**Ctrl**鍵來複製 circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-255">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="d5ec9-256">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-256">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="d5ec9-257">如下列 XAML 所示，在每個控制項中 <xref:System.Windows.Controls.StackPanel> ，加入和事件的處理 <xref:System.Windows.UIElement.DragOver> 程式 <xref:System.Windows.UIElement.Drop> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-257">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="d5ec9-258">將 <xref:System.Windows.UIElement.DragOver> 事件處理常式命名為， `panel_DragOver` 並將 <xref:System.Windows.UIElement.Drop> 事件處理常式命名為 `panel_Drop` 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-258">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="d5ec9-259">開啟 MainWindows.xaml.cs 或 MainWindow.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-259">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="d5ec9-260">為 <xref:System.Windows.UIElement.DragOver> 事件處理常式新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-260">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="d5ec9-261">這個 <xref:System.Windows.UIElement.DragOver> 事件處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-261">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-262">檢查拖曳的資料是否包含 <xref:System.Windows.DataObject> 由 Circle 使用者控制項封裝在中，並在呼叫中傳遞的「物件」資料 <xref:System.Windows.DragDrop.DoDragDrop%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-262">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="d5ec9-263">如果出現「物件」資料，則會檢查是否按下**Ctrl**鍵。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-263">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="d5ec9-264">如果按下**Ctrl**鍵，則會將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.Copy> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-264">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="d5ec9-265">否則，請將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.Move> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-265">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="d5ec9-266">為 <xref:System.Windows.UIElement.Drop> 事件處理常式新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-266">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="d5ec9-267">這個 <xref:System.Windows.UIElement.Drop> 事件處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d5ec9-267">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="d5ec9-268">檢查是否已 <xref:System.Windows.UIElement.Drop> 處理事件。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-268">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="d5ec9-269">比方說，如果在處理事件的另一個圓圈上放置圓形 <xref:System.Windows.UIElement.Drop> ，您不想要包含圓形的面板也可以處理它。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-269">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="d5ec9-270">如果 <xref:System.Windows.UIElement.Drop> 未處理事件，則會檢查是否按下**Ctrl**鍵。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-270">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="d5ec9-271">如果在發生時按下**Ctrl**鍵 <xref:System.Windows.UIElement.Drop> ，則會建立 Circle 控制項的複本，並將它加入至的 <xref:System.Windows.Controls.Panel.Children%2A> 集合 <xref:System.Windows.Controls.StackPanel> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-271">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="d5ec9-272">如果未按下**Ctrl**鍵，則會將圓形從 <xref:System.Windows.Controls.Panel.Children%2A> 其父面板集合移至其所 <xref:System.Windows.Controls.Panel.Children%2A> 放置的面板集合。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-272">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="d5ec9-273">設定 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性，以通知 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法是否已執行移動或複製作業。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-273">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="d5ec9-274">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-274">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="d5ec9-275">選取中的文字 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-275">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="d5ec9-276">將文字拖放至 Circle 控制項。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-276">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="d5ec9-277">將 Circle 控制項從從左面板拖放至右面板。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-277">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="d5ec9-278">會從左側面板的集合中移除圓形 <xref:System.Windows.Controls.Panel.Children%2A> ，並將其新增至右側面板的 [子系] 集合。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-278">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="d5ec9-279">將 Circle 控制項從它所在的面板拖曳到另一個面板，並在按下**Ctrl**鍵時放置它。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-279">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="d5ec9-280">會複製圓形，並將複本新增至 <xref:System.Windows.Controls.Panel.Children%2A> 接收面板的集合。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-280">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="d5ec9-281">![拖曳 Circle 時按住 CTRL 鍵](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="d5ec9-281">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ec9-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ec9-282">See also</span></span>

- [<span data-ttu-id="d5ec9-283">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="d5ec9-283">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
