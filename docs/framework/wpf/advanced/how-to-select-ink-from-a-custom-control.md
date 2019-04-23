---
title: HOW TO：從自訂控制項選取筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 5c9b2f3d64e4cbb309772d6a1d9fa88f589df84c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173588"
---
# <a name="how-to-select-ink-from-a-custom-control"></a><span data-ttu-id="e42ba-102">HOW TO：從自訂控制項選取筆墨</span><span class="sxs-lookup"><span data-stu-id="e42ba-102">How to: Select Ink from a Custom Control</span></span>
<span data-ttu-id="e42ba-103">藉由新增<xref:System.Windows.Ink.IncrementalLassoHitTester>若您的自訂控制項，您可以啟用您的控制項，讓使用者可以選取使用套索工具，其方式類似於筆墨<xref:System.Windows.Controls.InkCanvas>選取使用套索的筆墨。</span><span class="sxs-lookup"><span data-stu-id="e42ba-103">By adding an <xref:System.Windows.Ink.IncrementalLassoHitTester> to your custom control, you can enable your control so that a user can select ink with a lasso tool, similar to the way the <xref:System.Windows.Controls.InkCanvas> selects ink with a lasso.</span></span>  
  
 <span data-ttu-id="e42ba-104">這個範例假設您熟悉建立具備筆墨功能的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="e42ba-104">This example assumes you are familiar with creating an ink-enabled custom control.</span></span>  <span data-ttu-id="e42ba-105">若要建立接受筆跡輸入的自訂控制項，請參閱[建立筆墨輸入控制項](creating-an-ink-input-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e42ba-105">To create a custom control that accepts ink input, see [Creating an Ink Input Control](creating-an-ink-input-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e42ba-106">範例</span><span class="sxs-lookup"><span data-stu-id="e42ba-106">Example</span></span>  
 <span data-ttu-id="e42ba-107">當使用者繪製套索，<xref:System.Windows.Ink.IncrementalLassoHitTester>預測哪些筆劃套索路徑界限內完成後會使用者套索。</span><span class="sxs-lookup"><span data-stu-id="e42ba-107">When the user draws a lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> predicts which strokes will be within the lasso path's boundaries after the user completes the lasso.</span></span>  <span data-ttu-id="e42ba-108">判斷被套索路徑界限內的筆劃可以視為被選取。</span><span class="sxs-lookup"><span data-stu-id="e42ba-108">Strokes that are determined to be within the lasso path's boundaries can be thought of as being selected.</span></span>  <span data-ttu-id="e42ba-109">選取的筆劃可能也會變成未選取。</span><span class="sxs-lookup"><span data-stu-id="e42ba-109">Selected strokes can also become unselected.</span></span>  <span data-ttu-id="e42ba-110">例如，如果使用者會反轉繪製套索，時的方向<xref:System.Windows.Ink.IncrementalLassoHitTester>可能取消選取一些筆劃。</span><span class="sxs-lookup"><span data-stu-id="e42ba-110">For example, if the user reverses direction while drawing the lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> may unselect some strokes.</span></span>  
  
 <span data-ttu-id="e42ba-111"><xref:System.Windows.Ink.IncrementalLassoHitTester>引發<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，可讓您的自訂控制項，以回應使用者繪製套索時。</span><span class="sxs-lookup"><span data-stu-id="e42ba-111">The <xref:System.Windows.Ink.IncrementalLassoHitTester> raises the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, which enables your custom control to respond while the user is drawing the lasso.</span></span>  <span data-ttu-id="e42ba-112">例如，您可以變更筆劃的外觀，當使用者選取，並取消選取它們。</span><span class="sxs-lookup"><span data-stu-id="e42ba-112">For example, you can change the appearance of strokes as the user selects and unselects them.</span></span>  
  
## <a name="managing-the-ink-mode"></a><span data-ttu-id="e42ba-113">管理筆墨模式</span><span class="sxs-lookup"><span data-stu-id="e42ba-113">Managing the Ink Mode</span></span>  
 <span data-ttu-id="e42ba-114">如果套索出現不同於您的控制項上的筆墨，它是很有幫助使用者。</span><span class="sxs-lookup"><span data-stu-id="e42ba-114">It is helpful to the user if the lasso appears differently than the ink on your control.</span></span> <span data-ttu-id="e42ba-115">若要這麼做，您的自訂控制項必須追蹤的使用者是撰寫的還是選取筆墨。</span><span class="sxs-lookup"><span data-stu-id="e42ba-115">To accomplish this, your custom control must keep track of whether the user is writing or selecting ink.</span></span> <span data-ttu-id="e42ba-116">若要這樣做最簡單的方式是將宣告含有兩個值的列舉類型： 一個用來表示使用者正在寫入筆跡，一個用來指出使用者已選取筆墨。</span><span class="sxs-lookup"><span data-stu-id="e42ba-116">The easiest way to do this is to declare an enumeration with two values: one to indicate that the user is writing ink and one to indicate that the user is selecting ink.</span></span>  
  
 [!code-csharp[HowToSelectInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 <span data-ttu-id="e42ba-117">接下來，新增兩個<xref:System.Windows.Ink.DrawingAttributes>至類別： 一個用來使用時，使用者撰寫的墨水，使用使用者選取的筆墨另一個。</span><span class="sxs-lookup"><span data-stu-id="e42ba-117">Next, add two <xref:System.Windows.Ink.DrawingAttributes> to the class: one to use when the user writes ink, one to use when the user selects ink.</span></span>  <span data-ttu-id="e42ba-118">在建構函式，初始化<xref:System.Windows.Ink.DrawingAttributes>，並附加兩者<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>至相同的事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="e42ba-118">In the constructor, initialize the <xref:System.Windows.Ink.DrawingAttributes> and attach both <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> events to the same event handler.</span></span> <span data-ttu-id="e42ba-119">然後設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>的屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至筆墨<xref:System.Windows.Ink.DrawingAttributes>。</span><span class="sxs-lookup"><span data-stu-id="e42ba-119">Then set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the ink <xref:System.Windows.Ink.DrawingAttributes>.</span></span>  
  
 [!code-csharp[HowToSelectInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 <span data-ttu-id="e42ba-120">新增屬性來公開的選取模式。</span><span class="sxs-lookup"><span data-stu-id="e42ba-120">Add a property that exposes the selection mode.</span></span> <span data-ttu-id="e42ba-121">當使用者變更選取模式，設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>的屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>適當<xref:System.Windows.Ink.DrawingAttributes>物件，並再重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>屬性設<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="e42ba-121">When the user changes the selection mode, set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the appropriate <xref:System.Windows.Ink.DrawingAttributes> object and then reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> Property to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#5](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <span data-ttu-id="e42ba-122">公開 （expose)<xref:System.Windows.Ink.DrawingAttributes>為屬性，因此應用程式可以判斷筆墨筆劃及選取筆劃的外觀。</span><span class="sxs-lookup"><span data-stu-id="e42ba-122">Expose the <xref:System.Windows.Ink.DrawingAttributes> as properties so applications can determine the appearance of the ink strokes and selection strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#6](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <span data-ttu-id="e42ba-123">當屬性<xref:System.Windows.Ink.DrawingAttributes>物件的變更，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>必須再重新附加至<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="e42ba-123">When a property of a <xref:System.Windows.Ink.DrawingAttributes> object changes, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> must be reattached to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="e42ba-124">中的事件處理常式<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>事件時，重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>至<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="e42ba-124">In the event handler for the <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> event, reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#7](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a><span data-ttu-id="e42ba-125">使用 IncrementalLassoHitTester</span><span class="sxs-lookup"><span data-stu-id="e42ba-125">Using the IncrementalLassoHitTester</span></span>  
 <span data-ttu-id="e42ba-126">建立並初始化<xref:System.Windows.Ink.StrokeCollection>，其中包含所選取的筆劃。</span><span class="sxs-lookup"><span data-stu-id="e42ba-126">Create and initialize a <xref:System.Windows.Ink.StrokeCollection> that contains the selected strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#8](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 <span data-ttu-id="e42ba-127">當使用者開始所繪製的筆劃時，筆墨或套索，取消選取任何選取的筆劃。</span><span class="sxs-lookup"><span data-stu-id="e42ba-127">When the user starts to draw a stroke, either ink or the lasso, unselect any selected strokes.</span></span> <span data-ttu-id="e42ba-128">然後，如果使用者繪製套索，建立<xref:System.Windows.Ink.IncrementalLassoHitTester>藉由呼叫<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>，訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，並呼叫<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>。</span><span class="sxs-lookup"><span data-stu-id="e42ba-128">Then, if the user is drawing a lasso, create an <xref:System.Windows.Ink.IncrementalLassoHitTester> by calling <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subscribe to the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, and call <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span></span> <span data-ttu-id="e42ba-129">此程式碼可以是另一個方法，並從呼叫<xref:System.Windows.UIElement.OnStylusDown%2A>和<xref:System.Windows.UIElement.OnMouseDown%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e42ba-129">This code can be a separate method and called from the <xref:System.Windows.UIElement.OnStylusDown%2A> and <xref:System.Windows.UIElement.OnMouseDown%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#9](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 <span data-ttu-id="e42ba-130">新增到的手寫筆點<xref:System.Windows.Ink.IncrementalLassoHitTester>使用者繪製套索時。</span><span class="sxs-lookup"><span data-stu-id="e42ba-130">Add the stylus points to the <xref:System.Windows.Ink.IncrementalLassoHitTester> while the user draws the lasso.</span></span>  <span data-ttu-id="e42ba-131">呼叫下列方法從<xref:System.Windows.UIElement.OnStylusMove%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>， <xref:System.Windows.UIElement.OnMouseMove%2A>，和<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e42ba-131">Call the following method from the <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, and <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 <span data-ttu-id="e42ba-132">處理<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>事件以回應使用者選取，然後取消選取的筆劃。</span><span class="sxs-lookup"><span data-stu-id="e42ba-132">Handle the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> event to respond when the user selects and unselects strokes.</span></span>  <span data-ttu-id="e42ba-133"><xref:System.Windows.Ink.LassoSelectionChangedEventArgs>類別具有<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>和<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>已選取取得筆劃的內容，然後將其取消選取，分別。</span><span class="sxs-lookup"><span data-stu-id="e42ba-133">The <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> class has the <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> and <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> properties that get the strokes that were selected and unselected, respectively.</span></span>  
  
 [!code-csharp[HowToSelectInk#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 <span data-ttu-id="e42ba-134">當使用者完成繪製套索時，取消訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，並呼叫<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>。</span><span class="sxs-lookup"><span data-stu-id="e42ba-134">When the user finishes drawing the lasso, unsubscribe from the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event and call <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span></span>  
  
 [!code-csharp[HowToSelectInk#12](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a><span data-ttu-id="e42ba-135">加以整合。</span><span class="sxs-lookup"><span data-stu-id="e42ba-135">Putting it All Together.</span></span>  
 <span data-ttu-id="e42ba-136">下列範例是自訂的控制項，可讓使用者使用套索選取筆墨。</span><span class="sxs-lookup"><span data-stu-id="e42ba-136">The following example is a custom control that enables a user to select ink with a lasso.</span></span>  
  
 [!code-csharp[HowToSelectInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e42ba-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e42ba-137">See also</span></span>

- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [<span data-ttu-id="e42ba-138">建立筆墨輸入控制項</span><span class="sxs-lookup"><span data-stu-id="e42ba-138">Creating an Ink Input Control</span></span>](creating-an-ink-input-control.md)
