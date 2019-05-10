---
title: Windows Form 中的滑鼠事件
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 818364ceddb03df51ed656c8ff7b69fd433ac86a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750887"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="36da2-102">Windows Form 中的滑鼠事件</span><span class="sxs-lookup"><span data-stu-id="36da2-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="36da2-103">當您處理滑鼠輸入時，您通常會要知道滑鼠指標的位置，以及滑鼠按鈕的狀態。</span><span class="sxs-lookup"><span data-stu-id="36da2-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="36da2-104">本主題提供如何從滑鼠事件取得此資訊的詳細說明，並說明在 Windows Form 控制項中引發滑鼠點按事件的順序。</span><span class="sxs-lookup"><span data-stu-id="36da2-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="36da2-105">如需清單和所有滑鼠事件的描述，請參閱 <<c0> [ 滑鼠輸入的運作方式在 Windows Form 中](how-mouse-input-works-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="36da2-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="36da2-106">另請參閱[事件處理常式概觀 (Windows Form)](event-handlers-overview-windows-forms.md)並[事件概觀 (Windows Form)](events-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="36da2-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="36da2-107">滑鼠資訊</span><span class="sxs-lookup"><span data-stu-id="36da2-107">Mouse Information</span></span>

<span data-ttu-id="36da2-108"><xref:System.Windows.Forms.MouseEventArgs> 會傳送至有關點按滑鼠按鈕和追蹤滑鼠移動之滑鼠事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="36da2-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="36da2-109"><xref:System.Windows.Forms.MouseEventArgs> 提供滑鼠目前狀態的相關資訊，包括滑鼠指標在用戶端座標中的位置、按了哪個滑鼠按鈕，以及是否已捲動滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="36da2-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="36da2-110">有幾個滑鼠事件 (例如只是通知滑鼠指標何時進入或離開控制項界限的事件) 會傳送 <xref:System.EventArgs> 至事件處理常式，而沒有進一步的資訊。</span><span class="sxs-lookup"><span data-stu-id="36da2-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="36da2-111">如果您想要知道滑鼠按鈕的目前狀態或滑鼠指標的位置，而且您想要避免處理滑鼠事件，您也可以使用 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.MouseButtons%2A> 和 <xref:System.Windows.Forms.Control.MousePosition%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="36da2-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="36da2-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> 會傳回目前按下哪些滑鼠按鈕的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="36da2-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="36da2-113"><xref:System.Windows.Forms.Control.MousePosition%2A> 會傳回滑鼠指標的螢幕座標，等於 <xref:System.Windows.Forms.Cursor.Position%2A> 所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="36da2-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="36da2-114">在螢幕與用戶端座標之間轉換</span><span class="sxs-lookup"><span data-stu-id="36da2-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="36da2-115">因為有些滑鼠位置資訊是在用戶端座標中，而有些是在螢幕座標中，所以您可能需要將某個點從一個座標系統轉換到另一個座標系統。</span><span class="sxs-lookup"><span data-stu-id="36da2-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="36da2-116">使用 <xref:System.Windows.Forms.Control> 類別中所提供的 <xref:System.Windows.Forms.Control.PointToClient%2A> 和 <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法，可讓您輕鬆執行此作業。</span><span class="sxs-lookup"><span data-stu-id="36da2-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="36da2-117">標準點按事件行為</span><span class="sxs-lookup"><span data-stu-id="36da2-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="36da2-118">如果您想要以適當順序來處理滑鼠點按事件，您需要知道在 Windows Form 控制項中引發點按事件的順序。</span><span class="sxs-lookup"><span data-stu-id="36da2-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="36da2-119">除了下列清單中註明的個別控制項，當按下並放開滑鼠按鈕時 (不論哪一個滑鼠按鈕)，所有 Windows Form 控制項都是以相同順序引發點按事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="36da2-120">以下是針對按一下滑鼠按鈕時，所引發的事件順序：</span><span class="sxs-lookup"><span data-stu-id="36da2-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="36da2-121"><xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="36da2-122"><xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="36da2-123"><xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="36da2-124"><xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="36da2-125">以下是針對按兩下滑鼠按鈕時，所引發的事件順序：</span><span class="sxs-lookup"><span data-stu-id="36da2-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="36da2-126"><xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="36da2-127"><xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="36da2-128"><xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="36da2-129"><xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="36da2-130"><xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="36da2-131"><xref:System.Windows.Forms.Control.DoubleClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="36da2-132">(依據有問題的控制項是否將 <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> 樣式位元設為 `true`，這會有所不同。</span><span class="sxs-lookup"><span data-stu-id="36da2-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="36da2-133">如需有關如何設定 <xref:System.Windows.Forms.ControlStyles> 位元的詳細資訊，請參閱 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法。)</span><span class="sxs-lookup"><span data-stu-id="36da2-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="36da2-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="36da2-135"><xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="36da2-136">程式碼範例，示範滑鼠的順序 click 事件，請參閱[How to:處理使用者輸入事件在 Windows Form 控制項](how-to-handle-user-input-events-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="36da2-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="36da2-137">個別控制項</span><span class="sxs-lookup"><span data-stu-id="36da2-137">Individual Controls</span></span>

<span data-ttu-id="36da2-138">下列控制項不符合標準滑鼠點按事件行為：</span><span class="sxs-lookup"><span data-stu-id="36da2-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="36da2-139"><xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.RadioButton> 控制項</span><span class="sxs-lookup"><span data-stu-id="36da2-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="36da2-140">針對 <xref:System.Windows.Forms.ComboBox> 控制項，如果使用者按一下編輯欄位、按鈕或是清單中的項目，就會發生下述事件行為。</span><span class="sxs-lookup"><span data-stu-id="36da2-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="36da2-141">按一下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-142">以滑鼠右鍵按一下：任何引發的 click 事件</span><span class="sxs-lookup"><span data-stu-id="36da2-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="36da2-143">按兩下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-144">按兩下滑鼠右鍵：任何引發的 click 事件</span><span class="sxs-lookup"><span data-stu-id="36da2-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="36da2-145"><xref:System.Windows.Forms.TextBox>、<xref:System.Windows.Forms.RichTextBox>、<xref:System.Windows.Forms.ListBox>、<xref:System.Windows.Forms.MaskedTextBox> 和 <xref:System.Windows.Forms.CheckedListBox> 控制項</span><span class="sxs-lookup"><span data-stu-id="36da2-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="36da2-146">當使用者在這些控制項內的任何位置按一下，就會發生下述事件行為。</span><span class="sxs-lookup"><span data-stu-id="36da2-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="36da2-147">按一下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-148">以滑鼠右鍵按一下：任何引發的 click 事件</span><span class="sxs-lookup"><span data-stu-id="36da2-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="36da2-149">按兩下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>、<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="36da2-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="36da2-150">按兩下滑鼠右鍵：任何引發的 click 事件</span><span class="sxs-lookup"><span data-stu-id="36da2-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="36da2-151"><xref:System.Windows.Forms.ListView> 控制項</span><span class="sxs-lookup"><span data-stu-id="36da2-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="36da2-152">唯有當使用者按一下 <xref:System.Windows.Forms.ListView> 控制項中的項目，才會發生下述事件行為。</span><span class="sxs-lookup"><span data-stu-id="36da2-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="36da2-153">在控制項上任何其他地方按一下，都會不引發任何事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="36da2-154">如果您想要使用驗證來搭配 <xref:System.Windows.Forms.ListView> 控制項，除了下述事件，您可能也會想要了解 <xref:System.Windows.Forms.ListView.BeforeLabelEdit> 和 <xref:System.Windows.Forms.ListView.AfterLabelEdit> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="36da2-155">按一下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-156">按一下滑鼠右鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-157">按兩下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="36da2-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="36da2-158">按兩下滑鼠右鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="36da2-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="36da2-159"><xref:System.Windows.Forms.TreeView> 控制項</span><span class="sxs-lookup"><span data-stu-id="36da2-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="36da2-160">唯有當使用者按一下 <xref:System.Windows.Forms.TreeView> 控制項中的項目本身，或是項目右邊，才會發生下述事件行為。</span><span class="sxs-lookup"><span data-stu-id="36da2-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="36da2-161">在控制項上任何其他地方按一下，都會不引發任何事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="36da2-162">如果您想要使用驗證來搭配 <xref:System.Windows.Forms.TreeView> 控制項，除了下述事件，您可能也會想要了解 <xref:System.Windows.Forms.TreeView.BeforeCheck>、<xref:System.Windows.Forms.TreeView.BeforeSelect>、<xref:System.Windows.Forms.TreeView.BeforeLabelEdit>、<xref:System.Windows.Forms.TreeView.AfterSelect>、<xref:System.Windows.Forms.TreeView.AfterCheck> 和 <xref:System.Windows.Forms.TreeView.AfterLabelEdit> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="36da2-163">按一下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-164">按一下滑鼠右鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="36da2-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="36da2-165">按兩下滑鼠左鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="36da2-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="36da2-166">按兩下滑鼠右鍵：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="36da2-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="36da2-167">切換控制項的繪製行為</span><span class="sxs-lookup"><span data-stu-id="36da2-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="36da2-168">切換控制項 (例如衍生自 <xref:System.Windows.Forms.ButtonBase> 類別的控制項) 與滑鼠點按事件搭配組合，具有下列特殊繪圖行為：</span><span class="sxs-lookup"><span data-stu-id="36da2-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="36da2-169">使用者按下滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="36da2-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="36da2-170">控制項會以所按下的狀態繪製。</span><span class="sxs-lookup"><span data-stu-id="36da2-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="36da2-171">便會引發 <xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="36da2-172">使用者放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="36da2-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="36da2-173">控制項會以所引發的狀態繪製。</span><span class="sxs-lookup"><span data-stu-id="36da2-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="36da2-174">便會引發 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="36da2-175">便會引發 <xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="36da2-176">便會引發 <xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="36da2-177">如果使用者在按下滑鼠按鈕的同時，將指標移出切換控制項 (例如在按下滑鼠按鈕的同時，將滑鼠從 <xref:System.Windows.Forms.Button> 控制項移開)，切換控制項將會以所引發的狀態繪製，而且只會發生 <xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="36da2-178">在此情況下，不會發生 <xref:System.Windows.Forms.Control.Click> 或 <xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="36da2-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="36da2-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36da2-179">See also</span></span>

- [<span data-ttu-id="36da2-180">Windows Forms 應用程式中的滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="36da2-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
