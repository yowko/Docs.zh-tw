---
title: 使用者自訂描繪控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 26b4f062c120bf543a5e597fc8c734e8cc336bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542193"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="135e6-102">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="135e6-102">User-Drawn Controls</span></span>
<span data-ttu-id="135e6-103">.NET Framework 會提供您能夠輕鬆地開發您自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="135e6-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="135e6-104">您可以建立使用者控制項，也就是一組標準的控制項繫結在一起的程式碼，或您可以設計自己的控制項，從頭組成。</span><span class="sxs-lookup"><span data-stu-id="135e6-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="135e6-105">您甚至可以使用繼承建立繼承自現有的控制項的控制項，並將新增到其繼承的功能。</span><span class="sxs-lookup"><span data-stu-id="135e6-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="135e6-106">方法使用時，.NET Framework 提供的功能，以繪製自訂的圖形化介面，任何您所建立的控制項。</span><span class="sxs-lookup"><span data-stu-id="135e6-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="135e6-107">繪製控制項的作業透過在控制項的程式碼執行<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="135e6-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="135e6-108">單一引數<xref:System.Windows.Forms.Control.OnPaint%2A>方法<xref:System.Windows.Forms.PaintEventArgs>物件，提供的所有資訊和轉譯控制項時所需的功能。</span><span class="sxs-lookup"><span data-stu-id="135e6-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="135e6-109"><xref:System.Windows.Forms.PaintEventArgs>做為屬性提供將用於程式控制項的呈現的兩個主要物件：</span><span class="sxs-lookup"><span data-stu-id="135e6-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="135e6-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 物件的矩形，表示要繪製之控制項的一部分。</span><span class="sxs-lookup"><span data-stu-id="135e6-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="135e6-111">這可以是整個控制項或根據如何繪製控制項的控制項的一部分。</span><span class="sxs-lookup"><span data-stu-id="135e6-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="135e6-112"><xref:System.Drawing.Graphics> 物件-封裝數個圖形導向的物件和方法，提供繪製控制項所需的功能。</span><span class="sxs-lookup"><span data-stu-id="135e6-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="135e6-113">如需有關<xref:System.Drawing.Graphics>物件，以及如何使用它，請參閱[How to： 建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="135e6-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="135e6-114"><xref:System.Windows.Forms.Control.OnPaint%2A>繪製或重新整理在畫面上，控制項時引發事件和<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件都代表在其中繪製，就會進行的矩形。</span><span class="sxs-lookup"><span data-stu-id="135e6-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="135e6-115">如果需要重新整理整個控制項<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>將代表整個控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="135e6-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="135e6-116">如果只有部分控制項需要重新整理，不過，<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件將代表需要重新繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="135e6-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="135e6-117">這種情況的範例狀況是當控制項已部分遮蔽其他控制項或表單中的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="135e6-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="135e6-118">繼承自<xref:System.Windows.Forms.Control>類別，您必須覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法並提供圖形轉譯程式碼中的。</span><span class="sxs-lookup"><span data-stu-id="135e6-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="135e6-119">如果您想要提供自訂的圖形化介面，以使用者控制項或繼承的控制項，您也可以執行，藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="135e6-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="135e6-120">範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="135e6-120">An example is shown below:</span></span>  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 <span data-ttu-id="135e6-121">上述範例示範如何呈現控制項，以非常簡單的圖形表示法。</span><span class="sxs-lookup"><span data-stu-id="135e6-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="135e6-122">它會呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>基底類別的方法，它會建立<xref:System.Drawing.Pen>物件用來繪製，而最後的橢圓形的矩形中繪製取決於<xref:System.Windows.Forms.Control.Location%2A>和<xref:System.Windows.Forms.Control.Size%2A>的控制項。</span><span class="sxs-lookup"><span data-stu-id="135e6-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="135e6-123">雖然大部分的轉譯程式碼將會明顯比這更複雜，但是這個範例示範如何使用<xref:System.Drawing.Graphics>物件內含<xref:System.Windows.Forms.PaintEventArgs>物件。</span><span class="sxs-lookup"><span data-stu-id="135e6-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="135e6-124">請注意，如果您繼承自類別已有的圖形表示法，例如<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Button>，而且您不想要併入您呈現的表示法，您不應該呼叫基底類別的<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="135e6-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="135e6-125">中的程式碼<xref:System.Windows.Forms.Control.OnPaint%2A>第一次繪製控制項時，以及重新整理時，將執行控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="135e6-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="135e6-126">若要確保每次會調整大小重繪控制項，加入下列控制項的建構函式：</span><span class="sxs-lookup"><span data-stu-id="135e6-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="135e6-127">使用<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>實作非矩形控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="135e6-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="135e6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="135e6-128">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [<span data-ttu-id="135e6-129">操作說明：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="135e6-129">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="135e6-130">組成控制項</span><span class="sxs-lookup"><span data-stu-id="135e6-130">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [<span data-ttu-id="135e6-131">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="135e6-131">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
