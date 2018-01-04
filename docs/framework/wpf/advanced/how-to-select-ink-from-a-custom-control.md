---
title: "如何：從自訂控制項選取筆墨"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 972ece6964d1f3cc42c6221c3b18336e3353bc18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-ink-from-a-custom-control"></a><span data-ttu-id="4c7bd-102">如何：從自訂控制項選取筆墨</span><span class="sxs-lookup"><span data-stu-id="4c7bd-102">How to: Select Ink from a Custom Control</span></span>
<span data-ttu-id="4c7bd-103">藉由新增<xref:System.Windows.Ink.IncrementalLassoHitTester>若您的自訂控制項，您可以啟用您的控制項，讓使用者可以選取使用套索工具，其方式類似於筆墨<xref:System.Windows.Controls.InkCanvas>選取使用套索的筆墨。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-103">By adding an <xref:System.Windows.Ink.IncrementalLassoHitTester> to your custom control, you can enable your control so that a user can select ink with a lasso tool, similar to the way the <xref:System.Windows.Controls.InkCanvas> selects ink with a lasso.</span></span>  
  
 <span data-ttu-id="4c7bd-104">這個範例假設您已熟悉如何建立已啟用筆墨的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-104">This example assumes you are familiar with creating an ink-enabled custom control.</span></span>  <span data-ttu-id="4c7bd-105">若要建立接受筆跡輸入的自訂控制項，請參閱[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-105">To create a custom control that accepts ink input, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7bd-106">範例</span><span class="sxs-lookup"><span data-stu-id="4c7bd-106">Example</span></span>  
 <span data-ttu-id="4c7bd-107">當使用者繪製套索，<xref:System.Windows.Ink.IncrementalLassoHitTester>預測套索使用者後，將會在套索路徑的界限內的筆劃。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-107">When the user draws a lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> predicts which strokes will be within the lasso path's boundaries after the user completes the lasso.</span></span>  <span data-ttu-id="4c7bd-108">判斷套索路徑的界限內的筆劃可以視為被選取。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-108">Strokes that are determined to be within the lasso path's boundaries can be thought of as being selected.</span></span>  <span data-ttu-id="4c7bd-109">選取的筆劃可能也會變成未選取。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-109">Selected strokes can also become unselected.</span></span>  <span data-ttu-id="4c7bd-110">例如，如果使用者反轉方向繪製套索時<xref:System.Windows.Ink.IncrementalLassoHitTester>可以取消選取一些筆劃。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-110">For example, if the user reverses direction while drawing the lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> may unselect some strokes.</span></span>  
  
 <span data-ttu-id="4c7bd-111"><xref:System.Windows.Ink.IncrementalLassoHitTester>引發<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，可讓您自訂控制項，以回應使用者繪製套索時。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-111">The <xref:System.Windows.Ink.IncrementalLassoHitTester> raises the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, which enables your custom control to respond while the user is drawing the lasso.</span></span>  <span data-ttu-id="4c7bd-112">例如，您可以變更筆劃的外觀，當使用者選取並取消選取。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-112">For example, you can change the appearance of strokes as the user selects and unselects them.</span></span>  
  
## <a name="managing-the-ink-mode"></a><span data-ttu-id="4c7bd-113">管理筆墨模式</span><span class="sxs-lookup"><span data-stu-id="4c7bd-113">Managing the Ink Mode</span></span>  
 <span data-ttu-id="4c7bd-114">如果套索方式不同於您的控制項上的筆墨出現時，就會很有幫助使用者。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-114">It is helpful to the user if the lasso appears differently than the ink on your control.</span></span> <span data-ttu-id="4c7bd-115">若要完成此動作，自訂控制項必須持續追蹤的使用者是寫入，或選取筆墨。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-115">To accomplish this, your custom control must keep track of whether the user is writing or selecting ink.</span></span> <span data-ttu-id="4c7bd-116">若要這樣做最簡單的方式是宣告的列舉，具有兩個值： 一個用來表示使用者正在寫入筆跡和一個用來表示使用者選取的筆墨。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-116">The easiest way to do this is to declare an enumeration with two values: one to indicate that the user is writing ink and one to indicate that the user is selecting ink.</span></span>  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 <span data-ttu-id="4c7bd-117">接下來，加入兩個<xref:System.Windows.Ink.DrawingAttributes>類別： 時，使用者撰寫的墨水，一個使用使用者選取的筆墨時所要使用其中一個。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-117">Next, add two <xref:System.Windows.Ink.DrawingAttributes> to the class: one to use when the user writes ink, one to use when the user selects ink.</span></span>  <span data-ttu-id="4c7bd-118">在建構函式，初始化<xref:System.Windows.Ink.DrawingAttributes>和附加兩者<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>至相同的事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-118">In the constructor, initialize the <xref:System.Windows.Ink.DrawingAttributes> and attach both <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> events to the same event handler.</span></span> <span data-ttu-id="4c7bd-119">然後設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至筆墨<xref:System.Windows.Ink.DrawingAttributes>。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-119">Then set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the ink <xref:System.Windows.Ink.DrawingAttributes>.</span></span>  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 <span data-ttu-id="4c7bd-120">加入屬性，以便公開選取模式。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-120">Add a property that exposes the selection mode.</span></span> <span data-ttu-id="4c7bd-121">當使用者變更選取模式，設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>適當<xref:System.Windows.Ink.DrawingAttributes>物件，然後重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>屬性<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-121">When the user changes the selection mode, set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the appropriate <xref:System.Windows.Ink.DrawingAttributes> object and then reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> Property to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <span data-ttu-id="4c7bd-122">公開<xref:System.Windows.Ink.DrawingAttributes>做為屬性，因此應用程式可以判斷筆墨筆劃與選取項目筆劃的外觀。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-122">Expose the <xref:System.Windows.Ink.DrawingAttributes> as properties so applications can determine the appearance of the ink strokes and selection strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <span data-ttu-id="4c7bd-123">當屬性<xref:System.Windows.Ink.DrawingAttributes>物件變更，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>必須重新附加至<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-123">When a property of a <xref:System.Windows.Ink.DrawingAttributes> object changes, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> must be reattached to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="4c7bd-124">中的事件處理常式<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>事件時，重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>至<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-124">In the event handler for the <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> event, reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a><span data-ttu-id="4c7bd-125">使用 IncrementalLassoHitTester</span><span class="sxs-lookup"><span data-stu-id="4c7bd-125">Using the IncrementalLassoHitTester</span></span>  
 <span data-ttu-id="4c7bd-126">建立和初始化<xref:System.Windows.Ink.StrokeCollection>，其中包含所選取的筆劃。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-126">Create and initialize a <xref:System.Windows.Ink.StrokeCollection> that contains the selected strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 <span data-ttu-id="4c7bd-127">當使用者開始繪製的筆劃時，墨水或套索，取消選取任何選取的筆劃。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-127">When the user starts to draw a stroke, either ink or the lasso, unselect any selected strokes.</span></span> <span data-ttu-id="4c7bd-128">然後，如果使用者繪製套索，建立<xref:System.Windows.Ink.IncrementalLassoHitTester>藉由呼叫<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>，訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件和呼叫<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-128">Then, if the user is drawing a lasso, create an <xref:System.Windows.Ink.IncrementalLassoHitTester> by calling <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subscribe to the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, and call <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span></span> <span data-ttu-id="4c7bd-129">這個程式碼可以是不同的方法，並從呼叫<xref:System.Windows.UIElement.OnStylusDown%2A>和<xref:System.Windows.UIElement.OnMouseDown%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-129">This code can be a separate method and called from the <xref:System.Windows.UIElement.OnStylusDown%2A> and <xref:System.Windows.UIElement.OnMouseDown%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 <span data-ttu-id="4c7bd-130">將手寫筆指向<xref:System.Windows.Ink.IncrementalLassoHitTester>使用者繪製套索時。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-130">Add the stylus points to the <xref:System.Windows.Ink.IncrementalLassoHitTester> while the user draws the lasso.</span></span>  <span data-ttu-id="4c7bd-131">呼叫下列方法，從<xref:System.Windows.UIElement.OnStylusMove%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>， <xref:System.Windows.UIElement.OnMouseMove%2A>，和<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-131">Call the following method from the <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, and <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 <span data-ttu-id="4c7bd-132">處理<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>時使用者會選取並取消選取筆劃回應事件。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-132">Handle the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> event to respond when the user selects and unselects strokes.</span></span>  <span data-ttu-id="4c7bd-133"><xref:System.Windows.Ink.LassoSelectionChangedEventArgs>類別具有<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>和<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>選取而且未選取，分別取得 strokes 屬性。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-133">The <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> class has the <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> and <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> properties that get the strokes that were selected and unselected, respectively.</span></span>  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 <span data-ttu-id="4c7bd-134">當使用者完成繪製套索時，取消訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件和呼叫<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-134">When the user finishes drawing the lasso, unsubscribe from the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event and call <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span></span>  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a><span data-ttu-id="4c7bd-135">加以整合。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-135">Putting it All Together.</span></span>  
 <span data-ttu-id="4c7bd-136">下列範例是可讓使用者使用套索選取筆墨的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4c7bd-136">The following example is a custom control that enables a user to select ink with a lasso.</span></span>  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4c7bd-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c7bd-137">See Also</span></span>  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [<span data-ttu-id="4c7bd-138">建立筆墨輸入控制項</span><span class="sxs-lookup"><span data-stu-id="4c7bd-138">Creating an Ink Input Control</span></span>](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
