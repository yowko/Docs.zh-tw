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
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966491"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="107f8-102">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="107f8-102">User-Drawn Controls</span></span>
<span data-ttu-id="107f8-103">.NET Framework 提供您輕鬆開發自己的控制項的能力。</span><span class="sxs-lookup"><span data-stu-id="107f8-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="107f8-104">您可以建立一個使用者控制項, 這是一組由程式碼系結在一起的標準控制項, 您也可以從頭開始設計自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="107f8-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="107f8-105">您甚至可以使用繼承來建立繼承自現有控制項的控制項, 並加入其固有的功能。</span><span class="sxs-lookup"><span data-stu-id="107f8-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="107f8-106">無論您使用哪種方法, .NET Framework 都會提供功能, 為您所建立的任何控制項繪製自訂的圖形化介面。</span><span class="sxs-lookup"><span data-stu-id="107f8-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="107f8-107">控制項的繪製是藉由在控制項的<xref:System.Windows.Forms.Control.OnPaint%2A>方法中執行程式碼來完成。</span><span class="sxs-lookup"><span data-stu-id="107f8-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="107f8-108"><xref:System.Windows.Forms.Control.OnPaint%2A>方法的單一引數<xref:System.Windows.Forms.PaintEventArgs>是物件, 可提供呈現控制項所需的所有資訊和功能。</span><span class="sxs-lookup"><span data-stu-id="107f8-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="107f8-109">會<xref:System.Windows.Forms.PaintEventArgs>提供兩個主要物件的屬性, 以用於呈現控制項:</span><span class="sxs-lookup"><span data-stu-id="107f8-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="107f8-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件-代表將繪製之控制項部分的矩形。</span><span class="sxs-lookup"><span data-stu-id="107f8-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="107f8-111">這可以是整個控制項, 或是控制項的一部分, 視控制項繪製的方式而定。</span><span class="sxs-lookup"><span data-stu-id="107f8-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="107f8-112"><xref:System.Drawing.Graphics>物件-封裝數個圖形導向的物件和方法, 以提供繪製控制項所需的功能。</span><span class="sxs-lookup"><span data-stu-id="107f8-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="107f8-113">如需<xref:System.Drawing.Graphics>物件和其使用方式的詳細資訊, 請參閱[如何:建立繪圖](../advanced/how-to-create-graphics-objects-for-drawing.md)的繪圖物件。</span><span class="sxs-lookup"><span data-stu-id="107f8-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="107f8-114">每當在螢幕上繪製或重新整理控制項時, 就會引發<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 事件,而物件則代表繪製將會發生的矩形。<xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="107f8-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="107f8-115">如果需要重新整理整個控制項, 則<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>會代表整個控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="107f8-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="107f8-116">不過, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>如果只需要重新整理控制項的一部分, 物件只會代表需要重新繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="107f8-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="107f8-117">例如, 當控制項在使用者介面中由另一個控制項或表單部分遮蔽時, 就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="107f8-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="107f8-118">從<xref:System.Windows.Forms.Control>類別繼承時, 您必須覆<xref:System.Windows.Forms.Control.OnPaint%2A>寫方法, 並在內提供圖形呈現程式碼。</span><span class="sxs-lookup"><span data-stu-id="107f8-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="107f8-119">如果您想要提供自訂的圖形介面給使用者控制項或繼承的控制項, 您也可以藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="107f8-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="107f8-120">範例如下所示:</span><span class="sxs-lookup"><span data-stu-id="107f8-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="107f8-121">上述範例示範如何使用非常簡單的圖形表示來呈現控制項。</span><span class="sxs-lookup"><span data-stu-id="107f8-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="107f8-122">它會呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>基類的方法, 它會<xref:System.Drawing.Pen>建立要繪製的物件, 最後在控制項的<xref:System.Windows.Forms.Control.Location%2A>和<xref:System.Windows.Forms.Control.Size%2A>所決定的矩形中繪製橢圓形。</span><span class="sxs-lookup"><span data-stu-id="107f8-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="107f8-123">雖然大部分的轉譯程式碼會明顯複雜, 但此範例會示範<xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs>物件中包含的物件使用方式。</span><span class="sxs-lookup"><span data-stu-id="107f8-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="107f8-124">請注意, 如果您要繼承的類別已經有圖形化標記法 (例如<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Button>), 而且您不想將該標記法併入轉譯中, 則不應該呼叫基類的<xref:System.Windows.Forms.Control.OnPaint%2A>方法.</span><span class="sxs-lookup"><span data-stu-id="107f8-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="107f8-125">當第一次<xref:System.Windows.Forms.Control.OnPaint%2A>繪製控制項時, 以及每次重新整理時, 控制項的方法中的程式碼就會執行。</span><span class="sxs-lookup"><span data-stu-id="107f8-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="107f8-126">若要確保每次調整控制項的大小時都會重新繪製控制項, 請將下列程式程式碼新增至控制項的函式:</span><span class="sxs-lookup"><span data-stu-id="107f8-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="107f8-127"><xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>使用屬性來執行非矩形的控制項。</span><span class="sxs-lookup"><span data-stu-id="107f8-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107f8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="107f8-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="107f8-129">如何：建立繪圖的繪圖物件</span><span class="sxs-lookup"><span data-stu-id="107f8-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="107f8-130">組成控制項</span><span class="sxs-lookup"><span data-stu-id="107f8-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="107f8-131">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="107f8-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
