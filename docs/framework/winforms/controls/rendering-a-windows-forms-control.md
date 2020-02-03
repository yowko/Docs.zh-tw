---
title: 呈現控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: 0e1a7ca5dc0414d518c081b1db2dca5477d4f743
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742393"
---
# <a name="rendering-a-windows-forms-control"></a><span data-ttu-id="e4fee-102">呈現 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="e4fee-102">Rendering a Windows Forms Control</span></span>
<span data-ttu-id="e4fee-103">呈現是指在使用者畫面上建立視覺表示的程式。</span><span class="sxs-lookup"><span data-stu-id="e4fee-103">Rendering refers to the process of creating a visual representation on a user's screen.</span></span> <span data-ttu-id="e4fee-104">Windows Forms 使用 GDI （新的 Windows 圖形程式庫）來呈現。</span><span class="sxs-lookup"><span data-stu-id="e4fee-104">Windows Forms uses GDI (the new Windows graphics library) for rendering.</span></span> <span data-ttu-id="e4fee-105">提供 GDI 存取的 managed 類別位於 <xref:System.Drawing?displayProperty=nameWithType> 命名空間及其子命名空間中。</span><span class="sxs-lookup"><span data-stu-id="e4fee-105">The managed classes that provide access to GDI are in the <xref:System.Drawing?displayProperty=nameWithType> namespace and its subnamespaces.</span></span>  
  
 <span data-ttu-id="e4fee-106">控制項呈現包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="e4fee-106">The following elements are involved in control rendering:</span></span>  
  
- <span data-ttu-id="e4fee-107">基底類別所提供的繪製功能 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e4fee-107">The drawing functionality provided by the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="e4fee-108">GDI 圖形程式庫的基本元素。</span><span class="sxs-lookup"><span data-stu-id="e4fee-108">The essential elements of the GDI graphics library.</span></span>  
  
- <span data-ttu-id="e4fee-109">繪製區域的幾何。</span><span class="sxs-lookup"><span data-stu-id="e4fee-109">The geometry of the drawing region.</span></span>  
  
- <span data-ttu-id="e4fee-110">釋放圖形資源的程式。</span><span class="sxs-lookup"><span data-stu-id="e4fee-110">The procedure for freeing graphics resources.</span></span>  
  
## <a name="drawing-functionality-provided-by-control"></a><span data-ttu-id="e4fee-111">控制項所提供的繪圖功能</span><span class="sxs-lookup"><span data-stu-id="e4fee-111">Drawing Functionality Provided by Control</span></span>  
 <span data-ttu-id="e4fee-112">基底類別 <xref:System.Windows.Forms.Control> 透過其 <xref:System.Windows.Forms.Control.Paint> 事件提供繪製功能。</span><span class="sxs-lookup"><span data-stu-id="e4fee-112">The base class <xref:System.Windows.Forms.Control> provides drawing functionality through its <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="e4fee-113">每當控制項需要更新其顯示時，就會引發 <xref:System.Windows.Forms.Control.Paint> 事件。</span><span class="sxs-lookup"><span data-stu-id="e4fee-113">A control raises the <xref:System.Windows.Forms.Control.Paint> event whenever it needs to update its display.</span></span> <span data-ttu-id="e4fee-114">如需 .NET Framework 中事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e4fee-114">For more information about events in the .NET Framework, see [Handling and Raising Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="e4fee-115"><xref:System.Windows.Forms.Control.Paint> 事件的事件資料類別，<xref:System.Windows.Forms.PaintEventArgs>會保存繪製控制項所需的資料，也就是繪圖物件的控制碼，以及代表要在其中繪製之區域的矩形物件。</span><span class="sxs-lookup"><span data-stu-id="e4fee-115">The event data class for the <xref:System.Windows.Forms.Control.Paint> event, <xref:System.Windows.Forms.PaintEventArgs>, holds the data needed for drawing a control — a handle to a graphics object and a rectangle object that represents the region to draw in.</span></span> <span data-ttu-id="e4fee-116">這些物件會在下列程式碼片段中以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="e4fee-116">These objects are shown in bold in the following code fragment.</span></span>  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <span data-ttu-id="e4fee-117"><xref:System.Drawing.Graphics> 是封裝繪製功能的 managed 類別，如本主題稍後的 GDI 討論中所述。</span><span class="sxs-lookup"><span data-stu-id="e4fee-117"><xref:System.Drawing.Graphics> is a managed class that encapsulates drawing functionality, as described in the discussion of GDI later in this topic.</span></span> <span data-ttu-id="e4fee-118"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 是 <xref:System.Drawing.Rectangle> 結構的實例，並定義控制項可以在其中繪製的可用區域。</span><span class="sxs-lookup"><span data-stu-id="e4fee-118">The <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is an instance of the <xref:System.Drawing.Rectangle> structure and defines the available area in which a control can draw.</span></span> <span data-ttu-id="e4fee-119">控制項開發人員可以使用控制項的 [<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>] 屬性來計算 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>，如本主題稍後的 geometry 討論中所述。</span><span class="sxs-lookup"><span data-stu-id="e4fee-119">A control developer can compute the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> using the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property of a control, as described in the discussion of geometry later in this topic.</span></span>  
  
 <span data-ttu-id="e4fee-120">控制項必須藉由覆寫繼承自 <xref:System.Windows.Forms.Control>的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，來提供轉譯邏輯。</span><span class="sxs-lookup"><span data-stu-id="e4fee-120">A control must provide rendering logic by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="e4fee-121"><xref:System.Windows.Forms.Control.OnPaint%2A> 取得繪圖物件和矩形的存取權，以透過傳遞給它的 <xref:System.Windows.Forms.PaintEventArgs> 實例的 <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> 和 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性來繪製。</span><span class="sxs-lookup"><span data-stu-id="e4fee-121"><xref:System.Windows.Forms.Control.OnPaint%2A> gets access to a graphics object and a rectangle to draw in through the <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> properties of the <xref:System.Windows.Forms.PaintEventArgs> instance passed to it.</span></span>  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <span data-ttu-id="e4fee-122">基底 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法不會執行任何繪製功能，而只會叫用向 <xref:System.Windows.Forms.Control.Paint> 事件註冊的事件委派。</span><span class="sxs-lookup"><span data-stu-id="e4fee-122">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base <xref:System.Windows.Forms.Control> class does not implement any drawing functionality but merely invokes the event delegates that are registered with the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="e4fee-123">當您覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A>時，通常應該叫用基類的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，讓註冊的委派收到 <xref:System.Windows.Forms.Control.Paint> 事件。</span><span class="sxs-lookup"><span data-stu-id="e4fee-123">When you override <xref:System.Windows.Forms.Control.OnPaint%2A>, you should typically invoke the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class so that registered delegates receive the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="e4fee-124">不過，繪製其整個介面的控制項不應叫用基類的 <xref:System.Windows.Forms.Control.OnPaint%2A>，因為這會引進閃爍。</span><span class="sxs-lookup"><span data-stu-id="e4fee-124">However, controls that paint their entire surface should not invoke the base class's <xref:System.Windows.Forms.Control.OnPaint%2A>, as this introduces flicker.</span></span> <span data-ttu-id="e4fee-125">如需覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件的範例，請參閱[如何：建立顯示進度的 Windows Forms 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="e4fee-125">For an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> event, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4fee-126">請勿直接從控制項叫用 <xref:System.Windows.Forms.Control.OnPaint%2A>;相反地，請叫用 <xref:System.Windows.Forms.Control.Invalidate%2A> 方法（繼承自 <xref:System.Windows.Forms.Control>）或其他會叫用 <xref:System.Windows.Forms.Control.Invalidate%2A>的方法。</span><span class="sxs-lookup"><span data-stu-id="e4fee-126">Do not invoke <xref:System.Windows.Forms.Control.OnPaint%2A> directly from your control; instead, invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method (inherited from <xref:System.Windows.Forms.Control>) or some other method that invokes <xref:System.Windows.Forms.Control.Invalidate%2A>.</span></span> <span data-ttu-id="e4fee-127"><xref:System.Windows.Forms.Control.Invalidate%2A> 方法接著會叫用 <xref:System.Windows.Forms.Control.OnPaint%2A>。</span><span class="sxs-lookup"><span data-stu-id="e4fee-127">The <xref:System.Windows.Forms.Control.Invalidate%2A> method in turn invokes <xref:System.Windows.Forms.Control.OnPaint%2A>.</span></span> <span data-ttu-id="e4fee-128"><xref:System.Windows.Forms.Control.Invalidate%2A> 方法會多載，而且根據提供給 <xref:System.Windows.Forms.Control.Invalidate%2A> `e`的引數，控制項會重新繪製其部分或全部的螢幕區域。</span><span class="sxs-lookup"><span data-stu-id="e4fee-128">The <xref:System.Windows.Forms.Control.Invalidate%2A> method is overloaded, and, depending on the arguments supplied to <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, a control redraws either some or all of its screen area.</span></span>  
  
 <span data-ttu-id="e4fee-129">基底 <xref:System.Windows.Forms.Control> 類別會定義另一個適用于繪製的方法，也就是 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e4fee-129">The base <xref:System.Windows.Forms.Control> class defines another method that is useful for drawing — the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> method.</span></span>  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <span data-ttu-id="e4fee-130"><xref:System.Windows.Forms.Control.OnPaintBackground%2A> 繪製視窗的背景（也就是圖形），而且保證會快速，而 <xref:System.Windows.Forms.Control.OnPaint%2A> 繪製詳細資料，而且可能會變慢，因為個別的繪製要求會合並成一個 <xref:System.Windows.Forms.Control.Paint> 事件，其中涵蓋所有必須重新繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="e4fee-130"><xref:System.Windows.Forms.Control.OnPaintBackground%2A> paints the background (and thereby the shape) of the window and is guaranteed to be fast, while <xref:System.Windows.Forms.Control.OnPaint%2A> paints the details and might be slower because individual paint requests are combined into one <xref:System.Windows.Forms.Control.Paint> event that covers all areas that have to be redrawn.</span></span> <span data-ttu-id="e4fee-131">例如，如果您想要繪製控制項的漸層色彩背景，您可能會想要叫用 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>。</span><span class="sxs-lookup"><span data-stu-id="e4fee-131">You might want to invoke the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> if, for instance, you want to draw a gradient-colored background for your control.</span></span>  
  
 <span data-ttu-id="e4fee-132">雖然 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 具有類似事件的命名法，並採用與 `OnPaint` 方法相同的引數，但 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 不是真正的事件方法。</span><span class="sxs-lookup"><span data-stu-id="e4fee-132">While <xref:System.Windows.Forms.Control.OnPaintBackground%2A> has an event-like nomenclature and takes the same argument as the `OnPaint` method, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> is not a true event method.</span></span> <span data-ttu-id="e4fee-133">沒有 `PaintBackground` 事件，而且 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 不會叫用事件委派。</span><span class="sxs-lookup"><span data-stu-id="e4fee-133">There is no `PaintBackground` event and <xref:System.Windows.Forms.Control.OnPaintBackground%2A> does not invoke event delegates.</span></span> <span data-ttu-id="e4fee-134">覆寫 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 方法時，不需要衍生類別來叫用其基類的 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e4fee-134">When overriding the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> method, a derived class is not required to invoke the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> method of its base class.</span></span>  
  
## <a name="gdi-basics"></a><span data-ttu-id="e4fee-135">GDI + 基本概念</span><span class="sxs-lookup"><span data-stu-id="e4fee-135">GDI+ Basics</span></span>  
 <span data-ttu-id="e4fee-136"><xref:System.Drawing.Graphics> 類別提供繪製各種形狀（例如圓形、三角形、弧形和橢圓形）的方法，以及用來顯示文字的方法。</span><span class="sxs-lookup"><span data-stu-id="e4fee-136">The <xref:System.Drawing.Graphics> class provides methods for drawing various shapes such as circles, triangles, arcs, and ellipses, as well as methods for displaying text.</span></span> <span data-ttu-id="e4fee-137"><xref:System.Drawing?displayProperty=nameWithType> 命名空間及其子命名空間包含的類別會封裝圖形元素，例如圖案（圓形、矩形、弧形等等）、色彩、字型、筆刷等等。</span><span class="sxs-lookup"><span data-stu-id="e4fee-137">The <xref:System.Drawing?displayProperty=nameWithType> namespace and its subnamespaces contain classes that encapsulate graphics elements such as shapes (circles, rectangles, arcs, and others), colors, fonts, brushes, and so on.</span></span> <span data-ttu-id="e4fee-138">如需 GDI 的詳細資訊，請參閱[使用 Managed 圖形類別](../advanced/using-managed-graphics-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="e4fee-138">For more information about GDI, see [Using Managed Graphics Classes](../advanced/using-managed-graphics-classes.md).</span></span> <span data-ttu-id="e4fee-139">GDI 的基本知識也會在[如何：建立顯示進度的 Windows Forms 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)中描述。</span><span class="sxs-lookup"><span data-stu-id="e4fee-139">The essentials of GDI are also described in the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="geometry-of-the-drawing-region"></a><span data-ttu-id="e4fee-140">繪圖區域的幾何</span><span class="sxs-lookup"><span data-stu-id="e4fee-140">Geometry of the Drawing Region</span></span>  
 <span data-ttu-id="e4fee-141">控制項的 [<xref:System.Windows.Forms.Control.ClientRectangle%2A>] 屬性會指定使用者畫面上控制項可用的矩形區域，而 <xref:System.Windows.Forms.PaintEventArgs> 的 [<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>] 屬性則會指定實際繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="e4fee-141">The <xref:System.Windows.Forms.Control.ClientRectangle%2A> property of a control specifies the rectangular region available to the control on the user's screen, while the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property of <xref:System.Windows.Forms.PaintEventArgs> specifies the area that is actually painted.</span></span> <span data-ttu-id="e4fee-142">（請記住，繪製作業是在採用 <xref:System.Windows.Forms.PaintEventArgs> 實例作為其引數的 <xref:System.Windows.Forms.Control.Paint> 事件方法中完成。</span><span class="sxs-lookup"><span data-stu-id="e4fee-142">(Remember that painting is done in the <xref:System.Windows.Forms.Control.Paint> event method that takes a <xref:System.Windows.Forms.PaintEventArgs> instance as its argument).</span></span> <span data-ttu-id="e4fee-143">控制項可能只需要繪製其可用區域的一部分，如同控制項的小部分顯示變更的情況。</span><span class="sxs-lookup"><span data-stu-id="e4fee-143">A control might need to paint only a portion of its available area, as is the case when a small section of the control's display changes.</span></span> <span data-ttu-id="e4fee-144">在這些情況下，控制項開發人員必須計算要在其中繪製的實際矩形，並將其傳遞給 <xref:System.Windows.Forms.Control.Invalidate%2A>。</span><span class="sxs-lookup"><span data-stu-id="e4fee-144">In those situations, a control developer must compute the actual rectangle to draw in and pass that to <xref:System.Windows.Forms.Control.Invalidate%2A>.</span></span> <span data-ttu-id="e4fee-145">採用 <xref:System.Drawing.Rectangle> 或 <xref:System.Drawing.Region> 做為引數之 <xref:System.Windows.Forms.Control.Invalidate%2A> 的多載版本，會使用該引數來產生 <xref:System.Windows.Forms.PaintEventArgs>的 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e4fee-145">The overloaded versions of <xref:System.Windows.Forms.Control.Invalidate%2A> that take a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.Region> as an argument use that argument to generate the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property of <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
 <span data-ttu-id="e4fee-146">下列程式碼片段顯示 `FlashTrackBar` 的自訂控制項如何計算要在中繪製的矩形區域。</span><span class="sxs-lookup"><span data-stu-id="e4fee-146">The following code fragment shows how the `FlashTrackBar` custom control computes the rectangular area to draw in.</span></span> <span data-ttu-id="e4fee-147">`client` 變數表示 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e4fee-147">The `client` variable denotes the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property.</span></span> <span data-ttu-id="e4fee-148">如需完整範例，請參閱[如何：建立顯示進度的 Windows Forms 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="e4fee-148">For a complete sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a><span data-ttu-id="e4fee-149">釋放圖形資源</span><span class="sxs-lookup"><span data-stu-id="e4fee-149">Freeing Graphics Resources</span></span>  
 <span data-ttu-id="e4fee-150">繪圖物件的成本很高，因為它們使用系統資源。</span><span class="sxs-lookup"><span data-stu-id="e4fee-150">Graphics objects are expensive because they use system resources.</span></span> <span data-ttu-id="e4fee-151">這類物件包括 <xref:System.Drawing.Graphics?displayProperty=nameWithType> 類別的實例，以及 <xref:System.Drawing.Brush?displayProperty=nameWithType>、<xref:System.Drawing.Pen?displayProperty=nameWithType>和其他圖形類別的實例。</span><span class="sxs-lookup"><span data-stu-id="e4fee-151">Such objects include instances of the <xref:System.Drawing.Graphics?displayProperty=nameWithType> class as well as instances of <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>, and other graphics classes.</span></span> <span data-ttu-id="e4fee-152">只有在需要時才建立圖形資源，並在您完成使用它之後立即發行，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="e4fee-152">It is important that you create a graphics resource only when you need it and release it soon as you are finished using it.</span></span> <span data-ttu-id="e4fee-153">如果您建立的型別會執行 <xref:System.IDisposable> 介面，請在完成使用時呼叫它的 <xref:System.IDisposable.Dispose%2A> 方法，以便釋放資源。</span><span class="sxs-lookup"><span data-stu-id="e4fee-153">If you create a type that implements the <xref:System.IDisposable> interface, call its <xref:System.IDisposable.Dispose%2A> method when you are finished with it in order to free resources.</span></span>  
  
 <span data-ttu-id="e4fee-154">下列程式碼片段顯示 `FlashTrackBar` 自訂控制項如何建立和釋放 <xref:System.Drawing.Brush> 資源。</span><span class="sxs-lookup"><span data-stu-id="e4fee-154">The following code fragment shows how the `FlashTrackBar` custom control creates and releases a <xref:System.Drawing.Brush> resource.</span></span> <span data-ttu-id="e4fee-155">如需完整的原始程式碼，請參閱[如何：建立顯示進度的 Windows Forms 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="e4fee-155">For the complete source code, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e4fee-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4fee-156">See also</span></span>

- [<span data-ttu-id="e4fee-157">操作說明：建立顯示進度的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e4fee-157">How to: Create a Windows Forms Control That Shows Progress</span></span>](how-to-create-a-windows-forms-control-that-shows-progress.md)
