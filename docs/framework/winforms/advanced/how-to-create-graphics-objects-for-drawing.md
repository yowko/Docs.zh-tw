---
title: 如何：建立繪製的圖形物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142429"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="82564-102">如何：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="82564-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="82564-103">在使用 GDI+ 繪製線條和形狀、渲染文本或顯示和操作圖像之前，需要創建一個<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="82564-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="82564-104">該<xref:System.Drawing.Graphics>物件表示 GDI+ 繪圖表面，是用於創建圖形圖像的物件。</span><span class="sxs-lookup"><span data-stu-id="82564-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="82564-105">使用圖形有兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="82564-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="82564-106">創建<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="82564-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="82564-107">使用<xref:System.Drawing.Graphics>物件繪製線條和形狀、渲染文本或顯示和操作圖像。</span><span class="sxs-lookup"><span data-stu-id="82564-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="82564-108">創建繪圖物件</span><span class="sxs-lookup"><span data-stu-id="82564-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="82564-109">繪圖物件可以通過多種方式創建。</span><span class="sxs-lookup"><span data-stu-id="82564-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="82564-110">創建繪圖物件</span><span class="sxs-lookup"><span data-stu-id="82564-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="82564-111">在表單或控制項<xref:System.Windows.Forms.PaintEventArgs><xref:System.Windows.Forms.Control.Paint>的情況下，接收對繪圖物件的引用，作為 的一部分。</span><span class="sxs-lookup"><span data-stu-id="82564-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="82564-112">這通常是在為控制項創建繪製代碼時獲取繪圖物件的引用的方式。</span><span class="sxs-lookup"><span data-stu-id="82564-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="82564-113">同樣，在處理 的事件<xref:System.Drawing.Printing.PrintPageEventArgs>時<xref:System.Drawing.Printing.PrintDocument.PrintPage>，還可以獲取繪圖物件作為<xref:System.Drawing.Printing.PrintDocument>屬性。</span><span class="sxs-lookup"><span data-stu-id="82564-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="82564-114">-或-</span><span class="sxs-lookup"><span data-stu-id="82564-114">-or-</span></span>  
  
- <span data-ttu-id="82564-115">調用控制項<xref:System.Windows.Forms.Control.CreateGraphics%2A>或表單的方法以獲取對表示該控制項或表單的繪圖<xref:System.Drawing.Graphics>表面的物件的引用。</span><span class="sxs-lookup"><span data-stu-id="82564-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="82564-116">如果要在已存在的表單或控制項上繪製，請使用此方法。</span><span class="sxs-lookup"><span data-stu-id="82564-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="82564-117">-或-</span><span class="sxs-lookup"><span data-stu-id="82564-117">-or-</span></span>  
  
- <span data-ttu-id="82564-118">從<xref:System.Drawing.Graphics>繼承的任何<xref:System.Drawing.Image>物件創建物件。</span><span class="sxs-lookup"><span data-stu-id="82564-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="82564-119">當您要更改已有的映射時，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="82564-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="82564-120">以下各節詳細介紹了每個過程。</span><span class="sxs-lookup"><span data-stu-id="82564-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="82564-121">繪製事件處理常式中的繪製事件</span><span class="sxs-lookup"><span data-stu-id="82564-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="82564-122">在程式設計<xref:System.Windows.Forms.PaintEventHandler>控制項 或<xref:System.Drawing.Printing.PrintDocument.PrintPage>的 時<xref:System.Drawing.Printing.PrintDocument>，繪圖物件作為 或<xref:System.Windows.Forms.PaintEventArgs><xref:System.Drawing.Printing.PrintPageEventArgs>的屬性之一提供。</span><span class="sxs-lookup"><span data-stu-id="82564-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="82564-123">從"繪製"事件中的"繪製事件"中獲取對繪圖物件的引用</span><span class="sxs-lookup"><span data-stu-id="82564-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="82564-124">聲明物件<xref:System.Drawing.Graphics>。</span><span class="sxs-lookup"><span data-stu-id="82564-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="82564-125">分配變數以引用作為 的<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>一部分傳遞的物件。</span><span class="sxs-lookup"><span data-stu-id="82564-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="82564-126">插入代碼以繪製表單或控制項。</span><span class="sxs-lookup"><span data-stu-id="82564-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="82564-127">下面的示例演示如何引用<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>事件中<xref:System.Windows.Forms.Control.Paint>的物件：</span><span class="sxs-lookup"><span data-stu-id="82564-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="82564-128">創建圖形方法</span><span class="sxs-lookup"><span data-stu-id="82564-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="82564-129">您還可以使用控制項或表單<xref:System.Windows.Forms.Control.CreateGraphics%2A>的方法來獲取對表示該控制項或表單的繪圖表面<xref:System.Drawing.Graphics>的物件的引用。</span><span class="sxs-lookup"><span data-stu-id="82564-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="82564-130">使用"創建圖形"方法創建繪圖物件</span><span class="sxs-lookup"><span data-stu-id="82564-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="82564-131">調用要<xref:System.Windows.Forms.Control.CreateGraphics%2A>呈現圖形的表單或控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="82564-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="82564-132">從影像物件創建</span><span class="sxs-lookup"><span data-stu-id="82564-132">Create from an Image Object</span></span>  
 <span data-ttu-id="82564-133">此外，還可以從從<xref:System.Drawing.Image>類派生的任何物件創建繪圖物件。</span><span class="sxs-lookup"><span data-stu-id="82564-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="82564-134">從圖像創建繪圖物件</span><span class="sxs-lookup"><span data-stu-id="82564-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="82564-135">調用<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>方法，提供要從中創建<xref:System.Drawing.Graphics>物件的 Image 變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="82564-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="82564-136">下面的示例演示如何使用<xref:System.Drawing.Bitmap>物件：</span><span class="sxs-lookup"><span data-stu-id="82564-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> <span data-ttu-id="82564-137">只能從非索引<xref:System.Drawing.Graphics>的 .bmp 檔創建物件，例如 16 位、24 位和 32 位 .bmp 檔。</span><span class="sxs-lookup"><span data-stu-id="82564-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="82564-138">非索引 .bmp 檔的每個圖元都包含一種顏色，而索引 .bmp 檔的圖元將索引保留到顏色表。</span><span class="sxs-lookup"><span data-stu-id="82564-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="82564-139">繪製和操作形狀和圖像</span><span class="sxs-lookup"><span data-stu-id="82564-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="82564-140">創建物件後，可以使用物件<xref:System.Drawing.Graphics>繪製線條和形狀、渲染文本或顯示和操作圖像。</span><span class="sxs-lookup"><span data-stu-id="82564-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="82564-141">與<xref:System.Drawing.Graphics>物件一起使用的主體物件是：</span><span class="sxs-lookup"><span data-stu-id="82564-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="82564-142">類<xref:System.Drawing.Pen>— 用於繪製線條、勾畫形狀或渲染其他幾何表示。</span><span class="sxs-lookup"><span data-stu-id="82564-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="82564-143">類<xref:System.Drawing.Brush>— 用於填充繪圖區域，如填充形狀、圖像或文本。</span><span class="sxs-lookup"><span data-stu-id="82564-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="82564-144">類<xref:System.Drawing.Font>— 提供渲染文本時要使用的形狀的說明。</span><span class="sxs-lookup"><span data-stu-id="82564-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="82564-145">結構<xref:System.Drawing.Color>— 表示要顯示的不同顏色。</span><span class="sxs-lookup"><span data-stu-id="82564-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="82564-146">使用已創建的繪圖物件</span><span class="sxs-lookup"><span data-stu-id="82564-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="82564-147">使用上面列出的相應物件繪製所需的內容。</span><span class="sxs-lookup"><span data-stu-id="82564-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="82564-148">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="82564-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="82564-149">渲染</span><span class="sxs-lookup"><span data-stu-id="82564-149">To render</span></span>|<span data-ttu-id="82564-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="82564-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="82564-151">線條</span><span class="sxs-lookup"><span data-stu-id="82564-151">Lines</span></span>|[<span data-ttu-id="82564-152">操作說明：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="82564-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="82564-153">圖形</span><span class="sxs-lookup"><span data-stu-id="82564-153">Shapes</span></span>|[<span data-ttu-id="82564-154">如何：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="82564-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="82564-155">Text</span><span class="sxs-lookup"><span data-stu-id="82564-155">Text</span></span>|[<span data-ttu-id="82564-156">如何：在 Windows Form 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="82564-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="82564-157">影像</span><span class="sxs-lookup"><span data-stu-id="82564-157">Images</span></span>|[<span data-ttu-id="82564-158">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="82564-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="82564-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82564-159">See also</span></span>

- [<span data-ttu-id="82564-160">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="82564-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="82564-161">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="82564-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="82564-162">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="82564-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="82564-163">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="82564-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
