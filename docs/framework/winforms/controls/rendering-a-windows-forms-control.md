---
title: 呈現 Windows Form 控制項
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
ms.openlocfilehash: 9641b6906bc2acaa525aed6df57f189d39317d35
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614668"
---
# <a name="rendering-a-windows-forms-control"></a><span data-ttu-id="1d2f2-102">呈現 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="1d2f2-102">Rendering a Windows Forms Control</span></span>
<span data-ttu-id="1d2f2-103">轉譯是指使用者的畫面上建立的視覺表示法的程序。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-103">Rendering refers to the process of creating a visual representation on a user's screen.</span></span> <span data-ttu-id="1d2f2-104">Windows Form 使用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]（的新 Windows 圖形程式庫） 進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-104">Windows Forms uses [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (the new Windows graphics library) for rendering.</span></span> <span data-ttu-id="1d2f2-105">Managed 的類別，可提供存取權[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]位於<xref:System.Drawing?displayProperty=nameWithType>命名空間和其子命名空間。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-105">The managed classes that provide access to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] are in the <xref:System.Drawing?displayProperty=nameWithType> namespace and its subnamespaces.</span></span>  
  
 <span data-ttu-id="1d2f2-106">控制項的呈現，需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="1d2f2-106">The following elements are involved in control rendering:</span></span>  
  
- <span data-ttu-id="1d2f2-107">基底類別所提供的繪圖功能<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-107">The drawing functionality provided by the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="1d2f2-108">基本項目[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]圖形程式庫。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-108">The essential elements of the [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] graphics library.</span></span>  
  
- <span data-ttu-id="1d2f2-109">繪圖區域的幾何。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-109">The geometry of the drawing region.</span></span>  
  
- <span data-ttu-id="1d2f2-110">釋放圖形資源的程序。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-110">The procedure for freeing graphics resources.</span></span>  
  
## <a name="drawing-functionality-provided-by-control"></a><span data-ttu-id="1d2f2-111">繪製控制項所提供的功能</span><span class="sxs-lookup"><span data-stu-id="1d2f2-111">Drawing Functionality Provided by Control</span></span>  
 <span data-ttu-id="1d2f2-112">基底類別<xref:System.Windows.Forms.Control>提供的繪圖功能，透過其<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-112">The base class <xref:System.Windows.Forms.Control> provides drawing functionality through its <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="1d2f2-113">控制項會引發<xref:System.Windows.Forms.Control.Paint>每當需要更新其顯示的事件。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-113">A control raises the <xref:System.Windows.Forms.Control.Paint> event whenever it needs to update its display.</span></span> <span data-ttu-id="1d2f2-114">如需.NET Framework 中的事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-114">For more information about events in the .NET Framework, see [Handling and Raising Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="1d2f2-115">事件資料類別<xref:System.Windows.Forms.Control.Paint>事件， <xref:System.Windows.Forms.PaintEventArgs>，保存的控制項繪製所需的資料-圖形物件，表示要在其中繪製區域的矩形物件的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-115">The event data class for the <xref:System.Windows.Forms.Control.Paint> event, <xref:System.Windows.Forms.PaintEventArgs>, holds the data needed for drawing a control — a handle to a graphics object and a rectangle object that represents the region to draw in.</span></span> <span data-ttu-id="1d2f2-116">這些物件會顯示在粗體顯示在下列程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-116">These objects are shown in bold in the following code fragment.</span></span>  
  
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
  
 <span data-ttu-id="1d2f2-117"><xref:System.Drawing.Graphics> 會封裝繪圖功能的 managed 的類別的討論內容所述[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]本主題稍後的。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-117"><xref:System.Drawing.Graphics> is a managed class that encapsulates drawing functionality, as described in the discussion of [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] later in this topic.</span></span> <span data-ttu-id="1d2f2-118"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>的執行個體<xref:System.Drawing.Rectangle>結構，並且定義控制項可在其中繪圖的可用區域。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-118">The <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is an instance of the <xref:System.Drawing.Rectangle> structure and defines the available area in which a control can draw.</span></span> <span data-ttu-id="1d2f2-119">控制項開發人員可以計算<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>使用<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>控制項，如本主題稍後的幾何的討論中所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-119">A control developer can compute the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> using the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property of a control, as described in the discussion of geometry later in this topic.</span></span>  
  
 <span data-ttu-id="1d2f2-120">控制項必須提供轉譯邏輯，藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，它繼承自<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-120">A control must provide rendering logic by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="1d2f2-121"><xref:System.Windows.Forms.Control.OnPaint%2A> 取得存取圖形物件和要透過在其中繪製的矩形<xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A>而<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性的<xref:System.Windows.Forms.PaintEventArgs>傳遞給它的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-121"><xref:System.Windows.Forms.Control.OnPaint%2A> gets access to a graphics object and a rectangle to draw in through the <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> properties of the <xref:System.Windows.Forms.PaintEventArgs> instance passed to it.</span></span>  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <span data-ttu-id="1d2f2-122"><xref:System.Windows.Forms.Control.OnPaint%2A>方法的基底<xref:System.Windows.Forms.Control>類別不會實作任何繪製功能，但是只會叫用事件委派，會向<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-122">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base <xref:System.Windows.Forms.Control> class does not implement any drawing functionality but merely invokes the event delegates that are registered with the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="1d2f2-123">當您覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>，您通常應該叫用<xref:System.Windows.Forms.Control.OnPaint%2A>方法的基底類別，好讓註冊的委派能接收<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-123">When you override <xref:System.Windows.Forms.Control.OnPaint%2A>, you should typically invoke the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class so that registered delegates receive the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="1d2f2-124">不過，繪製其整個介面的控制項不應該叫用基底類別的<xref:System.Windows.Forms.Control.OnPaint%2A>，因為這會引入閃爍。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-124">However, controls that paint their entire surface should not invoke the base class's <xref:System.Windows.Forms.Control.OnPaint%2A>, as this introduces flicker.</span></span> <span data-ttu-id="1d2f2-125">如需範例，會覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>事件，請參閱[How to:建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-125">For an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> event, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d2f2-126">不會叫用<xref:System.Windows.Forms.Control.OnPaint%2A>直接從您的控制項; 相反地，叫用<xref:System.Windows.Forms.Control.Invalidate%2A>方法 (繼承自<xref:System.Windows.Forms.Control>) 或透過其他方法會叫用<xref:System.Windows.Forms.Control.Invalidate%2A>。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-126">Do not invoke <xref:System.Windows.Forms.Control.OnPaint%2A> directly from your control; instead, invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method (inherited from <xref:System.Windows.Forms.Control>) or some other method that invokes <xref:System.Windows.Forms.Control.Invalidate%2A>.</span></span> <span data-ttu-id="1d2f2-127"><xref:System.Windows.Forms.Control.Invalidate%2A>方法會接著叫用<xref:System.Windows.Forms.Control.OnPaint%2A>。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-127">The <xref:System.Windows.Forms.Control.Invalidate%2A> method in turn invokes <xref:System.Windows.Forms.Control.OnPaint%2A>.</span></span> <span data-ttu-id="1d2f2-128"><xref:System.Windows.Forms.Control.Invalidate%2A>多載方法，並根據引數提供給<xref:System.Windows.Forms.Control.Invalidate%2A> `e`，部分或所有其螢幕區域，會重新繪製控制項。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-128">The <xref:System.Windows.Forms.Control.Invalidate%2A> method is overloaded, and, depending on the arguments supplied to <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, a control redraws either some or all of its screen area.</span></span>  
  
 <span data-ttu-id="1d2f2-129">基底<xref:System.Windows.Forms.Control>類別會定義可用於繪圖的另一種方法 —<xref:System.Windows.Forms.Control.OnPaintBackground%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-129">The base <xref:System.Windows.Forms.Control> class defines another method that is useful for drawing — the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> method.</span></span>  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <span data-ttu-id="1d2f2-130"><xref:System.Windows.Forms.Control.OnPaintBackground%2A> 繪製背景 (，因此圖形) 視窗的而且保證會快速完成，同時<xref:System.Windows.Forms.Control.OnPaint%2A>繪製詳細資料，並可能會變慢，因為個別的繪製要求會結合成一個<xref:System.Windows.Forms.Control.Paint>涵蓋一定要的所有區域的事件重新繪製。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-130"><xref:System.Windows.Forms.Control.OnPaintBackground%2A> paints the background (and thereby the shape) of the window and is guaranteed to be fast, while <xref:System.Windows.Forms.Control.OnPaint%2A> paints the details and might be slower because individual paint requests are combined into one <xref:System.Windows.Forms.Control.Paint> event that covers all areas that have to be redrawn.</span></span> <span data-ttu-id="1d2f2-131">您可能想要叫用<xref:System.Windows.Forms.Control.OnPaintBackground%2A>如果，比方說，您想要繪製控制項的漸層色彩背景。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-131">You might want to invoke the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> if, for instance, you want to draw a gradient-colored background for your control.</span></span>  
  
 <span data-ttu-id="1d2f2-132">雖然<xref:System.Windows.Forms.Control.OnPaintBackground%2A>具有類似事件的命名法，而且會採用相同的引數當做`OnPaint`方法，<xref:System.Windows.Forms.Control.OnPaintBackground%2A>不是真正事件的方法。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-132">While <xref:System.Windows.Forms.Control.OnPaintBackground%2A> has an event-like nomenclature and takes the same argument as the `OnPaint` method, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> is not a true event method.</span></span> <span data-ttu-id="1d2f2-133">沒有任何`PaintBackground`事件和<xref:System.Windows.Forms.Control.OnPaintBackground%2A>不叫用事件委派。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-133">There is no `PaintBackground` event and <xref:System.Windows.Forms.Control.OnPaintBackground%2A> does not invoke event delegates.</span></span> <span data-ttu-id="1d2f2-134">當覆寫<xref:System.Windows.Forms.Control.OnPaintBackground%2A>方法，衍生的類別不需要叫用<xref:System.Windows.Forms.Control.OnPaintBackground%2A>其基底類別的方法。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-134">When overriding the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> method, a derived class is not required to invoke the <xref:System.Windows.Forms.Control.OnPaintBackground%2A> method of its base class.</span></span>  
  
## <a name="gdi-basics"></a><span data-ttu-id="1d2f2-135">GDI + 基本概念</span><span class="sxs-lookup"><span data-stu-id="1d2f2-135">GDI+ Basics</span></span>  
 <span data-ttu-id="1d2f2-136"><xref:System.Drawing.Graphics>類別提供方法來繪製各種圖案，例如圓形、 三角形、 弧線和省略符號，以及顯示文字的方法。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-136">The <xref:System.Drawing.Graphics> class provides methods for drawing various shapes such as circles, triangles, arcs, and ellipses, as well as methods for displaying text.</span></span> <span data-ttu-id="1d2f2-137"><xref:System.Drawing?displayProperty=nameWithType>命名空間和其子命名空間包含類別來封裝圖形項目，例如 （圓形、 矩形、 弧線和其他項目） 的圖形、 色彩、 字型、 筆刷等等。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-137">The <xref:System.Drawing?displayProperty=nameWithType> namespace and its subnamespaces contain classes that encapsulate graphics elements such as shapes (circles, rectangles, arcs, and others), colors, fonts, brushes, and so on.</span></span> <span data-ttu-id="1d2f2-138">如需詳細資訊[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]，請參閱 <<c2> [ 使用 Managed 圖形類別](../advanced/using-managed-graphics-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-138">For more information about [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], see [Using Managed Graphics Classes](../advanced/using-managed-graphics-classes.md).</span></span> <span data-ttu-id="1d2f2-139">基本知識[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]也有說明[How to:建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-139">The essentials of [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] are also described in the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="geometry-of-the-drawing-region"></a><span data-ttu-id="1d2f2-140">幾何的繪圖區域</span><span class="sxs-lookup"><span data-stu-id="1d2f2-140">Geometry of the Drawing Region</span></span>  
 <span data-ttu-id="1d2f2-141"><xref:System.Windows.Forms.Control.ClientRectangle%2A>控制項的屬性會指定在使用者的畫面上，控制項可用之矩形區域雖然<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>指定實際繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-141">The <xref:System.Windows.Forms.Control.ClientRectangle%2A> property of a control specifies the rectangular region available to the control on the user's screen, while the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property of <xref:System.Windows.Forms.PaintEventArgs> specifies the area that is actually painted.</span></span> <span data-ttu-id="1d2f2-142">(請記得在中完成繪製<xref:System.Windows.Forms.Control.Paint>採用的事件方法<xref:System.Windows.Forms.PaintEventArgs>作為其引數的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-142">(Remember that painting is done in the <xref:System.Windows.Forms.Control.Paint> event method that takes a <xref:System.Windows.Forms.PaintEventArgs> instance as its argument).</span></span> <span data-ttu-id="1d2f2-143">控制項可能需要繪製只有部分可用的區域中，在此情況下當一小部分的控制項的顯示變更。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-143">A control might need to paint only a portion of its available area, as is the case when a small section of the control's display changes.</span></span> <span data-ttu-id="1d2f2-144">控制項開發人員必須在這些情況下，計算實際的矩形繪製，並傳遞至<xref:System.Windows.Forms.Control.Invalidate%2A>。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-144">In those situations, a control developer must compute the actual rectangle to draw in and pass that to <xref:System.Windows.Forms.Control.Invalidate%2A>.</span></span> <span data-ttu-id="1d2f2-145">多載的版本<xref:System.Windows.Forms.Control.Invalidate%2A>採用<xref:System.Drawing.Rectangle>或是<xref:System.Drawing.Region>做為引數使用該引數來產生<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-145">The overloaded versions of <xref:System.Windows.Forms.Control.Invalidate%2A> that take a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.Region> as an argument use that argument to generate the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property of <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
 <span data-ttu-id="1d2f2-146">下列程式碼片段示範如何`FlashTrackBar`自訂控制項計算要在其中繪製的矩形區域。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-146">The following code fragment shows how the `FlashTrackBar` custom control computes the rectangular area to draw in.</span></span> <span data-ttu-id="1d2f2-147">`client`變數代表<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-147">The `client` variable denotes the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> property.</span></span> <span data-ttu-id="1d2f2-148">如需完整範例，請參閱[How to:建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-148">For a complete sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a><span data-ttu-id="1d2f2-149">釋放圖形資源</span><span class="sxs-lookup"><span data-stu-id="1d2f2-149">Freeing Graphics Resources</span></span>  
 <span data-ttu-id="1d2f2-150">圖形物件很耗費資源，因為它們使用系統資源。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-150">Graphics objects are expensive because they use system resources.</span></span> <span data-ttu-id="1d2f2-151">這類物件包含的執行個體<xref:System.Drawing.Graphics?displayProperty=nameWithType>類別的執行個體及<xref:System.Drawing.Brush?displayProperty=nameWithType>， <xref:System.Drawing.Pen?displayProperty=nameWithType>，和其他圖形類別。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-151">Such objects include instances of the <xref:System.Drawing.Graphics?displayProperty=nameWithType> class as well as instances of <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>, and other graphics classes.</span></span> <span data-ttu-id="1d2f2-152">請務必只有在您需要它，並釋放它時，建立圖形資源因為您使用完畢之後推出。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-152">It is important that you create a graphics resource only when you need it and release it soon as you are finished using it.</span></span> <span data-ttu-id="1d2f2-153">如果您建立的類型可實作<xref:System.IDisposable>介面，請呼叫其<xref:System.IDisposable.Dispose%2A>方法，當您完成時使用它以釋放資源。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-153">If you create a type that implements the <xref:System.IDisposable> interface, call its <xref:System.IDisposable.Dispose%2A> method when you are finished with it in order to free resources.</span></span>  
  
 <span data-ttu-id="1d2f2-154">下列程式碼片段示範如何`FlashTrackBar`建立自訂控制項，並釋放<xref:System.Drawing.Brush>資源。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-154">The following code fragment shows how the `FlashTrackBar` custom control creates and releases a <xref:System.Drawing.Brush> resource.</span></span> <span data-ttu-id="1d2f2-155">如需完整的原始程式碼，請參閱[How to:建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2f2-155">For the complete source code, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1d2f2-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d2f2-156">See also</span></span>

- [<span data-ttu-id="1d2f2-157">如何：建立顯示進度的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="1d2f2-157">How to: Create a Windows Forms Control That Shows Progress</span></span>](how-to-create-a-windows-forms-control-that-shows-progress.md)
