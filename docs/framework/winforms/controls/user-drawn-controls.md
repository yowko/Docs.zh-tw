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
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182015"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="524ac-102">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="524ac-102">User-Drawn Controls</span></span>
<span data-ttu-id="524ac-103">.NET 框架使您能夠輕鬆開發自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="524ac-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="524ac-104">您可以創建使用者控制項，這是一組由代碼綁定在一起的標準控制項，也可以從零開始設計自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="524ac-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="524ac-105">您甚至可以使用繼承創建從現有控制項繼承的控制項，並添加到其固有功能。</span><span class="sxs-lookup"><span data-stu-id="524ac-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="524ac-106">無論您使用何種方法，.NET Framework 都提供了為創建的任何控制項繪製自訂圖形介面的功能。</span><span class="sxs-lookup"><span data-stu-id="524ac-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="524ac-107">控制項的繪製是通過在控制項方法中執行代碼來完成的<xref:System.Windows.Forms.Control.OnPaint%2A>。</span><span class="sxs-lookup"><span data-stu-id="524ac-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="524ac-108"><xref:System.Windows.Forms.Control.OnPaint%2A>方法的單個參數是一個<xref:System.Windows.Forms.PaintEventArgs>物件，該物件提供呈現控制項所需的所有資訊和功能。</span><span class="sxs-lookup"><span data-stu-id="524ac-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="524ac-109">提供<xref:System.Windows.Forms.PaintEventArgs>將在呈現控制項時使用的兩個主體物件作為屬性：</span><span class="sxs-lookup"><span data-stu-id="524ac-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="524ac-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件 - 表示將繪製的控制項部分的矩形。</span><span class="sxs-lookup"><span data-stu-id="524ac-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="524ac-111">這可以是整個控制項，也可以是控制項的一部分，具體取決於控制項的繪製方式。</span><span class="sxs-lookup"><span data-stu-id="524ac-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="524ac-112"><xref:System.Drawing.Graphics>物件 - 封裝多個面向圖形的物件和方法，這些物件和方法提供了繪製控制項所需的功能。</span><span class="sxs-lookup"><span data-stu-id="524ac-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="524ac-113">有關<xref:System.Drawing.Graphics>物件以及如何使用它的詳細資訊，請參閱[如何：為繪圖創建繪圖物件](../advanced/how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="524ac-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="524ac-114">每當<xref:System.Windows.Forms.Control.OnPaint%2A>在螢幕上繪製或刷新控制項時，都會觸發該事件，並且<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件表示將在其中進行繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="524ac-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="524ac-115">如果需要刷新整個控制項，將<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>表示整個控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="524ac-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="524ac-116">但是，如果只需要刷新控制項的一部分，則<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件將僅表示需要重繪的區域。</span><span class="sxs-lookup"><span data-stu-id="524ac-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="524ac-117">這種情況的一個示例是，當控制項被使用者介面中的另一個控制項或表單部分遮蓋時。</span><span class="sxs-lookup"><span data-stu-id="524ac-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="524ac-118">從<xref:System.Windows.Forms.Control>類繼承時，必須重寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法並在 其中提供圖形呈現代碼。</span><span class="sxs-lookup"><span data-stu-id="524ac-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="524ac-119">如果要向使用者控制項或繼承的控制項提供自訂圖形介面，還可以重寫<xref:System.Windows.Forms.Control.OnPaint%2A>該方法。</span><span class="sxs-lookup"><span data-stu-id="524ac-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="524ac-120">範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="524ac-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="524ac-121">前面的示例演示如何使用非常簡單的圖形表示形式呈現控制項。</span><span class="sxs-lookup"><span data-stu-id="524ac-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="524ac-122">它調用基<xref:System.Windows.Forms.Control.OnPaint%2A>類的方法，它創建一個<xref:System.Drawing.Pen>要用來繪製的物件，最後在由 和<xref:System.Windows.Forms.Control.Location%2A><xref:System.Windows.Forms.Control.Size%2A>的 控制項確定的矩形中繪製橢圓。</span><span class="sxs-lookup"><span data-stu-id="524ac-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="524ac-123">儘管大多數呈現代碼將明顯比這更複雜，但此示例演示了<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>物件中包含的物件的使用。</span><span class="sxs-lookup"><span data-stu-id="524ac-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="524ac-124">請注意，如果要從已具有圖形表示形式（如<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Button>）的類繼承，並且不希望將該表示形式合併到渲染中，則不應調用基類<xref:System.Windows.Forms.Control.OnPaint%2A>的方法。</span><span class="sxs-lookup"><span data-stu-id="524ac-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="524ac-125">控制項方法中<xref:System.Windows.Forms.Control.OnPaint%2A>的代碼將在首次繪製控制項時以及刷新控制項時執行。</span><span class="sxs-lookup"><span data-stu-id="524ac-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="524ac-126">為確保每次調整控制項大小時重新繪製控制項，請向控制項的建構函式添加以下行：</span><span class="sxs-lookup"><span data-stu-id="524ac-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="524ac-127">使用<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>屬性實現非矩形控制項。</span><span class="sxs-lookup"><span data-stu-id="524ac-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524ac-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="524ac-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="524ac-129">如何：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="524ac-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="524ac-130">組成控制項</span><span class="sxs-lookup"><span data-stu-id="524ac-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="524ac-131">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="524ac-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
