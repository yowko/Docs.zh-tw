---
title: HOW TO：建立繪製的圖形物件
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
ms.openlocfilehash: aa4c3e3cd21d702927b3784254184a9cd329f121
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643364"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="ce8bf-102">HOW TO：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="ce8bf-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="ce8bf-103">您可以繪製線條與圖形之前，呈現文字，或顯示和管理映像[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您需要建立<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ce8bf-104"><xref:System.Drawing.Graphics>物件代表[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪圖介面，而是用來建立圖形影像物件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="ce8bf-105">使用圖形有兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="ce8bf-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="ce8bf-106">建立<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="ce8bf-107">使用<xref:System.Drawing.Graphics>物件來繪製線條和形狀、 呈現文字，或顯示和操作的映像。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="ce8bf-108">建立圖形物件</span><span class="sxs-lookup"><span data-stu-id="ce8bf-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="ce8bf-109">圖形物件可由各種不同的方式。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="ce8bf-110">若要建立圖形物件</span><span class="sxs-lookup"><span data-stu-id="ce8bf-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="ce8bf-111">接收圖形物件的參考的一部分<xref:System.Windows.Forms.PaintEventArgs>在<xref:System.Windows.Forms.Control.Paint>的表單或控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="ce8bf-112">這通常是取得圖形物件的參考，建立控制項的繪製程式碼時。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="ce8bf-113">您也可以做的屬性取得圖形物件的同樣地，<xref:System.Drawing.Printing.PrintPageEventArgs>處理時<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件<xref:System.Drawing.Printing.PrintDocument>。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="ce8bf-114">-或-</span><span class="sxs-lookup"><span data-stu-id="ce8bf-114">-or-</span></span>  
  
- <span data-ttu-id="ce8bf-115">呼叫<xref:System.Windows.Forms.Control.CreateGraphics%2A>方法的控制項或表單，以取得參考<xref:System.Drawing.Graphics>物件，表示該控制項或表單的繪圖介面。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="ce8bf-116">如果您想要在表單或已經存在的控制項上繪製，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="ce8bf-117">-或-</span><span class="sxs-lookup"><span data-stu-id="ce8bf-117">-or-</span></span>  
  
- <span data-ttu-id="ce8bf-118">建立<xref:System.Drawing.Graphics>從繼承自任何物件的物件<xref:System.Drawing.Image>。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="ce8bf-119">當您想要變更現有的映像時，這個方法很有用。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="ce8bf-120">下列各節提供有關這些程序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="ce8bf-121">在 [小畫家] 事件處理常式的 PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="ce8bf-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="ce8bf-122">進行程式設計時<xref:System.Windows.Forms.PaintEventHandler>控制項或<xref:System.Drawing.Printing.PrintDocument.PrintPage>for <xref:System.Drawing.Printing.PrintDocument>，圖形物件可作為屬性之一<xref:System.Windows.Forms.PaintEventArgs>或<xref:System.Drawing.Printing.PrintPageEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="ce8bf-123">若要取得在繪製事件 PaintEventArgs 圖形物件的參考</span><span class="sxs-lookup"><span data-stu-id="ce8bf-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="ce8bf-124">宣告<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="ce8bf-125">指派的變數來參考<xref:System.Drawing.Graphics>物件做為一部分傳遞<xref:System.Windows.Forms.PaintEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="ce8bf-126">插入程式碼以繪製的表單或控制項。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="ce8bf-127">下列範例示範如何參考<xref:System.Drawing.Graphics>物件從<xref:System.Windows.Forms.PaintEventArgs>在<xref:System.Windows.Forms.Control.Paint>事件：</span><span class="sxs-lookup"><span data-stu-id="ce8bf-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="ce8bf-128">包含 CreateGraphics 方法</span><span class="sxs-lookup"><span data-stu-id="ce8bf-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="ce8bf-129">您也可以使用<xref:System.Windows.Forms.Control.CreateGraphics%2A>方法的控制項或表單，以取得參考<xref:System.Drawing.Graphics>物件，表示該控制項或表單的繪圖介面。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="ce8bf-130">若要建立 Graphics 物件，包含 CreateGraphics 方法</span><span class="sxs-lookup"><span data-stu-id="ce8bf-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="ce8bf-131">呼叫<xref:System.Windows.Forms.Control.CreateGraphics%2A>表單或控制項的項目，您想要呈現圖形的方法。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="ce8bf-132">從映像物件建立</span><span class="sxs-lookup"><span data-stu-id="ce8bf-132">Create from an Image Object</span></span>  
 <span data-ttu-id="ce8bf-133">此外，您可以從任何物件都衍生自建立 graphics 物件<xref:System.Drawing.Image>類別。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="ce8bf-134">若要建立 Graphics 物件，從映像</span><span class="sxs-lookup"><span data-stu-id="ce8bf-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="ce8bf-135">呼叫<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>方法，並提供您想要建立的映像變數名稱<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="ce8bf-136">下列範例示範如何使用<xref:System.Drawing.Bitmap>物件：</span><span class="sxs-lookup"><span data-stu-id="ce8bf-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
>  <span data-ttu-id="ce8bf-137">您只能建立<xref:System.Drawing.Graphics>從非索引.bmp 檔案，例如 16 位元、 24 位元和 32 位元之.bmp 檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="ce8bf-138">每個像素的非索引.bmp 檔案包含一種色彩，相較於像素為單位的色彩表來保存索引的索引的.bmp 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="ce8bf-139">繪圖和圖案和影像操作</span><span class="sxs-lookup"><span data-stu-id="ce8bf-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="ce8bf-140">在建立之後，<xref:System.Drawing.Graphics>物件可能會用來繪製線條和形狀、 呈現文字，或顯示和操作的映像。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="ce8bf-141">搭配使用的主體物件<xref:System.Drawing.Graphics>物件：</span><span class="sxs-lookup"><span data-stu-id="ce8bf-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="ce8bf-142"><xref:System.Drawing.Pen>類別，用於繪製線條、 大綱圖形，或轉譯其他幾何表示相互轉換。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="ce8bf-143"><xref:System.Drawing.Brush>類別，用於填滿圖形，例如 填滿的圖案、 影像或文字的區域。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="ce8bf-144"><xref:System.Drawing.Font>類別 — 提供什麼圖形來轉譯文字時使用的描述。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="ce8bf-145"><xref:System.Drawing.Color>結構，表示要顯示的不同色彩。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="ce8bf-146">若要使用您已建立的圖形物件</span><span class="sxs-lookup"><span data-stu-id="ce8bf-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="ce8bf-147">使用適當的物件來繪製您的需要上面所列。</span><span class="sxs-lookup"><span data-stu-id="ce8bf-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="ce8bf-148">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="ce8bf-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="ce8bf-149">若要轉譯</span><span class="sxs-lookup"><span data-stu-id="ce8bf-149">To render</span></span>|<span data-ttu-id="ce8bf-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce8bf-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="ce8bf-151">線條</span><span class="sxs-lookup"><span data-stu-id="ce8bf-151">Lines</span></span>|[<span data-ttu-id="ce8bf-152">如何：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="ce8bf-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="ce8bf-153">圖形</span><span class="sxs-lookup"><span data-stu-id="ce8bf-153">Shapes</span></span>|[<span data-ttu-id="ce8bf-154">如何：繪製外框的形狀</span><span class="sxs-lookup"><span data-stu-id="ce8bf-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="ce8bf-155">文字</span><span class="sxs-lookup"><span data-stu-id="ce8bf-155">Text</span></span>|[<span data-ttu-id="ce8bf-156">如何：Windows Form 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="ce8bf-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="ce8bf-157">影像</span><span class="sxs-lookup"><span data-stu-id="ce8bf-157">Images</span></span>|[<span data-ttu-id="ce8bf-158">如何：使用 GDI + 呈現影像</span><span class="sxs-lookup"><span data-stu-id="ce8bf-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ce8bf-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce8bf-159">See also</span></span>

- [<span data-ttu-id="ce8bf-160">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="ce8bf-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="ce8bf-161">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="ce8bf-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="ce8bf-162">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="ce8bf-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="ce8bf-163">如何：使用 GDI + 呈現影像</span><span class="sxs-lookup"><span data-stu-id="ce8bf-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
